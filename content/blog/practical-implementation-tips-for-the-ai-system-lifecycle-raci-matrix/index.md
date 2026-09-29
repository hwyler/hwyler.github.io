---
title: "Practical Implementation Tips for the AI System Lifecycle RACI Matrix"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-controls"
  - "ai-ethics"
  - "ai-governance-matrix"
  - "ai-project-lifecyvle"
  - "ai-raci-matrix"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "technology"
---

# Why a Lifecycle RACI Matrix Matters

Most AI governance failures trace back to one root cause: nobody owned the problem at the moment it mattered. A model drifts in production and nobody monitors it because the data scientist who built it moved to another project. A bias issue surfaces and nobody knows whether the product owner, the AI risk manager, or the compliance officer should investigate. An AI system reaches end-of-life and sensitive training data sits on decommissioned servers because nobody owned the disposal process.

A lifecycle RACI matrix assigns accountability, responsibility, consultation, and information obligations to named roles at every stage of an AI system's life, from initial business case through retirement. It spans three lines of defense: operational management builds and runs the system, specialized support functions provide risk, compliance, and security oversight, and internal audit provides independent assurance. Governance bodies approve major decisions and set strategic direction.

Without this matrix, organizations rely on informal ownership that works when the team is small and breaks catastrophically when the organization scales, when people change roles, or when a regulator asks who was accountable for a specific decision.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/66869f910de243d9cad8bfbd_detailed-macro-view-electronic-microchip-1.jpg?w=1024)

* * *

## Understanding the Three Lines Model for AI

### First Line: Operational Management

These are the people who build, deploy, and run AI systems day to day. They own the risk because they create the risk.

**AI Asset Owner** holds ultimate business accountability. This person owns the business case, approves major decisions, and is answerable to the governance body for the system's outcomes. They don't build the model. They own the business result the model produces.

**Product Owner** translates business requirements into product specifications, manages stakeholder expectations, and drives the product roadmap. They define what the AI system should do, not how.

**Data Owner** governs the data the AI system consumes. They authorize data access, ensure data quality, and maintain accountability for data assets throughout the lifecycle. This role is chronically underresourced in most organizations.

**Data Scientist** develops and trains models, performs data analysis and feature engineering, validates model performance, and implements machine learning algorithms. They are responsible for the technical quality of the model.

**AI/ML Engineer** takes models from development to production. They build scalable ML pipelines, optimize model performance in production environments, and maintain model infrastructure. The gap between a working notebook and a production system is where this role lives.

**Data Engineer** manages data pipelines and infrastructure, ensures data flow and integration, implements data quality controls, and maintains data processing systems. Without reliable data engineering, every other role fails.

**AI Architect** designs the technical architecture, defines technology standards, ensures scalability and integration, and guides technical implementation decisions. They own the blueprint.

**IT Operation Manager** ensures stability, availability, and performance of IT systems supporting AI infrastructure, manages incident response, and oversees system monitoring.

**Tip:** The most common RACI failure in the first line is confusing the AI Asset Owner with the Product Owner. They are not the same role. The AI Asset Owner is a senior business executive accountable for whether the AI system delivers business value. The Product Owner is a mid-level role managing requirements and delivery. When organizations merge these roles, the business accountability function disappears because the Product Owner doesn't have the authority or visibility to make portfolio-level decisions. Keep them separate. The AI Asset Owner should attend governance body meetings and sign off on phase transitions. The Product Owner should attend project reviews and manage day-to-day delivery. If you can't identify a business executive willing to be the AI Asset Owner, that tells you the project lacks genuine business commitment.

* * *

### Second Line: Specialized Support

These roles provide expertise, challenge, and oversight. They don't build or run the AI system, but they ensure it meets risk, compliance, security, and ethical standards.

**Chief AI Officer** (or AI Program Manager) oversees overall AI strategy and governance, drives AI adoption, ensures ethical AI practices, and aligns AI initiatives with business strategy. This role is accountable for the organizational AI program, not individual systems.

**AI Risk Manager** identifies and manages AI-specific risks, develops risk mitigation strategies, monitors risk indicators, and ensures compliance with risk frameworks. This role provides the risk lens that first-line teams often lack.

**AI Compliance Manager** ensures regulatory compliance, monitors evolving regulations, implements compliance controls, and manages audit requirements. In organizations with mature red teaming capabilities, an AI Red Team Manager may support this function.

