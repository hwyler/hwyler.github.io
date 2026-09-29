---
title: "Tips for Implementing and Assessing AI Model Cards and Bills of Materials"
date: 2026-07-31
tags: 
  - "ai"
  - "ai-bill-of-materials"
  - "ai-governance"
  - "ai-technical-documentation"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "business"
  - "chatgpt"
  - "hernan-huwyler"
  - "iso-23894"
  - "llm"
  - "ml-bom"
  - "model-card"
  - "technology"
---

Pull ten AI model cards from ten different vendors. Read the limitations section on each one.

Most say close to nothing.

A line about ongoing monitoring. A sentence about responsible use. No numbers, no subgroup breakdown, no named owner, no version tied to the model actually running in production right now.

That gap is about to matter more than it ever has. High-risk AI systems in the EU now need technical documentation that survives a regulator's questions, not a marketing page. Auditors are starting to ask for the AI components behind a model, the machine learning bill of materials that inventories what actually went into it, not just the card that summarizes it. Most organizations still treat both documents as something you generate once at launch and never open again.

This piece covers both properly. Start with the bill of materials, the structural inventory a model card sits on top of. Then walk through what belongs in an actual model card, field by field. Then get to the ten tips that decide whether either document holds up when someone outside your team actually reads it.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/chatgpt-image-jul-31-2026-05_55_55-pm-edited.png)

## Understanding the Bill of Material, the Framework Underneath Every Model Card

A model card is a summary. The ML-BOM Machine Learning Bill of Materials is the inventory that summary is supposed to be honest about.

Think of it as the AI equivalent of a software bill of materials, the practice that got standardized industry-wide once organizations realized nobody could answer "which of our systems use this vulnerable library" without one. The ML-BOM does the same job for a machine learning model. It answers a blunter question. What, exactly, is inside this thing, and where did each piece come from.

Model identifiers pin the model to a specific, unambiguous reference, not a friendly nickname that could point to five different checkpoints.  
  
1\. Model metadata covers the basics: name, version, license, developer, purpose, and the parameters that shape behavior. Model architecture documents the network design and how information moves through it.  
  
2\. Datasets records what trained and tested the model and how that data was selected, arguably the hardest field to get right and the one most often left thin. Tokenizers and prompt templates capture how raw input gets converted into something the model actually processes, which matters more than most teams assume once a template changes without notice.  
  
3\. Hardware, software, and frameworks lists every library, runtime, and dependency the model relies on, plus the protocols used when the model operates inside a larger agent or workflow.  
  
4\. Training and testing details cover the computational environment, the hyperparameters, and the evaluation setup. Intended use and ethical considerations state what the model is for, its known limits, and the guardrails around it.  
  
5\. Environmental impact records the resource cost, increasingly a real procurement question rather than a disclosure nobody reads.

Smaller teams will not populate every one of these on day one, and that is fine. Start with identifiers and datasets, the two fields that carry the most risk if they are wrong, and build outward from there.

When constructing a machine learning bill of materials, establish the exact model identifier before you document another word. A stable, unique identifier allows your risk systems to automatically match the asset against vulnerability feeds, license databases, and dependency trackers.

A model referenced only by a friendly display name is a governance dead end. It cannot be mapped to anything systematically. I mandate that teams anchor this identifier first, even if the rest of the documentation remains thin. Once the identifier is locked, every subsequent control in the technical file has a verifiable center of gravity.

The second failure pattern occurs in data documentation. Move past treating the dataset field as a casual description, you must treat it as evidentiary documentation I routinely reject model cards that summarize data provenance with a single line stating "proprietary internal data".

That phrasing tells an auditor absolutely nothing. It obscures selection bias, masks consent violations, and hides whether your training set overlaps with your evaluation set. Require a precise accounting of the source, the collection methodology, and the known representation gaps. Most critically, demand a direct declaration confirming that your training and evaluation data are strictly disjoint.

In my practice, this single data provenance field predicts more downstream regulatory exposure than any other metric in your entire technical file.

## What Belongs in a Model Card, Field by Field

A model card lives inside the ML-BOM as the description of the model component itself. It breaks into three groups: what the model is, how it performs, and what to watch out for.

### Model Parameters

- Approach: the general learning method behind the model. Common values include supervised, unsupervised, reinforcement learning, semi-supervised, and self-supervised. This one field tells a reviewer what kind of failure modes to expect before reading another line.

- Task: the specific job the model does. Classification, regression, clustering, anomaly detection, generation, and recommendation are typical values. A card that skips this field is asking the reader to guess.

- Architecture family: the broad category of network design, such as a transformer, a convolutional network, or a recurrent network. This tells a technical reviewer what kind of behavior to expect at a glance.

- Model architecture: the specific implementation, named precisely enough that someone could locate the actual class or configuration behind it, not just a marketing label.

- Datasets: what trained and evaluated the model, cross-referenced against the ML-BOM entry rather than restated loosely.

- Inputs and outputs: the exact data types the model accepts and produces, described concretely enough to catch a mismatch before integration.

- Configuration parameters and hyperparameters: the settings that shaped training and inference, recorded so a future reviewer can tell whether a performance change came from the model itself or from a config tweak.

### Quantitative Analysis

- Benchmarks: the specific, named tests the model was measured against, not a vague reference to industry standards.

- Metrics: the measurements actually reported, defined precisely enough that two different teams would calculate them the same way.

- Performance metrics: the results themselves, broken out by the subgroups that matter for your deployment, not one blended number.

- Graphics: visual evidence, distributions, and error curves that a single summary statistic cannot show on its own.

### Considerations

- Users and use cases: who the model is actually built for, and just as important, who it is not built for.

- Technical limitations: the conditions under which the model is known to underperform, stated plainly rather than buried in a footnote.

- Performance tradeoffs: what improves and what degrades depending on how the model gets tuned or deployed.

- Fairness assessments: how the model performs across the groups relevant to your specific context, with an actual test result attached, not a claim.

- Ethical considerations: risks named specifically enough to act on, each paired with what mitigates it.

