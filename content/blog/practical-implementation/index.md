---
title: "Practical AI Compliance Implementation"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-governance"
  - "ai-projects"
  - "ai-risk-management"
  - "ai-roi"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "iso-42001"
  - "technology"
---

# Tips for an AI Legal Compliance Audit Program

## I. AI Governance and Oversight

Every AI compliance audit starts here. Without governance structure, every other audit area produces findings with no owner to remediate them.

**What to audit:**

Verify that the organization has a documented AI governance framework with clear accountability at the board or executive committee level. Check whether a named individual, such as a Chief AI Officer, holds explicit responsibility for AI compliance. Confirm that the governance structure defines decision rights for AI system approval, deployment, modification, and decommissioning.

Review meeting minutes from the governance body. Determine whether AI risk and compliance topics appear as standing agenda items with documented decisions, not just informational updates. Check whether the governance body receives regular reporting on AI system performance, incidents, and regulatory changes.

Verify that AI governance policies are reviewed at defined intervals and updated when business circumstances, legal requirements, or technical environments change. Confirm that the governance framework addresses all organizational roles with respect to AI: development, procurement, operation, and use.

**Original implementation tip:** Most organizations create a governance charter and file it. Audit the governance body's effectiveness, not just its existence. Pull the last six months of meeting minutes. Count how many decisions were made versus how many items were "noted." If the body only receives reports and never makes binding decisions about AI system deployment, risk acceptance, or policy exceptions, it's a governance theater. Flag it. Effective governance produces documented decisions with assigned owners and deadlines. If you can't find those in the minutes, the structure isn't functioning regardless of how well the charter reads.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/futuristic-office-with-digital-interface.png?w=1024)

* * *

## II. AI Inventory and Assessment

You can't audit what you can't find. Most organizations undercount their AI systems by a significant margin.

**What to audit:**

Confirm that the organization maintains a comprehensive inventory of all AI systems in development, production, and decommissioned status. The inventory should cover internally developed systems, third-party procured systems, embedded AI components within larger platforms, and AI features activated within existing enterprise software.

Each inventory entry should document the system's intended purpose, the business process it supports, the data it processes, the AI techniques it uses, the deployment environment, the responsible owner, the date of last validation, and the risk classification tier.

Verify the completeness of the inventory by cross-referencing against procurement records, cloud service agreements, API consumption logs, and IT asset management databases. Test whether shadow AI, meaning systems deployed without governance approval, exists by sampling business units and interviewing process owners.

**Original implementation tip:** Send a structured survey to every department head asking three questions. Does your team use any tool that makes predictions, recommendations, classifications, or automated decisions? Does any vendor you use describe their product as using AI, machine learning, or automation? Has anyone on your team built or customized a model using Python, R, or any analytics platform? The third question catches the data science experiments running on individual laptops that never entered the official inventory. I've found production-grade models influencing real business decisions running from a senior analyst's desktop machine, completely invisible to IT and governance. The survey surfaces these within a week.

* * *

## III. Impact Assessments and Risk Mitigation

Impact assessments determine whether an AI system creates unacceptable risks for individuals, groups, or society. Most organizations either skip them entirely or treat them as checkbox exercises.

**What to audit:**

Verify that the organization has a documented procedure defining when an AI system impact assessment is required, who performs it, what methodology is used, and how results feed into deployment decisions.

Check whether impact assessments cover effects on legal positions and life opportunities of individuals, physical and psychological well-being, fundamental rights, fairness across demographic groups, environmental sustainability, and societal implications.

Review a sample of completed impact assessments. Confirm they include identification of potential harms, analysis of likelihood and severity, evaluation of acceptability, treatment measures with assigned owners, and documentation of residual risk accepted by an authorized person.

Verify that impact assessments are reassessed when the AI system's purpose, scope, data inputs, or operating environment changes materially.

