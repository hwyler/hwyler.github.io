---
title: "AI Performance Auditing"
date: 2026-03-13
tags: 
  - "ai"
  - "ai-atestation"
  - "ai-audit"
  - "ai-audit-procedure"
  - "ai-audits"
  - "ai-bias-audit"
  - "ai-controls"
  - "ai-governance"
  - "ai-model-performance-controls"
  - "ai-attestations"
  - "ai-conformance"
  - "ai-projects"
  - "ai-reviews"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "au-bias-audit"
  - "business"
  - "chatgpt"
  - "iso-42001"
  - "iso-23894"
  - "technology"
---

### How to Audit AI Systems Beyond Approval and Into Real Operations

Most organizations audit AI model approval thoroughly and audit AI model operations barely at all. They verify that someone signed off on the model before deployment. They confirm that a risk assessment was completed. They check the documentation. Then they stop.

Meanwhile, the deployed model drifts. Its accuracy degrades by a fraction of a percentage point each week. Its fairness metrics shift as the population it serves changes. Its third-party API dependency updates without notice, subtly altering output behavior. Its inference latency creeps upward as data volumes grow. None of these changes trigger any audit finding because nobody is auditing operations.

A 2025 TÜV Austria white paper on AI trustworthiness found that common audit pitfalls include data leakage that inflates reported performance, bias that emerges only after deployment, and models that pass controlled testing but experience performance degradation of up to 20% when moving to real-world conditions. These aren't hypothetical risks. They're documented patterns in production AI systems across industries.

The strongest AI audit programs are continuous, not periodic. They cover 15 controls spanning governance, data quality, model development, production monitoring, security, and continuous improvement. This post covers all 15, organized into the five audit phases that align with ISO/IEC 42001, NIST AI RMF, and IIA guidance, with practical implementation advice for each control.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/gemini_generated_image_j9h3hej9h3hej9h3-clean.png?w=1024)

## Why AI Auditing Requires a Different Approach

Traditional IT auditing assumes deterministic systems. You audit the configuration, verify it matches the standard, and move on. The configuration doesn't change by itself. The system behaves the same way tomorrow that it behaves today.

AI systems violate every one of these assumptions. Models change as they're retrained. Data distributions shift continuously. Performance varies across demographic groups, geographic regions, and time periods. A model that passes an audit in January may exhibit bias by March because the production population has shifted.

This means AI auditing must be continuous rather than periodic, operational rather than documentary, and multi-dimensional rather than focused on a single performance metric. A model might achieve 85% accuracy while simultaneously exhibiting significant fairness gaps across demographic groups. Testing accuracy alone misses the fairness problem. Testing fairness alone misses the accuracy problem. Testing both at a single point in time misses the drift problem.

The NIST AI Risk Management Framework structures AI governance through four functions: Govern, Map, Measure, and Manage. The Measure and Manage functions stress defining KPIs covering accuracy, false positive and negative rates, and trustworthiness, continuously monitoring risks including bias, privacy, and security, and conducting regular audits to evaluate mitigation effectiveness. ISO/IEC 42001 adds specific requirements for operational controls, performance evaluation, and continual improvement. The IIA's AI Auditing Framework emphasizes validating that AI works as intended, assessing related internal controls periodically, identifying ethical and social and financial risks, and evaluating third-party AI.

Together, these frameworks define a comprehensive audit scope that most current audit programs only partially cover.

Implementation tip: Before building your AI audit program, map your existing IT audit controls against the 15 AI-specific controls in this post. Identify which controls your current program already covers (even partially), which controls are completely missing, and which controls exist on paper but aren't tested in practice. Most organizations discover that they cover 4-6 of the 15 controls through existing IT and compliance audits. The remaining 9-11 controls represent the gap that an AI-specific audit program must fill. Starting with this gap analysis prevents duplication of effort and focuses investment on the controls that add the most audit value.

## Phase 1: Governance Controls

Three controls establish the governance foundation that every other audit activity depends on. Without these three, the remaining twelve controls lack the organizational structure to function.

Control 1: Governance Ownership and Escalation

Confirm that AI risks, incidents, and performance issues are reported to the CIO, CISO, CTO, compliance leadership, and the executive committee. If ownership is unclear, performance monitoring becomes fragmented and remediation slows.

What to audit: Verify that a formal AI governance structure exists with defined roles, responsibilities, and accountability. Check that an AI governance committee or designated leadership body meets regularly to review AI system performance, risk status, and incident reports. Confirm that escalation paths are documented and tested: when a model produces biased outputs, who gets notified, within what timeframe, and with what authority to act?

Review whether AI strategy is supported by feasibility analyses of identified use cases. Audit ROI on AI projects, control effectiveness per model, and end-user adoption rate. These metrics should reach leadership regularly, not just when problems occur.

What to look for: The most common finding in governance audits is that AI governance exists on paper but doesn't function in practice. The committee was established but hasn't met in six months. The escalation path is documented but has never been used. The reporting template exists but contains the same content from three quarters ago. Test for operational reality, not documentary compliance.

Control 2: Approved Use Case and Legal Permissibility

Audit whether the intended use of the model is documented, lawful, ethical, and aligned with responsible AI principles. A model can perform well technically and still fail from a compliance or conduct standpoint.

What to audit: Review the documented intended use for each AI system in scope. Verify that the use case was assessed against applicable regulations (GDPR, EU AI Act, sector-specific requirements) before deployment. Check whether the organization classified the AI system's risk level and applied controls proportionate to that classification. Confirm that ethical review was conducted for use cases affecting individuals.

What to look for: Use case documentation that's vague enough to justify any application of the model. "The model supports business decision-making" is not a sufficient use case description. "The model predicts customer churn probability for the consumer banking division, using transaction history and engagement data, to prioritize retention outreach" is sufficient. Vague use case documentation enables scope drift that creates unassessed risks.

Control 3: Policy and SOP Control Mapping

Check that responsible AI, acceptable use, data governance, procurement, and monitoring requirements are embedded in policies and standard operating procedures. If controls are not operationalized in SOPs, they usually do not survive scale.

What to audit: Verify that the following policies exist and are current: responsible AI policy, acceptable use policy for AI systems, data governance policy covering AI training and operational data, AI procurement policy, and AI monitoring and maintenance policy. For each policy, confirm that specific controls are operationalized in SOPs with defined roles, tasks, and procedures. Review AI project approval processes.

What to look for: Policies without corresponding SOPs. A responsible AI policy that states "the organization will ensure fairness in AI systems" without an SOP that defines who runs fairness tests, using what metrics, at what frequency, with what thresholds, and with what remediation procedures. The policy creates the obligation. The SOP creates the capability. Audit both.

Implementation tip: When auditing governance controls, test whether the governance framework actually influences operational decisions. Pull three recent AI-related decisions (model deployment approval, incident response, model update) and trace them through the governance process. Did the decision follow the documented approval path? Did the right stakeholders review it? Were risk assessments completed before the decision was made? Were conditions or findings from previous audits addressed? This trace-through approach reveals whether governance operates as a functioning system or as a filing requirement.

## Phase 2: Data and Development Controls

Four controls cover the data quality and model development practices that determine whether an AI system is built on a sound foundation.

Control 4: Data Quality and Data Representativeness

Review whether training, testing, and production data are accurate, complete, current, and representative of the target population and use case. Weak data quality remains one of the fastest ways to degrade model performance and fairness.

What to audit: Assess accuracy, completeness, and representativeness of data used for training and testing. Review data validation and quality control processes. Confirm data sources are reliable and current. Check whether data lineage is documented from source through preprocessing to model input. Verify that data governance controls cover the entire data lifecycle: collection, labeling, training, archival.

What to look for: Training data that overrepresents or underrepresents specific populations relative to the production context. A credit model trained predominantly on urban applicants that's deployed in rural markets. A healthcare model trained on data from academic medical centers that's used in community hospitals. Representativeness gaps are among the most common causes of post-deployment performance degradation and fairness failures.

Control 5: Model Development and Selection Discipline

Assess whether teams compared multiple techniques, aligned model complexity with the business need, tested training and test splits, and used cross-validation or bootstrap methods where appropriate. This helps detect weak model selection, overfitting, and unjustified complexity.

What to audit: Verify that multiple modeling techniques were compared before selection. Check alignment between use case complexity and the chosen AI technique. Review whether explainability was prioritized when required by industry standards or business needs. Confirm that latency, memory, and hardware constraints were considered early in the selection process. Verify that cross-validation, bootstrap sampling, and train-test splits were used to evaluate generalization.

What to look for: Models selected without documented comparison to alternatives. Model complexity that exceeds what the data volume can support (deep learning on 500-record datasets). Absence of cross-validation or holdout testing. Training and test sets that aren't properly separated, allowing data leakage that inflates reported performance. The TÜV Austria framework specifically highlights data leakage as a common audit finding that produces misleadingly optimistic performance metrics.

Control 6: Accuracy and Correctness Thresholds

Audit whether the model uses appropriate metrics for the use case, such as accuracy, precision, recall, F1, MAE, RMSE, MAPE, or R-squared, and whether thresholds match operational requirements. A good audit tests whether the chosen metric actually reflects business risk.

What to audit: Review the performance metrics selected for each model. Verify that the metrics are appropriate for the problem type (classification metrics for classification problems, regression metrics for regression problems). Confirm that acceptance thresholds are defined before deployment, not adjusted after results are known. Test whether the model meets its thresholds on production data, not just on the original test data.