**Data Protection Officer** manages privacy and data protection requirements, ensures GDPR and privacy law compliance, conducts privacy impact assessments, and handles data subject requests.

**Chief Information Security Officer** oversees security for AI systems, defines security standards, manages cybersecurity risks, and ensures data and model protection.

**AI Procurement Category Manager** manages vendor relationships, negotiates contracts and SLAs, evaluates vendor capabilities, and ensures procurement compliance. This role is critical for organizations that buy rather than build AI systems.

**AI Center of Excellence** establishes standards and best practices, provides technical guidance and training, promotes knowledge sharing, and drives AI capability development across the organization.

**Tip:** The second line must have genuine authority to challenge first-line decisions. In many organizations, the AI Risk Manager or AI Compliance Manager is consulted but has no power to block a deployment that fails risk or compliance requirements. This makes the second line decorative. Embed second-line approval gates into the lifecycle where they appear as "A" (Accountable) in the RACI matrix, particularly at design review, pre-deployment compliance review, and model validation approval. If the AI Risk Manager is accountable for approving the risk assessment before deployment, they have real authority. If they're only consulted, their findings become suggestions that project pressure can override.

* * *

### Third Line: Independent Assurance

**AI Internal Auditor** conducts technical auditing of AI systems, validates model performance and compliance, identifies control gaps, and provides independent assurance. The auditor doesn't build, doesn't operate, and doesn't consult on design. They test whether controls work.

**Tip:** Internal audit should not be consulted during the design or development phases. Their independence depends on having no involvement in building the thing they later audit. In the RACI matrix, audit appears as "I" (Informed) during design and development, and as "R" (Responsible) only during scheduled audits in the operations phase. If your auditor is consulting on system design, they can't independently audit that design later. Protect audit independence even when it's tempting to use their expertise during design. The short-term benefit of their input doesn't justify the long-term cost of compromised independence.

* * *

### Governance Bodies

**AI Committee** provides strategic oversight, ensures ethical and responsible AI development, approves major investments, and governs AI policies and standards. This is the decision-making body for AI at the enterprise level.

**AI/Model Risk Committee** approves and monitors AI and model risks and performance. This body reviews risk assessments, approves risk acceptance decisions, and monitors aggregate model risk across the portfolio. Regulated organizations such as those in financial services may need to have a separated committee to approve risk models.

**Tip:** Define the boundary between the AI Committee and the AI/Model Risk Committee clearly. The AI Committee makes strategic and investment decisions. The AI/Model Risk Committee makes risk acceptance and performance monitoring decisions. When both bodies exist, the most common dysfunction is overlap: both committees review the same materials and neither makes the decision, or each assumes the other approved it. Assign specific artifacts to each committee. The AI Committee approves the business case, the project charter, and the final deployment. The AI/Model Risk Committee approves the risk assessment, the model validation package, and ongoing performance reports. Document which committee has final authority for each decision type and publish the decision rights matrix.

* * *

## Stage 1: Business Case Identification and Planning

### Defining the Business Problem

The AI Asset Owner is accountable and the Product Owner is responsible for defining the business problem in measurable terms and establishing KPIs. The second line (AI Risk Manager, AI Compliance Manager) should be consulted early, not after the business case is approved.

**What to implement:**

The business case analysis must include specific, measurable KPIs, a stakeholder value proposition, and success criteria. The Product Owner develops these artifacts while the AI Asset Owner approves them.

Simultaneously, the Product Owner must identify all relevant stakeholders, determine applicable regulations, classify the AI system under EU AI Act risk categories, and produce a compliance gap analysis. The Chief AI Officer or AI Program Manager is accountable for ensuring this regulatory assessment is completed. The AI Compliance Manager is consulted.

The feasibility study, covering technical, operational, and financial dimensions, is the Product Owner's responsibility with the Chief AI Officer accountable. The Data Owner, AI Architect, and others are consulted on specific dimensions. This study must include a build-versus-buy analysis and vendor risk assessment if procurement is involved.

**Tip:** Gate the business case approval strictly. The RACI shows the AI Committee as accountable for approving the project to proceed. Enforce this by requiring a formal presentation to the governance body with the business case, feasibility study, and initial risk and impact assessments as a complete package. Do not allow projects to begin development with "provisional" or "verbal" approval. I've seen organizations where data scientists start building models months before governance approval because the Product Owner gave informal permission. By the time the governance body reviews the project, significant investment has already been made, creating sunk cost pressure to approve regardless of the assessment results. Gate the funding, not just the approval. No budget is released until the AI Committee's approval is documented in meeting minutes.