- Environmental impact: the energy and resource cost of training and running the model, increasingly a line item procurement teams ask for directly.

When I review a model card, I skip the technical specifications and go straight to the considerations section. I do this because it is almost always hollow. Your model parameters and quantitative analysis will usually look perfectly fine. That happens because those metrics are pulled straight out of the training pipeline by an automated script. They require zero additional effort. The considerations section is entirely different. It requires an actual human being to sit down, step back from the code, and critically think through how the system will behave in the real world.

Because it requires actual judgment, it is exactly the section that gets abandoned the moment an engineering team feels deadline pressure. If your schedule only gives you enough time to review a single part of a model card, make it this one. It tells you instantly whether you are looking at a real risk assessment or just a box-checking exercise.

## Field-by-Field Assessment Guide for Model Cards

Model cards started as a fix for a specific problem: AI teams were shipping models with almost no record of what the model was trained on, how it performed across different groups of people, or where it was likely to fail. A model card is the answer to that gap, a structured document meant to travel with the model itself, so that anyone deciding whether to trust it, deploy it, or build a control around it has something concrete to work from instead of a marketing page.

The approach below treats a model card the way an auditor treats a set of financial statements: every field is either present and adequate, present and thin, or missing entirely, and each of those three states tells you something different about the risk you're inheriting by using the model. A field that's simply absent isn't neutral, it's a signal that either nobody thought to document it or nobody wanted to. Reviewing a model card well means reading past the narrative language vendors tend to favor and asking, field by field, whether what's written actually supports the decision you need to make: approve this model for the use case in front of you, reject it, or send it back with a list of what's missing before a decision can be made responsibly.

The fields below are ordered the way they typically appear across widely used model card structures, starting with basic identity and working through intended use, technical characteristics, data provenance, performance, fairness, safety, and finally the operational and compliance information that governs the model once it's live. For each field, you'll find the kinds of values you should expect to see, worked examples, how to actually review it, and the vulnerabilities and risks a thin or missing entry tends to expose.

### Model Identity and Basic Details

**Typical values and examples:** A model name and version string (for example, "FraudScore-v3.2" or "Qwen-7B-Instruct"), the model family or architecture type (transformer, gradient-boosted tree, diffusion model), the developing organization, a named contact or team responsible for the model, a license type ("Apache 2.0," "proprietary, internal use only," "research use only, no commercial deployment"), and a release date alongside the date of the last update.

**How to review:** Confirm the model can be traced to exactly one accountable owner, not a generic team mailbox, and that the versioning is specific enough to distinguish this release from the last one. Check that the license terms actually match what you intend to do with the model; a "research use only" license attached to a model someone wants to put into a customer-facing product is an immediate stop, not a footnote.

**Vulnerabilities, threats, and priority:** A model with no clear owner or inconsistent versioning is a governance failure waiting to surface at the worst possible time, usually during an incident, when nobody can say with confidence which version was actually running in production. This maps directly to the cybersecurity and model drift risk categories referenced in AI assurance frameworks such as the NIST AI Risk Management Framework, and it should be treated as a release blocker for anything classified as high-risk, not a documentation nicety to fix later.

### Intended Purpose and Use Cases

**Typical values and examples:** A description of the model's purpose ("triage chatbot for customer support inquiries," "credit risk scoring for personal loan applications"), the intended task type (classification, generation, forecasting, decision support), the intended user roles (developers, clinicians, customer support agents, automated downstream systems), the intended deployment environment (cloud, on-device, specific geographic regions), and, critically, an explicit list of out-of-scope or prohibited uses.

**How to review:** Compare the stated purpose against your actual planned deployment, not against a loose paraphrase of it. If the card lists out-of-scope uses, check every one of them against what your organization or its users might realistically attempt, deliberately or not. If out-of-scope uses aren't listed at all, treat that absence as a documentation gap rather than an implicit "anything goes."

**Vulnerabilities, threats, and priority:** Misalignment between what a model was built for and what it actually gets used for is one of the most common root causes of AI-related harm on record, a research model repurposed into a safety-critical workflow, a general-purpose chatbot pressed into a role requiring domain expertise it was never evaluated on. Regulatory frameworks including the EU AI Act treat this misalignment as a primary driver of foreseeable risk to health, safety, and fundamental rights, which makes this field one of the highest-priority checks in the entire card, particularly for anything touching credit, employment, health, or law enforcement decisions.

### Model Architecture and Technical Characteristics

**Typical values and examples:** A high-level architecture description (encoder-decoder transformer, convolutional network, ensemble of decision trees), parameter count or model size, input and output formats (text, image, tabular data, bounding boxes, class probabilities), preprocessing and postprocessing steps (tokenization, normalization, output thresholding), and dependencies on external components such as embeddings, retrieval systems, or feature stores.

**How to review:** Check that stated input and output formats actually match what your integration expects; a mismatch here produces silent failures rather than obvious errors, which is worse. Look specifically at any external dependency, a retrieval index, a third-party embedding service, because that dependency now sits inside your risk boundary whether or not it was your engineering decision.

**Vulnerabilities, threats, and priority:** Complex architectures with opaque internal logic raise interpretability risk, which matters most in regulated or high-stakes decisions where a person affected by the output has a right to understand roughly why the model reached its conclusion. Undocumented external dependencies are a supply-chain risk hiding in plain sight: if the retrieval index or embedding provider changes or degrades, your model's behavior changes with it, and nothing in your own testing history would have caught it.

### Training Data Description and Provenance

**Typical values and examples:** Data sources (internal transaction logs, licensed third-party datasets, public web-scraped corpora, user-generated content), the time period the data covers, geographic and demographic coverage, collection methods (scraping, sensor data, manual annotation, purchased datasets), known gaps or exclusions, and governance notes covering consent and legal basis for use.

**How to review:** Ask specifically whether the data reflects the population you'll actually be applying the model to. A fraud model trained predominantly on urban transaction patterns and deployed against a largely rural customer base has a documented representativeness gap the moment you check this field, regardless of how strong its aggregate accuracy numbers look. Flag vague provenance statements like "collected from the internet" as a finding in their own right, not as an acceptable summary.

