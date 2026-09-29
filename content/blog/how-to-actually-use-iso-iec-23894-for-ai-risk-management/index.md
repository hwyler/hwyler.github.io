---
title: "How to Actually Use ISO/IEC 23894 for AI Risk Management"
date: 2026-03-28
tags: 
  - "ai"
  - "ai-governance"
  - "ai-projects"
  - "ai-risk-management"
  - "ai-risks"
  - "ai-security"
  - "artificial-intelligence"
  - "business"
  - "iso-22989"
  - "iso-31000"
  - "iso-38507"
  - "technology"
---

## Practical ISO/IEC 23894 Implementation for AI Risk Management (Without Turning It Into Shelf Decoration)

Most AI risk programs fail before the first risk is ever scored.

They fail because teams treat AI risk management as a [policy](https://hernanhuwyler.wordpress.com/2026/03/16/responsible-ai-policy-categories/) exercise, a model review checklist, or a late-stage legal sign-off. Then the first serious issue hits. Training data rights were unclear. A model drifts in production. A vendor changes an API. An automated decision harms a customer group nobody mapped. The organization scrambles, and trust evaporates fast.

This is why ISO/IEC 23894 matters. It gives organizations a practical structure for AI risk management that fits how AI is actually built, bought, deployed, and used. In this post, I’ll show you how to turn ISO/IEC 23894 into an [operational workflow,](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/) with governance approval gates, clear role ownership, and an implementation checklist that avoids the common failure points I keep seeing in audits, design reviews, and board briefings.

Here is why it fails: ISO/IEC 23894 is not a checklist. It is a guidance document built on top of ISO 31000, the general risk management standard, with AI-specific extensions layered in. If you treat it like a form to fill out, you will produce documentation that looks complete but protects nobody.

This post walks through the standard's actual structure, explains what each section demands in practice, and gives you the field-tested implementation tips I have gathered from helping organizations build AI risk management programs that survive contact with real AI systems.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/chatgpt-image-sep-11-2026-10_45_14-pm.png?w=1024)

## Why ISO/IEC 23894 Exists and What Problem It Solves

Before 2023, organizations managing AI risk had to improvise. They would borrow bits from information security frameworks, add some data governance controls, and hope the combination covered enough ground. It rarely did.

ISO/IEC 23894:2023 was created by ISO/IEC JTC 1/SC 42 to provide a structured approach for any organization that develops, deploys, or uses AI systems. The standard applies the well-established ISO 31000 risk management framework to the specific challenges AI introduces. Think of it as a translation layer. It takes proven risk management principles and shows you exactly where AI creates new wrinkles.

The standard covers three domains: principles that guide your thinking, a framework for embedding AI risk management into your organization, and processes for actually identifying, assessing, and treating AI-specific risks.

The biggest mistake organizations make is treating ISO/IEC 23894 as a standalone. It explicitly references and extends ISO 31000:2018. If your team has not read ISO 31000 first, they will misunderstand the guidance in 23894 because they will lack the foundational context. Buy both standards. Read 31000 first. Then read 23894 as the AI-specific annotation layer it was designed to be.

## The Three-Part Architecture You Need to Understand

ISO/IEC 23894 mirrors the clause structure of ISO 31000 deliberately. This is not an accident. The authors wanted organizations that already use ISO 31000 to integrate AI risk management without rebuilding everything from scratch. The three parts work together as a system.

### Part One: Principles (Clause 4)

The principles define the foundational values that should shape every AI risk decision your organization makes. ISO 31000 defines eight principles. ISO/IEC 23894 adds AI-specific guidance to five of them: Inclusive, Dynamic, Best Available Information, Human and Cultural Factors, and Continual Improvement.

The "inclusive" principle is where most organizations stumble first. AI systems affect a wider set of stakeholders than traditional software. The standard explicitly calls out that stakeholders can help identify risks in data collection, define fairness criteria, identify bias, and determine where human oversight is needed. This is not a suggestion. If your risk management process does not include diverse stakeholder input, you are missing risks that will surface later in the worst possible way.

The "dynamic" principle matters more for AI than for almost any other technology domain. AI systems based on machine learning can change their behavior through continuous learning. Customer expectations shift quickly. Regulatory requirements are updating constantly. Your risk management process needs to account for a system that is itself a moving target.

When I first helped a financial services firm apply the "Inclusive" principle, they interpreted "stakeholder involvement" as sending a survey to the compliance team. That is not what the standard means. You need a structured dialog with people who will be affected by the AI system's decisions. For a credit scoring model, that means talking to loan officers, applicants from different demographic groups, and consumer advocacy organizations. Map your stakeholders before you start the risk assessment, not after.

### Part Two: Framework (Clause 5)

The framework section describes how to embed AI risk management into your organizational structure. It covers leadership commitment, integration with existing management systems, organizational design, resource allocation, and communication.

Two sub-clauses deserve special attention.

Clause 5.2 on leadership and commitment adds an AI-specific requirement that many organizations overlook. Because trust and accountability are especially important for AI, the standard says top management should consider issuing public statements about their commitment to AI risk management. This is not corporate PR. It creates an accountability anchor. Once your CEO has publicly committed to responsible AI, the organization has real pressure to follow through.

Clause 5.4.3 on assigning roles is where the framework becomes [operational](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/). The standard requires that top management and oversight bodies allocate resources and identify specific individuals with authority to address AI risks and responsibility for monitoring AI risk processes. Not committees. Not shared inboxes. Named people with clear authority.

### Part Three: Processes (Clause 6)

This is where the standard gets specific about what you actually do. The risk management process follows a sequence: define scope and context, assess risks (identify, analyze, evaluate), treat risks, then monitor and report. Each step has AI-specific extensions.

The process section is the longest part of the standard for good reason. AI risk assessment requires you to think about assets, risk sources, events. Do not try to build your AI risk management process on a blank sheet of paper. Clause 6.4.1 specifically recommends using the catalogue of AI-related risk sources in Annex B as a baseline for organizations performing risk assessment for the first time. I have seen teams spend three months trying to brainstorm AI risk sources when the standard already provides a structured catalogue. Start there. Customize from there.

## Stage 1: Establishing Scope, Context, and Criteria

This stage determines what your AI risk management process covers and how it connects to your broader organizational context. Get this wrong and everything downstream is compromised.

The standard requires you to build an inventory of where AI systems are being developed or used in your organization. This sounds straightforward. It is not. In every organization I have worked with, the initial AI inventory missed at least 30% of actual AI usage. Teams embed machine learning models in spreadsheet macros, use AI-powered SaaS tools without formal procurement, or inherit AI components through acquisitions.

For external context, the standard provides Table 2 with specific considerations. You need to track relevant legal requirements for AI, ethical guidelines from government and industry groups, domain-specific AI frameworks, technology trends, and societal implications of AI deployment. For internal context, Table 3 adds considerations about how AI affects organizational culture, the availability of AI expertise, intellectual property implications, and data quality constraints.

Defining risk criteria for AI requires you to understand uncertainty across the entire AI system. The standard calls out data, software, mathematical models, physical extensions, and human-in-the-loop aspects. This is a broader scope than most organizations initially consider.

What to do: Build your AI system inventory first. Document every AI system or component, its purpose, its data sources, who built it, who operates it, and who is affected by its outputs. Then map the external and internal context factors from Tables 2 and 3. Only then define your risk criteria.

The standard warns that "AI is a fast-moving technology domain" and that measurement methods should be "consistently evaluated according to their effectiveness." I learned this the hard way when a client's risk criteria for a natural language processing system became obsolete within eight months because the underlying model was replaced with a fundamentally different architecture. Build a review trigger into your risk criteria. Any time the AI model architecture, training data source, or deployment context changes, the risk criteria should be re-evaluated. Do not wait for the annual review.

## Stage 2: Risk Assessment, the Core of the Process

Risk assessment has three sub-stages: identification, analysis, and evaluation. The standard treats each with specific AI guidance.

### Risk Identification

The standard breaks identification into five activities: identifying assets and their value, risk sources, potential events and outcomes, existing controls, and consequences. Each requires AI-specific thinking.

For assets, you need to consider three levels: organizational (data, models, the AI system itself, reputation, trust), individual (personal data, privacy, health, safety), and societal (environment, socio-cultural values, educational equity). This three-level approach is one of the most important contributions of the standard. Most organizations only think about organizational assets when they identify AI risks. The standard forces you to consider who bears the consequences.

For risk sources, Annex B provides categories including complexity of environment, lack of transparency and explainability, level of automation, machine learning specific risks, hardware issues, system life cycle issues, and technology readiness. Each category contains specific risk scenarios.

For consequences, the standard makes a critical distinction that many teams miss. It instructs you to "identify any differences between the groups who experience the benefits of the technology and the groups who experience negative consequences." This is not theoretical. A predictive policing system might benefit a city's police department while disproportionately harming specific communities. A hiring algorithm might benefit an HR team's efficiency while systematically disadvantaging certain applicant groups.

What to do: For each AI system in your inventory, work through all five identification activities. Use Annex B as your starting checklist for risk sources. Document consequences at all three levels: organization, individual, and society.

The standard lists methods for identifying potential events, including published standards, scientific papers, market data, incident reports, field trials, stakeholder reports, and expert interviews. When I run risk identification workshops, I always start with incident reports on similar systems. Nothing focuses a risk identification session like showing the team a real-world failure of a system similar to theirs. Search for published incidents, regulatory enforcement actions, and academic case studies related to your specific AI application domain before the workshop begins.

### Risk Analysis

Risk analysis requires you to assess both consequences and likelihood. The standard distinguishes between three types of impact assessment: business impact, individual impact, and societal impact.

For individual impact assessment, the standard specifies a detailed list of considerations: types of data used, intended impact, potential bias impact, potential impact on fundamental rights, fairness impact, safety implications, and the jurisdictional and cultural environment of the individual. This last point is easy to overlook. An AI system's impact on an individual can vary dramatically depending on the legal and cultural context in which that individual lives.

For likelihood assessment, the standard includes a nuanced warning that many organizations miss. It states that "there can be significant technical, economic and heuristic issues with decision-making based on likelihoods, particularly when the likelihood either can't be calculated or where the calculation has a large margin of error." In plain language: if you cannot reliably estimate how likely an AI failure is, do not pretend you can. Focus instead on consequence severity and your ability to detect and respond to failures.

What to do: Run separate impact assessments for business, individuals, and society. Do not collapse them into a single score. For each risk, decide whether a meaningful likelihood estimate is possible. If it is not, shift your analysis to focus on consequence severity and control effectiveness.

I once watched a team assign a "low likelihood" score to a bias risk in a hiring algorithm because the model had performed well in testing. Six months after deployment, the model was producing biased outcomes because the production data distribution had drifted from the test data. The team's likelihood estimate was based on a snapshot that was already stale. For AI systems, especially those using machine learning, likelihood estimates decay faster than for traditional systems. Reassess likelihood every time the model is retrained, the data source changes, or the deployment population shifts.

### Risk Evaluation

Risk evaluation compares the analyzed risks against your established criteria to determine which risks need treatment and what priority they receive. The standard defers to ISO 31000:2018 here without adding AI-specific guidance, which tells you something important. The evaluation step is about organizational judgment, not technical analysis. You need decision-makers at the table who understand both the technology and the business context.

## Stage 3: Risk Treatment and Implementation

Once risks are evaluated, you choose treatment options. The standard lists the same options as ISO 31000: avoid the risk, take or increase the risk to pursue opportunity, remove the risk source, change the likelihood, change the consequences, share the risk, or retain the risk by informed decision.

The AI-specific addition here is the concept of a risk-benefit analysis for residual risks. If you cannot reduce negative consequences to an acceptable level through treatment, the standard requires you to perform a risk-benefit analysis. This is particularly relevant for AI because some AI risks (like model opacity in deep learning) cannot be fully eliminated. You need to decide whether the benefits justify the residual risk.

What to do: For each risk that exceeds your tolerance thresholds, select a treatment option and document it in a risk treatment plan. For residual risks that remain above tolerance after treatment, conduct a formal risk-benefit analysis. Record the rationale for accepting any residual risks.

[Treatment plans](https://hernanhuwyler.wordpress.com/2026/03/16/how-to-build-an-ai-roadmap-that-delivers-value-controls-risk-and-survives-change/) for AI systems need to be version-aware. Traditional risk treatment plans assume relatively stable systems. AI systems, especially those using continuous learning, change over time. Your treatment plan should specify which version of the model it applies to and include trigger conditions for re-evaluation. I recommend tagging each treatment plan entry with the model version, training data date, and deployment configuration it was validated against. When any of these change, the treatment plan enters a mandatory review cycle.

## Stage 4: Monitoring, Recording, and Reporting

The standard's requirements for recording and reporting are more specific than many teams expect. Clause 6.7 requires organizations to establish a system for collecting and verifying information from both implementation and post-implementation phases, and to collect publicly available information on similar systems.

This information must be assessed for relevance to the trustworthiness of the AI system. The standard specifically asks whether previously undetected risks exist or whether previously assessed risks are no longer acceptable. When either condition is true, you must perform a review of risk management activities and evaluate the effects on existing controls.

The recording requirements include: system description and identification, methodology applied, intended use description, identity of assessors, terms of reference and date, release status, and degree to which objectives have been met. This is not optional documentation. It creates the audit trail that regulators and oversight bodies will examine.

What to do: Build a risk management record template that captures all required fields. Establish a cadence for collecting and reviewing post-implementation data. Create triggers that automatically initiate risk reassessment when conditions change.

The standard says risk management records "should allow the traceability of each identified risk through all risk management processes." In practice, this means you need a risk register with unique identifiers for each risk that persist across assessment cycles. I have seen organizations create new risk registers for each assessment, losing the historical thread. Use a single, versioned risk register where each risk has a persistent ID, and track its status changes over time. This is the only way to demonstrate to auditors that your process is continuous, not episodic.

## Implementation Tips

These apply across all stages and will determine whether your AI risk management program actually works.

### Tip 1: Align Risk Management with the AI System Life Cycle

Annex C of the standard maps risk management activities to AI system life cycle stages: inception, design and development, verification and validation, deployment, operation and monitoring, continuous validation, re-evaluation, and retirement or replacement. This mapping is not decorative. It tells you which risk management activities should happen at each stage.

Most organizations I work with front-load their risk management effort at the design stage and then drop attention during operation. The standard explicitly shows that risk assessment, treatment, monitoring, and recording continue through every life cycle stage, including retirement. When you decommission an AI system, you can lose decision expertise and information. Plan for that. Document what the system knew and how it made decisions before you turn it off.

### Tip 2: Handle Stakeholder Identification Seriously

The standard provides a list of stakeholder categories: the organization itself, customers, partners, third parties, suppliers, end users, regulators, civil organizations, individuals, affected communities, and societies. That is nine categories. Most organizations consult two or three.

Create a stakeholder map for each AI system at the inception stage. For each stakeholder category, document what information they need, how they are affected by the system, and how you will engage them. Update this map when the system's scope or deployment context changes. The stakeholder categories that matter most are often the ones farthest from the development team. Affected communities and end users rarely have a voice in risk assessment unless you build a specific mechanism to include them.

### Tip 3: Document Your Risk Criteria Decisions Explicitly

The standard's Table 4 on risk criteria includes a requirement that organizations "take reasonable steps to understand uncertainty in all parts of the AI system." This includes data, software, mathematical models, physical extensions, and human-in-the-loop aspects.

When defining risk criteria, write down not just what your criteria are, but why you chose those thresholds. I worked with an organization that set a 95% accuracy threshold for an AI diagnostic tool. When a regulator asked why 95% and not 97% or 99%, nobody could answer. The threshold had been copied from a different project. Document the reasoning behind every criterion. Reference the clinical studies, industry benchmarks, or stakeholder consultations that informed your decision. This documentation is what separates a defensible risk management process from an arbitrary one.

### Tip 4: Treat Transparency as a Multi-Audience Challenge

Annex B of the standard discusses transparency and explainability as risk sources. It makes a point that "the kind and level of information that is appropriate strongly depends on the stakeholders, use case, system type and legislative requirements." One-size-fits-all transparency does not work.

Build a transparency framework that segments by audience. The standard's Table 1 mentions tailoring transparency to "relevant personas" such as regulators, business owners, and model risk evaluators. In practice, I create three transparency tiers. Tier one is the public-facing description of what the AI system does and does not do. Tier two is the detailed technical documentation for internal reviewers and regulators. Tier three is the full model documentation, including training data provenance, architecture decisions, and test results. Each tier serves a different audience and contains different information. Trying to serve all audiences with one document produces a document that serves none of them.

## What This Standard Actually Does in Practice

## Part 1: The AI Risk Management Process

This is Clause 6 of the standard. It is the longest and most detailed section because it describes what you actually do.

### Step 1: Define Your Scope, Context, and Criteria

Before you assess any risks, you need to answer three questions. What AI systems are we managing? What is the environment around them? And what criteria will we use to decide if a risk matters?

The standard requires you to build an inventory of where AI is being developed or used in your organization. This inventory must be documented and included in your risk management process.

Practical example: A mid-size insurance company I worked with discovered during this step that 14 different teams were using AI-powered tools, but only 3 had been formally identified by the IT governance team. Six were SaaS products with embedded ML models. Two were spreadsheet-based models built by actuaries. Three were [vendor-provided](https://hernanhuwyler.wordpress.com/2026/03/15/how-to-negotiate-ai-agreements-that-protect-data-value-and-liability/) claims processing systems. The inventory step alone changed their understanding of their AI exposure.

For context, the standard requires you to consider nine categories of stakeholders:

- Your own organization

- Customers, partners, and third parties

- Suppliers

- End users

- Regulators

- Civil organizations

- Individuals affected by the AI system

- Affected communities

- Societies broadly

That last category is not abstract. If your AI system makes lending decisions, "societies" includes the economic communities shaped by those decisions over time.

The standard also requires you to consider whether your AI systems can harm human beings, deny essential services, infringe human rights through biased automated decisions, or contribute to environmental harm.

For risk criteria, the standard adds an AI-specific requirement that matters enormously in practice: you must understand uncertainty across all parts of the AI system. That includes the data, the software, the mathematical models, any physical components, and the human-in-the-loop aspects like data labeling. Most organizations define risk criteria only around the model itself and miss everything upstream and downstream.

Practical insight for risk managers: Your AI risk appetite should account for your organization's actual AI capacity and knowledge level. The standard says this directly. If your team has limited ML expertise, your risk appetite for complex deep learning systems should be lower than an organization with a mature data science function. This sounds obvious, but I have seen organizations approve high-risk AI projects with the same risk appetite they use for rule-based automation.

Practical insight for data scientists: The standard warns that "AI is a fast-moving technology domain" and that measurement methods should be "consistently evaluated according to their effectiveness." That means the metrics you use to evaluate model performance today might not be appropriate six months from now. Build metric review into your model monitoring cadence.

### Step 2: Identify Risks

Risk identification in ISO/IEC 23894 covers five distinct activities. Each one matters.

**Identify assets and their value.** The standard requires you to think about assets at three levels:

Organizational assets include your data, your trained models, the AI system itself (tangible), plus your reputation and stakeholder trust (intangible).

Individual assets include personal data (tangible), plus privacy, health, and safety (intangible).

Community and societal assets include the environment (tangible), plus socio-cultural beliefs, educational access, and equity (intangible).

Practical example: When a healthcare AI startup assessed assets for their diagnostic imaging tool, they initially listed only their model and training data. The three-level framework forced them to also consider patient safety (individual intangible), the hospital's reputation for diagnostic accuracy (organizational intangible), and equitable access to accurate diagnosis across demographic groups (societal intangible). Each of these surfaced risks that the initial asset list would have missed.

**Identify risk sources.** The standard provides categories: organizational factors, processes, personnel, physical environment, data, AI system configuration, deployment environment, hardware and software, and dependence on external parties. Annex B expands these into detailed scenarios (covered in Part 2 below).

**Identify potential events and outcomes.** The standard lists specific methods for finding these: published standards and papers, market data on similar systems, incident reports on similar systems, field trials, usability studies, stakeholder reports, expert interviews, and simulations.

Practical insight for AI security analysts: Incident reports on similar systems are the most underused source on this list. Before running any risk identification workshop, search for publicly reported failures, adversarial attacks, and regulatory actions against AI systems similar to yours. The [AIAAIC Repository,](https://www.aiaaic.org/aiaaic-repository) the [OECD AI Incidents Monitor](https://oecd.ai/en/incidents), and [vendor-specific](https://hernanhuwyler.wordpress.com/2026/03/15/how-to-negotiate-ai-agreements-that-protect-data-value-and-liability/) CVE databases are good starting points. Nothing sharpens a risk identification session like a real-world failure story from your domain.

**Identify existing controls.** Document what controls already exist and assess whether they actually work. The standard specifically calls out the importance of identifying control failures.

**Identify consequences.** This is where the standard adds its most valuable AI-specific guidance. It instructs you to identify differences between the groups that benefit from the technology and the groups that bear negative consequences. A resume screening tool might benefit the HR department (faster processing) while systematically disadvantaging applicants from certain educational backgrounds or geographic regions.

Consequences to organizations include investigation and repair time, lost opportunities, reputational damage, regulatory penalties, and litigation.

Consequences to individuals and societies are harder to quantify but often more severe: threats to health, violations of privacy, infringement of fundamental rights.

The standard makes a practical point that experienced practitioners already know: consequences for individuals and societies almost always affect the organization as well. A safety incident creates liability claims. A bias scandal damages the brand. Map these cascading effects explicitly.

### Step 3: Analyze Risks

Risk analysis requires three separate impact assessments:

**Business impact assessment.** How badly does this risk affect the organization? Consider criticality, tangible versus intangible impacts, and your established criteria.

**Individual impact assessment.** How does this risk affect the people whose data is used or whose lives are influenced by the AI system? The standard lists specific factors: types of personal data used, potential bias impact, potential impact on fundamental rights, fairness impact, safety of the individual, existing protections against bias, and the jurisdictional and cultural environment of the individual.

That last factor is easy to overlook but critical. An AI system's impact on an individual in the EU (where GDPR applies) differs from its impact on an individual in a jurisdiction with no data protection law. The same system creates different risk profiles in different markets.

**Societal impact assessment.** How broadly does the AI system reach into different populations? The standard specifically asks you to consider whether the system amplifies or reduces pre-existing patterns of harm to different social groups.

Example: A government agency deploying a predictive policing model would face very different societal impact conclusions than a private company using the same technology for retail theft prevention. The government use case reaches more broadly and carries the authority of the state, which amplifies both benefits and harms.

For likelihood assessment, the standard includes a warning that practitioners should take seriously: "There can be significant technical, economic and heuristic issues with decision-making based on likelihoods, particularly when the likelihood either can't be calculated or where the calculation has a large margin of error." In plain language: if you cannot meaningfully estimate how likely something is, do not force a number. Focus on consequence severity and your ability to detect and respond instead.

Practical insight for data scientists: Likelihood estimates for AI system failures decay faster than for traditional software. A model's failure probability changes every time the data distribution shifts, the model is retrained, or the user population changes. If you assign a likelihood score, attach an expiration date to it.

### Step 4: Evaluate Risks

Compare the analyzed risks against your criteria. Prioritize. Decide which risks need treatment. The standard defers to ISO 31000 here without AI-specific additions, which tells you this step is about organizational judgment, not technical analysis. Get decision-makers in the room who understand both the technology and the business.

### Step 5: Treat Risks

The standard provides seven treatment options, consistent with ISO 31000:

- Avoid the risk (stop or do not start the activity)

- Accept increased risk to pursue an opportunity

- Remove the risk source

- Change the likelihood

- Change the consequences

- Share the risk (contracts, insurance)

- Retain the risk by informed decision

The AI-specific addition: if you cannot reduce negative consequences to an acceptable level through any treatment option, you must perform a risk-benefit analysis for the residual risk. This matters because some AI risks cannot be fully eliminated. The opacity of a deep learning model, for example, is inherent to the technology. You need to decide if the benefits justify the residual risk, and you need to document that decision.

Practical insight for risk managers: Each treatment measure must be verified for effectiveness and recorded. Do not just document the plan. Document whether the treatment actually worked. I have seen organizations with detailed treatment plans and zero follow-up on whether the treatments reduced the risk as expected.

### Step 6: Monitor, Record, and Report

The standard's recording requirements are specific. Your risk management record must include:

- Description and identification of the analyzed system

- Methodology used

- Intended use of the AI system

- Who performed the risk assessment

- Terms of reference and date

- Release status of the assessment

- Whether and to what degree objectives were met

The standard also requires that you collect information from post-implementation phases and review publicly available information about similar systems. You must assess whether previously undetected risks exist or whether previously accepted risks are no longer acceptable.

The records must allow traceability of each identified risk through all risk management processes. This means persistent risk IDs, version-controlled risk registers, and a clear audit trail from identification through treatment and monitoring.

Practical insight for all three audiences: When the standard says "collect and review publicly available information on similar systems on the market," it means this is an ongoing obligation, not a one-time activity. Set up alerts for incident reports, regulatory actions, and published research about AI systems similar to yours. The best early warning system for your own AI risks is someone else's AI failure.

* * *

## Part 2: Risk Sources and Objectives (Your Identification Checklists)

Annexes A and B of the standard provide catalogs that serve as starting points for risk identification. The standard itself says these catalogs have "shown value" for organizations performing AI risk assessment for the first time. Use them as baselines, not as exhaustive lists.

### AI-Related Objectives to Protect (Annex A)

These are the things that can go wrong or right with AI systems. For each objective, the standard provides context on why it matters for AI specifically.

**Accountability.** AI changes who is responsible for decisions. When a person made a lending decision, that person was accountable. When an AI system makes that decision, accountability becomes unclear. Regulators worldwide are still working out who bears responsibility. You need to know the legislation in every market where your AI system operates.

**AI Expertise.** Building AI systems requires interdisciplinary specialists, not just software engineers. The standard also extends this to end users: they need enough understanding of the AI system to detect and override erroneous outputs.

Practical example: A manufacturing company deployed an AI-powered quality inspection system but did not train the floor operators on how the system made decisions or what its failure modes looked like. When the system began missing defects due to a lighting change in the factory, operators trusted the system's "pass" decisions for three weeks before someone escalated the rising customer complaint rate.

**Training and Test Data Quality.** Training and test data must be validated for currency, relevance, diversity, and consistency. If you source data externally, data quality is still your responsibility. The amount of data required varies with the functionality and complexity of the environment.

Practical insight for data scientists: The standard specifically calls out that training and test datasets should be independent when applicable. This is a basic ML practice, but the standard elevates it to a risk management concern. If your test set leaks into your training data, you have not just a technical problem but a governance failure.

**Environmental Impact.** AI can help the environment (optimizing energy use, reducing emissions) or hurt it (massive compute requirements for training). Both sides must be considered.

**Fairness.** Unfair outcomes can come from biased objective functions, imbalanced datasets, human biases in training data, biased product concepts, or decisions about when and where to deploy AI systems. The standard references ISO/IEC TR 24027 for deeper guidance on bias.

**Maintainability.** ML-based systems are trained, not programmed. Modifying them to fix defects or adapt to new requirements is fundamentally different from patching traditional software. Understand the implications before deploying.

**Privacy.** AI systems that depend on large datasets create privacy risks through data collection, through inference of sensitive information, and through model personalization. The standard notes that AI can infer sensitive personal data even when that data was not directly provided. A data protection impact assessment (per ISO/IEC 29134) is recommended.

Practical insight for AI security analysts: The standard highlights that protecting privacy in AI includes protecting access to models personalized for individuals or models that can be used to infer characteristics of similar individuals. This means model extraction attacks are a privacy risk, not just a security risk. If an attacker can replicate your model, they can potentially infer characteristics of your training data subjects.

**[Robustness](https://hernanhuwyler.wordpress.com/2026/03/15/the-model-robustness-and-monitoring-playbook/).** Can the system maintain performance under unexpected conditions? Neural networks are particularly challenging here because their nonlinear nature can produce unexpected behavior. Characterizing neural network robustness remains an open research problem.

**Safety.** AI systems in vehicles, manufacturing, robotics, and medical devices introduce safety risks that must be evaluated against domain-specific safety standards. The standard does not replace those domain standards. It adds to them.

**Security.** Beyond classical information security, AI introduces new attack surfaces: data poisoning (corrupting training data), adversarial attacks (crafted inputs that fool the model), and model stealing (extracting the model through query access). ISO/IEC 27005 covers general information security risk management. The AI-specific threats require additional consideration.

Practical example for security analysts: A financial institution's fraud detection model was trained on transaction data that included a small number of poisoned records inserted by an insider. The poisoned data taught the model to classify certain fraudulent transaction patterns as legitimate. Classical information security controls (access management, encryption) did not prevent this because the insider had authorized access to the data pipeline. AI-specific controls (data provenance tracking, statistical anomaly detection on training data) would have caught it.

**[Transparency and Explainability.](https://hernanhuwyler.wordpress.com/2026/03/15/modeling-practices-for-regulated-ai/)** Transparency is about what the organization communicates. Explainability is about what the system can reveal about its own decision-making. Both matter, and they serve different purposes. Transparency builds trust with stakeholders. Explainability enables validation and verification by the organization itself.

The standard also notes a tension: excessive transparency can create privacy, security, and intellectual property risks. You need to find the right level for each stakeholder group.

### AI-Related Risk Sources (Annex B)

These are the places where risks originate. Use this as a checklist during risk identification.

**Complexity of environment.** The more complex the operating environment, the harder it is to ensure your training data covers all possible situations. For autonomous driving, you cannot guarantee coverage of every scenario. For a chatbot answering questions about a fixed product catalog, coverage is more achievable. Assess how well-understood your system's environment is, because partial understanding creates uncertainty that is itself a risk source.

**Lack of transparency and explainability.** If you cannot explain why your model made a specific decision, you cannot fully validate it. This affects trustworthiness, accountability, safety, security, fairness, and robustness. The standard emphasizes that explainability matters for internal validation, not just external communication.

**Level of automation.** Systems range from fully human-controlled to fully automated. Higher automation means less human oversight, which amplifies both the efficiency gains and the risk exposure. For systems where a human must be "ready to take over when necessary," the handover itself is a risk source. Think about response time, operator attention, and situation awareness.

**Machine learning specific risks.** Data quality directly affects system behavior. Data collection processes are a risk source that is "especially hard to diagnose and detect." Data can become unrepresentative over time. Data sourcing creates [ethical and legal](https://hernanhuwyler.wordpress.com/2026/03/16/responsible-ai-policy-categories/) risks. Failing to secure the data pipeline opens the door to adversarial manipulation. Continuous learning systems can change their behavior in production in ways that were not anticipated at deployment.

Practical example: An e-commerce recommendation engine trained on user interaction data gradually learned to recommend increasingly sensationalized products because those generated more clicks. The continuous learning loop optimized for the engagement metric without any check on whether the recommendations were appropriate. The behavior drift was subtle enough that no one noticed for months.

**System hardware issues.** Hardware errors, soft errors from radiation, constraints when transferring models between different hardware platforms, and network issues for systems requiring remote processing. These are easier to overlook in AI because teams focus on model performance and forget about the physical infrastructure.

**System life cycle issues.** Risks exist at every stage:

- Design: failing to anticipate deployment contexts

- Verification and validation: inadequate testing causing regressions

- Deployment: misconfigured resources

- Maintenance: unsupported but still-running systems

- Reuse: using a system in a context it was not designed for (the standard gives the example of a social media face detection system repurposed for criminal suspect identification, a far more demanding use case)

- Decommissioning: losing the decision expertise embedded in the retired system

**Technology readiness.** Less mature technologies carry unknown risks. More mature technologies create complacency and technical debt. Both ends of the maturity spectrum require attention.

* * *

## Part 3: The Organizational Framework

This is Clause 5. It describes how to embed AI risk management into your o[rganization's structure and operations](https://hernanhuwyler.wordpress.com/2026/03/15/managing-ai-projects-with-agile-exploration-and-mlops/).

### Leadership and Commitment

Top management, supported by [Chief AI Officers](https://hernanhuwyler.wordpress.com/2026/03/16/practical-caio-responsibilities/), must do two things the standard calls out specifically for AI:

First, consider issuing public statements about the organization's commitment to AI risk management. This creates accountability and builds stakeholder confidence.

Second, recognize that AI risk management requires specialized resources and allocate them. An AI risk program staffed by people without AI expertise will produce documentation that misses the actual risks.

### Organizational Context

The standard provides two detailed tables for understanding your external and internal context.

For external context, AI-specific considerations include:

- AI-related legal requirements in your markets

- Ethical guidelines from government groups, regulators, standardization bodies, civil society, academia, and industry associations

- Domain-specific AI frameworks

- Societal implications of your AI deployments

- How continuous learning might affect your ability to meet contractual obligations

- Ownership and usage rights for training data provided by third parties

For internal context, AI-specific considerations include:

- How AI changes organizational culture by creating new roles and responsibilities

- Deskilling risks where human decision-making is increasingly replaced by AI

- The availability of AI tools that enable development without full understanding of the technology

- Intellectual property implications of AI systems

- Additional data quality constraints imposed by AI

- The need to educate stakeholders on AI capabilities, failure modes, and failure management

Practical insight for risk managers: The external context requirement to track "[guidelines on ethical use](https://hernanhuwyler.wordpress.com/2026/03/16/responsible-ai-policy-categories/) and design of AI and automated systems issued by government-related groups, regulators, standardization bodies, civil society, academia and industry associations" is broad. Create a regulatory and guidance tracker specific to AI. Assign someone to update it quarterly. The landscape is changing fast enough that annual reviews will miss significant developments.

### Roles and Accountabilities

The standard requires top management and oversight bodies to identify specific individuals with:

- Authority to address AI risks

- Responsibility for establishing and monitoring processes to address AI risks

Notice the standard says "individuals," not "committees." Named accountability matters.

Practical insight: If the person accountable for AI risk management does not have authority over the AI development teams, the role is ceremonial. Verify that the accountability chain has teeth.

### Communication and Consultation

The standard notes that stakeholders affected by AI systems can be "larger than initially foreseen, can include otherwise unconsidered external stakeholders and can extend to other parts of a society." Plan your stakeholder engagement broadly from the start, because discovering a critical stakeholder group after deployment creates reactive crises.

* * *

## Part 4: The Guiding Principles

Clause 4 defines eight risk management principles from ISO 31000. Five of them get AI-specific guidance.

**Inclusive.** AI systems affect more stakeholders than traditional systems. Engage diverse internal and external groups. Stakeholders help identify data risks, define fairness criteria, spot bias, determine where human oversight is needed, and shape transparency and explainability approaches. The standard suggests segmenting transparency frameworks by stakeholder persona (regulators, business owners, model risk evaluators) when a one-size-fits-all approach does not work.

**Dynamic.** AI systems change through continuous learning. Customer expectations shift rapidly. Regulations update frequently. Your risk management process must anticipate, detect, and respond to these changes in real time, not annually.

**Best available information.** Historical data about AI failures may be limited because the technology is relatively new. Future expectations change quickly. Track how your AI systems are used after deployment. Be aware that tracking external usage may be limited by IP, contractual, or market restrictions, and capture those limitations explicitly in your risk process.

**Human and cultural factors.** Monitor how your AI systems interact with pre-existing societal patterns that affect equitable outcomes, privacy, freedom of expression, fairness, safety, security, employment, the environment, and human rights.

**Continual improvement.** Monitor the AI ecosystem for performance successes, shortcomings, lessons learned, and new research findings. Feed previously unknown risks back into the improvement cycle.

* * *

## Part 5: Risk Management Across the AI System Life Cycle

Annex C maps risk management activities to the AI system life cycle defined in ISO/IEC 22989:2022. The life cycle stages are:

1. Inception

3. Design and development

5. Verification and validation

7. Deployment

9. Operation and monitoring

11. Continuous validation

13. Re-evaluation

15. Retirement or replacement

At the organizational level, the governing body sets risk appetite, establishes general criteria, and builds catalogs of risk criteria, risk sources, mitigation measures, monitoring techniques, and reporting formats. These catalogs improve over time as feedback flows up from individual AI system risk processes.

At the project level, each AI system goes through its own risk management cycle at each life cycle stage. Risk criteria, assessments, and treatment plans are established at inception, continuously updated during design and development, verified during testing, potentially adjusted during deployment, and monitored throughout operation.

The key takeaway: risk management is not a phase. It happens at every stage. The standard explicitly shows risk assessment, treatment, monitoring, and recording activities at every life cycle stage, including retirement.

Practical insight for data scientists: The re-evaluation stage is often skipped. The standard requires that existing risk sources be examined for relevance, criteria re-evaluated against changes in scope or purpose, and regulatory updates incorporated. Build re-evaluation triggers into your model governance process. Any change in model purpose, data source, or regulatory environment should start a re-evaluation cycle.

Practical insight for AI security analysts: The retirement stage creates specific risks. When you decommission an AI system, you can lose decision expertise and institutional knowledge embedded in that system. If a replacement system is deployed, the way the organization processes information and makes decisions changes. Both of these transitions create attack surface changes and knowledge gaps that need to be assessed as security risks.

* * *

## What to Do Monday Morning

If you are a risk manager: start with the AI system inventory. You cannot manage risks you do not know exist. Then map your stakeholders using the nine-category list. Then compare your existing risk criteria against the AI-specific factors in Table 4 of the standard.

If you are a data scientist: read Annex B on risk sources, particularly section B.5 on machine learning risks. Then review your current model documentation against the recording requirements in Clause 6.7. The gap between what you document today and what the standard requires is likely significant.

If you are an AI security analyst: start with Annex A sections on security (A.11), privacy (A.8), and robustness (A.9). Map your current threat model against the AI-specific attack surfaces the standard identifies: data poisoning, adversarial attacks, model stealing. Then check whether your security controls cover the full AI system life cycle or only the deployment and operation stages.

The standard gives you the structure. The work is in applying it honestly to your specific systems, your specific organization, and your specific stakeholders. That is where the real risk management happens.

## Key References and Related Standards

ISO/IEC 23894 does not exist in isolation. It references and connects to a broader ecosystem of standards that together form a comprehensive AI governance framework.

ISO 31000:2018, Risk management, Guidelines. This is the foundational standard. ISO/IEC 23894 is built directly on top of it.

ISO/IEC 22989:2022, Artificial intelligence, Concepts and terminology. Provides the AI-specific definitions and the system life cycle model referenced throughout 23894.

ISO Guide 73:2009, Risk management, Vocabulary. Defines the risk management terms used in both 31000 and 23894.

ISO/IEC 38507:2022, Governance implications of the use of artificial intelligence by organizations. Covers the governance layer that sits above risk management.

ISO/IEC TR 24028:2020, Overview of trustworthiness in artificial intelligence. Provides background on AI trustworthiness that informs several sections of 23894.

ISO/IEC TR 24027:2021, Bias in AI systems and AI-aided decision making. Essential reading for the fairness-related risk identification and analysis sections.

ISO/IEC 29134:2017, Guidelines for privacy impact assessment. Directly relevant when AI systems process personal data.

ISO/IEC 27005:2022, Guidance on managing information security risks. Covers the security dimension of AI risk, including threats like data poisoning and adversarial attacks.

NIST AI Risk Management Framework (AI RMF 1.0). While not referenced in the standard, this U.S. framework maps closely to ISO/IEC 23894 and is increasingly expected by American regulators and enterprise customers.

EU AI Act (Regulation 2024/1689). The European regulation that makes AI risk management a legal obligation for high-risk AI systems. ISO/IEC 23894 provides a structured path toward many of its requirements.

## Supporting AI ISO standards by Topic

### **Core AI Management & Governance Standards**

- **ISO/IEC 42001:2023** – Information technology — Artificial intelligence — Management system (AIMS).

- **ISO/IEC 38507:2022** – Governance implications of the use of AI by organizations.

- **ISO/IEC 23894:2023** – Guidance on risk management for AI.

- **ISO/IEC 42005:2025** – AI system impact assessment.

- **ISO/IEC 42006:2025** – Requirements for auditing bodies providing AI management system certification.

### **Foundational Frameworks & Terminology**

- **ISO/IEC 22989:2022** – AI concepts and terminology.

- **ISO/IEC 23053:2022** – Framework for AI systems using Machine Learning.

- **ISO/IEC 5338:2023** – AI system life cycle processes.

- **ISO/IEC 5339:2024** – Guidance for AI applications.

### **Trustworthiness, Ethics & Quality**

- **ISO/IEC 24028:2020** – Overview of trustworthiness in artificial intelligence.

- **ISO/IEC 24368:2022** – Overview of ethical and societal concerns.

- **ISO/IEC 25059:2023** – Quality model for AI systems (SQuaRE).

- **ISO/IEC 12791:2024** – Treatment of unwanted bias in ML tasks.

- **ISO/IEC 12792:2025** – Transparency taxonomy for AI systems.

- **ISO/IEC 42119-2:2025** – Testing of AI systems — Part 2: Test data and results.

- **ISO/IEC 4213:2022** – Assessment of machine learning classification performance.

### **Data Quality & Analytics**

- **ISO/IEC 24668:2022** – Process management framework for big data analytics.

- **ISO/IEC 5259-1:2024** – Data quality for analytics and ML — Part 1: Overview and terminology.

- **ISO/IEC 5259-3:2024** – Data quality management requirements and guidelines.

- **ISO/IEC 5259-4:2024** – Data quality process framework.

## The Choice in Front of You

Organizations that treat ISO/IEC 23894 as a compliance artifact will produce binders full of risk assessments that nobody reads, risk registers that go stale within weeks, and governance structures that exist on paper but have no operational authority. When something goes wrong, and with AI systems something eventually does go wrong, they will discover that their documentation protected nobody. Not the organization, not the individuals affected by the AI system, and not the communities that bore the consequences.

Organizations that treat ISO/IEC 23894 as a living operational tool will build AI risk management into their development pipelines, their deployment decisions, and their ongoing monitoring. They will have named individuals with real authority, risk criteria grounded in evidence, stakeholder engagement that surfaces risks early, and records that tell a coherent story from inception through retirement. When something goes wrong, they will know about it faster, respond more effectively, and demonstrate to regulators that they took reasonable steps.

The standard gives you the blueprint. What you build with it depends entirely on whether you treat AI risk management as paperwork or as practice.

To maximize **SEO authority** and drive high-value traffic back to your core assets, this "About the Author" section is restructured to emphasize your specific expertise in the **EU AI Act**, **Quantitative Risk**, and **ISO 42001**. I have humanized the tone to move from a standard bio to a "Partnership Invitation," while ensuring the links are prominent and descriptive.

* * *

## **About the Author: Prof. Hernan Huwyler, MBA, CPA, CAIO**

The frameworks, taxonomies, and implementation toolkits shared in this article are part of the ongoing applied research and executive advisory work of **Prof. Hernan Huwyler**. These materials are designed for operational realism and are freely available for adaptation in your own **AI Governance, Risk Management, and Compliance (GRC)** programs under proper attribution.

### **Bridging the Gap Between AI Theory and Production Controls**

As an **AI GRC Strategy Director** and **Quantitative Risk Lead**, Prof. Huwyler works with global organizations in financial services, healthcare, and the public sector to build frameworks that survive both production demands and regulatory scrutiny. His expertise is focused on tje risk-adjusted AI adoption, ensuring that innovation remains defensible through rigorous **algorithmic auditing** and **automated compliance protocols**.

### **Global Thought Leadership and Executive Education**

Based in the Copenhagen Metropolitan Area with a professional presence in Zurich, Geneva, Madrid, and Berlin, Prof. Huwyler operates where AI development is most active. He serves as an **Executive Advisor** and **Academic Director at IE Law School**, delivering specialized corporate training on:

- **EU AI Act Compliance Strategy** and **ISO 42001** integration.

- **Quantitative Risk Modeling** using Python and Monte Carlo simulations.

- **Predictive Risk Automation** for Board-level decision-making.

### **Explore Open-Source GRC Tools and Insights**

Prof. Huwyler maintains a public repository of **Python-based AI governance tools**, risk model templates, and automated compliance scripts to support the global practitioner community.

- **Technical Tools & Code:** Access the **[GitHub Repository](https://hwyler.github.io/hwyler/)** for risk model templates.

- **Expert Commentary:** Read the latest on GRC and Internal Audit at **[The Daily Executive Blog](https://mydailyexecutive.blogspot.com/)**.

- **Professional Network:** Connect on **[LinkedIn](https://www.linkedin.com/in/hernanwyler/)** to follow real-time updates on the evolving AI regulatory landscape.

* * *

### **Let’s Turn AI Governance into a Competitive Advantage**

If you are ready to move beyond "check-the-box" compliance and start capturing the **positive ROI of AI**, let’s connect. True governance isn't about slowing down; it’s about creating the structural discipline needed to achieve **massive savings through automation** and to build **new, resilient revenue streams** that regulators and customers can trust.