The project charter should define boundaries, constraints, key deliverables, and detailed acceptance criteria. Critically, it must include a change management plan and user training plan from the outset. The AI Asset Owner is accountable and the Product Owner is responsible. These plans aren't afterthoughts. They determine whether the AI system will be adopted. Projects that defer change management planning to the deployment phase consistently underdeliver on business value because users aren't prepared.

* * *

## Stage 2: AI System Design

### Model Selection and Architecture

The Data Scientist is responsible for evaluating and selecting potential AI/ML models and algorithms. The AI Architect is accountable for this selection, ensuring the chosen approach fits the technical architecture and standards.

The AI Architect is accountable for the overall technical architecture design, with the Data Scientist, AI/ML Engineer, and Data Engineer consulted. The IT Operation Manager is informed because they'll support the production infrastructure.

**What to implement:**

The design phase produces critical artifacts: system architecture diagrams, interface specifications, integration plans, data management plans, explainability design documents, and the AI risk assessment.

The risk assessment deserves special attention. The Product Owner is responsible, the AI Risk Manager is accountable, and nearly every other role is consulted. This breadth of consultation is intentional. AI risks span technical, business, compliance, security, and ethical dimensions. No single role can identify all risks.

The impact assessment follows the same pattern: the Product Owner drives it, the AI Compliance Manager is accountable, and broad consultation ensures comprehensive coverage.

**Tip:** The design review is the most important gate in the entire lifecycle. The RACI assigns the AI Architect as responsible, the AI Committee as accountable, and nearly every second-line function as consulted or informed. Treat this gate as a formal review requiring documented evidence that all design requirements, including ethical, security, and compliance requirements, are met before any development begins. I implement a design review checklist with mandatory sign-off from the AI Risk Manager, AI Compliance Manager, and CISO before the AI Committee grants development approval. If any of these three roles identifies an unresolved concern, the design review cannot pass. This creates healthy tension between the project team's desire to start building and the oversight functions' need to ensure the design is sound. The tension is productive. Removing it by making second-line involvement advisory rather than mandatory is how organizations ship systems that fail compliance requirements.

### Human Oversight and Bias Testing Design

The Product Owner is responsible for designing human oversight workflows with the AI Risk Manager accountable. The Data Scientist is responsible for defining fairness metrics and bias testing procedures with the AI Risk Manager accountable.

**What to implement:**

Human oversight protocols must define when human review is triggered, who performs it, what information they receive, what authority they have, and how their decisions are documented. Design these workflows before development, not after deployment.

Fairness testing plans must specify the protected attributes to be tested, the fairness metrics to be measured, the acceptable disparity thresholds, and the testing procedures. These decisions involve value judgments that the Data Scientist alone should not make. The AI Risk Manager's accountability ensures that fairness criteria reflect organizational policy and regulatory requirements, not just technical convenience.

**Tip:** Involve the AI Center of Excellence in both human oversight design and fairness testing design. They appear as "C" (Consulted) in the RACI for bias and fairness testing. Use this consultation to ensure that fairness testing approaches are consistent across the organization's AI portfolio. If every project team selects different fairness metrics, different thresholds, and different protected attributes, the organization can't report a coherent fairness posture to regulators or the board. The AI Center of Excellence should maintain a fairness testing standard that provides default metrics and thresholds, which project teams can deviate from only with documented justification approved by the AI Risk Manager.

* * *

## Stage 3: Data Collection and Preparation

### Data Requirements and Collection

The Data Owner is responsible for defining data requirements and is accountable for data collection compliance. The Data Scientist, AI/ML Engineer, and Data Engineer are consulted on technical requirements.

**What to implement:**

Data requirements specification must cover data sources (internal and external), data lineage, metadata documentation, and datasheets for training datasets. The Data Owner authorizes data access and confirms the legal basis for processing.

Data collection must ensure all legal, IP, copyright, regulatory, and ethical consents are in place. The Data Owner is accountable with the Data Engineer responsible for technical implementation. The AI Compliance Manager and Data Protection Officer are consulted to confirm compliance.