**Vulnerabilities, threats, and priority:** This is where the majority of bias and fairness failures originate, since a model can only be as representative as the data it learned from, and it's also where privacy exposure tends to start, since personal or sensitive data folded into a training set without a documented legal basis becomes a downstream liability the moment the model memorizes and later reproduces it. Widely cited work on model documentation, including the original Model Cards for Model Reporting proposal by Mitchell and colleagues, and the EU AI Act's technical documentation requirements under Annex IV, both treat training data provenance as one of the two or three fields that most determines whether the rest of the card can be trusted.

### Evaluation Data and Test Conditions

**Typical values and examples:** A description of the evaluation dataset's source, size, and coverage, an explicit statement of whether it overlaps with training data, the test environment (offline benchmark, simulated environment, limited pilot deployment), and a stated rationale for why that particular evaluation set was chosen.

**How to review:** The single most important check here is independence: confirm the evaluation data doesn't overlap with the training data, because contamination between the two produces performance numbers that look excellent and mean almost nothing about real-world behavior. Then check whether the evaluation set actually reflects your deployment distribution, language, region, user population, rather than a convenient benchmark that happened to be available.

**Vulnerabilities, threats, and priority:** Undetected train-test contamination is a data leakage risk that inflates every downstream metric in the card, meaning a reviewer who trusts the accuracy numbers without checking this field is building a risk assessment on a number that was never real. Evaluation on a narrow or non-representative dataset produces a second, quieter failure: strong reported performance that simply doesn't transfer to your actual users, a gap that typically isn't discovered until the model is already live and something has gone wrong.

### Performance Metrics and Results

**Typical values and examples:** Aggregate metrics appropriate to the task, accuracy, F1 score, area under the ROC curve, BLEU or ROUGE for generation tasks, mean absolute error for regression, along with task-specific figures like precision and recall for the classes that matter most, latency, and throughput. Stronger cards also report robustness under noise or adversarial conditions and confidence or uncertainty estimates.

**How to review:** Match the reported metric to the actual cost of errors in your use case, a high overall accuracy figure can hide an unacceptable false-negative rate on the one category that matters most, a missed fraud case or a missed medical finding, so ask for the specific metric, not just the headline number. Treat a single aggregate figure reported without any breakdown or confidence interval as an incomplete answer rather than a final one.

**Vulnerabilities, threats, and priority:** A model with strong average performance but no reported robustness or calibration information carries hidden risk in exactly the conditions where a control failure would matter most, noisy inputs, distribution shift, adversarial manipulation. This is a well-established gap in AI assurance literature: metrics chosen and reported without transparent methodology or uncertainty bounds create false confidence, and that false confidence is precisely what leads organizations to under-resource the human oversight a model actually needs.

### Disaggregated Performance and Fairness Considerations

**Typical values and examples:** Performance metrics broken out by relevant subgroup, demographic categories, language, geography, device type, alongside fairness metrics such as disparate impact ratio or differences in false positive and false negative rates across groups, and a narrative explanation of any observed disparities and what was attempted to address them.

**How to review:** Look specifically for whether the subgroups tested match the population your deployment will actually affect, and check the sample size behind each subgroup figure; a fairness metric computed on a handful of examples from an underrepresented group carries far less statistical weight than the headline percentage suggests. A commonly cited screening threshold in employment and lending contexts, the four-fifths rule, treats a selection rate for any group below 80% of the highest-performing group's rate as a signal warranting further review, a useful sanity check even outside those specific regulatory contexts.

**Vulnerabilities, threats, and priority:** Aggregate metrics reported without disaggregation routinely conceal serious disparities that only become visible once you split the results by group, which is exactly why this field carries some of the highest regulatory weight in frameworks like the EU AI Act for any system affecting access to credit, employment, housing, or public services. A card that reports strong overall accuracy but skips this section entirely should be treated as materially incomplete for any use case touching individual people, not as a model that simply "didn't need it."

### Known Limitations, Failure Modes, and Risk Statements

**Typical values and examples:** Documented weaknesses such as degraded performance on rare classes, unsupported languages, or out-of-domain inputs, specific behavioral failure modes for generative models, fabricated citations, sycophantic agreement with a user's incorrect premise, repetitive output loops under certain decoding settings, and explicit statements about conditions likely to produce unreliable output.

**How to review:** Read this section for specificity rather than reassurance. A card stating "the model may occasionally produce inaccurate information" is not meaningfully different from saying nothing, whereas a card describing the specific conditions under which inaccuracy spikes, long documents beyond a certain token count, ambiguous multi-step reasoning, out-of-domain queries in an underrepresented language, gives you something you can actually build a control around.

**Vulnerabilities, threats, and priority:** This section is the single richest source of information for building your own risk register entries, because it's the vendor or development team telling you, in their own words, where the model is expected to break. A card with a suspiciously clean "no known major limitations" statement on a capable, general-purpose model should be treated with active suspicion rather than comfort; every capable model has documented failure modes in the broader research literature, so their absence here usually means nobody looked hard enough, not that none exist.

### Safety, Security, and Adversarial Considerations

**Typical values and examples:** Documented exposure to known AI-specific threats, prompt injection for language models, adversarial example evasion for classifiers, model inversion or membership inference against models handling sensitive training data, along with the specific defenses in place, input and output filtering, rate limiting, access controls, and a statement of residual risk that remains even after those defenses are applied.

**How to review:** Compare the threats the card discusses against your own deployment's actual attack surface. A model exposed to untrusted public input carries a fundamentally different risk profile than the same model running behind an internal, authenticated interface, and the card should reflect that context, not a generic list copied across every deployment scenario. Where the card claims a mitigation is in place, ask what evidence supports that claim, a red-team test result, an adversarial benchmark score, rather than accepting the mitigation's existence as self-evidently sufficient.