What to look for: Models evaluated on metrics that don't align with business risk. A fraud detection model measured only on accuracy (which can be high even when the model catches zero fraud due to class imbalance) rather than on precision and recall (which measure fraud detection capability directly). Thresholds that were set after seeing results rather than before testing, which eliminates the threshold's value as an objective acceptance criterion.

Control 7: Explainability and Interpretability Controls

Verify that outputs can be explained to users, auditors, regulators, and decision-makers using methods such as SHAP values, feature importance, partial dependence plots, model cards, or decision logic diagrams. If performance cannot be explained, governance is not complete.

What to audit: Review whether the organization produces model cards or equivalent documentation for each production model. Verify that explainability methods (SHAP, LIME, feature importance rankings, partial dependence plots) are applied and their outputs are documented. Confirm that explanations are available at both the global level (how the model generally behaves) and the local level (why a specific prediction was made). Test whether decision-makers who use model outputs can articulate the basis for the model's recommendations.

What to look for: Models in production without any explainability documentation. Explainability analysis performed at deployment but never updated after model retraining. Decision-makers who use model outputs but cannot explain the model's logic even at a basic level. Explanations that are technically correct but incomprehensible to the regulatory audience they're supposed to serve.

Implementation tip: For controls 4 through 7, request the actual artifacts, not just attestations that the work was done. Ask to see the data quality report with specific metrics. Ask to see the model comparison table showing which alternatives were tested. Ask to see the SHAP summary plot for the current model version. Ask to see the model card with current performance metrics. IIA-focused guidance emphasizes testing that AI controls operate in practice, for example by sampling model outputs, re-running bias tests, and testing overrides, rather than just reviewing documentation. Documentary evidence that controls exist is necessary but insufficient. Operational evidence that controls function is what distinguishes a meaningful audit from a compliance exercise.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/futuristic-data-stream.png?w=1024)

## Phase 3: Production Monitoring Controls

Four controls cover the operational monitoring that keeps AI systems trustworthy after deployment. This is the phase where most audit programs are weakest.

Control 8: Fairness and Bias Monitoring

Check whether the organization tests for bias before and after deployment using relevant fairness metrics such as disparate impact ratio, statistical parity difference, and equal opportunity ratio. Also review whether underrepresentation and error disparities across groups are tracked and mitigated.

What to audit: Confirm that bias testing occurs both pre-deployment and in production on an ongoing basis. Review the specific fairness metrics used and verify they're appropriate for the use case. Check whether underrepresented groups are proportionally reflected in training and test data. Review remediation actions taken when bias is detected.

Quantitative benchmarks from the literature: Implementing proactive bias controls in healthcare models has been shown to improve disparate impact ratio from 0.67 to over 0.85. Comparative studies often find no inherent tradeoff between fairness and accuracy, suggesting that optimized approaches can maintain performance while improving equity.

What to look for: Bias testing performed only at initial deployment with no ongoing monitoring. Fairness metrics selected for convenience (using the metric that produces the most favorable result) rather than for relevance to the affected population. Absence of defined remediation procedures when bias is detected. Bias testing that covers gender and race but ignores age, disability, and other protected characteristics.

Control 9: Robustness and Adversarial Testing

Audit whether the model is tested under normal variation, edge cases, and malicious conditions, including red teaming where appropriate. This is essential for understanding brittleness, resilience, and real operating risk.

What to audit: Test natural robustness against real-world data variations. Review whether adversarial testing and red teaming are conducted to measure resilience against malicious attacks. Assess brittleness to determine how easily performance breaks down with slight input changes. Review whether safeguards against AI-specific attacks such as prompt injection, model inversion, and data poisoning are implemented.

Critical finding from the literature: Control protocols that perform well against default attacks can see safety levels drop from 96% to 17% when faced with red-team strategies that simulate monitors or exploit protocol internals. This finding underscores that basic adversarial testing is necessary but insufficient for high-risk systems. Sophisticated red teaming that simulates adaptive adversaries provides much more realistic resilience assessment.

What to look for: Models deployed without any adversarial testing. Red teaming exercises that follow scripted scenarios without simulating adaptive adversaries. Robustness testing limited to the same data distribution as the training data, which doesn't test how the model behaves on inputs it hasn't encountered.

Control 10: Drift Detection and Retraining Governance

Review whether the organization monitors for data drift, model drift, concept drift, and model decay, with documented thresholds for investigation, retraining, rollback, or retirement. This is one of the most important controls for production performance.

What to audit: Verify that scheduled retraining occurs when drift or decay is detected. Confirm that operators have a documented process for retraining when drift is identified. Compare statistical properties between training data and production data on a scheduled basis. Review whether drift thresholds are defined and tested. Confirm that version control links each model version to the specific training data and configuration that produced it. Review regularization techniques such as L1 or L2 to prevent overfitting and confirm the model card reflects current real-world limitations through edge-case testing and error-pattern analysis.

What to look for: Drift monitoring that exists in dashboard form but generates no alerts and triggers no retraining. Retraining processes that require manual initiation rather than automated triggering when thresholds are breached. Model versions in production that can't be traced to specific training datasets. Models that haven't been retrained since initial deployment despite operating in dynamic environments.

Control 11: Latency and Operational Performance Monitoring

Confirm that inference latency, component-level profiling, load testing, and scalability constraints are measured in production. A model that is accurate but too slow or unstable can still fail operationally and commercially.

What to audit: Track inference latency in production to detect slowdowns. Profile individual model components to identify bottlenecks. Conduct load testing to verify scalability under varying demand levels. Review whether performance KPIs and SLAs are defined with specific metrics (accuracy, throughput, response time, error rates) and target levels.

What to look for: Models with no latency monitoring in production. SLAs that define uptime but not response time or accuracy. Load testing performed only at initial deployment without subsequent testing as usage patterns evolve. Component-level profiling that's never been performed, leaving bottleneck sources unidentified.

Implementation tip: When auditing production monitoring controls, don't just verify that monitoring exists. Verify that monitoring findings trigger action. Pull the last six months of monitoring alerts for a sample model. For each alert that exceeded a defined threshold, trace the response: Was the alert investigated? Was a root cause identified? Was corrective action taken? Was the effectiveness of the corrective action verified? If alerts consistently fire without generating responses, the monitoring system is producing noise rather than governance. This finding, that monitoring exists but doesn't drive action, is among the most common and most consequential audit findings for AI systems in production.

## Phase 4: Security and Third-Party Controls

Two controls address the security perimeter and supply chain risks that affect AI system integrity.

Control 12: Third-Party and Vendor Component Assurance

Audit external models, APIs, datasets, and software components for performance assumptions, contract controls, dependency risks, and security vulnerabilities. Vendor reliance does not remove accountability for performance failure.

What to audit: Audit third-party components embedded in each model, including pre-trained models, external APIs, vendor-supplied datasets, and open-source libraries. Review AI software contract clauses for risk allocation, performance guarantees, change notification requirements, and audit rights. Conduct subject matter expert and vendor challenge sessions to verify that limitations described in the model card are realistic. Assess and monitor risks associated with vendor models, APIs, and tools on an ongoing basis, including performance and security.

What to look for: Third-party model components that were assessed at procurement but never reassessed after vendor updates. Contracts that lack AI-specific performance guarantees (accuracy, fairness, drift management). Open-source model dependencies with known vulnerabilities that haven't been patched. Vendor APIs that were updated without notification, changing output behavior without the organization's knowledge.

Control 13: Security and Integrity of Models and Data

Audit controls protecting models and data from tampering, unauthorized access, and integrity loss. This includes enforcement of least-privilege, role-based access control and strong authentication for all AI system components.

What to audit: Review access controls for model artifacts, training data, inference endpoints, and monitoring systems. Verify that privacy-preserving techniques (encryption, pseudonymization) are applied throughout the AI lifecycle. Check for safeguards against AI-specific attacks: input and output filtering, prompt injection defenses, model extraction prevention, and data poisoning detection. Review whether security testing includes AI-specific vulnerability categories beyond traditional infrastructure security.

What to look for: Model artifacts stored in repositories with overly broad access permissions. Training data accessible to personnel who don't need it for their current role. Inference APIs without rate limiting or authentication. Security testing that covers traditional infrastructure but ignores AI-specific attack vectors like adversarial inputs, prompt injection, or training data poisoning.

Implementation tip: Third-party AI component auditing requires technical depth that many audit teams lack. When auditing vendor AI components, bring a subject matter expert who can evaluate the vendor's model card for completeness and realism, assess whether the vendor's performance claims are supported by appropriate validation methodology, identify dependencies between vendor components and your own infrastructure that create combined risks, and evaluate whether vendor security practices extend to AI-specific threats. A general IT auditor can verify contractual compliance. An AI-literate auditor can evaluate whether the vendor's AI practices actually protect your organization. If your audit team lacks this capability, engage an external AI specialist for vendor component reviews.

## Phase 5: Continuous Improvement Controls

Two controls ensure that the audit program itself improves over time and that findings drive operational changes.

Control 14: Incident and Nonconformity Management

Audit the detection, logging, investigation, and corrective action processes for AI incidents and performance failures.

What to audit: Review incident logs for AI-related events over the past 12 months. For each incident, verify that root cause analysis was performed, corrective actions were defined and tracked, and effectiveness of corrective actions was verified. Check whether the incident management process includes AI-specific incident categories: model accuracy degradation, bias emergence, adversarial exploitation, hallucination in generative systems, and privacy leakage.