**Tip:** The RACI correctly assigns the Data Owner as accountable for data quality assessment, with the Data Scientist responsible for performing the assessment. Enforce this accountability by requiring the Data Owner to sign a fitness-for-use certification before the data enters model training. This certification states that the Data Owner has reviewed the data quality assessment, understands the limitations, and confirms the data is appropriate for the intended AI use case. Without this sign-off, the Data Scientist makes unilateral decisions about data quality that the Data Owner should be validating. I've seen models trained on datasets that the Data Owner would have rejected if they'd been asked, because nobody asked. The certification takes 30 minutes to review and sign. The cost of training a model on inappropriate data and discovering the problem in production is orders of magnitude higher.

### Privacy and Bias in Data

The Data Protection Officer is accountable for privacy compliance verification. The Data Owner is responsible for implementing privacy controls. The Data Scientist is responsible for anonymization techniques with the Data Owner accountable.

The Data Scientist is responsible for analyzing datasets for potential bias, with the Data Owner and Data Engineer consulted.

**What to implement:**

Privacy impact assessments must be completed before personal data enters the AI pipeline. Anonymization, pseudonymization, or other privacy-enhancing techniques must be applied before training begins. Access controls must be documented and enforced.

Bias assessment of training data must evaluate representativeness of the target population across protected attributes. Document demographic analysis and any imbalances identified, along with mitigation approaches.

**Tip:** The final data sign-off involves nearly every role in the RACI as informed, with the Data Owner responsible, the AI/Model Risk Committee accountable, and the AI Compliance Manager, AI Center of Excellence, and AI Internal Auditor consulted or informed. This broad involvement is appropriate because the training data fundamentally determines the AI system's behavior. However, coordinating sign-off from this many stakeholders creates bottleneck risk. Implement a structured data review meeting rather than sequential approvals. Bring all relevant parties into a single 90-minute review session where the data quality certification, privacy compliance checklist, and bias assessment are presented together. Each stakeholder provides their approval or raises concerns in the meeting. Document decisions in meeting minutes and circulate for same-day sign-off. Sequential approvals for the same dataset can take weeks. A coordinated review meeting produces the same rigor in 90 minutes.

* * *

## Stage 4: Data Analysis and Exploration

### Feature Engineering and Bias Review

The Data Scientist is responsible for exploratory data analysis, pattern identification, feature engineering, and assumption validation. The Data Owner is accountable throughout.

The critical checkpoint is feature bias assessment: the Data Scientist is responsible, the AI Risk Manager is accountable, and the Data Owner, Data Engineer, and AI Architect are consulted.

**What to implement:**

Feature bias assessment must verify that engineered features don't introduce or amplify bias and don't act as proxies for protected attributes. A zip code feature that correlates strongly with ethnicity is a proxy variable that introduces discrimination even if ethnicity isn't directly used. Document the proxy variable analysis and the fairness impact assessment for each feature.

The final feature set documentation requires formal approval, with the AI/Model Risk Committee accountable. The approved feature catalog becomes a controlled document that cannot be modified without re-approval.

**Tip:** Feature engineering is where subtle bias most often enters AI systems, and it's the stage where oversight is weakest in most organizations. Data Scientists make dozens of feature engineering decisions that individually seem reasonable but collectively can introduce systematic disparities. The AI Risk Manager's accountability for the feature bias assessment must be genuine, not nominal. Require the AI Risk Manager to review the proxy variable analysis before any feature set is finalized. If the AI Risk Manager doesn't have the technical skills to evaluate proxy variables, the AI Center of Excellence should provide technical support. The accountability stays with the AI Risk Manager. The technical analysis can be delegated. I implement a "feature impact review" where each proposed feature is evaluated against protected attributes using correlation analysis and disparate impact testing. Features with correlation above a defined threshold require documented justification for inclusion. This adds one to two days to the feature engineering phase and prevents bias issues that would otherwise surface during model validation, when they're far more expensive to fix.

* * *

## Stage 5: Model Development and Training

### Development Through Champion Selection

The Data Scientist is responsible for algorithm selection, model training, benchmarking, and hyperparameter tuning. The AI Architect is accountable for algorithm selection rationale, data partitioning, and training methodology.

Fairness testing during development is the Data Scientist's responsibility with the AI Risk Manager accountable. The Chief AI Officer is consulted, confirming that fairness standards are met before the model advances.

**What to implement:**

Model development must follow the approved model development plan with documented algorithm selection rationale. The Data Scientist develops and compares multiple model candidates, documenting benchmarking results and performance metrics.

