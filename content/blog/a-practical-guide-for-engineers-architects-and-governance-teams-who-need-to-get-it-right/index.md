---
title: "A Practical Guide for Engineers, Architects, and Governance Teams Who Need to Get It Right"
date: 2026-07-30
tags: 
  - "ai"
  - "ai-controls"
  - "ai-development"
  - "ai-governance"
  - "ai-red-team"
  - "ai-threat-models"
  - "ai-threats"
  - "ai-vulnerability-testing"
  - "ai-projects"
  - "artificial-intelligence"
  - "chatgpt"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "llm"
  - "technology"
---

Organizations shouldn´t treat AI security as an extension of their existing cybersecurity program. They run the usual penetration tests, validate API authentication, review access controls, and call it done. Then something breaks. A model starts returning outputs it was never designed to produce. A retrieval pipeline exposes data that should have stayed locked. An autonomous agent executes an action nobody authorized.

The problem is not that organizations are careless. The problem is that AI systems fail in ways that traditional security frameworks were never built to catch. This guide covers the full picture: the threat landscape, the controls that actually work, the governance processes that hold everything together, and the specific decisions you need to make before your next AI system goes live.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/chatgpt-image-jul-30-2026-06_03_48-pm.png?w=1024)

## Why AI Security Is a Different Problem

Traditional software is deterministic. Given the same inputs, it produces the same outputs. Its behavior is explicitly programmed and can be inspected through source code. Conventional security frameworks evolved around those assumptions, and they work well for software that behaves predictably.

AI systems violate every one of those assumptions.

A model does not execute instructions. It generates probabilistic outputs based on learned patterns. You cannot read its source code to understand what it will do next. Small changes to input can produce dramatically different outputs. The same model, given slightly different context, can behave in entirely different ways. And because AI systems learn from data rather than being explicitly programmed, the data itself becomes an attack surface that has no equivalent in traditional software.

This is not a theoretical concern. It changes what you need to protect, who is responsible for protecting it, and how you verify that protection is working.

## The Three Delivery Models You Need to Account For

Before you can secure an AI system, you need to understand what kind of system you are actually running. There are three common delivery models, and each one carries a different set of responsibilities.

The first is using a hosted model or AI service. A provider operates the model and its serving infrastructure. You own the security of your application, your prompts, the data you retrieve and inject, the identities with access, the tool permissions, output handling, and monitoring. The provider's security posture matters, but it does not substitute for yours.

The second is running an externally sourced model on your own infrastructure. In addition to everything in the first case, you now own model selection, artifact integrity, deployment hardening, isolation, patching, and capacity management. The origin and ongoing maintenance of the model become supply chain concerns that belong to you.

The third is training or adapting a model yourself. On top of both previous cases, you additionally own the training data, the pipeline that processes it, the evaluation process, the resulting model artifacts, and every release decision. Fine-tuning a hosted model falls somewhere between the first and third options, because responsibilities are genuinely shared with the provider.

Real systems often combine all three. A product might use a hosted general-purpose large language model, a self-hosted image classifier, and a fine-tuned embedding model in the same request path. The mistake organizations consistently make is assigning one security label to the whole product. Record responsibilities per component. That is the only way to know who actually owns each risk.

## The Five Steps to Organize AI Security

Once you understand your delivery model, you need a structured approach to actually doing something about it. The most practical framework for this is five sequential steps that build on each other.

### Govern First

You cannot secure what you have not inventoried. Start by building a clear picture of where AI is being used in your organization, who owns each system, and what the relevant policies are. This means an AI program that covers development, deployment, procurement, and retirement, with named owners for each system and documented responsibilities across security, engineering, privacy, and compliance.