What to look for: AI incidents classified as generic IT incidents rather than receiving AI-specific investigation. Incidents that were resolved (system restored to operation) without root cause analysis (understanding why it happened and preventing recurrence). Corrective actions that were defined but never verified for effectiveness.

Control 15: Internal Audit, Management Review, and Continuous Improvement

Verify that scheduled internal audits of the AI management system occur, that management reviews AI performance and risks, and that audit findings drive changes to models and processes.

What to audit: Confirm that internal audits of AI systems follow a defined program with scope, criteria, and reporting requirements. Review management review minutes for evidence that AI performance data, risk assessments, and audit findings are discussed and that decisions are documented. Look for trend reports, lessons learned documentation, and evidence that metrics drive changes to models or processes. Verify that the organization maintains an AI system inventory classified by risk level.

The ETSI TS 104 008 standard on Continuous Auditing-Based Conformity Assessment introduces a framework for automated, ongoing assessment that aligns with post-market monitoring obligations. This represents the direction AI auditing is moving: from periodic point-in-time assessments to continuous automated monitoring supplemented by periodic human review.

What to look for: Internal audits that review documentation without testing operational controls. Management reviews that receive AI performance reports without discussing them or making decisions based on them. Absence of a continuous improvement loop: no evidence that audit findings, incident analyses, or monitoring data actually change how AI systems are developed, deployed, or operated.

Implementation tip: Build your audit program as a living framework that evolves with each audit cycle. After each audit, update your control inventory based on new findings, emerging regulations, and evolving best practices. The AI audit landscape is changing rapidly. ISO/IEC 42001 was published in 2023. The EU AI Act's obligations are phasing in through 2027. New technical standards like ETSI TS 104 008 are introducing continuous auditing concepts. An audit program designed in 2024 and never updated will be inadequate by 2026. Schedule an annual review of your audit program scope, control inventory, and testing methodology. Update it to reflect new standards, new threats, and lessons learned from previous audit cycles.

## Structuring the Audit Program: The Five-Phase Approach

The 15 controls organize into five audit phases that mirror the AI system lifecycle and align with ISO 42001 clauses 8-10.

Phase 1 (Planning and Scoping) covers controls 1-3: governance ownership, use case approval, and policy mapping. This phase confirms scope and AI inventory, understands business purpose and risk context, and maps standards and evaluation criteria.

Phase 2 (Design and Pre-Deployment Review) covers controls 4-7: data quality, model development, accuracy thresholds, and explainability. This phase reviews data management controls, validates model design and testing, and verifies defined acceptance criteria.

Phase 3 (Performance Measurement and Monitoring) covers controls 8-11: bias monitoring, robustness testing, drift detection, and latency monitoring. This phase inspects the KPI framework, confirms monitoring implementation, and evaluates fairness and robustness in production.

Phase 4 (Security and Third-Party Governance) covers controls 12-13: vendor assurance and security integrity. This phase audits third-party components, reviews contract controls, and tests AI-specific security measures.

Phase 5 (Change Management and Continuous Improvement) covers controls 14-15: incident management and continuous improvement. This phase checks version control and change governance, reviews incident response, and verifies the improvement loop.

This phased structure enables audit teams to conduct focused reviews of specific phases when full audit cycles aren't feasible, while ensuring that the complete program covers all 15 controls over the audit cycle.

Implementation tip: When time or resource constraints prevent a full 15-control audit, prioritize based on operational risk. For a newly deployed AI system, prioritize Phase 2 controls (data quality, model development, accuracy, explainability) because pre-deployment gaps are the hardest to remediate after launch. For a system that's been in production for over 12 months, prioritize Phase 3 controls (bias monitoring, drift detection, robustness, latency) because operational degradation is the most likely risk source. For a system using significant third-party components, prioritize Phase 4 controls. This risk-based prioritization ensures that limited audit resources address the highest-probability, highest-impact risks first.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/collaborative-discussion-in-soft-pink-light.png?w=1024)

## Standard Audit Program for AI System Performance

This is my recommended procedures in a logical audit plan to assess the control performance of AI systems.This audit program is designed for adaptation to the organization's specific risk profile, regulatory environment, and AI portfolio maturity. Control owners, evidence requirements, and testing depth should be calibrated based on the risk classification of each AI system in the inventory.

  
AI System Performance Audit Program

**Prepared by:** Prof. Hernan Huwyler, MBA CPA CIAO  
**Framework References:** ISO/IEC 42001, ISO/IEC 23894, EU AI Act, NIST AI RMF, 2024 Global Internal Audit Standards  
**Scope:** Enterprise AI systems in development, production, and procurement  

* * *

## Area 1: Governance and Risk Management

* * *

### Control 1.1 — AI Governance Framework and Policy Architecture

**Control Description:**  
The organization shall establish and maintain an enterprise-wide AI governance framework that defines roles, responsibilities, accountability structures, and decision rights across the AI lifecycle. This includes designation of policy owners, model owners, data stewards, AI operators, and risk approvers with documented authority levels. The framework shall reference ISO/IEC 42001 clauses on leadership commitment, organizational roles, and the establishment of an AI management system (AIMS). The governance structure shall ensure that AI-related decisions are traceable to accountable individuals and that escalation paths to executive leadership are formally documented and operational.

**Usual Control Owners:**  
Chief Information Officer, Chief Risk Officer, Chief Compliance Officer, Head of AI Center of Excellence, General Counsel, AI Ethics Committee Chair

**Evidence to Review:**

→ Approved AI governance policy and responsible AI policy  
→ Acceptable use policy for AI systems  
→ AI data governance policy  
→ AI procurement policy  
→ RACI matrix or responsibility assignment matrix for AI roles  
→ Organizational chart showing AI governance reporting lines  
→ Board or executive committee charter referencing AI oversight  
→ Meeting minutes from AI governance committee or equivalent body

**Audit Procedure:**

Obtain the current approved version of the AI governance policy and confirm the approval date, version number, approving authority, and next scheduled review date. Verify that the policy references ISO/IEC 42001 requirements or equivalent standards and covers responsible AI principles, acceptable use, data governance, and procurement controls.

Review the RACI matrix to confirm that roles for model ownership, data stewardship, risk approval, deployment authorization, and incident escalation are explicitly assigned to named individuals or defined positions. Cross-reference these role assignments against the organizational chart to confirm reporting lines to the CIO, CISO, CTO, or executive committee as appropriate.

Select a sample of three to five AI systems currently in production. For each system, trace whether a designated model owner and risk approver are documented, whether the deployment was formally approved through the defined governance process, and whether the approval evidence is retained.

Review the minutes of the last four AI governance committee meetings to confirm that AI risks, performance issues, and policy exceptions were discussed and that decisions were documented with action items and completion dates.

Confirm that the policy has been communicated to all AI roles and users. Request evidence of training completion records for responsible AI training as referenced in the policy. Verify that training content covers the governance framework, escalation procedures, and individual accountability.

Check the last date of policy review. If the policy has not been reviewed within the last twelve months or since the last material regulatory change, flag as a finding.

* * *

### Control 1.2 — AI System Inventory and Risk Classification

**Control Description:**  
The organization shall maintain a complete and current registry of all AI systems across the enterprise, including internally developed models, procured vendor models, embedded AI components in third-party software, and experimental or pilot deployments. Each system in the inventory shall be classified by risk level using a defined taxonomy aligned with regulatory requirements such as the EU AI Act risk categories (unacceptable, high-risk, limited, minimal) and the organization's internal risk appetite. The classification shall determine the level of controls, oversight, testing, and documentation required for each system. The registry shall be updated upon any material change in system scope, use case, data inputs, or deployment status.

**Usual Control Owners:**  
AI Program Manager, Chief Risk Officer, IT Asset Management Lead, Chief Information Security Officer, Data Protection Officer

**Evidence to Review:**

→ AI system inventory or registry (centralized database or spreadsheet)  
→ Risk classification methodology and taxonomy documentation  
→ Risk assessment records for each registered AI system  
→ Change log showing inventory updates in the last twelve months  
→ Mapping of AI systems to business processes and data assets  
→ Evidence of periodic inventory reconciliation against IT asset management systems

**Audit Procedure:**

Obtain the current AI system inventory and confirm the date of last update. Review the inventory fields to verify that each entry includes at minimum the system name, description, model type, intended use, deployment status, risk classification, model owner, data sources, and date of last assessment.

Select a sample of five AI systems from the inventory. For each, verify that the risk classification was performed using the documented methodology. Review whether the classification considered the intended use, the impact on users, clients, partners, and society, the data sensitivity, the degree of autonomy in decision-making, and applicable regulatory requirements including EU AI Act high-risk classification criteria where relevant.

Cross-reference the AI inventory against the IT asset register, procurement records for AI software, and cloud service agreements to identify AI systems that may be in use but not registered in the inventory. If unregistered systems are identified, flag as a control gap.

Review the change log to confirm that updates were made when systems moved between lifecycle stages such as from pilot to production, when use cases changed, or when material changes to model architecture or data inputs occurred.

Verify that high-risk classified systems have enhanced controls applied, including mandatory bias testing, explainability documentation, human oversight mechanisms, and executive-level approval for deployment.

* * *

### Control 1.3 — AI Risk Reporting to Executive Leadership

**Control Description:**  
AI risks, performance metrics, incidents, and control effectiveness results shall be reported to the CIO, CISO, CTO, Chief Risk Officer, and the executive committee or board risk committee on a defined schedule. The reporting shall include quantitative metrics such as ROI on AI projects, control effectiveness per AI model, end user adoption rate, accuracy and fairness metrics, latency measurements, and user satisfaction survey results. The reporting process shall ensure that material AI risks are escalated in a timely manner and that executive leadership has sufficient information to exercise informed oversight. The reporting cadence and content shall be documented in the AI governance policy or a supporting standard operating procedure.