Fairness audit during development tests for performance disparities across demographic subgroups. If fairness metrics are not met, mitigation actions must be applied and documented before the model can be selected as the champion.

The champion model selection requires documentation of architecture, parameters, and training process. The AI Architect provides formal approval.

**Tip:** The RACI assigns the AI Architect as accountable for the formal review and approval of the champion model, with the AI/Model Risk Committee providing governance approval. This two-level approval is important. The AI Architect validates technical soundness. The AI/Model Risk Committee validates that the model meets all development-stage criteria including fairness, robustness, and compliance requirements. Don't allow these approvals to merge into a single gate. I've seen organizations where the AI Architect approves the champion model and nobody else reviews it before deployment preparation begins. Separate the technical approval (AI Architect) from the governance approval (AI/Model Risk Committee) and require both before the model advances to evaluation and validation. The technical approval confirms the model works. The governance approval confirms it's safe to evaluate for production deployment.

* * *

## Stage 6: Model Evaluation and Validation

### Independent Validation

The Data Scientist is responsible for performance evaluation with the AI Risk Manager accountable. The AI Risk Manager is also accountable for the bias and fairness audit, where the Data Scientist performs the testing.

Business acceptance testing involves nearly every first-line role, with the AI Asset Owner accountable and the Product Owner responsible. The AI Risk Manager and AI Compliance Manager are consulted.

Robustness testing is the AI/ML Engineer's responsibility with the AI Architect accountable. The AI Compliance Manager and CISO are consulted, confirming security and adversarial resilience.

**What to implement:**

This stage produces the evidence package that supports the deployment decision. The Product Owner compiles all testing and validation reports into a single package, with the Chief AI Officer accountable.

The deployment approval gate is critical. The Product Owner submits the complete evidence package for governance approval. The AI Committee is accountable for the final deployment decision. The Chief AI Officer, AI Risk Manager, AI Compliance Manager, the AI Center of Excellence, and the AI Internal Auditor are all consulted or informed.

External audit, regulator notification, or conformity assessment may be required for high-risk systems under the EU AI Act. Document compliance with applicable requirements.

**Tip:** The evidence package for governance review should be a self-contained document that the AI Committee can evaluate without needing to request additional information. Include the model validation report, bias and fairness audit results, business acceptance testing results, robustness testing report, explainability documentation, model card, operator handbook, and staff training certification. If any artifact is incomplete or missing, the package should not be submitted. I implement a "package completeness checklist" that the Product Owner must complete before submission. Each artifact is listed with a status (complete, incomplete, not applicable) and a link to the document. The Chief AI Officer reviews the checklist before it reaches the AI Committee. Incomplete packages waste governance body time and create pressure to approve with conditions, which invariably means the conditions are forgotten. A complete package submitted once is faster than an incomplete package submitted three times with follow-up requests.

* * *

## Stage 7: Model Deployment

### Production Deployment

The AI/ML Engineer is responsible for most deployment activities: developing the deployment plan, setting up the production environment, building model serving infrastructure, packaging the model, releasing it to production, and deploying monitoring tools. The AI Architect is accountable for infrastructure and deployment architecture decisions. The IT Operation Manager is accountable for environment setup and monitoring infrastructure.

Security and compliance verification during deployment is the Product Owner's responsibility with the CISO accountable. The AI Compliance Manager and AI Risk Manager are consulted.

**What to implement:**

The deployment plan must include rollback procedures, versioning, and integration points. The rollback strategy is not optional. Every deployment must have a tested method for reverting to the previous state if problems emerge in production.

Operational readiness verification covers infrastructure, personnel, access rights, and monitoring tools. The AI Asset Owner is responsible, with the Chief AI Officer accountable. This checkpoint confirms that everything needed to operate and monitor the system is in place before go-live.

The final deployment requires the AI Architect as accountable, with the AI Committee and AI/Model Risk Committee informed. The Product Owner and AI Internal Auditor are informed.

**Tip:** Separate the deployment into two distinct events: staging deployment and production go-live. The RACI shows both activities with different accountability structures. Staging deployment allows final integration testing in a production-equivalent environment without affecting real users or data. Production go-live is the point of no return. Between staging and go-live, conduct a 24 to 48 hour observation period where monitoring dashboards are verified, alert configurations are tested, and the operations team confirms they can execute the runbook. I've seen organizations deploy directly to production and discover within hours that monitoring alerts were misconfigured, the operations team didn't have the correct access permissions, and the rollback procedure had never been tested in the production environment. The staging period catches these issues when they're easy to fix. After go-live, they become incidents.