**Original implementation tip:** Pull three completed impact assessments and trace their findings forward. Did any identified risk result in a design change, a new control, or a deployment restriction? If every impact assessment concludes with "risk is acceptable" and no mitigation actions, the process isn't functioning as a genuine risk filter. It's a rubber stamp. The audit finding isn't about the document quality. It's about whether the assessment ever changes an outcome. If it doesn't, the organization is accumulating liability while believing it's managing it.

* * *

## IV. Data Confidentiality and Security

AI systems process data at scale. The confidentiality and security controls around that data often lag behind what organizations apply to their traditional systems.

**What to audit:**

Verify that data classification policies explicitly cover data used in AI system development and operation, including training data, validation data, test data, and production inference data.

Confirm that access controls for training datasets and model artifacts are at least as restrictive as the highest classification of data contained within them. Check whether training data containing personally identifiable information (PII) is handled in compliance with applicable privacy regulations (GDPR, CCPA, or jurisdiction-specific equivalents).

Review whether encryption standards are applied to data at rest and in transit for AI system data pipelines. Verify that data retention and disposal policies are applied to AI-specific data, including intermediate datasets, feature stores, and model training logs.

Test whether AI development environments (notebooks, experimentation platforms, model registries) are included in the organization's vulnerability management and penetration testing scope.

Audit data anonymization and pseudonymization techniques applied to training data. Verify that re-identification risk has been assessed.

**Original implementation tip:** Most security teams include production AI systems in their scope but exclude development environments. That's where the real exposure lives. Data scientists routinely copy production data into development notebooks for experimentation. Those notebooks often run on personal machines or unmanaged cloud instances with no encryption, no access logging, and no data loss prevention controls. Audit the development environment specifically. Check whether training data can be exported from managed environments to unmanaged ones. If a data scientist can download a dataset containing customer PII to their laptop without triggering any alert, you have a material finding. It happens more often than security teams realize.

* * *

## V. AI Vendor Management

When you procure an AI system, you import the vendor's risk. Your regulatory obligations don't transfer.

**What to audit:**

Verify that the organization has an AI-specific vendor risk assessment process that supplements the standard third-party risk management framework. Confirm that AI vendor assessments cover model transparency, training data provenance, bias testing evidence, performance benchmarks, incident notification commitments, and audit rights.

Review a sample of AI vendor contracts. Check for clauses covering model update notification requirements, performance service level agreements with measurable metrics, data handling and privacy obligations, intellectual property ownership of model outputs and fine-tuned models, right to audit, right to require corrective actions, and termination rights if performance degrades below thresholds.

Verify that the organization conducts its own independent validation of vendor AI models using its own data rather than relying solely on vendor-provided validation results.

Confirm that vendor AI systems are included in the organization's continuous monitoring program with drift detection applied to vendor model outputs.

**Original implementation tip:** Request the vendor's model card or technical documentation during procurement. If the vendor can't provide basic information about training data sources, known limitations, fairness testing methodology, and performance benchmarks, document that refusal as a risk finding. Then ask yourself whether you'd accept a financial product from a bank that refused to disclose its methodology. The same standard should apply. I maintain a standard AI vendor due diligence questionnaire with 25 questions. Most vendors can answer about 10 of them today. The gap between what you asked and what they answered becomes your residual risk register entry, and it gives you contractual leverage to demand improvements.

* * *

## VI. Transparency

Transparency requirements are expanding across jurisdictions. The EU AI Act, various US state laws, and sector-specific regulations increasingly require organizations to disclose when AI is being used and how it makes decisions.

**What to audit:**

Verify that the organization has identified all AI systems that interact with individuals, whether customers, employees, applicants, or members of the public.

Confirm that users are notified when they are interacting with an AI system. Check whether the notification is clear, timely, and accessible. Review the content of disclosures for accuracy and completeness.

For AI systems that produce decisions affecting individuals' rights or opportunities, verify that the organization can provide a meaningful explanation of how the system reached its output. "Meaningful" means understandable to the affected person, not just to a data scientist.