**Usual Control Owners:**  
Chief Risk Officer, Chief Information Officer, AI Program Manager, Head of Internal Audit, Chief Compliance Officer

**Evidence to Review:**

→ AI risk reports submitted to executive committee in the last four quarters  
→ Board risk committee meeting minutes referencing AI risks  
→ AI performance dashboards or scorecards with defined KPIs  
→ Escalation records for material AI incidents or performance failures  
→ AI strategy document with feasibility analyses for identified use cases  
→ Risk appetite statement referencing AI-specific thresholds

**Audit Procedure:**

Obtain the last four quarterly AI risk reports submitted to executive leadership. For each report, verify that it includes the defined metrics: ROI on AI projects, control effectiveness per model, end user adoption rate, accuracy metrics, fairness metrics, latency, and satisfaction survey results. If any metric is consistently absent, determine whether it was excluded by design or due to a monitoring gap.

Review the board risk committee or executive committee meeting minutes for the same period. Confirm that AI risks were a standing agenda item or were discussed at least quarterly. Check whether the minutes reflect that leadership asked questions, requested additional information, or directed remediation actions.

Select a sample of two material AI incidents or performance issues from the incident log. Trace the escalation path to confirm that the incident was reported to the appropriate leadership level within the timeframes defined in the escalation procedure.

Review the AI strategy document and confirm that identified use cases are supported by feasibility analyses that include risk assessments. Verify that the executive committee reviewed and approved the AI strategy.

Assess whether the risk appetite statement includes AI-specific risk thresholds or tolerance levels. If AI risks are not referenced in the risk appetite statement, flag as a gap in risk governance integration.

* * *

### Control 1.4 — AI Policy and SOP Control Mapping

**Control Description:**  
All controls defined in AI governance policies shall be operationalized in standard operating procedures that specify the tasks, responsibilities, tools, frequencies, evidence requirements, and escalation paths for each control activity. SOPs shall cover model development, deployment, procurement, monitoring, retraining, incident response, and decommissioning. The mapping between policy requirements and SOP procedures shall be documented and maintained so that each policy control can be traced to a specific operational procedure with a designated owner and a defined output. Without this mapping, controls typically do not survive at scale and become unenforceable during audit or regulatory examination.

**Usual Control Owners:**  
Chief Compliance Officer, AI Program Manager, Head of AI Operations, Process Owners for each SOP, Internal Audit

**Evidence to Review:**

→ Control mapping matrix linking AI policy requirements to SOPs  
→ Approved SOPs for model development, deployment, monitoring, retraining, and decommissioning  
→ SOP for AI procurement and vendor assessment  
→ SOP for bias testing and fairness evaluation  
→ SOP for incident response and escalation for AI-related events  
→ Version control records for SOPs showing review and update history

**Audit Procedure:**

Obtain the control mapping matrix and verify that each control requirement in the AI governance policy, responsible AI policy, acceptable use policy, data governance policy, and procurement policy is linked to a specific SOP with a designated owner. Identify any policy requirements that do not have a corresponding SOP and flag as unmapped controls.

Select a sample of five SOPs from the mapping. For each, verify that the SOP includes the procedure steps, responsible roles, required tools or systems, frequency of execution, evidence to be produced and retained, and escalation paths for exceptions or failures.

For each sampled SOP, request evidence of the last three executions. Confirm that the procedure was followed as documented, that the required evidence was produced, and that the designated owner signed off on the output. If execution evidence is incomplete or missing, assess whether the SOP is operational or exists only on paper.

Review the version control records for each sampled SOP. Confirm that each SOP has been reviewed within the last twelve months or following the last material change to the related policy, system, or regulation. Verify that changes were approved by the designated authority.

Test one SOP end-to-end by walking through a recent instance with the process owner. Confirm that the operator can describe the procedure, identify the evidence produced, and explain the escalation path for exceptions.

* * *

## Area 2: Data Governance and Quality

* * *

### Control 2.1 — Data Quality and Representativeness

**Control Description:**  
The organization shall implement controls to ensure that data used for training, testing, validation, and production inference is accurate, complete, current, relevant, and representative of the target population and intended use case. Data quality controls shall cover the entire data lifecycle including collection, labeling, preprocessing, transformation, storage, and archival. The organization shall maintain data lineage and provenance documentation to trace the origin, transformation history, and quality checks applied to each dataset. Data validation processes shall detect and remediate issues related to missing values, duplicates, outliers, labeling errors, and sampling bias. These controls are essential to mitigate risks of biased outputs, degraded model performance, and regulatory noncompliance with requirements such as those in the EU AI Act regarding training data quality for high-risk AI systems.

**Usual Control Owners:**  
Chief Data Officer, Data Stewards, Data Engineering Lead, Model Development Team Lead, Data Protection Officer

**Evidence to Review:**

→ Data quality policy and data governance framework documentation  
→ Data lineage and provenance records for training and test datasets  
→ Data quality assessment reports including completeness, accuracy, and representativeness metrics  
→ Data validation and cleansing logs  
→ Dataset documentation or datasheets including source, collection methodology, labeling protocols, and known limitations  
→ Sampling methodology documentation showing how training and test data were split  
→ Records of data refresh or update cycles

**Audit Procedure:**

Obtain the data governance framework and data quality policy. Verify that they define quality dimensions (accuracy, completeness, timeliness, relevance, representativeness), assign ownership for data quality at the dataset level, and specify validation procedures and remediation processes.

Select a sample of three AI models in production. For each model, obtain the training dataset documentation and verify that it includes the data source, collection methodology, labeling protocols, known limitations, volume, feature count, and temporal coverage. Compare the documented dataset characteristics against the model card to confirm consistency.

Review the data lineage records for each sampled model. Trace the data from its original source through each transformation step to the final training and test sets. Verify that each transformation is documented and that quality checks were applied at each stage.

Examine the data quality assessment reports. Confirm that representativeness was evaluated by comparing the demographic, geographic, or operational distribution of the training data against the target population. If the model card from the presentation is used as reference, check whether the dataset included sufficient representation across relevant groups and whether underrepresentation was identified and addressed.

Review the train-test split methodology. Confirm that the split ratio is documented (for example, the 80-20 split referenced in the class presentation), that the split was performed to avoid data leakage, and that the test set is representative of production conditions.

Verify that data refresh cycles are defined and followed. If the training data has not been updated within the period defined in the data governance policy, flag as a potential data staleness risk contributing to drift.

* * *

### Control 2.2 — Data Protection and Privacy Controls

**Control Description:**  
The organization shall apply privacy-preserving techniques and comply with applicable data protection regulations throughout the AI system lifecycle. Controls shall include encryption of data at rest and in transit, pseudonymization or anonymization of personal data used in training and inference, access controls limiting data exposure to authorized personnel, and data minimization practices ensuring that only data necessary for the defined purpose is collected and processed. Where personal data is used for model training, the organization shall document the legal basis for processing, conduct data protection impact assessments where required, and ensure that data subject rights can be exercised. These controls align with GDPR requirements, the EU AI Act data governance obligations for high-risk systems, and ISO/IEC 42001 Annex B guidance on data management throughout the AI lifecycle.

**Usual Control Owners:**  
Data Protection Officer, Chief Information Security Officer, Chief Privacy Officer, Legal Counsel, Data Engineering Lead

**Evidence to Review:**

→ Data protection impact assessments (DPIAs) for AI systems processing personal data  
→ Records of legal basis determination for personal data processing in AI training  
→ Encryption standards and configuration documentation for data at rest and in transit  
→ Pseudonymization or anonymization methodology documentation  
→ Access control lists and role-based access configurations for AI data repositories  
→ Data retention and deletion schedules for training and inference data  
→ Data subject rights request logs and response records

**Audit Procedure:**

Obtain the list of AI systems that process personal data from the AI system inventory. Cross-reference against the data protection impact assessment register to confirm that a DPIA was completed for each system where required by regulation or internal policy.

Select a sample of two AI systems processing personal data. For each, review the DPIA to confirm that it identifies the data categories processed, the purpose of processing, the legal basis, the risks to data subjects, and the mitigating controls applied. Verify that the DPIA was approved by the Data Protection Officer and that it was reviewed after any material change to the system.

Review the encryption configuration documentation for the data repositories and pipelines used by the sampled systems. Confirm that encryption standards meet organizational and regulatory requirements for data at rest and in transit.

Examine access control lists for AI data repositories, model training environments, and production inference systems. Verify that access follows the principle of least privilege and that role-based access control is enforced. Check that access reviews were conducted within the last six months.

Review data retention schedules to confirm that training data, inference logs, and model artifacts are retained and deleted in accordance with the defined schedule and applicable regulations. Verify that deletion records exist for data that has exceeded its retention period.

* * *

## Area 3: Model Development and Selection

* * *

### Control 3.1 — Model Selection Validation and Technique Comparison

**Control Description:**  
The organization shall document the model selection process to confirm that multiple modeling techniques were evaluated and compared before the final technique was selected for development and deployment. The selection process shall assess the alignment between the complexity of the use case and the chosen AI technique, prioritize model explainability when required by industry standards, regulatory obligations, or business needs, and consider operational constraints including inference latency, memory usage, and hardware limitations from the initial design phase. Techniques evaluated may include logistic regression, random forest, support vector machines, neural networks, and ensemble methods as appropriate to the problem domain. The organization shall document the rationale for the selected technique, the comparison metrics used, and the trade-offs accepted. Regularization methods such as L1 (Lasso) or L2 (Ridge) shall be applied where appropriate to prevent overfitting and improve generalization. This control ensures that model selection is a deliberate, documented, and defensible engineering decision rather than a default or convenience choice.