### API Documentation and Version Control

The Data Scientist is responsible for API documentation with the AI Architect accountable. Version control for models, code, and deployment artifacts is the Data Scientist's responsibility with the AI Architect accountable.

**Tip:** Version control is not just a technical hygiene practice. It's a regulatory requirement for high-risk AI systems under the EU AI Act. Every model version, every code change, and every deployment artifact must be tracked with timestamps, attribution, and the ability to reconstruct any previous state. Implement version control from day one, not retroactively. The cost of implementing version control during development is near zero. The cost of reconstructing version history after a regulator requests it is enormous and the results are unreliable. Use Git-based repositories for code and model artifacts. Use a model registry (MLflow, Weights and Biases, or equivalent) for model versions. Ensure that every production model can be traced back to its training data, training code, and validation results through the version control system.

* * *

## Stage 8: Model Operation, Monitoring, and Maintenance

### Continuous Operations

This stage spans the longest period of the AI system's lifecycle and involves the broadest set of roles in ongoing activities.

The AI/ML Engineer is responsible for post-deployment validation, continuous performance monitoring, and infrastructure maintenance. The AI Risk Manager is accountable for ongoing monitoring decisions.

The Data Owner is accountable for data drift detection, with the Data Scientist responsible for technical monitoring.

Scheduled audits are the AI Internal Auditor's responsibility with the AI/Model Risk Committee accountable. This is where the third line exercises its independent assurance function.

**What to implement:**

Post-deployment validation confirms stability and performance within the first days or weeks of production. The AI Risk Manager is accountable, confirming that the system performs as expected on real production data.

Continuous monitoring covers model accuracy, latency, data drift, model degradation, and user feedback. The RACI distributes these responsibilities across multiple roles: the AI/ML Engineer monitors technical performance, the Data Scientist monitors data drift, the Product Owner collects user feedback, and the AI Risk Manager provides oversight.

Decision logging and audit trails are the Data Scientist's responsibility with the AI Risk Manager and AI Compliance Manager accountable. Every model decision must be recorded for traceability and regulatory compliance.

The RACI for the operations phase involves many roles with overlapping monitoring responsibilities. Without clear coordination, monitoring activities fragment and gaps emerge between what the AI/ML Engineer monitors (technical performance), what the Data Scientist monitors (data drift), and what the Product Owner monitors (user feedback). Implement a single operational dashboard that consolidates all monitoring dimensions. Assign the AI/ML Engineer or IT Operation Manager as the dashboard owner responsible for ensuring all data feeds are active and current. Hold a weekly 30-minute operations review where all monitoring stakeholders review the dashboard together. This catches issues that fall between responsibilities. If the Data Scientist notices drift but the AI/ML Engineer hasn't seen a performance impact yet, the weekly review surfaces the early warning. Without this coordination, the Data Scientist documents the drift in their log and the AI/ML Engineer doesn't learn about it until performance actually degrades weeks later.

### Incident Response and Continuous Improvement

The AI/ML Engineer is responsible for incident investigation and resolution with the AI Risk Manager accountable. The CISO is consulted on security-related incidents.

Continuous improvement reviews are the AI/ML Engineer's responsibility with the AI Architect accountable. Consolidated reporting to the governance body is the Product Owner's responsibility with the AI Asset Owner accountable.

Build an incident severity classification specific to AI systems. Traditional IT incident classifications (P1 through P4 based on business impact and urgency) don't capture AI-specific incident types. Add AI-specific categories: model producing biased outputs affecting a protected group (always P1 regardless of volume), model performance degraded beyond monitoring thresholds (P2 minimum), data drift detected without performance impact yet (P3 but with mandatory investigation timeline), and user reports of unexpected or unexplainable outputs (P3 with escalation to P2 if pattern emerges). Map each severity level to the RACI roles involved in response. P1 AI incidents should immediately involve the AI Risk Manager, AI Compliance Manager, and CISO alongside the first-line technical team. P3 incidents can be handled by first-line teams with second-line notification.

* * *

## Stage 9: Model Retraining and Updates

### Trigger Identification Through Champion Promotion

Retraining follows a disciplined process: confirm the trigger, collect new data, retrain a challenger model, validate it, test it against production traffic, deploy incrementally, document everything, and obtain governance approval to promote the new champion.

