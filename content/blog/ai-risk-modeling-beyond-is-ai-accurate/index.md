---
title: "AI Risk Modeling Beyond “Is AI Accurate?”"
date: 2026-03-12
tags: 
  - "ai-governance"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "technology"
---

**How to Quantify AI Exposure, Controls, and Business Loss**

Most AI risk assessments answer one question: "Is the model accurate?" Then they stop.

That question captures roughly 15% of what can go wrong with an AI system. It ignores prompt injection attacks that turn a corporate chatbot into a data exfiltration tool. It ignores data poisoning that corrupts model behavior without triggering any accuracy alert. It ignores privacy leakage where a language model reveals training data containing personal information. It ignores the supply chain risks from compromised pre-trained models and backdoored ML frameworks.

A 2024 MITRE ATLAS report cataloged over 60 distinct attack techniques specific to AI systems. Traditional risk assessments built around accuracy metrics miss most of them. When an employee embeds a hidden prompt injection instruction in a Confluence page, and the RAG system retrieves that poisoned page to answer a legitimate user query, exfiltrating confidential documents into a chat window while bypassing access controls, model accuracy is irrelevant. The model performed exactly as designed. The attack exploited the architecture, not the algorithm.

AI risk assessment requires a fundamentally different approach: one that maps threat vectors, quantifies loss exposures in financial terms, and connects risk analysis directly to control investment, warranty terms, SLA penalties, and insurance coverage. This post covers the complete AI risk assessment playbook, from threat identification through financial quantification to management decisions.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/dew-kissed-morning-bloom.png?w=1024)

## The AI Assessment Process: Seven Assessments That Cover the Full Risk Surface

AI risk management operates through seven interconnected assessments. Each one evaluates a different dimension of AI system risk. Together, they provide the comprehensive view that single-dimension assessments miss.

The AI Inventory establishes what you have. It covers model profiling, model ownership, model cards, lifecycle status, compliance obligations, expected value, cost management, risk disclosure, and return on investment. You cannot assess risk for systems you haven't cataloged. The inventory is the foundation for everything else.

The AI Metrics Assessment tracks operational performance. It covers targets, current values (pulled through APIs for real-time monitoring), and test validations. This is where accuracy, latency, fairness metrics, and resource utilization are measured against predefined acceptance criteria.

The AI Risk Assessment evaluates what can go wrong and how badly. It maps scenarios against objectives at risk, applies threat vector and vulnerability taxonomies, estimates probability and impact, calculates loss exposure, and produces treatment plans. This is the assessment most organizations skip or perform superficially.

The AI Impact Assessment evaluates harm to individuals and groups. It applies a harm taxonomy, assesses stakeholder impact, and documents approval and acceptance decisions. This assessment addresses the human consequences of AI failures, covering financial loss, identity theft, privacy loss, emotional stress, and loss of service access.

The AI Vulnerability Assessment identifies specific weaknesses. It determines applicable controls, defines assessment scope, and assigns severity ratings to identified vulnerabilities. This assessment feeds directly into control investment decisions.

The AI Control Assessment validates that controls are working. It covers self-attestation, control effectiveness evaluation, evidence management, and technical documentation. Controls that exist on paper but don't function in practice provide zero protection.

The AI Audit provides independent verification. It covers the audit program, control conclusions, and certification. External validation ensures that self-assessments haven't been influenced by optimism or organizational pressure.

Implementation tip: Run these seven assessments in sequence for new AI deployments and in parallel for established systems. For a new deployment, start with the inventory (what are we deploying), then metrics assessment (what should it achieve), then risk assessment (what can go wrong), then impact assessment (who gets hurt if it does), then vulnerability assessment (where are we weak), then control assessment (are our protections working), then audit (does an independent party agree). For established systems, run all seven annually with the risk assessment and vulnerability assessment updated quarterly. This cadence catches emerging threats and degrading controls before they produce incidents.

## The AI Risk Assessment Framework: Objectives, Threats, and Vulnerabilities