Check whether AI-generated content, such as images, text, or synthetic media, is labeled as AI-generated where required by applicable regulations.

Review transparency documentation for different audience types. Technical users, business decision-makers, affected individuals, and regulators each need different levels of detail.

**Original implementation tip:** Test transparency from the end-user's perspective. Go through the customer or employee journey that involves an AI system and note every point where you should be informed that AI is involved. Compare what you find against what the organization documents as its transparency controls. I've done this exercise at organizations that believed they had full transparency compliance and found customer-facing chatbots with no AI disclosure, automated hiring screening with no candidate notification, and credit decisioning with no explanation mechanism. The gap between what the compliance team believes is disclosed and what the end user actually sees is almost always larger than expected. Document it with screenshots.

* * *

## VII. Incident Response and User Rights

AI systems fail. When they do, the organization needs a response mechanism that addresses both the technical failure and the rights of affected individuals.

**What to audit:**

Verify that the organization's incident response plan explicitly covers AI system incidents, including model failures, biased outputs, data breaches in AI pipelines, adversarial attacks (data poisoning, model inversion, prompt injection), and unintended autonomous actions.

Confirm that incident classification criteria distinguish between AI-specific incidents and general IT incidents. An AI system producing systematically biased credit decisions is a different category of incident from a server outage, and it requires different response procedures.

Check whether the organization has a process for affected individuals to exercise their rights regarding AI decisions. This includes the right to human review of automated decisions, the right to an explanation, the right to contest an AI-driven decision, and the right to opt out of automated decision-making where applicable.

Verify that incident response timelines comply with applicable regulations. The EU AI Act requires reporting serious incidents to market surveillance authorities. GDPR requires breach notification within 72 hours. Sector-specific regulations may impose additional timelines.

Review incident logs for the past 12 months. Check whether AI-related incidents were captured, investigated, root-caused, and remediated with documented evidence.

**Original implementation tip:** Run a tabletop exercise simulating an AI-specific incident. Choose a scenario where a high-risk AI system produces discriminatory outcomes that affect a protected group, media coverage begins, and a regulator requests information. Walk through the response process and document every point where the team doesn't know what to do, who to notify, or where to find the required documentation. Most incident response plans were written for traditional IT incidents. They break down when the incident involves algorithmic bias, explainability demands, or fundamental rights complaints. The tabletop exercise exposes those gaps in two hours. Fix them before a real incident does.

* * *

## VIII. Geographic and Cross-Border Compliance

AI regulation varies dramatically by jurisdiction. An AI system legal in one country may be prohibited or heavily regulated in another.

**What to audit:**

Verify that the organization has mapped every AI system against the jurisdictions where it operates, where it processes data, where it affects individuals, and where it is developed.

Confirm that the organization has identified applicable AI-specific regulations by jurisdiction. Key regulations to map include the EU AI Act (for any system affecting EU individuals or deployed within the EU), GDPR Article 22 (automated individual decision-making), US state laws such as Colorado's AI Act, Illinois BIPA for biometric AI, NYC Local Law 144 for automated employment decision tools, China's AI regulations including the Algorithm Recommendation Regulation and Deep Synthesis Provisions, Canada's proposed AIDA, Brazil's LGPD provisions on automated decisions, and sector-specific regulations in financial services, healthcare, and employment.

Verify that cross-border data transfers supporting AI systems comply with applicable data transfer mechanisms (Standard Contractual Clauses, adequacy decisions, binding corporate rules).

Check whether the organization monitors regulatory developments across its operating jurisdictions and has a process for assessing the impact of new regulations on existing AI systems.