**Usual Control Owners:**  
Lead Data Scientist, ML Engineering Manager, AI Program Manager, Model Risk Manager, Chief Data Officer

**Evidence to Review:**

→ Model selection report or technical design document comparing candidate techniques  
→ Evaluation metrics and benchmark results for each candidate model  
→ Documentation of business requirements including explainability, latency, and scalability needs  
→ Model architecture documentation for the selected technique  
→ Records of regularization techniques applied (L1, L2) and hyperparameter tuning  
→ Cross-validation results and bootstrap sampling outputs  
→ Sign-off records from the model owner and risk approver on the final selection

**Audit Procedure:**

Obtain the model selection report for a sample of three AI models deployed in the last twelve months. For each, verify that the report documents at least three candidate techniques that were evaluated, the metrics used for comparison (such as accuracy, precision, recall, F1, MAE, RMSE, or R-squared as appropriate to the use case), and the benchmark results for each candidate.

Review whether the selection rationale explicitly addresses the trade-off between model complexity and explainability. If the model operates in a regulated sector or supports decisions with material impact on individuals, verify that explainability was weighted as a selection criterion and that simpler models were preferred when they met performance requirements.

Confirm that operational constraints were considered during selection. Review whether latency requirements, memory limitations, hardware availability, and scalability needs were documented as input to the selection process. If a complex model such as a deep neural network was selected over a simpler alternative, verify that the performance improvement justified the added complexity and operational cost.

Examine the cross-validation methodology used to evaluate generalization. Confirm that k-fold cross-validation or equivalent was applied and that results are documented. Review bootstrap sampling outputs if used to estimate population statistics.

Check whether regularization was applied to the selected model. Review documentation of L1 or L2 regularization parameters and confirm that overfitting was assessed by comparing training and test performance metrics.

Verify that the model selection was formally approved by the designated model owner and risk approver with documented sign-off.

* * *

### Control 3.2 — Pre-Deployment Validation and Testing

**Control Description:**  
Prior to production deployment, each AI model shall undergo formal validation and testing against defined acceptance criteria using independent data that was not used during training. The validation process shall include testing the model's performance using appropriate metrics, evaluating the model under various conditions and environments beyond the original training configuration, and documenting the results with formal sign-off by the model owner, risk approver, and where applicable, an independent validation function. The validation shall confirm that the model meets the operational requirements and priorities of the intended use case. The data split into training and testing sets shall be documented, and the test set shall be representative of production conditions. Known limitations, edge cases, and failure modes shall be identified and recorded in the model card or equivalent documentation. This control aligns with SR 11-7 principles for model validation in financial institutions and ISO/IEC 42001 requirements for AI system verification and validation.

**Usual Control Owners:**  
Model Validation Team Lead, Lead Data Scientist, Model Risk Manager, AI Program Manager, Quality Assurance Lead

**Evidence to Review:**

→ Pre-deployment validation report with test results and acceptance criteria  
→ Documentation of train-test split methodology and ratios  
→ Test results across multiple environments or data conditions  
→ Model card documenting intended use, limitations, and known failure modes  
→ Edge-case test results and error pattern analysis  
→ Formal sign-off records from model owner, risk approver, and independent validator  
→ Records of SME and vendor challenge sessions reviewing model card limitations

**Audit Procedure:**

Obtain the pre-deployment validation report for a sample of three AI models deployed in the last twelve months. For each, verify that the report documents the acceptance criteria used, the metrics evaluated, the test data characteristics, and the results achieved.

Review the train-test split documentation. Confirm the split ratio, verify that the split method prevented data leakage, and assess whether the test set is representative of production data conditions. As referenced in the class presentation, an 80-20 split is a common approach but the rationale should be documented regardless of the ratio used.

Verify that the model was tested under various conditions beyond the original training environment. This includes testing with different data sources, time periods, or operational scenarios to evaluate robustness. If the model was only tested on the original training environment, flag as a validation gap.

Review the model card for each sampled model. Confirm that it documents the model type, version, intended use, purpose and scope, limitations, compliance and legal considerations, training data characteristics, evaluation metrics, known biases, and monitoring plans. Cross-reference the model card limitations against the edge-case test results and error pattern analysis to verify that documented limitations are realistic and supported by testing evidence.

Confirm that SME and vendor challenge sessions were conducted to review the limitations described in the model card, as emphasized in the class presentation. Request meeting records, participant lists, and outcomes of these challenge sessions.

Verify formal sign-off by the model owner, risk approver, and independent validator. If independent validation was not performed, assess whether the risk classification of the model warranted independent review and flag accordingly.

* * *

## Area 4: Model Performance and Trustworthiness

* * *

### Control 4.1 — Accuracy and Correctness Threshold Monitoring

**Control Description:**  
The organization shall define, measure, and monitor accuracy and correctness metrics that are appropriate for each AI model's use case and operational context. For classification models, relevant metrics include accuracy, precision, recall, and F1 score. For regression models, relevant metrics include mean absolute error (MAE), mean absolute percentage error (MAPE), root mean squared error (RMSE), and R-squared. The selected metrics shall align with the operational requirements and business priorities of the intended use, not solely with technical benchmarks. The organization shall establish minimum performance thresholds for each metric, monitor performance against these thresholds in production, and trigger investigation and remediation when performance falls below defined levels. The audit of accuracy shall identify and improve the model's weaknesses and limitations, diagnose the sources of errors, and evaluate performance under various conditions as stated in the ISO 42001 audit framework.

**Usual Control Owners:**  
Lead Data Scientist, Model Risk Manager, AI Operations Lead, Business Process Owner, Model Owner

**Evidence to Review:**

→ Performance metric definitions and threshold documentation for each model  
→ Production performance monitoring dashboards or reports  
→ Comparison of training performance versus production performance  
→ Error analysis reports identifying sources of prediction errors  
→ Records of investigations triggered by threshold breaches  
→ Remediation and retraining records following accuracy degradation  
→ Model performance comparison reports across different environments and databases

**Audit Procedure:**

Obtain the performance metric definitions for a sample of three production AI models. For each, verify that the selected metrics are appropriate for the model type and use case. Confirm that classification models use precision, recall, F1 or equivalent, and that regression models use MAE, RMSE, MAPE, R-squared, or equivalent.

Review the documented minimum performance thresholds. Assess whether the thresholds were set based on operational requirements and business risk tolerance rather than arbitrary technical benchmarks. If thresholds were not formally defined, flag as a control gap.

Obtain the production monitoring dashboards or reports for the last six months. For each sampled model, review the trend in performance metrics over time. Identify any instances where performance fell below the defined thresholds and verify that an investigation was initiated, documented, and resolved.

Review error analysis reports to confirm that the sources of prediction errors have been diagnosed. Verify that the analysis distinguishes between systematic errors, data quality issues, and model limitations.

Confirm that model performance was evaluated using different environments and databases, not solely the original training and test data. As referenced in the class presentation, review whether performance was validated across multiple conditions to assess generalization.

Compare training performance metrics against current production performance metrics. If a material gap exists, assess whether drift monitoring controls detected the divergence and whether retraining was initiated.

* * *

### Control 4.2 — Explainability and Interpretability Verification

**Control Description:**  
The organization shall ensure that AI model outputs can be explained to regulators, auditors, prosecutors, decision-makers, and end users using documented interpretability methods. Explainability controls shall provide insight into how a model produced its output, making it easier to understand the model's behavior, satisfy regulatory obligations, and support the decision-making process. Methods shall include SHAP (SHapley Additive exPlanations) values providing local explanations for each prediction and highlighting the contribution of each feature, feature importance rankings identifying the most significant features driving predictions, partial dependence plots visualizing the relationship between specific features and model outputs, model cards documenting architecture, training data, limitations, and evaluation results, and decision logic diagrams illustrating the model's decision pathways. The organization shall also ensure that model complexity is restricted where necessary to facilitate interpretability, particularly in regulated sectors or use cases where decisions have material impact on individuals. If outputs cannot be explained, the model shall not be considered governance-ready regardless of accuracy performance.

**Usual Control Owners:**  
Lead Data Scientist, Model Risk Manager, Chief Compliance Officer, Regulatory Affairs Lead, Model Owner

**Evidence to Review:**

→ Explainability methodology documentation for each model  
→ SHAP value outputs or equivalent local explanation reports  
→ Feature importance rankings and analysis  
→ Partial dependence plots for key features  
→ Model card with documented decision logic, limitations, and intended use  
→ Decision logic diagrams or model architecture documentation  
→ Records of explainability testing or review sessions with business stakeholders and regulators  
→ Regulatory mapping confirming explainability requirements applicable to the model

**Audit Procedure:**

Obtain the explainability methodology documentation for a sample of three production AI models. For each, verify that at least two interpretability methods are applied and documented, such as SHAP values combined with feature importance rankings, or partial dependence plots combined with decision logic diagrams.

Review the SHAP value outputs for a sample of predictions from each model. Confirm that the feature contributions are documented, that the explanations are consistent with the known behavior of the model, and that the outputs provide meaningful insight to a non-technical reviewer.

