---
title: "Your Vendor's \"We Don't Train On Your Data\" Promise Is a Sentence, Not A Data Architecture"
date: 2026-07-21
tags: 
  - "ai"
  - "ai-contract-clauses"
  - "ai-contracts"
  - "ai-controls"
  - "ai-governance"
  - "ai-procurement"
  - "artificial-intelligence"
  - "chatgpt"
  - "hernan-huwyler"
  - "iso-42001"
  - "llm"
  - "technology"
---

Why the real exposure in generative, predictive, and agentic AI contracts lives in fine-tuning, logs, and retrieval, not in the one line everyone quotes back to legal

Every procurement team has now heard the sentence. A vendor says it, a sales deck repeats it, and somebody on the buying side writes it into the approval memo as if it closes the risk. It doesn't. ”We don't train on your data” answers one question out of at least seven, and it is usually the easiest one for a vendor to answer honestly while still leaving you exposed everywhere else.

I've sat through enough of these reviews to notice the pattern. Legal asks the training question, gets a clean answer, and moves on. Nobody asks what happens to the prompt after the model responds. Nobody asks whether the fine-tuned version of the model your team spent six months shaping now belongs to you, the vendor, or nobody in particular. That gap is where the actual risk sits, and it applies whether you're buying a chatbot, a predictive underwriting model, or an autonomous agent that files its own tickets.

This isn't a US problem or a government-procurement problem. Every organization signing a contract for a large language model, a predictive risk engine, or an agentic system, anywhere in the world, is buying into the same layered technical reality. The contract language just hasn't caught up to it yet.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/chatgpt-image-jul-21-2026-06_46_52-am.png?w=1024)

## The Stack You Are Actually Buying

Nobody buys "an AI model". They buy a stack: infrastructure, a foundation model, a fine-tuned or customized variant sitting on top of it, a retrieval layer pulling in your documents, configuration logic wrapped around all of it, and whatever governance tooling the vendor bolted on to make the whole thing auditable.

Each layer behaves differently under a contract. Infrastructure is usually the vendor's own cloud tenancy or a hyperscaler's. The foundation model is licensed, not owned, by almost everyone including the vendor selling it to you. The fine-tuned variant might be built specifically on your data, which raises an entirely separate ownership question. The retrieval layer touches your live documents at query time. Configuration is the thin, portable layer of prompts and rules sitting on top of everything else.

If your technical team hasn't mapped which components are vendor-owned, which are shared across the vendor's other customers, and which are dedicated to you, you can't actually answer the questions that matter: where does data flow, what persists after the session ends, and what survives if you terminate the contract next year. Skipping that mapping step is how a well-intentioned procurement process ends up with a signed contract that protects nothing.

”Training” sounds like a single moment, something that happened once, in the past, before the vendor ever met you. It isn't. Pre-training builds the base model on a huge, general dataset. Fine-tuning adapts that base model to a narrower domain, sometimes using your organization's own data. Continuous improvement keeps adjusting the system after deployment, often using signals from how customers actually use it.

