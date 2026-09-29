---
title: "The Architecture Decisions CAIOs Cannot Delegate to Engineering"
date: 2026-09-11
tags: 
  - "ai"
  - "ai-governance"
  - "artificial-intelligence"
  - "batch-inference"
  - "chatgpt"
  - "cloud-computing"
  - "concept-drift"
  - "continuous-learning"
  - "edge-computing"
  - "embedding-tables"
  - "feature-store"
  - "iso-iec-42001"
  - "kafka"
  - "llm"
  - "machine-learning"
  - "ml-architecture"
  - "ml-systems"
  - "ml-systems-design"
  - "mlops"
  - "model-risk-management"
  - "model-serving"
  - "multi-objective-optimization"
  - "nist-ai-risk-management-framework"
  - "nvidia-triton-inference-server"
  - "offline-learning"
  - "online-inference"
  - "online-learning"
  - "production-ml"
  - "ranking-systems"
  - "recommender-systems"
  - "sr-11-7"
  - "technology"
  - "tensorflow-serving"
  - "vowpal-wabbit"
---

**How Machine Learning Systems Evolve Toward Production-Grade Architecture**

Failures in production for new AI systems usually trace back to a decision made in the initial week of a project, not to model accuracy. A model that solid scores in a notebook can fail the moment it meets real traffic, a strict latency budget, and infrastructure someone else has to keep alive at non operative hours. The shift underway across engineering organizations right now isn't about smarter algorithms. It's about treating prediction, learning, and optimization as systems problems with named, comparable trade-offs, instead of afterthoughts bolted onto a model that already works on a laptop.

This guide continues a systems-design briefing track built for two audiences at once: cloud architects and ML engineers who build these systems, and governance or risk staff who sign off on them before launch. By the end, an architect should be able to defend a batch-versus-online call in a design review without hand-waving, and a risk officer should know which question to ask about a proposed continuous-learning pipeline before it goes live, not after an incident review.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/09/chatgpt-image-sep-11-2026-09_58_51-pm.png?w=1024)

**1\. Reliability, Scalability, Maintainability, and Adaptability , The Four Constraints Behind Every Architecture Decision**

**Why It Matters**

- Every later decision in this guide traces back to one of these four properties.

- Skipping adaptability locks a team into slow, expensive full retrains later.

- Auditors now ask about these properties by name, not just about accuracy scores.

- Getting the frame wrong at the start creates rework that costs more than the original build.

**Key Terms**

- **Reliability**, the property of a system continuing to perform its intended function at an agreed level, even when hardware, software, or people fail.

- **Silent failur**e, a defect in a production ML system that produces no error message, because the system still returns a prediction, just an incorrect one.

- **Adaptability**, the built-in capacity of a system to absorb new data distributions or business requirements without a full rebuild or a service interruption.

**Explanation**

General software either works or it throws an error. An ML system has a third failure mode that general software rarely has: it keeps running, keeps returning answers, and those answers are wrong. Martin Kleppmann's _Designing Data-Intensive Applications_ frames reliability as correct behavior under adversity, and that definition still holds for ML systems. What changes is what "correct" means when there's no ground-truth label sitting next to the prediction at serving time.

Compare a checkout service to the fraud model running behind it. If the checkout service breaks, customers see a 500 error and complain within minutes. If the fraud model degrades, nobody sees an error. The page loads, a score comes back, a decision gets made, and the only sign something is wrong is a chargeback report that lands on someone's desk three weeks later. Standard uptime monitoring catches the first failure mode. It is blind to the second.

Scalability and maintainability round out the frame, and they fail for different reasons than reliability does. A system built for typical traffic can buckle at peak volume without any single component being unreliable on its own , it's the interaction between services under load that breaks. Amazon's own 2018 Prime Day event is a documented case: according to internal company documents reported by CNBC, an internal compute-and-storage system called Sable broke down under the traffic surge, causing cascading glitches across Prime, authentication, and video playback, and the company had to switch to a stripped-down fallback front page and temporarily cut off international traffic within the first fifteen minutes of the sale. The root cause wasn't a bad model or a bad line of code. It was capacity planning that didn't scale with demand, and autoscaling that needed manual intervention to catch up. Maintainability is the slower-moving version of the same risk: a system only one engineer understands is easy to run today and a liability the day that engineer leaves.