Examine the feature importance rankings. Verify that the most influential features are identified, that their importance aligns with domain knowledge, and that no unexpected or potentially discriminatory features dominate the model's predictions.

Review the model card for each sampled model. Confirm that it documents the model architecture, training data characteristics, intended use, known limitations, and evaluation results. Verify that the documented limitations have been validated through edge-case testing and error-pattern analysis as described in the class presentation.

Assess whether the model's complexity is appropriate for the required level of explainability. If a complex model such as a deep neural network is deployed in a context requiring high interpretability, verify that the additional complexity is justified and that supplementary explanation techniques adequately compensate for the reduced inherent transparency.

Request evidence of explainability review sessions with business stakeholders, compliance officers, or regulators. Confirm that participants were able to understand the model's decision-making process based on the explanations provided. If no such sessions have occurred, flag as a gap in governance readiness.

Review the regulatory mapping to confirm that applicable explainability requirements have been identified and that the model's interpretability methods satisfy those requirements. For models subject to the EU AI Act high-risk obligations, verify that transparency requirements are addressed.

* * *

### Control 4.3 — Bias and Fairness Testing

**Control Description:**  
The organization shall implement controls to identify and mitigate unfair or discriminatory treatment in AI model outputs, both before and after deployment. Fairness testing shall measure outcomes using established metrics including disparate impact ratio (DIR), statistical parity difference (SPD), and equal opportunity ratio (EOR). The organization shall also track representation metrics such as distributional measurements and the proportion of underrepresented groups in training and test data, and prediction error metrics such as mean squared error, mean absolute error, and root mean squared percentage error disaggregated by group. The data used to train and test the model shall be assessed for accuracy, completeness, and representativeness of the target population. Detected biases shall be documented with root cause analysis and mitigation strategies, and the effectiveness of mitigation shall be validated through retesting. Fairness testing shall be integrated into audit routines as a recurring control activity rather than treated as a post-deployment cleanup exercise.

**Usual Control Owners:**  
Lead Data Scientist, Model Risk Manager, Chief Compliance Officer, AI Ethics Committee, Diversity and Inclusion Lead, Data Protection Officer

**Evidence to Review:**

→ Fairness testing methodology and metrics documentation  
→ Bias assessment reports with results for each defined fairness metric  
→ Demographic parity analysis and disparate impact analysis results  
→ Training data representativeness assessment  
→ Bias root cause analysis and mitigation action plans  
→ Post-mitigation retesting results  
→ Records of fairness testing frequency and schedule compliance  
→ Regulatory and legal review of fairness obligations applicable to the model

**Audit Procedure:**

Obtain the fairness testing methodology documentation. Verify that it defines the protected attributes to be tested, the fairness metrics to be measured, the tolerance thresholds for each metric, the testing frequency, and the remediation process for detected biases.

Select a sample of three production AI models. For each, obtain the most recent bias assessment report. Verify that the report includes results for disparate impact ratio, statistical parity difference, and equal opportunity ratio at minimum. Check whether prediction error metrics are disaggregated by group to identify differential accuracy.

Review the training data representativeness assessment for each sampled model. Confirm that the assessment evaluates whether the training data proportionally represents the relevant demographic, geographic, or operational groups in the target population. If underrepresentation was identified, verify that mitigation actions were taken, such as the approach described in the class presentation where representation of underrepresented groups was increased in the training data and the model was retrained.

Examine bias root cause analysis documentation for any detected biases. Verify that the root cause was identified, that mitigation strategies were documented and implemented, and that post-mitigation retesting confirmed the effectiveness of the remediation.

Confirm that fairness testing is scheduled as a recurring control activity with defined frequency. Review the testing schedule and verify compliance with the schedule over the last twelve months. If fairness testing was only performed at initial deployment and not repeated, flag as a gap.

Review the regulatory and legal analysis to confirm that applicable non-discrimination and fairness obligations have been identified and that the fairness testing program is designed to satisfy those obligations.

* * *

### Control 4.4 — Robustness and Adversarial Testing

**Control Description:**  
The organization shall test AI models for robustness under normal operational variations, unexpected conditions, edge cases, and adversarial attacks designed to manipulate or confuse the model. Robustness testing shall assess three dimensions: natural robustness, measuring how the model performs when exposed to normal variations in real-world data such as changes in data sources or environmental conditions; adversarial robustness, measuring the model's resilience against malicious attacks or manipulations including prompt injection, model inversion, and data poisoning, often tested using red teaming exercises; and brittleness, measuring how easily the model's performance degrades when facing slight changes in input data. The organization shall define acceptance criteria for each robustness dimension, document the test scenarios and results, and remediate identified vulnerabilities before or shortly after deployment. Adversarial testing should be conducted by personnel independent of the model development team where feasible.

**Usual Control Owners:**  
Chief Information Security Officer, Lead Data Scientist, Red Team Lead, Model Risk Manager, AI Operations Lead, Penetration Testing Team

**Evidence to Review:**

→ Robustness testing methodology and acceptance criteria documentation  
→ Natural robustness test results under varied data conditions  
→ Adversarial testing and red teaming reports  
→ Edge-case test results and error pattern analysis  
→ Brittleness assessment results  
→ Vulnerability remediation records and retesting evidence  
→ Red team exercise scope, participants, and findings

**Audit Procedure:**

Obtain the robustness testing methodology for a sample of three production AI models. Verify that the methodology defines test scenarios for natural robustness, adversarial robustness, and brittleness, and that acceptance criteria are specified for each dimension.

Review the natural robustness test results. Confirm that the model was tested with data from different sources, time periods, or operational conditions to evaluate stability under real-world variation. If testing was limited to a single data source or condition, flag as insufficient coverage.

Examine the adversarial testing and red teaming reports. Verify that the scope of adversarial testing included relevant attack vectors for the model type, such as prompt injection for LLM-based systems, data poisoning for models trained on external data, or input perturbation attacks for classification models. Confirm that the red team included personnel independent of the model development team.

Review edge-case test results and error pattern analysis. As referenced in the class presentation, verify that edge cases were tested and that error patterns were analyzed to ensure that the limitations documented in the model card are accurate and realistic.

Assess the brittleness evaluation. Confirm that the model's sensitivity to small input changes was measured and documented, and that performance degradation under minor perturbations falls within acceptable limits.

Review vulnerability remediation records. For each vulnerability identified during robustness testing, verify that a remediation action was documented, implemented, and confirmed through retesting before the model entered production or within the defined remediation timeline.

* * *

## Area 5: Operations and Continuous Monitoring

* * *

### Control 5.1 — Drift Detection and Retraining Governance

**Control Description:**  
The organization shall implement continuous or periodic monitoring to detect changes in AI model performance over time, encompassing four categories of drift: data drift, which compares statistical properties between the training data and new production data; model drift, which measures how predictions change when applied to new unseen data; concept drift, which identifies changes in the relationship between inputs and outputs due to shifts in the underlying context or assumptions; and model decay, which tracks the gradual loss of model accuracy due to changes in data or environment. The organization shall define thresholds for each drift category that trigger investigation, retraining, rollback, or retirement. AI operators shall have a documented process for updating and retraining models when drift is detected, including approval requirements, validation of retrained models, and version control. This is one of the most critical controls for production AI performance and is frequently absent or underdeveloped in organizations that have otherwise mature AI governance frameworks.

**Usual Control Owners:**  
AI Operations Lead, Lead Data Scientist, ML Engineering Manager, Model Risk Manager, Model Owner

**Evidence to Review:**

→ Drift monitoring policy and procedures with defined thresholds  
→ Drift detection tool configuration and alert settings  
→ Drift monitoring reports or dashboard outputs for the last six months  
→ Records of investigations triggered by drift alerts  
→ Retraining approval records and retrained model validation results  
→ Version control logs showing model versions, change dates, and change rationale  
→ Rollback or retirement records for models that could not be remediated through retraining

**Audit Procedure:**

Obtain the drift monitoring policy and procedures. Verify that the policy defines the four categories of drift (data drift, model drift, concept drift, model decay), specifies monitoring methods and tools for each category, establishes quantitative thresholds that trigger investigation, and documents the decision framework for retraining, rollback, or retirement.

Select a sample of three production AI models. For each, obtain the drift monitoring reports or dashboard outputs for the last six months. Verify that monitoring is active and producing results at the defined frequency. If monitoring has gaps or was suspended, determine the reason and flag as a control failure.

Review the alert configuration for each sampled model. Confirm that alerts are triggered when drift metrics exceed defined thresholds and that alerts are routed to the designated model owner and AI operations team.

Examine the investigation records for any drift alerts triggered in the monitoring period. For each alert, verify that an investigation was initiated within the defined timeframe, that the root cause was identified, and that a decision was made and documented regarding retraining, rollback, or continued monitoring with justification.

For any model that was retrained during the monitoring period, review the retraining approval records. Confirm that the retrained model was validated against the same acceptance criteria used for initial deployment, that performance was compared against the previous version, and that the retrained model was formally approved before replacing the production version.

Review the version control logs to confirm that all model changes are tracked with version numbers, change dates, change descriptions, and the identity of the approver. Verify that rollback to previous versions is possible if the retrained model underperforms.

Assess the overall maturity of drift monitoring across the AI portfolio. If drift monitoring is only implemented for a subset of production models, determine the rationale for exclusion and assess whether unmonitored models present unacceptable risk.

* * *

### Control 5.2 — Latency and Operational Performance Monitoring