**Vulnerabilities, threats, and priority:** For any model accepting input from users you don't fully control, this is one of the two or three fields that most determines deployment risk, alongside training data provenance and intended use. A capable generative model with no adversarial testing or prompt injection discussion documented anywhere in its card should be assumed vulnerable by default rather than assumed safe by omission, a principle consistent with how established security assessment practice treats undocumented attack surfaces in conventional software.

### Privacy and Data Protection Considerations

**Typical values and examples:** A statement on whether personal or sensitive data was used in training, data minimization and anonymization practices applied, privacy risk assessments covering re-identification or unintended memorization, and compliance notes addressing data-subject rights where applicable.

**How to review:** Even when the card states no personal data was directly stored, check whether the model could still expose privacy risk indirectly, through memorization of rare training examples or through inference of sensitive attributes from otherwise non-sensitive inputs. This distinction, between a model storing data and a model that can be made to reveal information about the data it learned from, is frequently missed in a quick read of this section.

**Vulnerabilities, threats, and priority:** Membership inference and model inversion are established, demonstrated attack classes against models trained on sensitive data, meaning the absence of any privacy discussion in a card for a model trained on personal information should trigger an internal privacy impact assessment before deployment proceeds, not after. This maps directly onto data protection impact assessment expectations found in privacy regulation generally and is treated as a required documentation element under the EU AI Act's technical file requirements for high-risk systems.

### Human Oversight, Control, and Operational Use

**Typical values and examples:** A stated oversight model, fully automated decision-making, human-in-the-loop review of every output, or human-on-the-loop spot-checking, guidance for how a human reviewer should interpret model outputs, defined escalation thresholds, and any override or manual correction mechanism available to operators.

**How to review:** Check that the recommended oversight level actually matches the stakes of the decision the model informs; a model influencing credit or medical decisions with a card recommending only spot-check review, rather than review of every output, is a mismatch worth escalating regardless of how strong the model's other metrics look. Confirm the guidance given to human reviewers is concrete enough to act on, not a generic instruction to "use judgment."

**Vulnerabilities, threats, and priority:** Ambiguous or missing oversight guidance is a leading contributor to automation bias, the tendency of a human reviewer to defer to a model's output even when they have reason to question it, simply because no clear threshold was given for when to intervene. Regulatory frameworks increasingly treat documented, technically enforced human oversight as a non-negotiable requirement for high-risk AI systems rather than a best practice, which makes a thin entry here a strong candidate for a formal finding rather than a minor gap.

### Monitoring, Maintenance, and Lifecycle Management

**Typical values and examples:** A stated monitoring plan covering which metrics are tracked and how often, defined triggers for retraining, a documented version history summarizing what changed between releases, and criteria for eventually retiring or replacing the model.

**How to review:** Confirm the monitoring plan tracks something meaningful, actual drift in input distribution or output accuracy, rather than only infrastructure uptime, which tells you the system is running but says nothing about whether it's still behaving correctly. Check whether the documentation itself has a stated update cadence tied to the model's own version history, since documentation that isn't updated alongside the model quietly becomes inaccurate.

**Vulnerabilities, threats, and priority:** Every model degrades over time as the world it operates in shifts away from the distribution it was trained on, so the absence of a monitoring and retraining plan is itself an operational risk, not a placeholder to fill in later. This corresponds to the model drift risk category tracked across most AI assurance frameworks, and for any model influencing a recurring, high-volume decision, it deserves the same review rigor as the model's original performance metrics.

### Ethical, Societal, and Impact Considerations

**Typical values and examples:** A discussion of potential societal effects, labor displacement, misinformation risk, environmental cost, alongside a named framework of ethical principles the development team applied, fairness, transparency, accountability, and concrete recommendations for responsible use.

**How to review:** Assess whether the stated recommendations are specific enough to act on rather than generic statements of good intent, and consider whether the model could enable harmful uses even outside its stated intended purpose, a general-purpose generation model capable of producing convincing synthetic media, for instance, regardless of what its intended use case was.

**Vulnerabilities, threats, and priority:** This section matters most for powerful, widely deployable models where the realistic misuse surface extends well beyond the documented intended use, and its absence in a capable model should be read as a gap worth raising with whoever is responsible for use-case approval, not dismissed as a soft or unquantifiable concern.

### Environmental Considerations

**Typical values and examples:** Estimated energy consumption at different lifecycle stages, training, fine-tuning, and inference, the energy source powering that consumption, and reported carbon dioxide equivalent figures alongside any claimed offsets.

**How to review:** Where figures are reported, check whether they cover just training or the full lifecycle including ongoing inference, since a model queried millions of times a day can accumulate an inference-phase footprint that dwarfs its one-time training cost. Treat the complete absence of any environmental disclosure on a large-scale model as a documentation gap rather than an indication the cost doesn't exist, since most providers currently under-disclose this figure rather than having genuinely measured zero impact.

**Vulnerabilities, threats, and priority:** This is a lower-severity field relative to safety, fairness, or privacy, but it is an increasingly explicit regulatory disclosure expectation for general-purpose AI models under emerging AI-specific regulation, and its absence is worth noting in any formal technical file review even where it doesn't block a deployment decision on its own.

### Compliance and Regulatory Alignment Notes

**Typical values and examples:** A statement of whether the model has been assessed against a specific regulatory classification, such as a high-risk categorization under applicable AI regulation, references to harmonized standards applied during development, and pointers to more detailed supporting technical documentation or risk assessments held elsewhere.

**How to review:** Treat a high-level compliance claim as a pointer, not a conclusion, always ask for the underlying documentation it references rather than accepting the summary sentence as sufficient evidence on its own. Verify that any cited standard or framework is actually applicable to your jurisdiction and use case rather than assumed to transfer automatically from wherever the model was originally developed and assessed.

**Vulnerabilities, threats, and priority:** A vague compliance statement unsupported by an underlying technical file is one of the more common findings in a rigorous model card review, and for any system likely to fall under a high-risk classification in your operating jurisdiction, this gap should be resolved before deployment, not tracked as an open item to close later.