A concrete version of this: a payments team adds a new provider, and that provider's transaction records use a slightly different currency-formatting convention. The fraud model, trained on the old format, starts scoring nearly everything as low risk , not because fraud dropped, but because the input features it relies on no longer carry the signal they used to carry. The system stays up. Latency stays flat. Fraud losses climb for weeks before anyone connects the two.

The practical fix is to monitor business outcomes alongside system health: chargeback rate next to p99 latency, conversion rate next to uptime. Governance teams should require both in a model risk register before a launch gets approved, following the same logic regulators apply under guidance like the Federal Reserve and OCC's SR 11-7 , a model gets validated once and then watched continuously, not validated once and forgotten. That watching is the job of every architecture choice in the rest of this guide.

**2\. Batch and Online Prediction, Choosing How Fast an Answer Must Be**

**Why It Matters**

- The latency budget decides which serving pattern is feasible, before cost even enters the conversation.

- Choosing online prediction for a workload that didn't need it multiplies infrastructure spend for no user benefit.

- Fraud scoring, ad auctions, and safety filters have zero tolerance for batch staleness.

- Reversing this choice after a serving contract exists with downstream teams gets expensive fast.

**Key Terms**

- **Batch prediction**, a serving pattern that runs a model on a scheduled job over a bounded dataset and stores the outputs for later lookup.

- **Online prediction**, a serving pattern that computes a prediction synchronously in response to a single incoming request, typically through a REST or gRPC endpoint.

- **Latency budget**, the maximum time, usually measured in milliseconds, a system is allowed between receiving a request and returning a prediction.

**Explanation**

Batch prediction runs a model on a schedule , hourly, nightly, weekly , over every record that needs a score, then writes the results somewhere a downstream system can read cheaply: a warehouse table, a key-value store, a CSV drop. Online prediction skips the storage step and computes the answer at request time, usually inside a latency budget under 200 milliseconds. The distinction that actually matters isn't sample size. It's timing. A batch job can score one record or ten million in the same run; an online endpoint answers one request at a time, on demand.

That last point corrects a common mix-up. People assume "batch" means large-scale and "online" means small-scale, but both patterns handle either. The real trade-off is throughput against freshness. A nightly batch job can afford a heavier, more accurate model because it has hours to finish. An online endpoint has to answer in the time a user is willing to wait for a page to load, which rules out anything that can't run in a few dozen milliseconds unless the team pays for aggressive hardware and caching.

Netflix's recommendation precomputation and daily churn scoring are batch problems: staleness of a few hours costs nothing. Fraud scoring at checkout sits at the opposite end , a transaction has to clear in real time, so teams reach for online serving stacks like TensorFlow Serving or NVIDIA Triton Inference Server, usually paired with a low-latency feature store such as Redis that returns a user's recent transaction history in single-digit milliseconds instead of querying a data warehouse mid-request.

The decision rule for practitioners: ask whether a wrong-but-fresh answer is worse than a right-but-stale one. If staleness is cheap, batch is cheaper to build and run. If staleness is expensive , a fraudulent transaction that clears before the model catches it can't be undone , the cost of online infrastructure isn't optional. It's the price of the use case.

**3\. Cloud and Edge Computing , Deciding Where the Model Actually Runs**

**Why It Matters**

- Network latency, not model latency, is often what breaks a real-time feature.

- Regulated data , health records, biometric data , stays easier to keep compliant when it never leaves the device.

- Edge hardware constraints force compression trade-offs that change accuracy in ways architecture reviews should catch early.

- Offline capability is a hard requirement in some markets and difficult to retrofit late in a project.

**Key Terms**

- **Edge inference** , running a trained model directly on the device generating the data (a phone, a car, a factory sensor) instead of sending that data to a remote server.

- **Quantization** , a compression technique that reduces the numerical precision of a model's weights, commonly from 32-bit to 8-bit, to shrink model size and speed up inference on constrained hardware.

- **Data gravity** , the tendency for large volumes of data to be more expensive and slower to move than the computation that needs to run on them.

**Explanation**