**Control Description:**  
The organization shall measure and monitor the operational performance of AI models in production, including inference latency (the time from input receipt to output generation), component-level profiling latency (the time consumed by individual model components to identify bottlenecks), and load testing latency (how response times change under varying demand levels to verify scalability and reliability under pressure). The organization shall define performance targets and service level agreements for latency and throughput, implement continuous tracking in production to detect slowdowns, and establish procedures for quick resolution when performance degradation is identified. A model that is accurate but too slow, unstable, or unable to scale under production load conditions can fail operationally and commercially despite strong technical metrics.

**Usual Control Owners:**  
AI Operations Lead, ML Engineering Manager, Site Reliability Engineering Lead, Infrastructure Manager, Model Owner

**Evidence to Review:**

→ Latency and throughput SLA documentation for each production model  
→ Inference latency monitoring dashboards or reports  
→ Component-level profiling results identifying performance bottlenecks  
→ Load testing reports with results under varying demand levels  
→ Incident records for latency-related production issues  
→ Capacity planning documentation  
→ Remediation records for identified performance bottlenecks

**Audit Procedure:**

Obtain the latency and throughput SLA documentation for a sample of three production AI models. Verify that each model has defined performance targets for inference latency, availability, and throughput. Confirm that the targets were set based on operational and business requirements rather than solely technical capabilities.

Review the inference latency monitoring dashboards or reports for the last three months. For each sampled model, verify that latency is tracked continuously in production and that the monitoring data shows compliance with the defined SLAs. Identify any periods where latency exceeded the SLA and verify that an incident was logged and investigated.

Examine component-level profiling results. Confirm that individual model components have been profiled to identify where delays occur and that optimization efforts have targeted the identified bottlenecks.

Review load testing reports. Verify that load testing was conducted at realistic and peak demand levels, that the results demonstrate acceptable performance under pressure, and that scalability limitations were identified and documented. If load testing has not been performed, flag as a gap, particularly for models serving high-volume or real-time use cases.

Confirm that capacity planning documentation exists and that infrastructure scaling plans account for projected growth in model usage.

* * *

### Control 5.3 — Incident Response and Escalation for AI Systems

**Control Description:**  
The organization shall establish and maintain documented procedures for detecting, logging, investigating, escalating, and resolving AI-related incidents, including model compromise, data leakage, performance failures, biased or harmful outputs, and integration failures with downstream systems. The incident response procedure shall define severity levels, response timeframes, escalation paths to the CIO, CISO, CTO, compliance leadership, and the executive committee as appropriate, root cause analysis requirements, and corrective action processes. Incident response procedures shall be tested periodically through tabletop exercises or simulations. AI incidents shall be tracked in a central incident management system and included in the regular AI risk reporting to executive leadership.

**Usual Control Owners:**  
Chief Information Security Officer, AI Operations Lead, Incident Response Manager, Model Owner, Chief Risk Officer

**Evidence to Review:**

→ AI incident response policy and procedures  
→ Incident severity classification matrix for AI-related events  
→ Incident log or incident management system records for the last twelve months  
→ Root cause analysis reports for closed AI incidents  
→ Corrective action plans and completion records  
→ Tabletop exercise or simulation records  
→ Escalation records showing incidents reported to leadership

**Audit Procedure:**

Obtain the AI incident response policy and procedures. Verify that the policy defines the types of AI incidents covered, severity classification criteria, response timeframes for each severity level, escalation paths, root cause analysis requirements, and corrective action processes.

Review the incident log for the last twelve months. Identify all AI-related incidents recorded and verify that each incident was classified by severity, investigated within the defined timeframe, and resolved with documented corrective actions. If no AI incidents were recorded in twelve months of production operation, assess whether the incident detection and logging mechanisms are functioning effectively rather than assuming no incidents occurred.

Select a sample of three closed AI incidents. For each, review the root cause analysis report to confirm that the investigation identified the underlying cause, that corrective actions were specific and measurable, and that the effectiveness of corrective actions was validated.

Review escalation records to confirm that incidents meeting the defined severity thresholds were escalated to the CIO, CISO, CTO, or executive committee within the required timeframes.

Request evidence of tabletop exercises or incident response simulations conducted in the last twelve months. Verify that the exercise tested AI-specific scenarios such as model compromise, biased output detection, or data poisoning, and that lessons learned were documented and incorporated into procedure updates.

* * *

## Area 6: Third-Party and Vendor Management

* * *

### Control 6.1 — Third-Party AI Governance and Vendor Component Assurance

**Control Description:**  
The organization shall implement controls for assessing and managing risks associated with AI models, APIs, datasets, software components, and services procured from external vendors. These controls shall include due diligence assessments of vendor AI practices before procurement, contractual obligations for transparency including access to model cards, performance metrics, change notification requirements, and audit rights. The organization shall review third-party components embedded in AI systems for performance assumptions, dependency risks, security vulnerabilities, and alignment with the organization's responsible AI principles. Vendor reliance does not transfer accountability for performance failures, biased outputs, or regulatory noncompliance to the vendor. SME and vendor challenge sessions shall be conducted to verify that the limitations described in vendor model documentation are realistic and that the vendor's stated performance metrics are reproducible in the organization's operating environment.

**Usual Control Owners:**  
Vendor Management Lead, Chief Procurement Officer, Model Risk Manager, Chief Information Security Officer, Legal Counsel, AI Program Manager

**Evidence to Review:**

→ AI vendor assessment methodology and due diligence checklists  
→ Vendor risk assessment reports for AI suppliers  
→ AI software contracts including clauses for model transparency, change notification, performance SLAs, audit rights, and liability allocation  
→ Vendor model cards or equivalent documentation  
→ Records of vendor challenge sessions and SME reviews  
→ Third-party component inventory within each AI system  
→ Security assessment or SOC 2 Type II reports from AI vendors  
→ Records of vendor performance monitoring against contractual SLAs

**Audit Procedure:**

Obtain the AI vendor assessment methodology. Verify that it includes evaluation criteria for the vendor's AI governance practices, model development and testing standards, data quality controls, bias testing, security posture, and incident response capabilities.

Select a sample of three AI vendors or third-party AI components currently in use. For each, obtain the vendor risk assessment report and verify that the assessment was completed before procurement or contract renewal, that it covers the defined evaluation criteria, and that residual risks were documented and accepted by the appropriate authority.

Review the AI software contracts for each sampled vendor. Verify that contracts include clauses for model transparency and documentation access, advance notification of model changes, performance service level agreements, audit rights, data handling and privacy obligations, liability allocation for model failures or biased outputs, and termination and transition provisions.

Obtain the vendor model cards or equivalent documentation. Verify that the documentation includes the model type, intended use, training data characteristics, performance metrics, known limitations, and bias testing results. Compare the vendor's stated performance metrics against the organization's independent validation results to assess reproducibility.

Request records of vendor challenge sessions. Confirm that SME and vendor meetings were conducted to review and challenge the limitations described in the vendor model documentation, and that the outcomes were documented with any discrepancies noted and tracked.

Review the third-party component inventory for each sampled AI system. Verify that all external models, APIs, datasets, and software libraries are cataloged, that their versions are tracked, and that dependency risks and security vulnerabilities are assessed. Cross-reference against vulnerability databases for known issues.

Examine vendor performance monitoring records. Confirm that the organization tracks vendor AI system performance against contractual SLAs and that underperformance is documented and escalated.

* * *

## Area 7: Independent Audit and Continuous Improvement

* * *

### Control 7.1 — Internal Audit of the AI Management System

**Control Description:**  
The organization shall conduct scheduled internal audits of the AI management system to verify the design adequacy and operating effectiveness of AI governance, risk management, development, deployment, monitoring, and vendor management controls. The internal audit program shall be designed in accordance with ISO/IEC 42001 requirements for internal audit, the 2024 Global Internal Audit Standards, and the organization's internal audit methodology. Audits shall cover both the compliance dimension (policies, approval processes, risk controls, contract clauses) and the technical dimension (data quality, model training, bias testing, third-party components, algorithm behavior) as defined in the class presentation. The audit program shall use a risk-based approach to determine audit frequency, scope, and depth, with high-risk AI systems receiving more frequent and detailed audit coverage. Audit findings shall be reported to the CIO, CISO, CTO, compliance leadership, and the executive committee, and shall be tracked through a formal corrective and preventive action (CAPA) process.

**Usual Control Owners:**  
Chief Audit Executive, Head of Internal Audit, AI Audit Lead, Chief Risk Officer, Audit Committee Chair

**Evidence to Review:**

→ AI audit program plan with scope, frequency, and risk-based prioritization  
→ Completed internal audit reports for AI systems in the last twelve months  
→ Audit finding tracker with corrective action plans, owners, and completion dates  
→ Evidence of auditor competency in AI governance and technical audit areas  
→ Audit committee or executive committee meeting minutes discussing AI audit results  
→ Follow-up audit evidence confirming closure of prior findings  
→ Mapping of audit coverage against the AI system inventory and risk classification

**Audit Procedure:**

Obtain the AI audit program plan. Verify that the plan covers both compliance audit procedures (policies, AI project approval, AI risks and controls, AI software contract clauses) and technical audit procedures (data quality, model training, bias audit, third-party components, algorithm behavior) as defined in the class presentation framework.

Review the risk-based prioritization methodology. Confirm that audit frequency and depth are determined by the risk classification of each AI system, with high-risk systems receiving more frequent coverage. Cross-reference the audit plan against the AI system inventory to identify any production AI systems that have not been audited or are not scheduled for audit.

Examine completed internal audit reports for the last twelve months. For each report, verify that findings are clearly documented with root cause analysis, risk ratings, corrective action plans, assigned owners, and target completion dates.