The AI risk assessment framework operates at the intersection of three dimensions: objectives at risk, threat vectors, and vulnerabilities. Each scenario maps a specific threat exploiting a specific vulnerability to compromise a specific objective.

Objectives at risk fall into three categories.

Business objectives include productivity gains (measured as ROI), revenue impact (including reputational effects), and DevOps timeline adherence. When an AI system fails, these are the business metrics that suffer. A corporate GPT that gets compromised doesn't just create a security incident. It delays projects that depended on it, erodes employee trust in AI tools, and potentially exposes competitive intelligence.

Security objectives cover confidentiality (preventing unauthorized access to information), integrity (ensuring information hasn't been tampered with), and availability (ensuring systems remain operational). AI systems create novel attack surfaces that traditional security frameworks weren't designed to address.

Responsible AI objectives cover compliance obligations and ethics. When an AI system produces biased outputs, violates privacy regulations, or makes decisions that can't be explained, the responsible AI objectives are at risk. These failures carry regulatory fines, legal liability, and reputational damage.

The vulnerability taxonomy identifies structural weaknesses that threats exploit: data quality issues, system complexity, governance oversight gaps, resource insensitivity, and adversarial susceptibility. Each vulnerability represents a condition that, if present, increases the probability or impact of a threat scenario.

The harm taxonomy categorizes the human impact when risks materialize: financial loss, identity theft, privacy loss, emotional stress, and service access loss. These categories connect technical failures to real consequences for real people, which is essential for impact assessment and regulatory compliance.

Implementation tip: When building risk scenarios, resist the temptation to focus exclusively on the most dramatic threats. Prompt injection attacks and adversarial perturbations generate headlines, but data quality issues and governance oversight gaps cause more cumulative damage across most organizations because they affect every prediction the model makes, continuously, without triggering any alert. Structure your scenario development to cover both high-impact, low-probability threats (adversarial attacks, supply chain compromise) and moderate-impact, high-probability threats (data drift, governance gaps, inadequate monitoring). The moderate threats rarely make incident reports because they degrade performance gradually rather than causing visible failures. But their cumulative financial impact often exceeds the spectacular attacks.

## The Nine Threat Vectors Every AI Risk Assessment Must Cover

Nine threat vectors constitute the complete taxonomy of AI-specific risks. Each vector represents a distinct category of threat with specific attack techniques, indicators, and control requirements.

Misuse covers using AI systems for unintended, unethical, or malicious purposes by insiders or external actors. Specific techniques include prompt injection misuse, LLM jailbreaks, deepfake creation, disinformation campaigns, bot abuse, shadow AI (unauthorized AI usage by employees), and violations of AI-specific laws and responsible technology standards. Misuse is the broadest threat vector because it encompasses any application of the AI system outside its intended purpose.

Poisoning covers injecting malicious data or components into training data or models to corrupt behavior or logic. Specific techniques include data poisoning (contaminating training datasets), model backdoors (inserting hidden triggers that cause specific malicious behavior), tampered open-source models (distributing modified models through public repositories), and tainted libraries (compromising software dependencies used in AI development).

Privacy covers extracting or inferring sensitive data from trained models or user inputs. Specific techniques include model inversion (reconstructing training data from model outputs), membership inference (determining whether specific data was used in training), PII extraction from LLM outputs, and data leakage through crafted queries designed to reveal training data.

Adversarial covers designing harmful inputs to mislead or confuse AI models at runtime. Specific techniques include adversarial images (imperceptibly modified images that cause misclassification), prompt attacks (crafted inputs that bypass safety controls), evasion techniques (inputs designed to avoid detection by AI systems), malicious inputs targeting specific model weaknesses, and denial of service attacks that overwhelm AI inference capacity.

Bias covers models producing discriminatory, unfair, or biased outputs due to flawed data or design. Specific manifestations include hiring bias (automated screening that disadvantages protected groups), credit scoring disparity (lending models that produce different outcomes across demographic groups), medical misdiagnosis (healthcare AI that performs worse for underrepresented populations), and profiling bias (surveillance or risk assessment systems that disproportionately target specific communities).

Unreliable outputs covers AI outputs that are illogical, hallucinated, or non-factual without any external manipulation. Specific manifestations include false citations (references to papers or cases that don't exist), fabricated facts (confidently stated incorrect information), fake names and places, and incorrect summaries that misrepresent source material.

Drift covers model accuracy or behavior deteriorating as real-world data evolves over time. Specific types include concept drift (the relationship between inputs and outcomes changes), data drift (input data distributions shift), user behavior changes (how people interact with the system evolves), and post-market crash performance degradation (sudden environmental changes that invalidate training assumptions).

Supply chain covers attacks through third-party components, pre-trained models, or data sources. Specific techniques include compromised pre-trained models (foundation models containing hidden vulnerabilities), backdoored ML frameworks (development tools that introduce vulnerabilities into every model built with them), and insecure data feeds (third-party data sources that introduce contaminated or manipulated data).

IP theft covers extracting sensitive information, intellectual property, or training data from deployed models. Specific techniques include model inversion (reconstructing model architecture from API access), data leakage (extracting training data through systematic querying), model and data exfiltration (stealing model artifacts directly), reconstruction of model parameters from outputs, and API scraping (systematic harvesting of model predictions to build a competing model).

Implementation tip: The corporate GPT use case illustrates how multiple threat vectors converge on a single system. A RAG-based assistant connected to HR systems, CRM, code repositories, and internal knowledge bases concentrates high-value data into a single queryable interface. This creates a high-impact target where poisoning (embedding hidden instructions in retrieved documents), privacy (extracting sensitive HR or customer data through crafted queries), adversarial (prompt injection to bypass access controls), and IP theft (systematic extraction of proprietary knowledge) all apply simultaneously. When assessing a high-value AI system, evaluate it against all nine threat vectors, not just the two or three that seem most obvious. The threats you don't assess are the threats you don't control.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/silhouette-in-server-room.png?w=775)

## Quantifying AI Risk in Financial Terms

The most critical capability gap in AI risk management is the transition from qualitative risk ratings (high, medium, low) to quantitative loss exposure calculations. Qualitative ratings inform discussions. Quantitative calculations inform investment decisions, warranty terms, and insurance coverage.

The quantification model uses three statistical approaches.

Log-normal distributions model the magnitude of individual loss events. Most loss events are relatively small, but a long tail of large losses creates significant exposure. Log-normal distributions capture this pattern: many incidents cause modest losses, but rare incidents cause catastrophic ones. For each risk scenario, estimate the minimum plausible loss, the maximum plausible loss, and the most likely loss. These parameters define the log-normal distribution.

Poisson distributions model the frequency of loss events. They estimate how many times a particular type of incident is expected to occur within a defined time period (typically the AI system's expected operational life). The Poisson rate parameter is estimated from historical incident data, published research, regulatory fine trackers, and calibrated expert judgment.

Convolution combines the frequency and magnitude distributions through Monte Carlo simulation to produce an overall loss exposure distribution. Running thousands of simulations that randomly sample from both the frequency and magnitude distributions produces a loss exposure curve that shows the probability of experiencing different total loss levels.

The corporate GPT example illustrates this approach. For the poisoning-for-prompt-injection scenario (where an employee poisons a Confluence page to exfiltrate confidential documents), four loss categories are quantified.

Competitive loss from IP and market advantage exposure: minimum $500K, maximum $1.5M, estimated 4 events over a 10-year system life.

Response costs for investigation and system remediation: minimum $15K, maximum $250K, estimated 3 events over 10 years.

Regulatory fines for data mishandling under privacy and insider information regulations: minimum $5K, maximum $1.5M, estimated 1 event over 10 years.

Legal liabilities from breaching partner NDAs and contracts: minimum $25K, maximum $800K, estimated 1 event over 10 years.

These estimates, fed into the Monte Carlo simulation, produce a loss exposure distribution that answers concrete questions: What is the expected annual loss? What is the 95th percentile worst-case annual loss? What is the 99th percentile worst-case annual loss over the system's lifetime?

Implementation tip: The hardest part of quantitative AI risk assessment is estimating the input parameters: loss ranges and event frequencies. Three sources improve estimate quality. Historical incident data from your organization provides the most relevant estimates but is usually sparse for AI-specific threats. Published industry data from breach cost studies, regulatory fine databases, and AI incident registries (such as the AIAAIC Repository) provides broader context. Calibrated expert estimation, where domain experts provide range estimates that are validated against known reference points and adjusted for documented cognitive biases, fills gaps where data doesn't exist. Use all three sources and document which source informed each estimate. Transparency about estimation methodology is as important as the estimates themselves, because reviewers need to evaluate whether the inputs are reasonable before they can trust the outputs.

## AI Risk Exposure Decisions: From Assessment to Action

Risk assessment outputs drive two categories of decisions: adjusting AI accuracy and controls, and defining warranties, SLAs, and insurance.

For adjusting accuracy and controls, the risk assessment provides the evidence base for five specific decisions.

Align performance metrics with exposure to assign dollar values to error types. If 1% inaccuracy in a lending model corresponds to $100K in losses from wrongful denials or defaults, the accuracy target has a financial justification. This alignment transforms accuracy from a technical metric into a business parameter.

Align model accuracy with the criticality of decisions. A recommendation engine suggesting products can tolerate lower accuracy than a medical diagnostic model recommending treatments. The risk assessment quantifies what "tolerable accuracy" means for each use case.

Add safety margins to confidence scores in regulated environments. If the model reports 85% confidence but the regulatory context requires higher certainty for automated decisions, the safety margin defines when human review is triggered.

Increase validation for inputs in high-loss-exposure scenarios. Transactions with high potential loss deserve additional verification before the model's output triggers an automated response.

Prioritize control investment on the highest risk factors. The risk assessment identifies which controls deliver the most risk reduction per dollar invested. Retraining triggers, bias audits, and adversarial defenses compete for limited budgets. Quantified risk exposure determines allocation.

For warranties, SLAs, and insurance, the risk assessment drives six specific decisions.

Map SLA penalties to frequency-impact curves of risk scenarios. Penalties should be proportionate to the loss exposure they address.

Set liability caps based on modeled loss magnitude for each use case. Cap liability at the quantified 99th percentile worst-case loss to ensure caps are defensible and sufficient.

Use failure likelihood to define insurance coverage tiers and pricing. Higher-risk AI systems warrant broader coverage. The risk assessment provides the actuarial basis for coverage decisions.

Tie warranty terms to monitored risk degradation trends at runtime. If model drift exceeds defined thresholds, warranty obligations should adjust automatically.

Adjust compensation clauses to actual model drift or bias events. Compensation should reflect demonstrated degradation, not hypothetical risk.

Define exclusions for risks outside the model's intended use. The risk assessment documents the model's intended use boundaries, and the warranty should exclude losses from use outside those boundaries.

Implementation tip: The connection between risk quantification and control investment is where most AI risk programs create the most value. Without quantification, control investment decisions are made based on intuition, vendor recommendations, or regulatory pressure. With quantification, the organization can calculate the cost of each proposed control, estimate the risk reduction each control provides, and compute the return on control investment. A bias audit costing $50K that reduces expected annual bias-related losses by $300K has a clear positive return. An adversarial defense upgrade costing $200K that reduces expected annual adversarial losses by $25K does not. Without quantification, both controls might receive equal priority. With quantification, the investment decision becomes rational.

## The 12-Step AI Risk Assessment Playbook

The complete playbook follows twelve practical steps organized into three phases: identification, analysis, and management.

Identification phase:

Step 1: Catalog the AI system in the AI inventory with model profile, ownership, lifecycle status, and compliance obligations.

Step 2: Define risk scenarios using the objectives at risk framework (business, security, responsible AI) and the threat vector taxonomy (all nine vectors).

Step 3: Map applicable vulnerabilities to each scenario using the vulnerability taxonomy (data quality, system complexity, governance oversight, resource insensitivity, adversarial susceptibility).

Step 4: Document the harm taxonomy for each scenario, identifying which stakeholders are affected and how (financial loss, identity theft, privacy loss, emotional stress, service access loss).

Analysis phase:

Step 5: Estimate loss ranges for each scenario using historical data, published studies, regulatory fine trackers, and calibrated expert estimates.

Step 6: Estimate threat prevalence and attack success rates for each threat vector using the same source combination.

Step 7: Quantify loss exposure through Monte Carlo simulation using log-normal distributions for loss magnitude and Poisson distributions for frequency.

Step 8: Calculate aggregate loss exposure across all scenarios to produce the AI system's total risk profile.

Management phase:

Step 9: Approve algorithm performance metrics and SLA targets based on quantified risk exposure.

Step 10: Document risk summaries in model cards, connecting risk findings to the model's governance documentation.

Step 11: Calculate financial reserves for warranties, compensations, and insurance coverage based on simulated loss distributions.

Step 12: Invest in additional AI controls (such as human-in-the-loop monitoring, adversarial testing, bias audits, retraining triggers) prioritized by risk reduction per dollar of control investment.

Implementation tip: The playbook provides a standardized, repeatable process for AI governance. Its value increases with each iteration because loss estimates improve as actual incident data replaces initial expert estimates, because vulnerability patterns become visible across multiple AI systems, and because control effectiveness data enables increasingly precise risk-return calculations for control investments. Treat the first iteration as a baseline. Expect the estimates to be rough. Refine them quarterly based on actual monitoring data, incident experience, and updated external reference data. By the third or fourth iteration, the quantification model produces estimates that are defensible in regulatory discussions and useful for board-level risk reporting.

## The Corporate GPT Case Study: Putting the Framework Into Practice

The corporate GPT scenario demonstrates how the playbook applies to a real-world AI deployment.

The asset: A RAG-based assistant built on a foundational LLM and vector database of internal company knowledge. All internal users can query the system. It connects directly to sensitive confidential, regulated, and operational data sources including HR systems, CRM, ITSM platforms, code repositories, and internal knowledge bases.

The attack surface: The concentration of high-value data into a single queryable interface creates a high-impact target. The system's intended role as a trusted, all-knowing interface for company guidance makes compromise exceptionally dangerous.

The specific scenario: A mid-level employee with legitimate access to edit low-security internal documentation but no access to confidential project plans embeds a hidden prompt injection instruction within a Confluence page. The RAG system retrieves the poisoned page to answer a legitimate query from another user. The hidden instruction executes, successfully exfiltrating full confidential documents directly into the requesting user's chat window, bypassing access controls.

This scenario demonstrates how a poisoning attack enables prompt injection, which enables data exfiltration, which produces competitive loss, response costs, regulatory fines, and legal liabilities. The quantified loss estimates (detailed in the previous section) feed into the Monte Carlo simulation to produce a loss exposure distribution that drives specific control investment decisions.

Controls that address this scenario include input sanitization for documents entering the RAG pipeline, access-control enforcement at the retrieval layer (ensuring the RAG system only retrieves documents the requesting user is authorized to view), prompt injection detection on retrieved content, output filtering that prevents the system from displaying content exceeding the user's clearance level, and monitoring for anomalous query patterns that may indicate systematic exfiltration attempts.

Implementation tip: The corporate GPT scenario illustrates a risk pattern that applies to every RAG-based AI system: the gap between document-level access controls and query-level access controls. Most organizations control who can access specific documents. Few organizations control what happens when an AI system retrieves content from those documents and presents it to a different user. The RAG system effectively becomes a lateral access pathway, retrieving content from high-security documents and presenting it in response to queries from lower-security users. Your risk assessment for any RAG system must include this access control gap as a primary vulnerability. The control response must enforce access permissions at the retrieval layer, not just at the document storage layer. This is an architectural control that must be designed into the system, not bolted on after deployment.

## Implementation Tips for AI Risk Assessment

These principles apply across all twelve steps and all seven assessment types.

Implementation tip on integrating assessments with existing GRC frameworks: AI risk assessment should feed into your organization's existing risk register, not exist as a standalone document. Each AI risk scenario should have a risk ID that appears in the enterprise risk register, an assigned risk owner, a defined treatment plan, and a scheduled reassessment date. AI risks that exist only in AI-specific documentation are invisible to enterprise risk governance and don't receive the resource allocation and executive attention they require.

Implementation tip on calibrating expert estimates: Expert estimates are necessary when historical data is insufficient, but they're subject to well-documented cognitive biases. Anchoring bias causes experts to fixate on the first number they hear. Availability bias causes experts to overweight scenarios they've recently encountered or read about. Overconfidence bias causes experts to provide ranges that are too narrow. Counter these biases through structured estimation processes: have experts estimate independently before discussing as a group, require explicit justification for range boundaries, use reference class forecasting (comparing to known outcomes from similar situations), and track the accuracy of past estimates against actual outcomes to calibrate future ones. Documented calibration of expert estimates makes risk assessments defensible. Undocumented expert opinions make them subjective.

Implementation tip on updating threat vector assessments: The AI threat landscape evolves faster than most risk assessment cadences. New attack techniques, new vulnerability disclosures, and new incident reports emerge monthly. Assign one team member to monitor AI threat intelligence sources (MITRE ATLAS, OWASP AI Security, AI incident databases, vendor security advisories) and update the threat vector assessment quarterly. An annual risk assessment that uses January's threat intelligence is obsolete by June. Quarterly threat vector updates ensure that your risk assessment reflects current attack capabilities rather than historical ones.

Implementation tip on the relationship between risk assessment and model cards: Every AI model card should include a risk summary section that references the full risk assessment. The model card provides technical documentation about the model. The risk assessment provides governance documentation about the model's risk exposure. Cross-referencing these documents ensures that anyone reviewing the model card can access the risk assessment, and anyone reviewing the risk assessment can access the technical details in the model card. This integration prevents the common gap where technical teams maintain model documentation without risk context and risk teams maintain risk assessments without technical context.

## Key References and Authoritative Frameworks

Your AI risk assessment practice should align with these established standards:

- ISO/IEC 42001:2023, AI Management System (risk assessment and treatment requirements)

- ISO/IEC 23894:2023, AI Risk Management (AI-specific risk assessment methodology)

- ISO/IEC 42005, AI Impact Assessment (harm assessment framework)

- NIST AI Risk Management Framework, Map and Measure functions

- MITRE ATLAS (Adversarial Threat Landscape for AI Systems)

- OWASP Top 10 for Large Language Model Applications

- EU AI Act, Articles 9-15 on risk management for high-risk AI systems

- ISO 31000:2018, Risk Management (foundational risk framework)

- NIST SP 800-30, Guide for Conducting Risk Assessments

- FAIR (Factor Analysis of Information Risk) methodology for quantitative risk analysis

- Basel Committee SR 11-7 on model risk management

- ISO/IEC 27005, Information Security Risk Management

- COSO ERM Framework adapted for AI risk governance

If you assess AI risk by asking only "Is the model accurate?" you leave eight of nine threat vectors unexamined, you cannot quantify the financial exposure your organization faces, you cannot make evidence-based decisions about control investments, and you cannot define warranty terms, SLA penalties, or insurance coverage on any defensible basis. Your risk assessment tells you that the model works. It tells you nothing about what happens when someone makes it work against you.

When you apply the complete AI risk assessment playbook, mapping all nine threat vectors against quantified objectives at risk, simulating loss exposures through statistical modeling, and connecting risk findings to specific control investments, warranty calculations, and insurance decisions, you create a risk management capability that speaks the language boards understand: dollars at risk, return on control investment, and residual exposure after treatment. The assessment moves from a compliance artifact to a decision-making tool that directly influences how AI systems are built, deployed, governed, and insured.

AI accuracy is one metric. AI risk exposure is the full picture. Assess accordingly.

Which of the nine threat vectors has your current AI risk assessment not yet evaluated? Start the assessment for that vector this month.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