Cloud inference runs a model on centralized, elastic infrastructure: GPU or TPU clusters a provider scales up and down on demand. Edge inference runs the same category of model closer to where the data gets created , on the device itself, on a local server in a factory or store, or on a regional node a telecom provider operates. The distance between compute and data is the entire story here. Every network hop adds latency that no amount of model optimization removes, typically somewhere between 80 and 300 milliseconds round-trip depending on region and provider.

Cloud wins on model size and operational simplicity; a team doesn't manage firmware updates across a million phones. Edge wins on everything a network round trip threatens. Predictive text has to respond as fast as a person types, which rules out a server call, so it runs on-device through frameworks like TensorFlow Lite or Apple's Core ML using the phone's neural engine. Google Translate keeps popular language pairs, English to Spanish for instance, on-device for the same reason, and falls back to the cloud for rarer pairs where shipping and maintaining an on-device model isn't practical.

A useful worked comparison sits inside a single company. Unlocking a phone with Face ID has to happen in a fraction of a second and must not send biometric data anywhere, so it runs entirely on-device through the Secure Enclave and Core ML. A complex customer-support query routed to a large cloud-hosted model tolerates a second or two of latency and needs far more compute than any phone carries, so it goes to the cloud. Same company, same broad category of AI feature, two different architectures , driven entirely by latency tolerance and model size.

For practitioners, two checks and a hard constraint usually settle the question. Does the feature need sub-20-millisecond response? Does most of the relevant data already live at the edge , a factory generating 70 to 90 percent of its data on the floor, for example? Either "yes" pushes toward edge. A hard requirement to work with no connectivity at all settles it immediately, regardless of what the first two checks say. Cloud stays the default everywhere else, mostly because it's operationally the path of least resistance. There's also a blunter financial argument sitting underneath the latency one: every inference pushed to a phone or an on-prem box is inference the team isn't paying a cloud provider's per-request rate for, which gives high-volume, low-margin products the strongest financial reason to invest in edge, independent of how strict the latency requirement is.

**4\. From Isolated Serving to Hybrid Prediction Pipelines , Combining Batch, Online, Cloud, and Edge**

**Why It Matters**

- Pure batch or pure online rarely survives contact with real product requirements at scale.

- Two-stage architectures let teams reserve expensive models for the cases that actually need them.

- Hybrid designs reduce blast radius: a batch-layer failure doesn't take down real-time serving.

- This pattern is what most production recommendation and ranking systems run today, not the single-model textbook version.

**Key Terms**

- **Candidate generation**, a fast, approximate retrieval step that narrows a large catalog down to a manageable shortlist before an expensive ranking model runs.

- **Two-stage architecture**, a serving pattern that separates a cheap retrieval stage from an expensive ranking stage, applying the costly model only to the shortlist the first stage produced.

- **Fallback path**, a precomputed or cached prediction a system serves when the primary, fresher prediction path is unavailable or too slow.

**Explanation**

A hybrid pipeline precomputes what it can in batch and reserves online compute for the part of the problem that actually needs freshness. Instead of treating batch or online as a single, system-wide choice, the architecture splits the prediction into stages, and each stage gets the serving pattern that fits it rather than the one the whole system defaults to.

The naive alternative fails in both directions. Running everything online means paying real-time compute cost for a catalog that mostly doesn't change minute to minute , no restaurant nearby just opened in the last ten seconds. Running everything in batch means a user's most recent clicks, often the freshest and most predictive signal available, get ignored until the next scheduled job runs.

YouTube's publicly described recommendation system is a well-known version of this pattern: a candidate-generation network narrows millions of videos down to a few hundred using cheap, precomputed embeddings, then a separate ranking network scores that shortlist using fresh, per-request features like watch history from the last few minutes. Neither stage does the other's job. The expensive ranking model never touches the millions of videos it doesn't need to score, and the fast candidate step never has to be precise enough to make the final call by itself.

A brief aside: this kind of layered trade-off , freshness against cost, one model against two , is exactly what a professional ML systems credential like AWS's Certified Machine Learning Engineer – Associate exam or Google Cloud's Professional Machine Learning Engineer certification is built to test. Passing the exam matters less than being able to defend the choice out loud in a design review, which is the real skill underneath both.