**Original implementation tip:** Build a jurisdiction-by-system matrix. List every AI system in rows and every jurisdiction where it has exposure in columns. In each cell, note the applicable regulation and the compliance status (compliant, gap identified, assessment pending). Update it quarterly. Most organizations manage cross-border AI compliance as an ad hoc exercise where the legal team responds to specific questions. The matrix forces proactive identification of gaps. I've seen organizations discover through this exercise that a system deployed globally was subject to seven different AI-related regulatory frameworks they hadn't assessed. The matrix took one week to build and prevented what would have been a multi-jurisdiction compliance failure.

* * *

## IX. Commercial Contracts for AI

AI-related contractual risk is growing. Contracts that predate the current regulatory environment rarely address AI-specific obligations adequately.

**What to audit:**

Review contracts with AI vendors, AI customers, and data providers. Check whether contracts address model performance warranties with measurable metrics, liability allocation for AI system errors, biased outputs, or regulatory non-compliance, intellectual property rights over training data, model weights, fine-tuned models, and AI-generated outputs, data rights including use of customer data for model training and improvement, indemnification for AI-related regulatory penalties and third-party claims, audit rights specific to AI system components, change notification requirements for model updates, termination rights triggered by performance degradation or regulatory non-compliance, and insurance requirements covering AI-specific liabilities.

Verify that contracts with customers clearly define the scope of permitted AI system use and disclaim uses beyond the validated domain.

Check whether existing contracts have been reviewed and amended to reflect current AI regulatory requirements, particularly the EU AI Act obligations that flow through the supply chain.

**Original implementation tip:** Pull your top 10 AI vendor contracts and your top 10 contracts where you supply AI-enabled services. Create a clause coverage matrix checking for each of the items listed above. Mark each as "present," "partially addressed," or "absent." In my experience, most contracts written before 2023 score below 40% coverage on AI-specific terms. The clause coverage matrix gives your legal team a prioritized remediation list. Start with the contracts that involve high-risk AI systems under the EU AI Act, since those carry the highest regulatory penalty exposure and the most prescriptive supply chain obligations.

* * *

## X. Documentation and Continuous Monitoring

Documentation is the evidence layer that makes every other audit area defensible. Continuous monitoring is what keeps that evidence current.

**What to audit:**

Verify that technical documentation exists for every Tier 1 AI system covering intended purpose, system architecture, design choices, training data sources and quality assessments, validation results, known limitations, monitoring capabilities, and human oversight processes.

Confirm that documentation is version-controlled, timestamped, attributed to a named author, and stored in a managed repository with access controls. Check that documentation is approved by relevant management.

Verify that the organization has automated monitoring in place for data drift, concept drift, and model performance degradation. Confirm that monitoring thresholds are defined, that threshold breaches trigger alerts, and that alerts route to responsible individuals with documented response procedures.

Review evidence that monitoring alerts are investigated, documented, and resolved within defined timelines.

Check whether the organization retains event logs for deployed AI systems and that retention periods comply with applicable regulations and internal data retention policies.

**Original implementation tip:** Audit the documentation lifecycle, not just the documentation itself. Check when each document was last updated. Compare the last update date against the last model change date. If the model was updated six months ago but the documentation still reflects the original version, you have a documentation currency finding that undermines every compliance claim built on that documentation. I implement a documentation freshness check as a recurring automated control. A script compares the last-modified timestamp of each system's documentation against the last-modified timestamp in the model registry. Any mismatch older than 30 days generates an alert to the model owner. Simple to build, high impact, and it catches the drift between what's documented and what's actually running.

* * *

## XI. Ethical AI Principles Integration

Many organizations publish ethical AI principles. Few embed them operationally.

**What to audit:**

Verify that the organization has documented ethical AI principles covering fairness, accountability, transparency, privacy, safety, and human dignity.

Check whether those principles are referenced in operational processes. Specifically, verify that ethical principles are incorporated into AI system design requirements, impact assessment criteria, vendor selection criteria, deployment approval gates, and monitoring thresholds.

Confirm that there is a mechanism for employees and affected individuals to raise ethical concerns about AI systems and that those concerns are investigated with documented outcomes.