The Data Scientist is responsible for most technical activities. The AI Architect is accountable for trigger confirmation, data validation, and retraining methodology. The AI Risk Manager is accountable for regression testing including fairness and robustness revalidation.

**What to implement:**

Retraining triggers must be predefined and documented. Common triggers include performance dropping below a defined threshold, data drift exceeding monitoring limits, new training data becoming available that materially improves coverage, regulatory changes requiring model adjustments, and scheduled periodic retraining.

The challenger model must undergo the same evaluation rigor as the original champion: performance testing, fairness audit, robustness testing, and explainability validation. Retraining is not a shortcut past validation.

A/B testing or shadow deployment compares the challenger against the current champion on real production data. The Data Scientist is responsible with the AI Architect accountable. Only after the challenger demonstrates superior or equivalent performance across all criteria should promotion be considered.

Governance approval for champion promotion follows the same gate as original deployment: the Product Owner is responsible, the AI/Model Risk Committee is accountable, and the Chief AI Officer is consulted. The AI Committee provides final approval.

**Tip:** The most dangerous moment in the retraining cycle is incremental rollout. The RACI assigns the AI Architect as responsible and the AI/ML Engineer as accountable for canary or blue-green deployment. Ensure that rollback is possible at every stage of the incremental rollout. Define automated rollback triggers: if the new model's error rate exceeds the previous champion's error rate by more than a defined margin during canary deployment, automatic rollback occurs without waiting for human intervention. Manual rollback decisions during production incidents are too slow. By the time someone decides to roll back, hundreds or thousands of decisions may have been made by the underperforming model. Automated rollback triggers limit exposure. Test these triggers before every retraining deployment.

* * *

## Stage 10: Model Retirement

### Decommissioning Through Project Closure

Retirement is the most neglected lifecycle stage and the one where data protection failures most commonly occur.

The AI Architect is responsible for developing the decommissioning plan with the AI Asset Owner accountable. The AI Risk Manager, AI Compliance Manager, and AI Procurement Category Manager are consulted.

Stakeholder communication is the Product Owner's responsibility with the AI Asset Owner and AI Compliance Manager accountable.

Technical decommissioning, removing the model from production, disabling APIs, and dismantling infrastructure, is the IT Operation Manager's responsibility with the AI/ML Engineer accountable.

Data and model archiving is the Data Scientist's responsibility with the Product Owner accountable and the Data Protection Officer consulted.

Secure data destruction is the Data Scientist's responsibility with the AI Risk Manager accountable and the CISO consulted.

**What to implement:**

The decommissioning plan must cover timeline, technical steps, responsibilities, data handling (what is archived, what is destroyed, what retention periods apply), vendor offboarding if applicable, and transition plans for any processes that depended on the AI system.

Data retention compliance verification is the Product Owner's responsibility with the AI Risk Manager accountable. This checkpoint confirms that all data and model artifacts are either retained or deleted according to legal, regulatory, and internal policies. The Data Protection Officer is consulted to confirm privacy compliance.

Lessons learned documentation captures insights, challenges, and best practices from the entire lifecycle. The Product Owner is responsible with the Chief AI Officer accountable. This knowledge feeds into the AI Center of Excellence's standards and best practices.

The final decommissioning report is presented to the AI Committee (accountable) and AI/Model Risk Committee for project closure.

**Tip:** Data destruction during decommissioning requires the same rigor as data protection during operation. The RACI correctly assigns the AI Risk Manager as accountable for secure destruction with the CISO consulted. But most organizations focus destruction efforts on the production environment and forget about copies. Training data may exist in development notebooks, shared drives, feature stores, backup systems, vendor environments, and individual workstations. Before issuing a destruction certificate, conduct a data location audit that identifies every copy of the AI system's data across all environments. Destroy or confirm deletion of each copy with documented evidence. The destruction certificate should list every location where data existed and the method and date of destruction for each. I've seen decommissioned AI systems where the production data was properly destroyed but a complete copy of the training dataset, including personal data, sat in a data scientist's cloud storage account for 18 months after retirement because nobody checked.

* * *

## Cross-Cutting Implementation Tips

### Handling the Chief AI Officer Role

The RACI assigns the Chief AI Officer as accountable or consulted at numerous critical points, particularly governance approvals and strategic decisions. The matrix notes this role may be covered by an AI Program Manager or PMO Lead.