For practitioners, the build-versus-buy question shows up here directly. Standing up separate stacks for batch (a Spark job feeding a warehouse) and online (Triton or TensorFlow Serving behind a load balancer) doubles the operational surface a team has to maintain. Platforms like KServe or Ray Serve can host both stages behind one deployment and scaling model, which costs less to operate but locks the team into that platform's assumptions about how batch and online workloads share resources. Neither option is free; the choice trades operational headcount against platform flexibility.

Hybrid serving answers how a prediction gets computed and delivered. A separate question sits underneath it: how often does the model generating those predictions actually change. That's a learning-architecture decision, and it gets conflated with serving architecture more often than it should.

**5\. Offline and Online Learning , Deciding How Often the Model Itself Changes**

**Why It Matters**

- Serving architecture and learning architecture are separate decisions; teams often only design for the first.

- Concept drift erodes accuracy silently between scheduled retraining cycles.

- Online learning trades reproducibility for freshness, a trade governance staff need to understand before approving it.

- The infrastructure bar for safe online learning is higher than most teams expect going in.

**Key Terms**

- **Offline learning** , training a model on a fixed, historical batch of data, typically over multiple passes (epochs), then freezing it as a static artifact until the next scheduled retrain.

- **Online learning** , updating model parameters continuously from a live data stream, usually seeing each example once, so the model adapts within minutes instead of weeks.

- **Concept drift** , a change over time in the statistical relationship between input features and the target label, which degrades a frozen model's accuracy even though the model itself hasn't changed.

**Explanation**

Offline learning is the default most teams start with and never revisit: collect data, engineer features, train and validate against a holdout set, deploy a frozen model, monitor it until the next scheduled retrain. Online learning replaces that cycle with a continuous loop , events stream in, get turned into labeled examples, and update the model's weights in small increments, often within minutes of the event happening. GPT-3's training used batch sizes in the hundreds of thousands to millions of samples across multiple epochs; an online learner, by contrast, typically updates on microbatches of a few hundred examples and sees each one exactly once.

The trade is stability against adaptation speed. Offline learning gives strong, reproducible convergence and a clean rollback point: if a new model underperforms, revert to the last known-good artifact. Online learning gives a model that tracks a moving target , user interest, fraud patterns, seasonal demand , without waiting for the next retrain window, at the cost of far more operational complexity. A single bad batch of mislabeled events can degrade a live online model within minutes, with no equivalent of "revert to last week's build" if checkpoints aren't handled carefully.

The infrastructure gap between the two is real, not cosmetic. Offline learning needs a training job and a model registry. Online learning needs an event stream , Kafka, Kinesis, or Pulsar , a stream processor to turn raw events into labeled training examples, usually Flink or Spark Structured Streaming, and an incremental trainer running an algorithm suited to single-pass updates. Vowpal Wabbit's FTRL implementation and the Python library River are common choices here, alongside a way to push updated weights to the serving layer without downtime. Most teams that attempt online learning underestimate the last two pieces and end up with a system that updates constantly but can't be safely evaluated before those updates reach real users.

Evaluation looks different too. Offline learning leans on holdout sets, cross-validation, and standard batch metrics like AUC or precision-at-k, computed before anything reaches a user. Online learning relies mainly on live evaluation, because there often isn't a clean holdout set for a stream that never stops. Champion-challenger setups route a small slice of traffic to the new, continuously updating model and compare it against the current production version in real time, and prequential evaluation scores each prediction against its label the moment that label arrives, then rolls results up over sliding windows of an hour or a day. Skipping this step is the fastest way to ship an online learner that looks fine in aggregate and quietly underperforms for a slice of users nobody was watching.

For practitioners, the honest starting point is frequent offline retraining, not online learning. If daily or even hourly retraining keeps concept drift within an acceptable band, that's a simpler system to operate, audit, and roll back than a continuous loop. Online learning earns its complexity only when the cost of staleness , lost engagement, missed fraud, bad recommendations , clearly exceeds the cost of the streaming infrastructure it requires. Teams that skip that comparison and build online learning because it sounds more sophisticated usually end up operating a system nobody fully trusts.

**6\. From Periodic Retraining to Continuous Learning Loops , A Worked Case**

**Why It Matters**

- Continuous learning loops are how the largest consumer platforms track minute-by-minute shifts in user interest.

- The engineering cost of continuous learning is only justified when staleness has a measurable dollar cost.