Review whether ethical AI training is provided to all personnel involved in AI system development, procurement, and operation. Check training completion records.

Verify that the organization has considered how its AI systems could be used to create societal harms and how they could reinforce historical biases.

**Original implementation tip:** Ask three data scientists, three product managers, and three compliance officers to name the organization's ethical AI principles from memory. If they can't, the principles aren't embedded. They're published. This is a five-minute test that tells you more about operational integration than a week of document review. The gap between what's on the intranet and what practitioners actually apply when making design decisions is the real audit finding. If the principles don't influence daily decisions, recommend that the organization either operationalize them through checklists, training, and approval gates, or stop claiming they have ethical AI principles. The latter option tends to motivate action.

* * *

## XII. Bias Detection and Mitigation

Bias in AI systems creates legal, regulatory, and reputational exposure. Most organizations acknowledge the risk but don't measure it quantitatively.

**What to audit:**

Verify that the organization has a documented bias testing methodology applied before deployment and on an ongoing basis for all AI systems that affect individuals.

Confirm that bias testing uses quantitative fairness metrics, not subjective assessments. Common metrics include demographic parity (equal positive outcome rates across groups), equalized odds (equal true positive and false positive rates across groups), and predictive parity (equal predictive value across groups).

Review which protected attributes are tested. Check whether the selection of attributes aligns with applicable anti-discrimination regulations in each jurisdiction where the system operates.

Verify that bias testing results are documented, reviewed by an authorized person, and that mitigation actions are taken when metrics exceed defined thresholds. Confirm that mitigation effectiveness is measured.

Check whether bias testing covers the full pipeline: training data bias, algorithmic bias introduced during model training, and emergent bias in production due to data drift or feedback loops.

**Original implementation tip:** Review the organization's bias testing results for the past 12 months. Look for two patterns. First, check whether any system ever failed a bias test. If every system passes every time, either the thresholds are too lenient or the testing methodology isn't rigorous enough. Second, check whether bias metrics change over time. A model that showed acceptable demographic parity at deployment can develop significant disparities after six months of production data drift. If the organization only tests at deployment and never retests, they're measuring a snapshot and ignoring the movie. Require ongoing bias monitoring with the same rigor applied to performance monitoring.

* * *

## XIII. Model Validation and Performance Monitoring

Model validation confirms that an AI system works as intended. Performance monitoring confirms that it continues to work as intended.

**What to audit:**

Verify that the organization has an independent model validation process. Independence means the validator is organizationally separate from the development team. In financial services, SR 11-7 requires this explicitly. Outside financial services, the same principle applies.

Confirm that validation covers conceptual soundness (is the model's theoretical basis appropriate?), outcome analysis (does the model perform accurately on data it hasn't seen?), sensitivity analysis (how do outputs change when inputs vary?), and limitations documentation (where should the model not be used?).

Check that no Tier 1 AI system moves to production without a completed and approved validation report.

Verify that the organization monitors model performance continuously using automated tools. Confirm that monitoring covers data drift using statistical tests like Population Stability Index or Kolmogorov-Smirnov, concept drift where the relationship between inputs and outcomes changes, and aggregate performance metrics against baseline benchmarks.

Review whether monitoring thresholds are defined, and verify that threshold breaches trigger documented investigation and remediation.

Confirm that models are revalidated at defined intervals and when material changes occur (new training data, architecture changes, new use cases, or significant drift detection).

**Original implementation tip:** Request evidence of the last model revalidation triggered by a monitoring alert. Follow the chain from alert to investigation to decision to action. If the organization monitors drift but the alerts don't result in documented decisions, the monitoring is decorative. The value chain is: detect, investigate, decide, act, document. If any link is broken, the monitoring program gives false assurance. I've audited organizations with sophisticated monitoring dashboards where threshold breaches sat uninvestigated for months because nobody owned the response. The monitoring technology worked perfectly. The governance around it didn't exist.