### Caveats and Recommendations for Deployers

**Typical values and examples:** A consolidated list of known caveats already discussed elsewhere in the card, paired here with concrete deployment guidance, recommended confidence thresholds, suggested human review checkpoints, monitoring configuration recommendations, and rate-limiting guidance.

**How to review:** Cross-reference every caveat listed here against the corresponding evidence earlier in the card; a caveat mentioned in this closing section without a matching discussion in the performance or limitations fields is a sign the documentation was assembled inconsistently rather than derived from a single coherent evaluation. Check that the recommendations are specific and testable, "implement human review for low-confidence outputs" is actionable, "use responsibly" is not.

**Vulnerabilities, threats, and priority:** This section is where an incomplete card most often reveals itself, because vague or generic recommendations here usually indicate the underlying evaluation work was equally generic. Treat a strong, specific, evidence-backed recommendations section as one of the better proxies available for judging whether the rest of the card can be trusted, and a thin one as grounds to request the underlying technical assessment before relying on the model for any consequential decision.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/chatgpt-image-jul-31-2026-06_00_59-pm.png?w=1024)

## Field Reference Table for Model Card Considerations

The table below walks through every chapter and field found in the source considerations block, ordered within each chapter from the fields that appear most consistently across model cards to the more specialized, model-specific entries that show up less often. Use it as a companion to the review guidance above: this version focuses on exactly what values each field can take and what each one is documenting.

**How to read this table in practice:** start at the top of each chapter and work down. The fields near the top of each section are the ones you should expect to find populated in nearly every reasonably complete model card, their absence is a meaningful gap. The fields toward the bottom of each section, the architecture-specific quirks, the granular fairness methodology, the per-lifecycle-stage energy breakdown, show up mostly in the more mature, detailed cards. Their presence is a positive signal about how seriously the model's governance was handled; their absence isn't automatically disqualifying, but it does mean you're working with less information than you could have, and that gap should be logged, not silently assumed away.