Review the audit finding tracker. Verify that all open findings have assigned owners and realistic completion dates, that overdue findings are escalated, and that closed findings have documented evidence of remediation and retesting.

Confirm that auditors performing AI audits have appropriate competency. Review training records, certifications, or evidence of subject matter expertise in AI governance, data science, model risk, and the applicable regulatory frameworks.

Review the audit committee or executive committee meeting minutes for discussion of AI audit results. Confirm that leadership reviewed the audit findings, discussed remediation progress, and directed actions where needed.

* * *

### Control 7.2 — Continuous Improvement and Lessons Learned

**Control Description:**  
The organization shall maintain a continuous improvement process for the AI management system that incorporates trend analysis of monitoring data, performance metrics, incident findings, audit results, and regulatory developments. Lessons learned from AI incidents, model failures, bias detections, drift events, and audit findings shall be documented and used to update controls, procedures, training materials, and risk assessments. The improvement process shall ensure that the AI governance framework, SOPs, and control activities evolve in response to operational experience and changing requirements. Performance evaluation and assessment outputs shall be reviewed to decide on AI model improvements, as referenced in the ISO 42001 building blocks presented in the class. Regular management reviews shall assess the overall effectiveness of the AI management system and direct improvements based on evidence.

**Usual Control Owners:**  
AI Program Manager, Chief Risk Officer, Head of Internal Audit, Model Risk Manager, Quality Management Lead

**Evidence to Review:**

→ Continuous improvement procedure documentation  
→ Lessons learned register from AI incidents, audit findings, and performance reviews  
→ Trend analysis reports from monitoring data and performance metrics  
→ Management review meeting minutes with decisions on AI system improvements  
→ Updated SOPs, policies, or controls reflecting lessons learned  
→ Training material updates incorporating lessons from incidents or audits  
→ Corrective and preventive action (CAPA) log with status tracking

**Audit Procedure:**

Obtain the continuous improvement procedure documentation. Verify that the procedure defines how monitoring data, incident findings, audit results, and regulatory developments are collected, analyzed, and used to update the AI management system.

Review the lessons learned register. Confirm that entries exist from AI incidents, model failures, drift detections, bias findings, and audit results over the last twelve months. For a sample of three entries, trace forward to verify that the lesson resulted in a documented change to a control, SOP, training material, or risk assessment.

Examine trend analysis reports. Verify that monitoring data and performance metrics are analyzed for trends at least quarterly and that the analysis identifies patterns requiring attention, such as recurring drift events, repeated fairness test failures, or persistent latency issues.

Review management review meeting minutes from the last twelve months. Confirm that the management review assessed the overall effectiveness of the AI management system, reviewed performance evaluation outputs, and directed specific improvements. Verify that decisions are documented with action items, owners, and target dates.

Review the CAPA log. Verify that corrective and preventive actions from all sources (incidents, audits, monitoring, management reviews) are tracked to completion, that effectiveness is verified after implementation, and that the CAPA process feeds back into the control framework.

Confirm that at least one policy, SOP, or control was updated in the last twelve months as a result of the continuous improvement process. If no updates occurred despite active monitoring and auditing, assess whether the absence of changes reflects genuine stability or a breakdown in the improvement feedback loop.  

## Emerging Trends That Will Change AI Auditing

Four trends from current research and standards development will reshape AI auditing practices over the next two to three years.

Continuous auditing replaces point-in-time assessments. The ETSI TS 104 008 framework for Continuous Auditing-Based Conformity Assessment defines methodologies for automated, ongoing conformity assessment. This addresses the fundamental limitation of periodic audits: AI systems change between audits, meaning the system the auditor evaluated may not be the system currently in production. Continuous auditing integrates automated checks into CI/CD pipelines, continuously verifying model accuracy, latency, resource usage, and data drift with thresholds and alerts.

Functional trustworthiness couples statistical rigor with risk-based requirements. The TÜV Austria framework introduces the concept of coupling a statistical definition of an AI's application domain with risk-based performance requirements and statistical testing. This approach moves beyond simple accuracy thresholds to define what performance means in context: a medical AI requires different statistical rigor than a product recommendation engine.

Structural metrics for hallucination detection improve on semantic baselines. For retrieval-augmented generation systems, structural alignment metrics like Entity Grounding and Relation Preservation provide more interpretable and bounded measures of hallucination than traditional semantic similarity metrics. These metrics achieve significantly higher detection performance (AUC approximately 0.979) for dangerous entity substitutions in legal documents.

Agentic AI requires specialized governance. AI systems that act autonomously over extended periods, managing memory and making sequential decisions, require audit approaches that traditional model evaluation doesn't cover. The Audited Skill-Graph Self-Improvement framework treats agent self-improvement as the compilation of an auditable skill graph, where improvements are promoted only after passing verifier-backed replay checks.

Implementation tip: Start preparing for continuous auditing now, even if your current audit program is periodic. Build automated performance checks into your AI deployment pipeline that run on every model update. Configure automated monitoring that compares production metrics against defined thresholds continuously. Create automated reporting that documents control status in real time rather than quarterly. These capabilities serve your current periodic audit program by providing better evidence, and they position you for the transition to continuous auditing as regulatory expectations evolve. Organizations that build continuous monitoring capabilities now will transition smoothly. Organizations that wait until continuous auditing is mandated will face compressed implementation timelines under regulatory pressure.

## Implementation Tips for AI Audit Programs

These principles apply across all 15 controls and all five audit phases.

Implementation tip on testing controls operationally: The most important distinction in AI auditing is between documentary compliance and operational compliance. Documentary compliance means the policy exists, the procedure is written, and the template is filled in. Operational compliance means the policy is followed, the procedure is executed, and the template reflects actual system behavior. Test operationally by sampling model outputs and independently verifying accuracy. Re-run bias tests independently rather than reviewing the team's bias test results. Test override mechanisms by examining how often human reviewers actually override AI recommendations and whether overrides follow documented procedures. If the override rate is below 2%, investigate whether human oversight is decorative rather than functional.

Implementation tip on the three lines of defense for AI: Structure your AI audit program using the three lines model. First line: the AI development and operations team owns and operates controls (data quality processes, model validation, production monitoring). Second line: risk management and compliance functions set standards, define policies, and monitor first-line control effectiveness (responsible AI policy, fairness standards, compliance monitoring). Third line: internal audit provides independent assurance that first and second line controls are designed adequately and operating effectively. Each control among the 15 should have explicit ownership assigned to one of the three lines. Controls without assigned ownership receive attention from nobody.

Implementation tip on building an audit evidence pack: For each AI system in scope, build an audit evidence pack that links risks to controls to operational evidence to improvement actions. The pack should contain the AI system inventory entry, the risk assessment, the model card, the monitoring dashboard outputs, incident logs, bias test results, and any corrective action records. This pack creates traceability from identified risks through implemented controls to evidence of control operation. Auditors can review the pack to assess control adequacy without requiring separate evidence requests for each control, which reduces audit burden on the development team and speeds the audit process.

Implementation tip on audit findings that matter: The most valuable AI audit findings aren't documentation gaps. They're operational gaps where controls exist but don't function, where monitoring runs but doesn't trigger action, where governance structures exist but don't make decisions, and where policies are written but aren't followed. Focus your audit energy on testing whether controls work, not just whether they exist. A finding that "the drift monitoring dashboard has been showing amber status for 4 months without triggering an investigation" is more valuable than a finding that "the model card is missing a version date."

## Key References and Authoritative Frameworks

Your AI audit program should align with these established standards:

- ISO/IEC 42001:2023, AI Management System (clauses 8-10 for operation, performance evaluation, and improvement)

- NIST AI Risk Management Framework 1.0, particularly the Measure and Manage functions

- NIST Generative AI Profile (2024 addition addressing emerging AI challenges)

- IIA AI Auditing Framework and 2024 IIA Standards

- ETSI TS 104 008, Continuous Auditing-Based Conformity Assessment for AI

- TÜV Austria Trusted AI Framework (functional trustworthiness and audit catalog)

- EU AI Act, Articles 9-15 and Annex IV for high-risk AI system requirements

- ISO/IEC 23894:2023, AI Risk Management

- Basel Committee SR 11-7, Model Risk Management

- UK PRA SS1/23, Model Risk Management Principles

- ISO/IEC 27001:2022, Information Security Management

- ISO/IEC 42005, AI Impact Assessment

- ISACA COBIT 2019 for IT governance of AI systems

- Three Lines Model (IIA) adapted for AI governance and assurance

If you audit AI systems by reviewing approval documentation, verifying that policies exist, and confirming that someone signed off on deployment, you will consistently produce clean audit reports for systems that are quietly failing in production. The documentation will be in order. The model will be drifting. The bias will be emerging. The third-party components will be changing. And the next audit will produce the same clean report because it's testing the same documentation rather than testing operational reality.

When you build an AI audit program that covers all 15 controls across all five phases, that tests operational compliance rather than documentary compliance, that samples model outputs independently rather than reviewing the team's own reports, and that evolves toward continuous auditing as standards and regulations advance, you create an assurance function that actually protects the organization. The audit catches drift before it causes harm. It identifies bias before regulators do. It validates that governance structures function rather than merely exist. And it drives continuous improvement by producing findings that operations teams can act on, not just file.

The strongest AI audit programs are continuous, not periodic. Start building that capability today.

Which of the 15 controls is weakest in your current AI audit program? Make that control the focus of your next audit cycle.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