* * *

## XIV. Human Oversight and Intervention

Human oversight is a legal requirement under the EU AI Act for high-risk systems and a governance best practice everywhere else. Most organizations define it vaguely.

**What to audit:**

Verify that the organization has identified which AI systems require human oversight based on risk classification, regulatory requirements, and impact assessment results.

Confirm that human oversight mechanisms are documented and operational. These can include human-in-the-loop (a human must approve each AI decision before it takes effect), human-on-the-loop (a human monitors AI decisions and can intervene), or human-in-command (a human can override or shut down the system at any time).

Check whether the personnel performing human oversight have the training, authority, and tools to effectively oversee the AI system. Verify training records. Confirm that oversight personnel understand the system's intended purpose, known limitations, and the conditions under which they should intervene or override.

Verify that the organization has defined intervention triggers: specific conditions under which human override is mandatory rather than discretionary.

Test whether the override mechanism actually works. Can the designated person stop, modify, or reverse an AI system's output in practice, or only in theory?

**Original implementation tip:** Observe the human oversight process in real time for one high-risk AI system. Watch what the oversight person actually does when an AI system produces an output. Are they genuinely reviewing the output and applying judgment? Or are they clicking "approve" on every recommendation because the volume is too high, the interface doesn't surface relevant information, or they don't understand what they're reviewing? Automation bias, where humans rubber-stamp AI outputs because they trust the system, is the most common failure mode in human oversight programs. If the approval rate is above 98% with no documented rationale for the rare rejections, the oversight is likely not functioning as intended. This is a finding that document review alone will never surface. You have to observe the process.

* * *

## XV. AI Misuse Prevention and Monitoring

AI systems can be misused internally or externally in ways the organization didn't anticipate. Misuse prevention is increasingly a regulatory expectation.

**What to audit:**

Verify that the organization has documented the intended use and reasonably foreseeable misuse scenarios for each AI system. The EU AI Act specifically requires high-risk system providers to consider foreseeable misuse.

Confirm that technical and organizational controls exist to prevent identified misuse scenarios. These can include input validation to reject out-of-scope queries, rate limiting to prevent bulk exploitation, access controls limiting who can use the system and for what purpose, output filtering to prevent harmful content generation, and monitoring for anomalous usage patterns that indicate misuse.

Check whether the organization monitors for actual misuse. Review monitoring logs and incident records for evidence of detected misuse attempts and the response taken.

Verify that employees receive training on acceptable AI use policies and that the policies cover both internal AI systems and the use of external AI tools (such as public large language models) for business purposes.

Confirm that the organization has assessed how its AI systems could be weaponized for purposes like generating deepfakes, conducting social engineering at scale, circumventing other controls, or enabling discrimination.

**Original implementation tip:** Test the AI system's response to misuse attempts. For generative AI systems, submit prompts designed to elicit harmful content, extract training data, or bypass safety filters. For classification systems, submit inputs outside the intended domain and verify the system either rejects them or flags them rather than producing a confident but meaningless output. Document the results. Most organizations rely on vendor-implemented safety guardrails without verifying they work in their specific deployment context. A vendor's safety filter tested on generic content may not catch domain-specific misuse relevant to your organization. Your misuse testing should reflect your specific risk profile and use cases, not generic benchmarks.

* * *

## XVI. Continuous Improvement and Adaptation

AI regulation, technology, and risk landscapes evolve continuously. An audit program built for today's environment will be outdated within 12 months.

**What to audit:**

Verify that the organization has a process for monitoring regulatory developments across all jurisdictions where its AI systems operate. Confirm that new regulations and guidance are assessed for impact on existing AI systems and governance frameworks within a defined timeframe.

Check whether audit findings, incident post-mortems, and monitoring alert trends are analyzed for systemic issues and fed back into governance framework improvements. Verify that root cause analysis is performed on significant AI incidents and that corrective actions address root causes, not just symptoms.