| Chapter | Field | Title | Potential Values (with examples) | Explanation |
| --- | --- | --- | --- | --- |
| **1\. Users and Use Cases** | Users | Intended User Roles | Role labels such as "Academic Researcher" "Enterprise Security Analyst," "Edge Device Engineer," "Local AI Enthusiast / Privacy-First User" | Names the categories of people expected to interact with or deploy the model. This is the anchor field for the whole section, every use case listed should trace back to at least one of these roles. |
|  | Use Cases | Concrete Use Case Descriptions | Free-text scenarios, e.g., "real-time code completion within an IDE," "translating business content while preserving tone and cultural nuance," "low-latency triage chatbot escalating complex queries," "summarizing long-form research using a 128K context window," "on-device visual perception paired with natural-language navigation," "analyzing internal security logs without data leaving the firewall" | Describes specific, real applications tied to the roles above. The more concrete the use case (naming a context window size, a deployment environment, a data-sensitivity constraint), the more useful the field is for matching the model against your actual deployment. |
| **2\. Technical Limitations** | Hallucination and Inaccuracy | Plausibility Over Accuracy | Descriptive text, e.g., "prioritizes plausible-sounding text over factual accuracy (sycophancy)" | The most universally documented limitation across generative models. Flags that fluent output is not the same as correct output. |
|  | Context Window Constraints | Memory Boundaries | Token limits, e.g., "32,768 native tokens," "128K via extended scaling" | Describes how much text the model can process or "remember" in a single interaction before earlier content is dropped or degraded. |
|  | Reasoning and Math Deficiencies | Multi-Step Logic Gaps | Descriptive text on struggles with complex, multi-step logic or arithmetic | Common across LLM families regardless of size; signals where a model needs external tools (calculators, solvers) rather than being trusted to reason unaided. |
|  | Knowledge Cutoff | Frozen-in-Time Knowledge | A date or version marker, e.g., "training data through \[month/year\]" | The model has no access to events or information after this point unless paired with retrieval or search tools. |
|  | Opacity (Lack of Traceable Reasoning) | Black-Box Architecture | Descriptive text on inability to trace how a specific output was generated | Explains why standard explainability methods struggle with large, complex architectures, relevant to any interpretability requirement. |
|  | Probabilistic Output Inconsistency | Non-Deterministic Output | Descriptive text, e.g., "same prompt yields different results across seeds or context carryover" | Notes that outputs aren't guaranteed to repeat exactly, which matters for testing, auditing, and reproducibility expectations. |
|  | Bias Reinforcement | Training-Data Bias Amplification | Descriptive text, often flagging synthetic-data effects | Explains how a model can replicate or amplify biases in its source data, a risk that has grown as synthetic training data use has increased. |
|  | _(Model-specific examples)_ | Architecture-Specific Quirks | E.g., "Greedy Decoding Degradation," "Native Context Window Boundaries," "Synthetic Data 'Sanding' Effects" (model collapse on rare cases), "Thinking Mode History Overhead" | These appear less consistently across cards because they're specific to a model family's architecture or training method rather than universal LLM limitations, still important, but narrower in applicability. |
| **3\. Performance Tradeoffs** | Accuracy vs. Interpretability | Explainability Cost | Descriptive text, e.g., "complex models are black boxes; simpler models sacrifice performance for transparency" | The most commonly cited tradeoff, relevant to any regulated or high-stakes use where explainability is a requirement, not a nice-to-have. |
|  | Accuracy vs. Speed/Latency | Inference Time Cost | Descriptive text, sometimes with numeric latency figures | Highly accurate models often cost more compute per response; production systems frequently favor a faster, slightly less accurate model. |
|  | Bias vs. Variance (Generalization) | Overfitting/Underfitting Balance | Descriptive text on flexible (low-bias, high-variance) vs. simple (high-bias) models | Explains why a model that performs well on training data may not generalize, or why an overly simple model misses real patterns. |
|  | Complexity vs. Resource Constraints (Cost) | Compute/Budget Tradeoff | Descriptive text, sometimes with hardware specs (GPU/CPU requirements) | Larger models need more data, training time, and compute, a direct cost and deployment-feasibility constraint. |
|  | Precision vs. Recall | False Positive/Negative Balance | Descriptive text, sometimes with numeric thresholds | For classification tasks, states whether the model is tuned to minimize false positives or false negatives, critical for fraud, medical, or safety contexts. |
|  | _(Model-specific examples)_ | Family-Specific Tradeoffs | E.g., "Intelligence Plateau in Domain-Specific Tasks," "Enhanced Quantization Sensitivity," "Context Window Consistency," "Conciseness vs. Contextual Nuance," "Agentic Capability Limitations," "Hardware Efficiency vs. Throughput," "Decoding Strategy Rigidity" | These are narrower, model-size or architecture-specific tradeoffs. They appear in more detailed cards and matter most when comparing versions within the same model family (e.g., 7B vs. 32B parameter variants). |
| **4\. Ethical Considerations** | Name | Consideration Name/Description | Short label plus expanded description, e.g., "Algorithmic and Cultural Bias," "Vulnerability to Adversarial Attacks (Jailbreaking)," "Misinformation or Hallucinations," "Privacy/PII Content Leakage," "Environmental Impact (Inference Energy)," "Instruction Misalignment" | Names a specific ethical risk tied to the model, since there's no universal standard list, well-written cards use this field to add clarifying context beyond the label itself. |
|  | Mitigation Strategy | Recommended Mitigation | Descriptive text, e.g., "use RLAIF and rule-based rewards," "implement an input/output safety filter," "use RAG to ground responses," "deploy locally with PII scrubbing," "apply 4-bit quantization to reduce power draw," "standardize output formats with system prompts" | Pairs each named risk with a concrete, actionable step. A risk listed without a paired mitigation should be read as an incomplete entry. |
| **5\. Fairness Assessments** | Group At Risk | At-Risk Group Identification | Descriptive text, e.g., "people identified by race, gender, or disability status," "non-English/non-Spanish speakers," "speakers of regional dialects or specific geographic regions" | Identifies the specific population the assessment is evaluating for disparate treatment. This is the field that determines whether the rest of the assessment is even relevant to your deployment population. |
|  | Harms | Documented Harm | Descriptive text, e.g., "discriminatory outcomes in task assignment," "quality-of-service harm: oversimplified or hallucinated answers in non-primary languages" | States the specific negative outcome observed during testing, ideally with a concrete example rather than a generic statement. |
|  | Mitigation Actions | Fairness Mitigation | Descriptive text, e.g., "RLAIF and rule-based rewards aligned to legal standards," "multilingual supervised fine-tuning on reasoning tasks" | The corrective action recommended or applied to reduce the documented harm. |
|  | _(Underlying methodology, less commonly itemized directly)_ | Assessment Method | Data Bias Auditing, Disaggregated Performance Metrics, Impact Assessments, Adversarial Testing, Algorithmic Fairness Interventions | These describe how the fairness assessment was conducted across the model lifecycle. More rigorous cards name which of these methods were used; many cards only report the outcome (`groupAtRisk`/`harms`/`mitigationStrategy`) without specifying methodology, which is itself worth flagging as a gap. |
| **6\. Environmental Considerations, Energy Consumption** | Activity | Lifecycle Stage | One of: design, data-collection, data-preparation, training, fine-tuning, validation, deployment, inference, other | Identifies which phase of the model lifecycle the reported energy figure applies to. Training is reported most often; inference (the ongoing, per-query cost) is reported far less often despite frequently being the larger cumulative cost. |
|  | Energy Sources | Energy Source Type | One of: coal, oil, natural-gas, nuclear, wind, solar, geothermal, hydropower, biofuel, unknown, other | States what generated the electricity used for that activity, central to any claimed environmental benefit. |
|  | Energy Description | Provider Identity | Organization name, address, and description, e.g., a named data center and its location | Documents who supplied the energy, supporting traceability and verification of the reported figures. |
|  | Activity Energy Cost | Total Energy Cost | Numeric value in kilowatt-hours (kWh) | The raw energy consumption figure for the activity, the base number every other environmental figure derives from. |
|  | CO2 Cost Equivalent | Carbon Cost (Debit) | Numeric value in tonnes of CO2 equivalent (tCO2eq) | The greenhouse gas impact of the reported energy cost, standardized so it can be compared across energy sources and activities. |
|  | CO2 Cost Offset | Carbon Offset (Credit) | Numeric value in tonnes of CO2 equivalent (tCO2eq) | Any offset applied against the debit above. Reported least consistently of all environmental fields, and worth checking against the debit figure rather than accepting the net claim at face value. |

## The 10 Implementation Tips That Actually Decide Card Quality

Everything above is structure. This is judgment, the part that decides whether a completed card actually protects you or just looks complete.

I have sat in enough of these reviews to recognize the pattern by now. Someone asks for the fairness section. Someone says it is coming in the next revision. The next revision never quite arrives, and six months later the card still says exactly what it said at launch.

1. Treat a missing field as a finding, not a blank.

A card with no fairness section, no adversarial testing discussion, or a suspiciously clean "no known limitations" line rarely means the system is clean. Far more often it means nobody looked, or somebody looked and did not want to write down what they found. Every review should end with an explicit list of what is absent, not only an assessment of what is present. Silence is not neutral. Silence is a finding waiting to be named.

2. Map every field to the regulatory requirement it satisfies.

A field like intended purpose does more than tidy up documentation. Under the EU AI Act, it directly satisfies Article 13(3)(b)(i). A field like disaggregated performance satisfies a separate obligation in the same article. Reviewing or producing a card without this mapping means nobody can say with confidence whether it would survive a conformity assessment. Build the mapping once, per use case category, and reuse it. Do not rebuild it from scratch every time.

3. Never accept an aggregate metric without asking for the subgroup breakdown.

This is the single highest-leverage check in the entire process. A strong overall accuracy number can hide a disparity that fails badly for one specific group, language, region, or device type, and that gap only becomes visible once someone insists on the breakdown. If the card reports one number and stops there, the review is incomplete. Not finished. Incomplete.