This step is not exciting. Organizations consistently underinvest in it because it feels like administrative overhead rather than technical work. But every governance failure that appears later in the lifecycle, unclear ownership during an incident, unreviewed AI systems procured by individual business units, models running in production with no documented [risk assessment,](https://hernanhuwyler.wordpress.com/2026/05/08/the-pren-18228-problem-why-your-ai-risk-assessment-will-fail-the-first-real-test/) can be traced back to skipping this foundation.

An original implementation tip: do not treat the AI inventory as a one-time exercise. Shadow AI is a real phenomenon. Employees find hosted AI tools, use them with company data, and create risks the security team does not know about. Build a lightweight intake process that lets teams register new AI use cases before they go into production, and make the barrier low enough that people actually use it. The alternative is discovering the shadow systems after an incident.

### Understand Which Threats Actually Apply

The threat landscape for AI systems is large, but not every threat applies to every system. A model used for internal reporting has a completely different risk profile from an autonomous agent with access to external APIs and the ability to send communications on behalf of users.

The way to navigate this is threat modeling: the process of moving from a catalog of possible attacks to a specific, prioritized list of risks that apply to your system. Walk through each threat type and ask two questions. First, does this threat theoretically apply given the architecture? Second, if it materialized, what would the impact actually be?

Consider a concrete example. You do not need to protect against model inversion attacks that attempt to reconstruct training data if your training data is not sensitive. It sounds obvious, but the pattern of applying controls without first checking whether the underlying threat is relevant wastes significant security budget.

The threat types that matter most, and the questions that help you identify which ones apply to your system, fall into three broad areas.

The first is threats through model inputs. This includes adversarial examples designed to force wrong classifications, prompt injection attacks that use crafted text or hidden instructions to manipulate model behavior, and attempts to extract information about training data or model behavior through systematic querying.

The second is threats during development and training. This includes data poisoning, where malicious samples are introduced into training data to corrupt model behavior, direct manipulation of model artifacts, and supply chain attacks where a compromised third-party model or dataset introduces vulnerabilities before you even begin.

The third is conventional security threats applied to AI-specific assets. Model weights, training datasets, prompt templates, and evaluation sets are all assets with significant value and [specific vulnerabilitie](https://hernanhuwyler.wordpress.com/2026/03/15/ai-threat-and-vulnerability-assessment/)s. They need the same protection as any other sensitive business asset, and in many cases they need more.

### Adapt Your Existing Security Practices

AI security does not replace your existing security program. It extends it. The controls you already have for access management, change control, incident response, and supply chain management all remain relevant. What changes is that AI-specific assets need to be added to your asset inventory, AI-specific threats need to be added to your threat model, and your testing practices need to include AI-specific techniques.

The most important adaptation is in how you handle the supply chain. If you are using a ready-made model, whether open source or from a commercial provider, that model's training data, training process, and any fine-tuning that happened upstream are all outside your direct control. Proper supply chain management means evaluating provider security posture, understanding what evidence they provide for their controls, and documenting what you have verified and what you are accepting as residual risk.

Document risk assessment decisions as you make them. This is required under the EU AI Act for high-risk AI systems and it is good practice regardless of regulatory jurisdiction. A risk assessment that exists only in the memory of the person who did it provides no value when that person leaves the organization or when a regulator asks for evidence.

### Reduce Potential Impact

This step deserves more attention than it typically gets. The underlying principle is simple: AI models can always be wrong or manipulated, so the architecture needs to limit what happens when they are.

The most important controls here are least privilege for model actions, human oversight for high-impact decisions, and guardrails that constrain what the model can do regardless of what it outputs. In an agentic system where the model can trigger real-world actions, these controls are not optional enhancements. They are the difference between a model error that produces a bad response and a model error that sends an unauthorized communication, executes a financial transaction, or modifies production data.

Confidential data minimization is equally important. A model that never had access to sensitive data cannot leak it. Apply data minimization before training, before retrieval, and before injecting context into prompts. Every piece of sensitive data that enters the model's context window is data that the model could potentially reproduce in output or expose through inference.

### Demonstrate That Controls Are Working

Governance processes and technical controls only provide value if they demonstrably work. The final step is establishing evidence: through testing, through monitoring, through documentation, and through communication to the stakeholders who need to know the AI systems they rely on are under control.

This means AI-specific security testing, not just standard penetration testing applied to the API in front of the model. It means continuous validation of model behavior, not just a one-time evaluation before launch. It means monitoring that watches for behavioral drift, unusual query patterns, and resource consumption anomalies that could indicate abuse or attack.

## Building the Risk Case for AI Systems from Quality Objectives to Funded Decisions

Organizations trying to govern an AI project make the same sequencing mistake. They start by listing threats, prompt injection, data poisoning, model theft, and then scramble to figure out which ones matter. That order is backwards. A threat only matters once you know what it's threatening, and what it's threatening only becomes clear once you've named the quality objective the system is supposed to protect in the first place. The working method below reverses that instinct: start with what the AI system needs to preserve, find where the architecture actually fails to preserve it, connect those failures to the ways an attacker or an accident could exploit them, size the resulting exposure in terms a finance or legal team can act on, and then choose, deliberately, whether to build, insure, outsource, reprice, or walk away. Each step depends on the one before it. Skip the first and every later number is a guess dressed up as analysis.

### Name the Quality Objective Before You Name a Threat

Every AI system, whether it's a fraud classifier, a customer support agent, or a document summarizer, exists to protect a small set of properties.

- Confidentiality: the training data, the input, the model weights, and anything retrieved into a prompt should stay with the people entitled to see it.

- Integrity: the model should behave the way it was designed to behave, not the way an attacker or a corrupted dataset nudges it to behave.

- Availability: the system should keep answering requests instead of collapsing under a flood of expensive queries.

Beyond those three classic security pillars, AI systems carry two more objectives that conventional software rarely has to worry about at the same intensity: an ethical objective, meaning the system shouldn't produce biased, discriminatory, or harmful outputs even when nobody attacked it, and a business objective, meaning the system needs to actually do the job it was funded to do, accurately enough, often enough, to justify its cost.

The reason this step has to come first is that it determines everything downstream. A vulnerability only becomes worth discussing once you can say which of these five objectives it threatens. A retrieval pipeline that pulls in unverified vendor documents is a confidentiality and integrity problem if those documents can carry hidden instructions. A fraud model trained eighteen months ago with no retraining trigger is a business-objective and ethical problem, because it silently drifts away from the population it's supposed to be classifying fairly and accurately. Naming the objective at risk before you go looking for a vulnerability keeps the exercise from turning into an unstructured list of scary-sounding attack names that nobody can prioritize.

A useful discipline here is to walk the system's actual engineering lifecycle and ask, at each stage, which quality objective is on the line. When the team frames the use case and writes acceptance criteria, the question is whether AI should even be used for this task, and what the worst plausible outcome looks like if it's wrong, that's where the ethical and business objectives get defined in the first place. When the team sources or builds the model, the question shifts to trust in the supply chain: can you trust where this model or dataset came from, and what evidence does the vendor actually hand over versus what they simply claim. When the team adapts model behavior through system prompts, retrieval indexes, or fine-tuning data, the live question becomes which untrusted inputs could change how the model behaves, this is where integrity risk concentrates most heavily in modern generative systems. When the model gets wired into an actual product, with tool access, API calls, identities, and secrets attached, the objective at risk expands to include everything the model can now read, modify, or trigger, and under whose permissions it's doing so. Evaluation and release is where you'd normally claim the risk is handled, but a test suite only characterizes behavior on the inputs you thought to test, it doesn't prove correctness on the inputs you didn't. And once the system is running, the objective at risk becomes whether you can even detect that something has drifted, been abused, or started failing, before a customer or a regulator notices first.

### Find Where the Architecture Actually Breaks

With the objective named, the next step is to look for the specific, concrete weakness in the planned architecture, stack, and deployment circumstances that could let that objective fail. This is different from listing generic attack categories. A vulnerability is a property of your system, not a property of AI in general: weak isolation between trusted system instructions and untrusted retrieved text, a service account with payment permissions far broader than the task requires, a training pipeline with no automated check for population drift, a vector database storing sensitive documents without access control matched to the people who should actually see them.

Four properties of AI systems make this hunt harder than it is in ordinary software, and worth keeping in mind explicitly while you do it.

- The model is not the system. A vendor's safety testing on their base model tells you very little about whether your retrieval layer, your agent orchestration, or your output parser introduces a new weakness once that model is wired into your product.

- Evaluation characterizes behavior, it does not prove correctness. A test result is only as good as the data, the threat assumptions, the model version, and the configuration it was run against, and all four of those need to travel with the result, not get lost after the fact.

- In a generative AI system, data can double as instruction. Anything that lands in the prompt, whether it's a user message, a retrieved PDF, a tool's output, or something pulled from stored memory, can end up steering model behavior even when the engineers who built the pipeline intended it as pure content. That single property is responsible for a huge share of the vulnerabilities showing up in production AI systems today.

- Small changes invalidate old evidence. Swap the model version, tweak the prompt template, add a new retrieval source, or adjust a detection threshold, and every piece of testing you did before that change stops being trustworthy until you rerun it.

A practical way to run this stage without missing anything is to draw the actual flow, on a whiteboard or in a diagram, of data, instructions, and actions moving through the system, and at every step, write down the artifact sitting there: which model, which dataset, which prompt template, which retrieval source, which tool, which piece of infrastructure, and who owns or supplies it. That inventory is what turns a vague sense of unease into a specific list of weaknesses you can actually work with.

AI threat modeling efforts waste time working through a full menu of possible attacks, prompt injection, model inversion, membership inference, evasion, supply chain poisoning, and evaluating every single one regardless of whether it could actually occur given how the system was built. A decision-tree approach fixes that by treating architecture as the filter, not the checklist.

The method works the way a differential diagnosis works in medicine: rather than asking about every disease in a textbook, a clinician asks about symptoms to eliminate whole categories at once. Applied to AI security, the equivalent questions are architectural, not symptomatic: is this a generative model or a classical predictive one, who trained it, who hosts it, does it pull in external data at inference time, can it trigger downstream actions.

Each answer removes an entire branch of threats from consideration rather than adding one more item to assess. A classification model with no text generation capability has no exposure to output injection. A system running entirely on a vendor-hosted model with no fine-tuning has no development-time data poisoning surface, because that responsibility sits with the supplier's engineering process, not yours. This narrowing is what separates a useful threat model from an exhaustive but unfocused inventory: it produces a short list of threats that are actually reachable given the system in front of you, not a long list of threats that are theoretically possible somewhere in the universe of AI systems.

Illustrative example of a decision-tree framework mapping AI threat models across system types:

| # | Question | If YES → threats to assess | If NO → | Next question |
| --- | --- | --- | --- | --- |
| 1 | Does the system use a predictive or classification model (fraud, credit, medical, spam, etc.)? | Evasion attacks, adversarial examples, label anddata poisoning | Skip predictive-specific threats | Go to 2 |
| 2 | Is it used for a high-stakes decision (safety, fraud, medical, credit, hiring)? | Evasion attack severity escalates, treat as high priority | Evasion risk still applies but lower priority | Go to 3 |
| 3 | Is the system Generative AI? | Direct prompt injection | Skip all generative-specific threats below | Go to 6 |
| 4 | Does the system insert external or retrieved content into the prompt (RAG, system prompts, tool output, memory)? | Indirect prompt injection, augmentation data manipulation | Skip this branch | Go to 5 |
| 5 | Is that retrieved and augmentation data stored somewhere (vector DB, memory store)? | Augmentation data leak, protect the store itself | Skip | Go to 6 |
| 6 | Who trained or fine-tuned the model: you, or a supplier? | You: training-data poisoning, dev-time model leak, model extraction risk. Supplier: supply-chain model poisoning, shift to contractual or supplier assurance | — | Go to 7 |
| 7 | Who hosts and runs the model: you, or a supplier? | You: runtime model poisoning, direct runtime model leak, your infra is the attack surface. Supplier: shift to supplier SLA and hosting assurance | — | Go to 8 |
| 8 | Was the training, fine-tuning and augmentation data sensitive? | Model inversion, membership inference, disclosure-in-output | Skip data-leak threats | Go to 9 |
| 9 | Is the model wired into an agent, can it invoke tools, APIs, or trigger other agents? | Agentic threats begin here: excessive tool permissions, goal hijacking, unauthorized tool use, agent-to-agent manipulation | Worst case bounded to text output, go to 12 | Go to 10 |
| 10 | Can the agent's tools send data outward (email, API call, external write, clickable link)? | Combine with Q11 to test the "lethal trifecta" | Exfiltration path closed, lower agentic severity | Go to 11 |
| 11 | Does the agent or a tool it can reach have access to sensitive data? | If YES to both 10 and 11 → lethal trifecta confirmed: manipulated behavior + data access + exfil path = treat as critical | Trifecta not complete, de-escalate | Go to 12 |
| 12 | Does the model or system generate text, code, or markup that gets rendered or executed downstream? | Output injection (XSS, malicious HTML/JS, unsafe commands) | Skip | Go to 13 |
| 13 | Is user and system input sensitive (PII, financial, medical, proprietary)? | Input data leak, applies regardless of predictive, generative or agentic | Skip | Go to 14 |
| 14 | Always evaluate, regardless of prior answers | Resource exhaustion , denial-of-service, cost abuse, plus conventional app-security controls (identity, logging, patching, infra hardening) | — | End |

The sequence itself follows a defensible logic that mirrors how established frameworks such as MITRE ATLAS and the OWASP guidance for LLM and agentic applications structure their own threat catalogs, by attack surface and lifecycle stage rather than by attacker motivation. Generative architecture gets asked first because it gates two of the most consequential threats in production systems today, direct and indirect prompt injection, neither of which applies to a traditional classifier. Training provenance comes next, splitting the analysis cleanly: a self-trained model inherits data poisoning risk during your own pipeline, while a supplier-trained model shifts the relevant question toward contractual assurance and verification of the vendor's own security posture, since you cannot inspect what you didn't build.

Whether the system augments its input, through retrieval, system prompts, or injected context, determines whether an entirely separate category of threats, augmentation data manipulation and augmentation data leakage, even needs to be on the table. And whether the model can trigger actions rather than simply return text is the single question that most changes the severity ceiling, because a model that can only produce output text has a bounded worst case, while a model wired to send emails, call APIs, or invoke other agents has a worst case defined by whatever permissions those integrations carry.

Red teams benefit from following this same ordering deliberately: attacking an architecture's actual reachable surface produces findings a development team can act on, while attacking every theoretical LLM vulnerability regardless of whether the system exhibits the precondition produces a report full of noise that erodes the credibility of the genuine findings buried inside it.

The step that most threat-modeling exercises skip, and that separates a technically complete assessment from an operationally useful one, is asking what happens after a threat is confirmed reachable: does the resulting bad behavior actually reach something worth protecting. A model that can be manipulated into a wrong output is a materially different risk depending on whether that output only displays on a screen or whether it triggers a payment, an email send, or a database write, and depending on whether the system has any path, an API call, an outbound message, a clickable link, capable of moving sensitive data to somewhere an attacker can retrieve it.

This is the same discipline good penetration testing has always applied to conventional software, treating a vulnerability as inert until an actual exploitation path and consequence are demonstrated, but it matters more for AI systems because the temptation to over-scope is stronger: an LLM is theoretically vulnerable to dozens of named attack classes, and without the architecture-first filtering and the reachability check at the end, both engineering teams and red teams end up spending their limited time defending against threats the system was never actually exposed to, while the two or three threats that genuinely apply, and genuinely have a path to harm, get the same amount of attention as everything else on the list instead of the attention they actually deserve.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/modern-device-close-up.png?w=1024)

### Connect the Weakness to a Threat, and the Threat to a Real Scenario

A vulnerability by itself doesn't tell you anything about how bad your day is going to get. It has to be connected to a threat vector, the mechanism an attacker, an insider, or plain negligence would actually use to exploit it, and from there to a concrete scenario involving a specific actor, a specific path, and a specific consequence. This is the step most governance programs skip, jumping straight from "we have a vulnerability" to "here's a control", without ever stating out loud who would exploit it and how.

Take a retrieval pipeline that ingests vendor-uploaded documents without sanitizing them (the vulnerability) and connect it to indirect prompt injection (the threat vector): an attacker embeds a hidden instruction inside a policy PDF, the system retrieves it, and the model treats the embedded text as an authoritative command rather than as untrusted content, drafting a noncompliant customer communication or leaking information it should have withheld. That's a scenario, not just a vulnerability-threat pairing, because it names the actor, the path, and the outcome.

Agentic systems deserve special attention here because the scenario-building step gets sharper stakes once a model can take action instead of just producing text. Three conditions have to line up simultaneously for the worst version of this to happen: untrusted data has to be able to reach the model during a session, the model or a connected agent has to have access to sensitive information, and that same model or agent has to have some way of sending data back out, an email tool, an API call, a link a user might click. When all three are present at once, a single successful manipulation of model behavior turns directly into data leaving the organization, and no amount of confidentiality control on the data itself will help if the exfiltration path through the model was never closed.

Not every theoretically possible threat deserves a scenario, and this is worth saying plainly because over-scoping wastes as much governance effort as under-scoping. If a classification model's training data was never sensitive to begin with, there's no meaningful scenario for someone stealing it through model inversion, the vulnerability might technically exist, but there's no path to a consequence worth pricing. The discipline of building an actual scenario, actor plus path plus consequence, is what filters a long catalog of theoretical weaknesses down to the short list that actually deserves budget.

### Size the Exposure and Choose Where the Money Goes

Once you have real scenarios instead of abstract threat categories, the next step is to put a number on each one, or at least a defensible range, covering both how often it's likely to happen and how much it costs when it does. This is where most AI governance documentation quietly gives up and reaches for a red, yellow, green heat map instead, which feels like an answer but isn't one, because a color tells a board nothing about whether the exposure behind it is ten thousand dollars or ten million.

The prioritization that follows from a properly sized exposure has more options on the table than most teams initially assume, and naming all of them explicitly changes the conversation from "how do we fix this" to "what's the most economical way to handle this". A project can be rejected outright, when the exposure is large, the mitigation is expensive or technically unproven, and the business case doesn't survive the honest number. A project can be accepted as presented, when the exposure is genuinely small relative to the benefit, and forcing controls onto it would cost more than the risk itself. Risk can be financed rather than engineered away, through cybersecurity or professional liability insurance sized to the calculated exposure, or by outsourcing the riskiest components, model hosting, fine-tuning, or specialized data handling, to a vendor better positioned to carry that risk than you are. Contract terms can shift the exposure directly: tightening warranties on a vendor's model behavior, changing the pricing of a service to reflect its actual risk profile, or negotiating indemnification clauses that put the cost of a failure where it's cheapest to absorb it. And of course, the exposure can be reduced directly through internal technical and compliance controls, retraining triggers, output filtering, scoped service credentials, human review gates, each control chosen because its cost is smaller than the expected loss it prevents, not because it appeared on a generic best-practices list.

The organizations that get real value out of this process are the ones that treat quantification as a discipline applied consistently, scenario by scenario, rather than as a one-time slide for a steering committee. A fraud-detection model with a known drift vulnerability, sized honestly, might show an expected loss in the tens of thousands of dollars if caught within two weeks and hundreds of thousands if it runs unnoticed for a quarter, numbers a finance team can reserve against, insure, or fund a control for. A vague "medium risk" rating on the same model tells that finance team nothing they can act on. The entire value of walking through quality objectives, vulnerabilities, threats, scenarios, and exposure in that specific order is that it ends, every time, at a number and a named decision, not at a color and a shrug.

## The Threat Landscape in Detail

### What Can Go Wrong With Model Inputs

Input threats are attacks that happen through the normal operation of the model. The attacker provides input and reads the output. No special access to infrastructure is required.

Prompt injection is the most widely discussed input threat, and for good reason. In a system where the model receives natural language instructions, any source of text that the model processes becomes a potential instruction channel. An attacker who can place content into a document, a web page, a database record, or any other source that gets retrieved and inserted into a prompt can potentially influence model behavior. This is called indirect prompt injection, and it is the key threat in most agentic AI systems because the model has no reliable built-in way to distinguish instructions it was given from data it was asked to process.

Direct prompt injection, where a user tries to override system instructions through their own input, is the more visible version of the same problem. Both require defense in depth: model alignment to reduce susceptibility, filtering at the input and output layers, and critically, architectural controls that limit what the model can do even if the injection succeeds. If a successfully injected prompt cannot trigger a harmful action because the architecture does not permit that action, the attack's blast radius is contained.

Evasion attacks target classification models. The attacker crafts input, sometimes imperceptibly different from legitimate input, that forces the model to make an incorrect decision. The relevance of this threat depends entirely on whether there is a plausible attacker with a plausible benefit from fooling the model. A spam filter is a meaningful target. A skin disease diagnostic tool used by a patient with no obvious motive to manipulate the result is a much lower-risk target in most contexts.

Model extraction happens when an attacker uses the model's outputs to approximate the model's behavior, effectively stealing its functionality through systematic querying. Rate limiting, output truncation, and monitoring for query patterns consistent with extraction are the relevant controls.

### What Can Go Wrong During Development

Development-time threats are often underestimated because they happen before the system goes live. But the vulnerabilities introduced during development follow the model into production.

Data poisoning is the introduction of malicious samples into training data to corrupt model behavior. This can be a deliberate attack where an adversary gains access to the training pipeline, or it can happen through the use of external data sources that have been compromised without your knowledge. The controls are quality assurance on training data, anomaly detection for samples that look inconsistent with the rest of the dataset, and careful supply chain management for any data sourced externally.

Model poisoning at the supply chain level means receiving a model artifact that has been manipulated before you acquired it. An open source model downloaded from a public repository could contain a backdoor that activates only under specific input conditions. Verifying artifact integrity and testing acquired models for unexpected behaviors are the relevant controls.

The development environment itself is an attack surface. Model weights, training datasets, evaluation sets, and configuration files stored in development environments need access controls, encryption, and integrity verification just like production assets. Breaches of development environments often remain undetected for extended periods precisely because development environments have historically received less security attention than production.

### What Can Go Wrong at Runtime

Runtime threats beyond input attacks include the full range of conventional security threats applied to AI-specific assets.

Model weights stored in production need protection from both disclosure and modification. A model that an attacker can read can be used to craft more effective evasion attacks. A model that an attacker can modify is a model that can be reprogrammed to behave in whatever way the attacker chooses. Encryption at rest, integrity verification, and strict access controls are the baseline.

Augmentation data, which includes the content retrieved for retrieval-augmented generation systems and the system prompts that define model behavior, is a high-value target. If an attacker can modify what gets retrieved and injected into prompts, they effectively control part of the model's context. Integrity protection for retrieval stores and system prompt management are therefore security controls, not just operational considerations.

Resource exhaustion is a meaningful threat for large language model deployments because inference costs money. An attacker who can force the system to process large volumes of expensive requests can create significant cost and availability problems. Rate limiting, session budgets, and cost monitoring are the relevant controls.

## Agentic AI: When the Stakes Get Higher

Agentic AI systems deserve particular attention because they change the consequences of every other threat. When a model can trigger real-world actions rather than just produce text output, the impact of prompt injection, data poisoning, or any other successful attack is no longer limited to a bad response. It extends to whatever the agent is capable of doing.

There is a useful concept called the lethal trifecta for understanding data exfiltration risk in agentic systems. You need three conditions to be simultaneously present for an attacker to exfiltrate data through a manipulated agent: the ability to inject malicious instructions into data the model processes, the model's access to sensitive data within the session, and the model's ability to send that data to an external destination. If any one of these three conditions is absent, the exfiltration attack fails. Removing one of the three through architecture is often more practical than trying to prevent the injection itself.

Least model privilege is the foundational control for agentic systems. Assign only the permissions the agent needs for its specific task. Separate read and write permissions. Require explicit approval for high-impact actions. These principles are well-established in conventional software security, but they require conscious application to agentic architectures where developers often assign broad permissions for convenience during development and never revisit those decisions before production.

Human oversight, meaning meaningful human review at decision points that matter, is a control, not just a policy preference. An agent that can take consequential actions without any human checkpoint in the path is an agent where model errors, manipulated behaviors, and unexpected outputs translate directly into real-world consequences with no opportunity to intervene.

## The Specific Risks of Generative AI

Generative AI systems share most of their threat landscape with other AI types, but several risks are materially higher or take different forms.

System prompts, the instructions that define how a hosted model should behave, are both a security control and an attack surface. They represent sensitive intellectual property that should be protected from disclosure, and they are a target for prompt injection attacks trying to override their content. Organizations frequently treat system prompts as configuration files without applying the access controls and integrity verification they would apply to any other sensitive configuration.

Retrieval-augmented generation systems introduce a particularly important input data risk. The content retrieved and injected into prompts often includes sensitive company information, personal data, or proprietary business logic. This content travels to the model provider's infrastructure in clear text if the model is externally hosted, it may not respect the original access controls that governed who could read the source documents, and it exists in the model's context window where it can potentially appear in outputs. Assess what is being retrieved, verify that the retrieval respects access controls, and apply data minimization to limit what sensitive content reaches the prompt.

Training data memorization is a genuine risk for large language models. A model trained on sensitive data can sometimes reproduce specific examples from that training set in its outputs. Testing for memorization before deployment, applying data minimization during training, and using privacy-preserving techniques during fine-tuning are the relevant controls.

Output injection is often overlooked. When model output is rendered in a browser or executed in some downstream process without proper encoding, it can contain content that performs injection attacks. This is a conventional security control applied to an unconventional output source, but organizations sometimes fail to apply their existing output encoding practices to AI-generated content.

## Risk Assessment: Moving From Threats to Decisions

Identifying threats is necessary but not sufficient. Every identified threat needs to be evaluated for likelihood and impact in your specific context, and then treated through one of four options.

Treatment means implementing controls to reduce the likelihood or impact of the risk. This is the most common approach and the bulk of what this guide covers.

Transfer means shifting the risk to a third party, through insurance, contractual agreements, or using a provider who takes on the relevant security responsibilities. This only works when you have verified that the third party is actually managing the risk, not just accepting contractual liability.

Termination means changing the approach to eliminate the risk entirely. Sometimes the right answer is not to use AI for a particular application because the risk cannot be adequately managed. Removing an unnecessary AI component eliminates all AI-related risks for that component.

Tolerance means acknowledging a risk and deciding to bear the potential consequences without further action. This is appropriate when the cost of treatment exceeds the expected impact. It requires explicit documentation of who made the acceptance decision and why, because an undocumented accepted risk is indistinguishable from an overlooked risk.

When assessing likelihood, consider the attacker's realistic motivation. Would an attacker actually benefit from fooling your model? What would they need to do to succeed? What is their likely budget and capability? Threats that exist in theory but have no plausible attacker with a plausible motive can often be accepted or managed with light controls.

When assessing impact, consider the full chain of consequences. Direct technical consequences like compromised data integrity are usually the most visible. Indirect consequences like regulatory penalties, reputational damage, and loss of customer trust often matter more to the organization. In regulated industries, a security incident affecting an AI system may trigger reporting obligations and regulatory scrutiny that dwarf the direct technical cost of the incident.

## The Controls That Actually Work

Selecting controls requires matching the control to the threat, the system type, and the level of risk. Here is the practical breakdown organized by what each control category addresses.

For governance and accountability, the essential controls are an AI program that inventories all AI use and assigns ownership, a security program that includes AI-specific assets and threats, compliance checking against applicable regulations, and ongoing security education for everyone who builds and operates AI systems. These are not glamorous controls. They are the foundation that makes every other control meaningful.

For the supply chain, the key control is treating every external model, dataset, and hosting provider as a potential source of inherited risk. Verify provider security posture before adoption. Test acquired models in your own context rather than relying solely on published benchmarks. Track and patch dependencies in AI infrastructure with the same discipline applied to application dependencies. This last point deserves emphasis: teams frequently delay patching AI infrastructure components because they fear breaking model reproducibility. That hesitation creates a predictable, accumulating vulnerability.

For protecting sensitive data, apply data minimization consistently. The less sensitive data that enters training pipelines, retrieval systems, and prompts, the smaller the disclosure risk. Obfuscate or remove sensitive values from training data. Apply short retention periods for data that does not need to be kept. Test your de-identification approaches for realistic re-identification risk, not just surface-level masking.

For model behavior integrity, the engineering controls during model development include adversarial training, model alignment techniques, ensemble approaches that reduce the impact of any single manipulated component, and continuous validation that tracks model behavior against approved baselines over time. At runtime, input filtering, output filtering, anomaly detection, and rate limiting form the monitoring and detection layer.

For runtime protection, access controls on model endpoints, integrity verification of model artifacts before serving, encryption for model parameters and inference data, and monitoring that watches for behavioral patterns consistent with attack or abuse form the defensive layer.

## Responsibility Assignment: Who Owns What

For every threat you identify, someone needs to own the response. In AI systems with multiple components from multiple sources, responsibility is frequently unclear.

When a component is hosted by a provider, you share responsibility for that component's security with the provider. The division depends on the specific hosting arrangement. Use a responsibility matrix to document which controls you own, which the provider owns, and which are shared. Then verify that the provider is actually implementing the controls assigned to them. Provider attestations and third-party audits are more reliable than self-reported compliance.

When a provider is not transparent about their security practices, you face three options. Accept the risk based on your assessment that the provider's posture is adequate even without verification. Implement your own compensating controls to address the risks the provider may not be managing. Or avoid using that provider for the application in question. The worst outcome is assuming the provider has it covered without checking.

For internally developed or fine-tuned models, your organization owns the entire stack. That means the training data pipeline, the model artifacts, the evaluation process, the deployment environment, the runtime controls, and the ongoing monitoring. The breadth of this responsibility is why organizations with limited AI security maturity are often better served by starting with externally hosted models for lower-risk applications while building internal capability.

## Standardize Your AI Assessments with Hernan Huwyler´s Threat Modeling Toolkit

You cannot secure an AI pipeline with a generic IT checklist. Traditional application security focuses heavily on the API wrapper, identity layers, and network configurations. It completely misses the attack surface unique to machine learning: poisoned training data, instruction overrides in system prompts, and unauthorized actions executed by autonomous agents. I built the [AI Threat Modeling and Vulnerability Assessment Toolkit](https://github.com/hwyler/ai-threat-modeling-toolkit) to give architects, risk managers, and security engineers a deterministic, repeatable way to move from abstract security theory to an actionable, architecture-specific threat model.

The toolkit provides a highly structured methodology tailored specifically to the type of AI system you are actually building. A predictive fraud model requires fundamentally different security controls than a Retrieval-Augmented Generation (RAG) chatbot or a multi-agent workflow. The repository ships with a [machine-readable vulnerability and threat vector catalog](https://github.com/hwyler/ai-threat-modeling-toolkit/tree/main/data), allowing you to script, filter, and score vulnerabilities programmatically. By running the included Python script (`generate_checklist.py`), your team can instantly generate a precise assessment scope customized to your system type and sourcing model (built vs. procured), ensuring you never waste time evaluating irrelevant risks.

Every vulnerability and threat vector within this toolkit is firmly anchored to community consensus. Instead of relying on isolated opinions, the catalogs are [actively mapped against the industry’s most respected frameworks](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/docs/06-source-alignment.md), including MITRE ATLAS, the OWASP Top 10 for LLM and Agentic Applications, NIST AI 100-2, and ISO/IEC 42001. Whether you are building an [asset inventory](https://github.com/hwyler/ai-threat-modeling-toolkit/tree/main/templates) before a red-team engagement or mapping classic STRIDE trust boundaries to an AI context, this open-source repository provides the exact templates and technical guidance required to execute a rigorous, defensible assessment.

The [control guidance document](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/docs/10-control-guide.md) links ISO/IEC 42001 Annex A controls directly to the vulnerability catalog, giving teams a traceable path from identified weakness to documented control requirement. For practitioners who need the full narrative behind each catalog entry, the [vulnerability guide](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/docs/07-vulnerability-guide.md) provides complete detail on every cataloged vulnerability without summarizing, and the [threat guide](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/docs/08-threat-guide.md) does the same for every threat vector, explaining the attack path, the system types most exposed, and the controls that address it. When an assessment moves from analysis into reporting, the [threat model report template](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/docs/09-threat-model-report-template.md) provides a fillable, questionnaire-driven structure designed for red-team engagements, covering system classification, asset inventory findings, threat modeling results, control gaps, and risk acceptance decisions in a format that holds up under audit review.

The [source alignment reference](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/docs/06-source-alignment.md) cross-references every catalog entry against the frameworks it maps to, so the catalog stays anchored to community consensus rather than one team's judgment. Assessment outputs go into the [risk register template](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/templates/risk_register.csv) and the [assessment report template](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/templates/assessment_report.md), both designed to produce artifacts that hold up under audit review. The toolkit is a living document: new attack techniques against AI systems are documented on a rolling basis, and the [contributing guide](https://github.com/hwyler/ai-threat-modeling-toolkit/blob/main/CONTRIBUTING.md) sets out how to propose new entries, update mappings, or correct citations as the field moves.

## What Testing AI Security Actually Looks Like

AI security testing is not just penetration testing applied to an AI API. It requires techniques specific to AI threats.

Adversarial testing for input threats means systematically crafting inputs designed to force wrong decisions, expose training data, extract model behavior, or manipulate outputs in harmful ways. For prompt injection specifically, it means testing with a wide range of injection attempts across multiple input channels, including indirect injection through retrieved content. Red team exercises that simulate an attacker trying to achieve a specific harmful outcome through the model are more valuable than checklist-based assessments.

Model behavior validation before release and continuously in production means maintaining a held-out evaluation set with known correct outputs and testing the model against it regularly. Any significant change to model behavior, whether from a model update, a prompt change, or a retrieval index update, should trigger revalidation. The evaluation set needs to include adversarial examples and edge cases, not just typical production inputs.

Supply chain verification means testing acquired model artifacts for integrity, checking for known vulnerabilities in the model's dependencies, and where possible, running behavioral tests designed to surface backdoors or unusual behaviors that would not appear in standard accuracy evaluation.

Privacy testing means evaluating whether the model can reproduce specific training data examples, whether embeddings can be used to reconstruct sensitive information, and whether de-identification approaches hold up against realistic linkage attacks.

## Documentation, Monitoring, and the Long Tail

The security work done before deployment matters. The monitoring and response capability after deployment matters equally.

Monitoring for AI systems needs to go beyond infrastructure metrics. Uptime and latency tell you whether the system is running. They do not tell you whether it is behaving as intended, whether it is being probed for vulnerabilities, whether its outputs are drifting in quality or safety, or whether its resource consumption is consistent with legitimate use. Build monitoring that watches model behavior and output characteristics alongside infrastructure health.

Incident response procedures for AI systems need to account for the specific ways AI incidents differ from conventional software incidents. The relevant artifacts include logs of model inputs and outputs, records of which model version and which retrieval content were in use at the time, and behavioral validation results that can establish what the model was doing before and after the incident. If those logs do not exist or were not retained, incident reconstruction becomes extremely difficult.

Documentation of risk assessments, control selections, and residual risk acceptance decisions creates the evidentiary record that regulators, auditors, and board committees will ask for. Under frameworks like the EU AI Act, this documentation is a legal requirement for high-risk AI systems. Even outside regulated contexts, documented decisions are the foundation for organizational learning. An organization that documents why it made a specific risk acceptance decision can revisit and update that decision as circumstances change. An organization that does not document its decisions is perpetually starting from scratch.

## Key Standards and Frameworks

The field has developed a body of standards and guidance that provide the technical foundation for AI security programs. ISO/IEC 42001 establishes requirements for AI management systems, providing the governance framework within which security controls operate. ISO/IEC 27090 addresses AI security specifically and is currently in development with substantial community contribution shaping its content. ISO/IEC 27091 addresses AI privacy. I[SO/IEC 23894 provides guidance on risk management for AI.](https://hernanhuwyler.wordpress.com/2026/03/28/how-to-actually-use-iso-iec-23894-for-ai-risk-management/)

At the regulatory level, the EU AI Act establishes mandatory requirements for high-risk AI systems, including risk management, technical documentation, data governance, transparency, human oversight, and post-market monitoring. NIST's AI Risk Management Framework provides a voluntary but widely adopted structure for identifying, assessing, and managing AI risks organized around four core functions. The UK NCSC and CISA joint guidelines for secure AI system development provide practical guidance organized around secure design, development, deployment, and operation.

These frameworks are not mutually exclusive. ISO/IEC 42001 provides the management system. NIST AI RMF provides the risk management process. Sector-specific regulations like the EU AI Act establish mandatory baseline requirements. A mature AI security program typically draws on all of them, using each framework where it provides the most useful structure.

## The Difference Between Documentation and Practice

An AI security program built entirely around documentation produces governance artifacts that satisfy auditors and inform no one. Risk registers that record threats without owners. Control frameworks that describe practices nobody follows. Compliance checklists completed after decisions are made rather than before.

The organizations that actually reduce AI security risk treat governance artifacts as operational tools, not as endpoints. The risk register is updated when new AI systems come online and when existing systems change. The threat model is revisited when the architecture changes or when new attack techniques emerge. Control effectiveness is verified through testing, not assumed through documentation. Residual risk acceptance decisions are made by people with the authority and information to make them, and those decisions are recorded with enough context that they can be revisited meaningfully when circumstances change.

The technical controls matter. The governance processes that ensure those controls remain effective over time matter just as much. An AI system that was secure at launch and has drifted due to model updates, changing retrieval content, or evolving attack techniques is not a secure AI system. Continuous validation, ongoing monitoring, and periodic reassessment are not optional enhancements for organizations with extra budget. They are how security is maintained in a technology domain where the threat landscape and the systems themselves are both changing continuously.

Getting AI security right requires understanding the specific ways AI systems fail, building the controls that address those failures, and maintaining the governance processes that keep those controls effective. Start with the inventory, do the threat modeling, assign the responsibilities, implement the controls proportional to the risk, test them, monitor them, and document the decisions. That is the full picture.

* * *

## References

ISO/IEC 42001:2023 - Artificial Intelligence Management Systems

[ISO/IEC 27090 - Cybersecurity and AI Security](https://www.iso.org/standard/56581.html) (in development, draft for approval)

ISO/IEC 27091 - Privacy and AI (in development)

ISO/IEC 27005:2022 - Information Security Risk Management

ISO/IEC 23894:2023 - AI Risk Management Guidance

NIST AI Risk Management Framework 1.0 (January 2023): [https://airc.nist.gov/RMF](https://airc.nist.gov/RMF)

EU Artificial Intelligence Act, Official Journal of the European Union (2024)

UK NCSC / CISA Joint Guidelines for Secure AI System Development: [https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development](https://www.ncsc.gov.uk/collection/guidelines-secure-ai-system-development)

DSIT Code of Practice for the Cyber Security of AI (UK): [https://www.gov.uk/government/publications/ai-cyber-security-code-of-practice](https://www.gov.uk/government/publications/ai-cyber-security-code-of-practice)

MITRE ATLAS - Adversarial Threat Landscape for AI Systems: [https://atlas.mitre.org](https://atlas.mitre.org/)

OpenCRE - Common Requirements Enumeration for AI Security Standards: [https://www.opencre.org](https://www.opencre.org/)

SANS Critical AI Security Guidelines: [https://www.sans.org](https://www.sans.org/)

AI Security Verification Standard (AISVS): [https://owasp.org/www-project-ai-security-and-privacy-guide](https://owasp.org/www-project-ai-security-and-privacy-guide)

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