- Fault-tolerance design for an online learning system looks different from fault tolerance for a stateless web service.

- This case shows offline and online learning combining, rather than one replacing the other.

**Key Terms**

- **Parameter server** , a distributed system role that stores and updates model weights, kept separate from the worker machines that compute gradients.

- **Collisionless embedding table** , a lookup structure that gives every distinct feature value, a user ID or a video ID for example, its own unique storage slot, avoiding the accuracy loss that comes from two different values sharing a slot.

**Explanation**

**Problem.** ByteDance needed a recommender for TikTok that reacted to a user's shifting interest within minutes, not at the next day's retrain. General production deep learning frameworks made that hard by design. Despite the widespread use of frameworks like TensorFlow and PyTorch, these general-purpose systems fall short here because they're built with the batch training stage and the serving stage fully separated, which blocks the model from interacting with customer feedback in real time.

**Step 1.** The team published their work as Monolith at a 2022 recommender-systems workshop. The paper, "Monolith: Real Time Recommendation System With Collisionless Embedding Table," was presented at the 5th Workshop on Online Recommender Systems and User Modeling, held alongside the 16th ACM Conference on Recommender Systems. Traditional recommenders lean on hash tables for the huge number of sparse ID features a system like this needs, and hash collisions between different IDs quietly cost accuracy. Monolith replaces that with collisionless embedding tables that give every ID feature its own unique representation, built on top of TensorFlow and supporting both batch and real-time training and serving.

**Step 2.** On top of that embedding structure, the team built a continuous training loop around a parameter-server design, where sparse embedding updates stream in constantly instead of waiting on a scheduled job. Rather than engineering for zero data loss, they measured how much reliability the system actually needed. Because only a small share of embeddings update on any given day, and user IDs are spread evenly across parameter-server machines, a single server failure touches a tiny slice of daily active users , on the order of 0.01 percent , with minimal impact on the model as a whole. That measurement let the team accept a lower redundancy budget than an "always-on, no-exceptions" design would have demanded, trading a small, bounded, well-understood risk for a simpler system.

**Result.** Published production experiments showed the collisionless embedding table producing consistent AUC gains , roughly 0.20 to 0.40 percent , over collision-tolerant baselines, and online training outperforming batch training in this recommendation setting. The system now runs in production behind TikTok's feed. The offline-trained embeddings and dense layers form the stable foundation; the online loop adds the fast-adapting layer on top.

For practitioners, the transferable lesson isn't "build a parameter server." It's the sequence: measure the actual cost of staleness first, then measure the actual failure tolerance the business can live with, and only then size the fault-tolerance budget around those two numbers instead of defaulting to the most redundant, most expensive option on the shelf.

**7\. Coupled and Decoupled Multi-Objective Optimization , One Loss Function or Many Models**

**Why It Matters**

- Almost every consumer-facing ranking system optimizes more than one goal, whether the team designed for that or not.

- A coupled, combined-loss architecture forces a full retrain every time the business wants to change a trade-off weight.

- Decoupled architectures let a spam model update weekly and a quality model update monthly, without either blocking the other.

- Reviewers examining recommender systems increasingly ask how competing objectives, like engagement against safety, get weighted and by whom.

**Key Terms**

- **Combined loss**, a single training objective built by summing two or more weighted loss terms, for example alpha times a quality loss plus beta times an engagement loss, into one number the model minimizes during training.

- **Decoupled architecture**, a design where each objective gets its own model, and the separate outputs get combined mathematically at serving time rather than during training.

- **Pareto trade-off**, the point at which improving one objective can only happen by making a competing objective worse, given the current models.

**Explanation**

A coupled architecture optimizes multiple goals inside a single model by summing weighted loss terms into one training objective , loss equals alpha times one loss plus beta times another , and training one model to minimize that combined number. A decoupled architecture instead trains a separate model per objective and combines their outputs afterward, at serving time, through a formula like alpha times one model's score plus beta times the other's.

The difference that matters is what happens when the business wants to change alpha or beta. In a coupled system, that change is baked into the weights learned during training, so adjusting the trade-off means retraining the whole model, validating it again, and redeploying , a cycle that can run days or weeks depending on the pipeline. In a decoupled system, the underlying models don't change at all; only the combination formula changes, which can happen the same afternoon and gets logged as a configuration change rather than a model release.