4. Require every named risk to carry a paired, evidenced mitigation.

Name plus mitigation is the right structure. A mitigation listed without supporting evidence, a test result, a red team score, an attack success rate, is a promise dressed up as a control. A mitigation only counts once it is paired with a measurable threshold that proves it actually works.

5. Check for train test contamination before trusting any performance number.

This is the most commonly skipped verification step, and one of the most consequential. If evaluation data overlaps with training data, every metric downstream of that overlap is inflated. A card that does not explicitly state the two sets are disjoint should be treated as unverified, not assumed clean. This one check protects you from building risk decisions on numbers that were never real.

6. Version the model, the prompt, the retrieval source, and the evaluation together, and retest after any one of them changes.

A model card is not a one-time artifact. Swap a model version, adjust a prompt template, or update a retrieval index, and the prior evidence stops applying even when nothing else in the card changes. A card that does not tie its results to a specific, dated version combination is documenting a system that no longer exists by the time anyone reads it.

7. Assign a named owner and a review cadence to the card itself, not only to the model.

A model card that is not refreshed on a defined schedule becomes actively misleading. A reader has no way to tell stale information from current information just by looking at it. Attach an owner. Set a quarterly review at minimum, more often for anything that moves fast. That is the difference between a static PDF and a living control, and it is the difference that actually holds up under audit.

8. Match the human oversight level to the actual stakes of the decision, not to a generic default.

A card recommending a spot check for a model that influences credit, medical, or employment decisions is a mismatch worth escalating on its own, regardless of how good the model's other metrics look. This is one of the fastest checks in a review because it needs no technical evaluation. It only needs a comparison between the stated oversight mechanism and the real consequence of the model being wrong.

9. Remember the model is not the system. Evaluate the integration, too.

A vendor's safety testing on a base model says very little about what happens once that model is wired into your product, with your retrieval layer, your tool access, your identities and permissions attached. The most dangerous vulnerabilities usually live in that integration layer. A card review that stops at the vendor's own documentation and never asks what your architecture adds to the attack surface has covered half the assessment at best.

10. Prefer quantitative security and robustness metrics over narrative safety claims.

"The model has been safety tested" is not a data point. An attack success rate against a defined adversarial benchmark, a prompt injection success rate, a membership inference score, these are data points, because they are measurable, comparable across versions, and provably false if they turn out to be wrong. Cards built around reassurance instead of numbers should go back for the underlying test results before anyone relies on them for anything that matters.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/chatgpt-image-jul-31-2026-06_17_52-pm.png?w=1024)

## Risk and Control Practices for Model Cards

Four habits apply across every stage above, from the ML-BOM through the card through the ten tips. None of them are about the documents themselves. They are about what keeps the documents honest once the initial review is over.

I constantly see teams treat the model card and the ML-BOM as two completely isolated chores. Don't do this. Wire them to each other. If I read a card that references a dataset completely missing from the BOM, or a BOM that contradicts the card’s own training specs, I know instantly that you lack a single source of truth. Pick one artifact to be your system of record. Force your tooling to generate the other from it.

Here is a hard reality about engineering culture. The people who built the model are the absolute worst people to document its flaws. This is just the natural byproduct of deadline pressure mixing with builder's optimism.

Hand the limitations section to someone entirely outside the build team. A fresh, slightly cynical set of eyes on that one specific section catches more actual exposure than a second pass on the entire technical file. You also need to stop leaving fields blank. If you leave a box empty, the auditor reviewing it later cannot tell if you skipped it on purpose or simply forgot it existed. Writing "Not applicable; this model has no user-facing output" is a highly defensible control. A blank space is just an unquantified liability. Document your intentional exclusions so nobody has to hunt down the original engineer a year later to figure out what happened.  
  
Finally, look at how you actually store these things. A model card passed around as a PDF attachment or a slide deck is useless. The moment it hits someone’s downloads folder, it stops being a control and turns into a rumor about what the model used to be.

Store both documents as versioned, machine-readable records anchored directly to your model registry. When you can run a diff across versions to see exactly what changed between releases, you have a surviving audit trail. Anything else is just paperwork.

## Why Model Cards and AI Bills of Materials Matter for Governance Roles

When an organization adopts AI, the model card and the AI bill of materials are the foundational documents that make the system legible to anyone who wasn't in the room when it was built. Without them, governance roles are flying blind. Here's why each role specifically depends on them.

## Auditors

Auditors need an artifact to test against. A model card gives them the declared intended use, performance metrics, training data provenance, and known limitations.Tthese are the claims they verify. If the card says the model achieves 94% accuracy on a specific benchmark, the auditor re-runs that benchmark. If the card says training data was deduplicated and PII-filtered, the auditor checks the pipeline logs.