Confirm that the organization benchmarks its AI governance maturity against recognized frameworks (NIST AI RMF, ISO 42001) and identifies specific improvement targets.

Review whether the organization conducts periodic internal audits of its AI governance program and whether audit results trigger concrete improvement actions with assigned owners and deadlines.

Verify that the organization updates its AI risk assessments when material changes occur in technology (new AI capabilities deployed), regulation (new laws or enforcement actions), the organization (mergers, new markets, new use cases), or the threat landscape (new attack vectors, new misuse patterns).

**Original implementation tip:** Build an AI governance improvement backlog. Every audit finding, incident lesson learned, regulatory change, and benchmark gap becomes a backlog item with a priority, an owner, and a target completion date. Review the backlog monthly in the AI governance body meeting. This replaces the typical pattern where audit reports produce management action plans that nobody tracks after the first 90 days. The backlog keeps improvement visible and accountable. Treat it like a product backlog: prioritize ruthlessly, complete items, and measure velocity. After 12 months, you can demonstrate concrete progress to regulators, auditors, and the board with evidence of what changed, not just what was planned.

* * *

## Audit Execution Tips Across All Areas

**Sampling strategy:** For organizations with large AI inventories, risk-based sampling is essential. Audit every Tier 1 (high-risk) AI system. Sample 30 to 50% of Tier 2 systems. Spot-check Tier 3 systems annually. Adjust sampling based on previous findings, incidents, and regulatory exposure.

**Evidence standards:** Accept only documented, timestamped, attributed evidence. Verbal assurances are not audit evidence. Screenshots expire. System-generated logs with integrity controls are the gold standard.

**Interview approach:** Interview the model owner, the model developer, and the model validator separately for each system audited. Compare their answers. Discrepancies between what the owner believes the system does and what the developer built are findings in themselves.

**Regulatory mapping:** For each audit finding, map it to the specific regulatory requirement it violates or the specific framework control it fails. Findings without regulatory or framework references lose urgency in remediation prioritization.

**Reporting:** Report findings in business impact terms, not technical terms. "The fraud detection model has not been revalidated in 14 months despite detecting concept drift" becomes "The organization faces estimated exposure of $X in undetected fraud and regulatory penalty risk due to a model operating outside validated parameters." The second statement gets executive attention. The first one gets filed.

* * *

## Key Regulatory and Framework References

**Regulations:**

- EU AI Act, Regulation (EU) 2024/1689

- GDPR, Regulation (EU) 2016/679, Article 22

- Colorado AI Act (SB 24-205)

- NYC Local Law 144 (Automated Employment Decision Tools)

- Illinois Biometric Information Privacy Act (BIPA)

- China Algorithm Recommendation Regulation

- China Deep Synthesis Provisions

- Brazil LGPD, Article 20

**Frameworks and Standards:**

- NIST AI Risk Management Framework 1.0 (2023)

- ISO/IEC 42001:2023

- ISO/IEC 23894:2023

- SR 11-7, Federal Reserve Board (2011)

- OCC Bulletin 2011-12

- OECD AI Principles (2019, updated 2024)

**Supplementary Guidance:**

- NIST AI 100-1 (Adversarial Machine Learning)

- ISO/IEC TR 24027 (Bias in AI Systems)

- ISO/IEC TR 24368 (AI Ethics)

- ENISA AI Threat Landscape (2024)

- EDPB Guidelines on Automated Decision-Making (2018)

* * *

Every audit area above produces findings that are actionable, mapped to regulatory requirements, and defensible under external scrutiny. The program is designed to mature over time. Year one establishes baseline coverage. Year two deepens testing of high-risk areas based on year one findings. Year three shifts toward continuous auditing with automated evidence collection.

An AI compliance audit program that only checks whether documents exist isn't protecting the organization. One that tests whether controls actually function, change outcomes, and produce evidence under pressure is what regulators and boards increasingly expect.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and internationally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