A vendor can tell you, accurately, that it does not use your data for pre-training, while quietly using it for fine-tuning or for reinforcement learning drawn from user interactions. Those are [different processes](https://hernanhuwyler.wordpress.com/2026/03/16/how-to-build-an-ai-roadmap-that-delivers-value-controls-risk-and-survives-change/) with different risk profiles, and a single blanket sentence in a sales deck rarely distinguishes between them.

This is why the specific verbs in your contract matter more than the general promise. If your data-use restriction only says ”train,” a vendor operating in good faith but reading narrowly can argue that fine-tuning, retraining, or adapting the model falls outside that one word. The fix is boring but effective: define the restriction to cover every verb in the lifecycle, explicitly. ”Train, fine-tune, retrain, adapt, or otherwise improve” closes the gap that a single word leaves open.

> If the contract only prohibits ”training”,, you have not restricted anything except the one process the vendor was least likely to run on your data in the first place.

## Fine-Tuning Creates Embedded Learning You Cannot Delete

Here's the part that surprises people who come from a traditional IT background, where deleting a file usually means the data is gone. If your organization's data was used to fine-tune a model, that data shaped the model's internal weights. Erasing the original files afterward does nothing to reverse what the model already absorbed.

Think of it less like deleting a document and more like unteaching a person a skill they already learned. You can take away their notes, but the knowledge is still there. A deletion clause that only promises to remove ”stored files” is answering a much smaller question than the one you actually care about, which is whether the model itself still carries a trace of your organization's patterns, terminology, or decision logic.

This forces a set of contract questions that most procurement checklists still skip: who owns the fine-tuned model once it exists, can the vendor reuse that tuned version for other customers, and does the tuned instance sit in a dedicated environment or a shared one where your patterns could bleed into someone else's results. None of these are answered by a generic data-deletion promise, no matter how strongly it's worded.

## Retrieval-Augmented Generation Is Not Training, But It Still Needs A Contract Clause

A lot of confusion in this space comes from conflating retrieval with training. When a model pulls your documents from a vector database at the moment someone asks a question, that's retrieval-augmented generation, commonly shortened to RAG. It's dynamic reference lookup during inference, not a process that changes the model's weights. Nothing about RAG teaches the model anything permanent.

That distinction matters, but it doesn't mean RAG is risk-free. Your documents still have to live somewhere to be retrievable, and that ”somewhere” raises the same questions any data-storage arrangement raises: where is it hosted, who can access it, how long is it retained, and is the retrieval index shared across the vendor's other tenants or isolated to you.

A frequently missed detail is what happens to embeddings, the numerical representations of your documents, after the contract ends. Deleting the original documents doesn't automatically delete the embeddings derived from them, and a vendor's data-processing agreement should say explicitly whether those vector representations are purged on termination or left sitting in the vendor's infrastructure indefinitely.

## Configuration Does Not Change Who Owns The Model

System prompts, controls, and behavior policies are the layer most teams spend the most hands-on time building, and it's also the layer with the least legal weight. Configuring a model changes how it behaves for you. It does not change who owns the underlying weights or the model's learned state.

The practical question worth asking here is portability, not ownership. Are your system prompts and guardrail configurations something you can export and take with you if you switch vendors, or are they stored in a proprietary format that locks you in without ever touching the core ownership question. Configuration data is usually retrievable. Model learning typically is not. Treat those as two separate exit-strategy problems, because they are.

Even a vendor that genuinely does not train on your data can still be sitting on a commercially valuable asset: the logs of everything you asked it and everything it answered. Prompts, outputs, usage patterns, and system telemetry all get stored somewhere by default unless the contract says otherwise.

This is where a useful three-way distinction from recent federal AI procurement debates translates well outside government contracting. There's telemetry, which is basic operational data any vendor legitimately needs to keep a service running, such as response times and error rates. There's what some call ”data dust,” the behavioral fingerprint left by how you actually use the system, which patterns you accept, which you reject, and what that reveals about your priorities and workflows. And there's feedback, the corrections and ratings your users provide, which can improve the vendor's product for everyone even when it never touches ”training” in the narrow sense.

Telemetry is fine to leave with the vendor. Data dust and feedback are where a systematic accumulation of insight into your organization's operations can quietly become a competitive advantage for the vendor, entirely separate from anything resembling model training. Most contracts don't distinguish between these three categories at all, which means most contracts are silent on the risk that actually matters most.

## Segregable Versus Non-Segregable Components

It helps to sort everything in an AI contract into two buckets. Segregable and returnable components include the documents you fed into retrieval, your configuration prompts, your policy overlays, and any logs you specifically required the vendor to retain. These can, in principle, be exported, audited, and handed back to you.

Embedded and difficult-to-unwind components include the model weights after fine-tuning, whatever performance optimizations the vendor's system learned from watching you use it, and any statistical adjustments baked into a customized model instance. These cannot be handed back in any meaningful sense, because they don't exist as a discrete, transferable object. They exist as a shift in the model's internal parameters.

Your procurement strategy needs to treat these two buckets completely differently. Ask for return and deletion rights on the first bucket. Ask for use restrictions, audit rights, and dedicated-instance guarantees on the second, because ownership language alone can't reach something that was never a separable asset to begin with.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/business-handshake-scene.png?w=1024)

## A Compliance Architecture Example: The Contract Review Vendor

Picture a mid-sized law firm buying an AI contract-review tool. The vendor fine-tunes a base model on a sample of the firm's past contracts to improve accuracy on the firm's specific clause language and drafting conventions. Six months in, the firm wants to switch vendors.

The firm's data-processing agreement says the vendor will ”delete customer data upon termination.” That clause gets satisfied the moment the vendor wipes the original contract files from its storage. It says nothing about the fine-tuned model that now performs better specifically because it learned the firm's drafting patterns, and it says nothing about whether the vendor can keep using that improved model for its next law-firm client.

A properly scoped contract would have specified, before signing, that the fine-tuned model instance is dedicated to the firm, that the vendor cannot reuse learned patterns from the firm's contracts for any other customer, and that on termination the vendor must either delete the tuned model entirely or transfer it, not just delete the source documents. That's the difference between a deletion clause that sounds protective and one that actually is.

## The Literacy Gap Is The Real Vulnerability

Vendors understand their own model lifecycle in detail: where improvement loops run, which components are multi-tenant, and how data gets leveraged indirectly even when the direct answer to ”do you train on it” is no. Most buyers only ever see the runtime output, the chat window or the API response, and have no visibility into anything upstream of that.

That asymmetry is the actual negotiation risk, more than any single clause. A procurement or legal team that can't distinguish fine-tuning from retrieval, or embedded learning from stored logs, can't scope data rights precisely, can't evaluate reuse risk, and can't draft restrictions that actually hold up against how the system works. Frameworks like ISO 42001 for AI management systems, or the NIST AI Risk Management Framework's actor categories for AI development, deployment, and operation, exist specifically to give non-specialist teams a shared vocabulary for this. Using that vocabulary in your own contract, rather than the vendor's marketing language, is a meaningful first defense.

## A Practical Contract Checklist

Before signing any generative, predictive, or [agentic AI contrac](https://hernanhuwyler.wordpress.com/2026/03/31/guide-to-ai-agent-risk-and-control-management-across-the-full-lifecycle/)t, confirm the following in writing, in the contract or the data-processing agreement itself, not in a sales deck or public FAQ:

1. Which categories of data are covered by any no-training promise: prompts, outputs, uploaded files, logs, and metadata should all be named explicitly, not implied.

3. Whether the promise applies to the specific product tier and region you're buying, since consumer, business, and enterprise plans often carry different terms from the same vendor.

5. Retention periods for each data category, stated as a specific timeframe, not as ”as long as necessary.”

7. Who can access your data in plaintext, including the vendor's own support staff and any subprocessors, and under what conditions.

9. Whether deletion on termination extends to fine-tuned model weights and retrieval embeddings, not only to the original source files.

11. Who owns any custom-built or fine-tuned model, and whether the vendor can reuse learned patterns from your data for other customers.

13. Whether audit rights, SOC 2 reports, or ISO 42001 certification are available for independent verification, rather than relying on the vendor's own attestation.

## Red Flags In The Wording

Watch for a few specific phrasings that sound protective but leave room to maneuver. ”We may use your data to improve our services” without a defined carve-out for confidential material is one. ”Anonymized” or ”de-identified” data use without a precise, contractual definition of what those terms mean is another, since de-identification standards vary enormously in practice.

Also watch for a training restriction that only covers a narrowly defined ”Customer Data” term while leaving prompts, outputs, or metadata sitting outside that definition entirely. And watch for any daylight between the vendor's marketing page and the actual signed agreement. If the two disagree, the signed agreement wins in a dispute, and a marketing promise that was never in the contract protects nobody.

## The Questions That Force An Honest Answer

Asking ”do you train on our data” invites a narrow, technically true, practically useless answer. These questions force the vendor to describe the actual data flow instead of reciting a slogan:

- What exact data is excluded from any training, fine-tuning, or model-improvement process, named category by category?

- What is the retention period for prompts, outputs, files, logs, and metadata, stated separately for each?

- Who can access this data, including support personnel and subprocessors, and under what access controls?

- Is this promise written into the signed contract or DPA, or does it only appear on a public webpage?

- Does the promise apply to this exact plan, tenant, and region we are purchasing?

- If we terminate, does deletion cover fine-tuned model weights and retrieval embeddings, or only the original source files?

A vendor that can answer all six specifically, in writing, has probably built real data governance into its product. A vendor that can only repeat the training slogan hasn't, regardless of how confidently it says the sentence.

## Where This Leaves You

Treat the no-training promise as necessary and clearly not sufficient. For anything involving client data, regulated information, or proprietary workflows, that means an enterprise-tier agreement with a real data-processing agreement attached, contract language that names every verb in the model lifecycle, and explicit terms covering fine-tuning ownership, embedding deletion, and log retention. None of that requires distrust of the vendor. It requires precision, because the underlying technology doesn't leave room for vague promises to hold up later.

If you're building or reviewing AI vendor contracts and want a second set of eyes on the language, or want the fuller checklist adapted to your specific stack, that's exactly the kind of work worth doing before signature, not after. Subscribe below to get the next piece in this series, which walks through how to actually negotiate the fine-tuning ownership clause line by line.

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