The AI BOM goes deeper: it lists every component in the supply chain, such as pre-trained base models, third-party datasets, open-source libraries, APIs, and firmware versions. This is what makes a security audit or SOC 2 examination possible. An auditor cannot assess supply-chain risk (a poisoned dependency, a license violation, a deprecated vulnerable library) without a complete inventory. Under the EU AI Act, [Annex IV §2(a)](https://ai-act-service-desk.ec.europa.eu/en/ai-act/annex-4) explicitly requires documentation of "recourse to pre-trained systems or tools provided by third parties and how those were used, integrated or modified." The BOM is that documentation.

Without these documents, an audit becomes anecdotal, spot-checking what the auditor happens to think of, rather than systematic.

## Compliance Officers

Compliance officers map organizational practice to legal obligations. The EU AI Act's [Article 13](https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-13) requires that high-risk AI systems be accompanied by instructions for deployers covering provider identity, system capabilities and limitations, accuracy metrics, human oversight measures, and data specifications. The model card is the natural container for most of that information; the BOM covers the supply-chain transparency requirements.

Compliance officers also need to demonstrate that the organization performed due diligence before deployment. If a regulator asks "did you know this model was trained on data scraped without consent?" or "did you know the base model had a known prompt-injection vulnerability?". The answer needs to be "yes, we documented it in the model card and BOM, assessed the risk, and applied mitigations." Ignorance is not a defensible position under the AI Act's risk-based framework ([Article 9](https://ai-act-service-desk.ec.europa.eu/en/ai-act/article-9) requires a documented risk management system).

The model card also supports the conformity assessment process. [Annex IV §7-8](https://ai-act-service-desk.ec.europa.eu/en/ai-act/annex-4) requires listing harmonised standards applied and attaching the EU declaration of conformity. These reference the technical documentation, which the model card and BOM feed into.

## Risk Managers

Risk managers quantify and prioritize. They need to know what can go wrong, how likely it is, and how severe the impact would be. The model card surfaces known failure modes, fairness disparities, hallucination rates, and adversarial vulnerabilities , these are the risk inputs. The risk review columns in the checklist you just received (evaluation methods, control checks, vulnerability coverage) are essentially a risk register in spreadsheet form.

The BOM adds a dimension that traditional risk management hasn't fully grappled with: software supply-chain risk in ML systems. A model can inherit vulnerabilities from its base model (e.g., a fine-tuned model that inherits a data-poisoning susceptibility), from its training data (e.g., a dataset containing copyrighted or consent-violating material), or from its inference infrastructure (e.g., a vulnerable inference server). The BOM makes these transitive risks visible and manageable.

Risk managers also need the model card's post-market monitoring plan ([Annex IV §9](https://ai-act-service-desk.ec.europa.eu/en/ai-act/annex-4)) to set up ongoing risk surveillance, drift detection, incident response, performance degradation alerts.

## CAIOs Chief AI Officers

CAIOs sit at the intersection of strategy, accountability, and governance. They are typically the person who signs off on AI deployment decisions and who answers to the board, regulators, and customers. They need the model card and BOM for three reasons:

1. **Strategic visibility**: The CAIO needs to know what AI systems exist in the organization, what they do, what data they depend on, and what risks they carry. The model card and BOM are the inventory that enables portfolio-level decisions: which models to invest in, which to retire, which to restrict.

3. **Accountability**: Under the EU AI Act, the provider (and in many cases the deployer) bears legal responsibility. If something goes wrong, such as a discriminatory outcome, a data breach, a hallucination that caused harm, the CAIO is the person who will be asked "what did you know and when did you know it?" The model card is the record of what was known at deployment time.

5. **Cross-functional alignment**: The CAIO orchestrates auditors, compliance, risk, engineering, and legal teams. The model card and BOM are the shared artifact that all these functions reference. Without a common document, each team maintains its own partial picture, gaps go unnoticed, and accountability diffuses.

## Related Reading

[Prof. Hernan Huwyler](https://linkedin.com/in/hernanwyler) writes regularly on AI governance, evidence, and audit-ready documentation. A few pieces that connect directly to the ground covered here:

- [How ISO 24970 and prEN 18229-1 Turn Post-Deployment Chaos Into Auditable Evidence](https://hernanhuwyler.wordpress.com/2026/06/28/how-iso-24970-and-pren-18229-1-turn-post-deployment-chaos-into-auditable-evidence/), on what actually counts as evidence once an AI system is live, not just at launch.

- [The prEN 18286 Reality Check: Ditch Generic AI Governance](https://hernanhuwyler.wordpress.com/2026/06/17/the-pren-18286-reality-check/), on why controls that look complete on paper collapse the moment someone asks for proof they operate.

- [Rules for AI Use, Accountability, BYOAI, Safety by Design, and Content Provenance](https://hernanhuwyler.wordpress.com/2026/03/16/rules-for-ai-use-accountability-byoai-safety-by-design-and-content-provenance/), on the policy layer that sits above the documentation covered in this piece.

- [Stop Chasing Evidence to Start Informing Decision-Making](https://mydailyexecutive.blogspot.com/2026/07/stop-chasing-evidence-to-start.html), on why evidence collection without quantified analysis behind it stops being useful to anyone outside compliance.

## Key References

- EU AI Act, Article 11 and Annex IV, technical documentation requirements for high-risk AI systems, enforceable from August 2, 2026.

- EU AI Act, Article 13, transparency and instructions for use, the article behind the field-to-requirement mapping in tip two.

- NIST AI Risk Management Framework and its Generative AI Profile, for the broader risk categories a model card should reflect.

- ISO/IEC 42001, the AI management system standard, for how card review fits into an ongoing governance program rather than a one-time exercise.

## Where This Actually Goes Wrong, and What It Looks Like Done Right

Treated as a compliance artifact, a model card gets written once, right before a launch or an audit, by whoever drew the short straw that week. It gets filed, forgotten, and quietly contradicted by the model within a few months, because nothing forces it to update when the model does. The first time anyone reads it again is during an incident, a regulator's request, or a board question nobody can answer cleanly, and by then it describes a system that no longer exists. That version of a model card protects nobody. It just proves, on paper, that a document once got created.

Treated as an operational tool, the same card becomes something else entirely. It is versioned alongside the model it describes. It has a named owner who knows keeping it current is their job. It gets checked at every meaningful change, not once a year. It answers a procurement team's questions before they ask them, an auditor's questions before they escalate, and an incident responder's questions before the incident gets worse. It gets read constantly, by people who trust it, because it has earned that trust field by field.

A model card is either a record of what someone once claimed, or it is a record of what you can actually prove. Only one of those survives contact with a regulator.  
  
By Prof. Hernan Huwyler, CAIO MBA CPA  
[Hernan Huwyler (0009-0002-1249-7387) - ORCID](https://orcid.org/0009-0002-1249-7387)  
[ResearchID.co - Hernan Huwyler](https://researchid.co/hewyler)  
[https://www.researchgate.net/profile/Hernan-Huwyler](https://www.researchgate.net/profile/Hernan-Huwyler)

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and advisory work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative [risk modeling,](https://github.com/hwyler/risk-model-app) predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and internationally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance, technical and business requirements.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