Neural style transfer, described by Gatys, Ecker, and Bethge in their widely cited 2015 paper on combining image content with painted style, is a clean example of the coupled pattern working well: the loss function sums a content-preservation term and a style-matching term, weighted before training starts, and a single optimization run produces the output image. That works because nobody needs to change the content-versus-style balance after the fact for a given run; each one is disposable. A newsfeed ranker sits at the opposite end. A quality model and an engagement model each ship and update on their own schedule, and a serving-layer formula combines their scores, so a product or trust-and-safety team can turn engagement weight down in response to a policy decision without retraining either underlying model.

Choosing alpha and beta, in either architecture, is a Pareto problem rather than a single right answer. Pushing engagement weight up typically buys short-term attention at the cost of average content quality, and pushing quality weight up does the reverse , there's rarely a setting where both improve at once once a model is reasonably well trained. Teams that treat this as a purely technical question tend to default to whatever weight maximizes the metric they're measured on, which is exactly why the weight itself belongs with a product or policy owner, not buried in a training script where nobody outside the ML team ever sees it.

The practical build-versus-buy call: a decoupled architecture costs more upfront , two training pipelines, two evaluation pipelines, an extra on-call rotation. That cost buys something specific: the ability to answer "what happens if we reduce the engagement weight" in an afternoon instead of a two-week retrain-and-revalidate cycle. For any system likely to face that question from a product lead, a policy team, or a regulator, the decoupled version earns its extra maintenance surface. For a one-off optimization problem nobody will need to reweight later, the coupled version is simpler, and there's no reason to pay for flexibility nobody will use.

**8\. From Combined Weights to Governed, Adjustable Ranking Systems**

**Why It Matters**

- A decoupled, documented objective architecture is what makes a ranking system auditable under frameworks like ISO/IEC 42001 or the NIST AI Risk Management Framework.

- Changes to alpha and beta weights are business decisions, not engineering decisions, and the architecture should make that separation visible.

- Teams that skip this separation can't answer basic incident-review questions after a ranking change causes a problem.

- The decisions in this guide compound , a weak choice in an early section makes every later section harder to fix.

**Key Terms**

- **Model risk register** , a governance artifact logging a model's intended use, known limitations, and monitoring plan, so a change to any component can be traced and reviewed.

- **Objective weight change log** , a record of when and why the coefficients combining separate objective models were adjusted, kept distinct from the model training log.

**Explanation**

A decoupled multi-objective system only pays off if weight changes get treated as governed events. That means logging who changed alpha or beta, when, and why, in a place separate from the model training log , because a weight adjustment doesn't look like "shipping a new model" to most engineering teams, and gets skipped in standard release tracking as a result. That gap is exactly what an auditor finds first.

This isn't a hypothetical compliance exercise. The Federal Reserve and OCC's SR 11-7 guidance, in place since 2011, requires banks to document and independently validate any model influencing a financial decision, with no carve-out for a quiet configuration change to a ranking weight. ISO/IEC 42001, the world's first AI-specific management system standard, introduced by ISO and the IEC in December 2023, and the NIST AI Risk Management Framework extend a comparable expectation well beyond banking: document changes, not just model versions, for any organization running a system with meaningful influence over people's outcomes. None of these frameworks tell a team which weight to pick. They require the team to show, on request, who picked it and why , a lower bar than getting the weight right, and one most systems still fail.

The gap shows up hardest during an incident review. A ranking system starts surfacing more sensational, lower-quality content after someone nudges the engagement weight up half a point to hit a quarterly metric. Six weeks later, when the pattern gets noticed, the team can usually pull up the model training log and confirm neither underlying model changed. What they often can't produce is a record of who changed the weight, when, or what alternative got considered , because nobody built that log, since a weight tweak never felt like a deployment worth logging.

The fix costs almost nothing next to the cost of not having it. Build the objective weight change log as a first-class artifact sitting next to the model registry, before the first decoupled multi-objective system ships, not after the first incident makes the gap obvious. That single habit is what turns a technically sound decoupled architecture into one that can survive an audit, a regulator's question, or a product postmortem , and it's the cheapest insurance in this entire guide relative to what it protects.