**Tip:** Regardless of title, this role must have three things: executive authority to approve or reject AI system progression through lifecycle gates, visibility across the entire AI portfolio (not just individual projects), and direct reporting access to the AI Committee. If the person in this role lacks any of these, the lifecycle gates they're accountable for become approvals without teeth. I've seen organizations assign the Chief AI Officer role to a senior data scientist or a technology director who had technical expertise but no executive authority. Their "accountability" consisted of being informed about decisions that had already been made. The role must carry genuine decision-making power or the governance structure documented in the RACI is fictional.

### Maintaining RACI Integrity Over Time

The matrix is useless if it doesn't reflect current reality.

**Tip:** Review the RACI matrix every six months or whenever organizational structure changes. For each role, verify that a named individual is assigned, that the individual understands their RACI responsibilities, and that they've actually performed those responsibilities during the review period. Check for orphaned accountabilities where the named individual has changed roles without a successor being assigned. Check for accumulated responsibilities where one person holds "A" for so many activities that they can't effectively exercise accountability for any of them. A single person accountable for 40 activities across 15 AI systems isn't accountable. They're overwhelmed. Distribute accountability realistically.

### The Governance Body Meeting Cadence

The AI Committee and AI/Model Risk Committee appear at critical decision points throughout the lifecycle. Without a regular meeting cadence, these approval gates become bottlenecks.

**Tip:** The AI Committee should meet monthly with a standing agenda that includes new project approvals, phase gate reviews, and portfolio health reporting. The AI/Model Risk Committee should meet bi-weekly or monthly with a standing agenda covering risk assessments awaiting approval, model validation reviews, monitoring reports, and incident reviews. Schedule these meetings in advance for the full year. AI projects that need governance approval shouldn't wait weeks for an ad hoc committee meeting. The regular cadence ensures that governance gates don't become project bottlenecks while maintaining genuine oversight. If urgent approvals are needed between scheduled meetings, define a streamlined approval process (such as circular resolution with documented rationale) that maintains the governance standard without requiring a full committee meeting.

### Documenting RACI Decisions, Not Just Assignments

The RACI matrix tells you who is involved. It doesn't tell you what they decided.

**Tip:** At every point in the lifecycle where an "A" (Accountable) role makes a decision, document the decision, the rationale, the alternatives considered, and any dissenting views. Store these decision records alongside the lifecycle artifacts. When a regulator or auditor asks "who approved this model for deployment and why?" you need more than a name. You need the evidence that the accountable person reviewed the relevant information and made an informed decision. Decision records that consist of "approved" with a signature and date are insufficient. Decision records that include "approved based on review of model validation report showing 94% accuracy exceeding the 90% threshold, fairness audit showing demographic parity within 3% acceptable range, and robustness testing confirming resilience to defined adversarial scenarios" are defensible.

* * *

## Key References

**Three Lines Model:**

- IIA Three Lines Model (2020)

- COSO Internal Control Framework

**AI Lifecycle:**

- ISO/IEC 5338:2023 (AI System Lifecycle Processes)

- ISO/IEC 22989:2022 (AI Concepts and Terminology)

- NIST AI RMF 1.0 (Govern, Map, Measure, Manage functions)

- ISO/IEC 42001:2023 (AI Management Systems)

**Model Risk Management:**

- SR 11-7, Federal Reserve Board (2011)

- OCC Bulletin 2011-12

**Data Governance:**

- DAMA DMBOK2

- ISO/IEC 5259 series (Data Quality for Analytics and ML)

**Security:**

- ISO/IEC 27001:2022

- NIST AI 100-1 (Adversarial Machine Learning)

**Privacy:**

- ISO/IEC 27701:2019

- GDPR, Regulation (EU) 2016/679

**AI Governance:**

- ISO/IEC 38507:2022 (Governance of AI)

- EU AI Act, Regulation (EU) 2024/1689

* * *

A RACI matrix that sits in a governance document and is never referenced during actual work is worse than having no matrix at all. It creates the illusion of accountability while nobody exercises it.

A RACI matrix that is embedded in project workflows, referenced at every phase gate, updated when roles change, and enforced when accountability is tested is the foundation of AI governance that works under pressure.

The difference between the two is not the matrix itself. It's whether the organization treats it as a living operational tool or as a compliance artifact that satisfied an auditor once and was never opened again.
