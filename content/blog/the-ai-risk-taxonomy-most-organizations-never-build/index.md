---
title: "The AI Risk Taxonomy Most Organizations Never Build"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-goverance"
  - "ai-projects"
  - "ai-risk-management"
  - "ai-risks"
  - "artificial-intelligence"
  - "business"
  - "fair-risk-management"
  - "hernan-huwyler"
  - "iso-23894"
  - "iso-27001"
  - "iso-31000"
  - "mitre-atlas"
  - "technology"
---

# Top Risk Scenarios and Controls That Actually Protect Your AI Project

A risk register with 15 vaguely worded AI risks and a color-coded heat map is not a taxonomy. It is a liability.

I reviewed an organization's AI risk assessment last year that listed "AI bias" as a single risk with a "medium-high" rating. That was it. No decomposition into the dozen distinct ways bias manifests. No distinction between bias in training data, bias from proxy variables, bias from temporal misalignment, or bias from feedback loops. No specific controls mapped to specific failure modes. When their credit model produced discriminatory outcomes six months later, nobody could trace the failure to a gap in their controls because their taxonomy was too shallow to reveal where the gaps were.

The difference between organizations that manage AI risk effectively and those that just talk about it comes down to granularity. You need a taxonomy that decomposes AI risk into specific, actionable scenarios, each linked to a named control with concrete activities. This post provides exactly that: a structured taxonomy of 100 AI risk scenarios across 14 domains, with recommended controls mapped to COBIT 2019 governance objectives. Every scenario follows a consistent structure: what can go wrong, why it matters, and what to do about it.

This is a long reference piece. Use it as a working document, not a single-sitting read.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/copenhagen.jpg?w=1024)

## Why Most AI Risk Taxonomies Fail

The typical AI risk taxonomy fails for three reasons.

First, it operates at the wrong altitude. "Model risk" is not a scenario. It is a category that contains dozens of scenarios, each with different causes, different impacts, and different controls. When you treat a category as a scenario, your controls become generic and your residual risk unmeasurable.

Second, it ignores organizational and process risks. Most AI taxonomies obsess over technical risks like adversarial attacks and data poisoning while overlooking the governance, people, and operational risks that cause the majority of real-world AI failures. A model that degrades because nobody owns monitoring in production is not a technical failure. It is a governance failure.

Third, it lacks traceability from risk to control. Identifying a risk without mapping it to a specific, implementable control activity is an academic exercise. The taxonomy must create a direct line from "what could go wrong" to "what are we doing about it" to "how do we verify it is working."

The taxonomy presented here addresses all three failures. It spans 14 domains from strategy through business continuity, covers 100 distinct scenarios, and links each one to a named control with specific activities. I have organized it to follow the natural lifecycle of AI in an enterprise, from strategic planning through development, deployment, operations, and ongoing governance.

Original implementation tip: When I first built an AI risk taxonomy for a European bank, I started with the technical risks because that is where the AI team's attention naturally went. We ended up with 40 technical scenarios and 5 organizational ones. After the first major incident, which was caused by unclear model ownership between data science and IT operations, we realized our taxonomy was inverted. The organizational and governance risks caused more actual damage than the technical ones. Start your taxonomy with strategy, governance, and people risks. Then layer in the technical domains. This sequencing forces the right conversations early.

## Domain 1: Business Value Risks

Strategy risks sit at the top of the taxonomy because every other risk domain inherits from them. If your AI strategy is flawed, your technical controls cannot compensate.

Two scenarios define this domain.

The first is strategy deficiency. Wasted resources and reputational damage may occur when an organization lacks a clear enterprise-wide AI strategy, leading to inefficient investments and potential misuse of AI. This is a Priority 1 risk.

The recommended control is an enterprise AI strategy. Develop and put in place a comprehensive AI strategy aligned with overall business objectives. Create clear guidelines for AI adoption and integration across departments. Establish governance structures with defined roles, responsibilities, performance metrics, and risk management protocols. Document policies and maintain evidence of governance through reports and records. Review and update the strategy regularly to reflect changes in technology, business needs, and regulatory requirements. Communicate the strategy across the organization to achieve alignment and stakeholder buy-in.

The second scenario is misaligned strategy. Missed opportunities may occur when insufficient stakeholder engagement leads to AI systems that do not support business goals or expose the organization to unacceptable risks. Also Priority 1.

The recommended control is stakeholder alignment. Establish stakeholder engagement processes to ensure AI systems align with business goals. Develop communication protocols and document policies for continuous alignment. Collect and maintain meeting records, stakeholder feedback, and communication logs as evidence.

Original implementation tip: The strategy risk I see most often is not the absence of a strategy. It is the presence of multiple competing strategies. The data science team has a roadmap. The IT department has an automation strategy. The business units each have their own AI wishlists. These strategies contradict each other in ways nobody notices until budget conflicts or architectural incompatibilities surface months later. Before you write a strategy document, conduct a strategy reconciliation exercise. Collect every existing AI-related plan, roadmap, and initiative list across the organization. Map them on a single page. The conflicts will be immediately visible. Resolve those conflicts first. Then write the unified strategy.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/firefly_small-blooming-azalea-flowers-with-many-small-flotating-dollar-coins-portrayed-in-neo-885492.jpg?w=1024)

## Domain 2: Governance Risks

Governance is where principles become operational. Eight scenarios span this domain, and most organizations have gaps in at least half of them.

Misaligned ethics is a Priority 1 scenario. Reputational damage may occur when AI decisions conflict with organizational cultural and ethical values, leading to poor decisions, negative public perception, and legal repercussions. The control is responsible AI principles: develop AI ethics guidelines, establish an ethics review board, and integrate ethical considerations into the design, development, and deployment of AI systems.

Overconfidence in automation is equally critical. Wasted resources result from unrealistic expectations about AI capabilities, leading to disappointment, wasted investments, and erosion of trust. The control is capability and limitations communication: communicate the limitations and potential risks of AI technologies and avoid overstating capabilities to ensure realistic expectations and informed decision-making.

Governance erosion occurs when AI negatively impacts existing governance mechanisms, reducing control over data processing and increasing breach risk. The control is control integration: update existing governance frameworks to incorporate AI-specific considerations and ensure alignment with established policies and risk management protocols.

Compliance failure carries the most immediate financial consequences. Regulatory penalties and reputational damage result from non-compliance with internal or external AI requirements. The control is compliance audit: regularly test, audit, monitor, and assess AI system compliance with internal policies, external regulations, and ethical guidelines, and report findings to relevant stakeholders.

Vendor lock-in limits flexibility when exit strategies for AI systems are absent. The control is exit planning: include exit strategy considerations in the design and procurement of AI systems, ensuring the ability to migrate to alternative providers.

Three Priority 2 governance scenarios round out this domain. Trust deficit limits innovation when organizations lack trust in AI technologies. The control is an AI framework that documents and communicates limitations and capabilities, provides clear explanations of AI decisions, and establishes processes for independent verification. Communication breakdown results from a lack of common language for AI concepts. The control is AI glossary management: develop and maintain a glossary of AI terms and ensure consistent terminology across the organization. Ownership vacuum leads to unauthorized AI development and security breaches when ownership and operating models are undefined. The control is operating model definition: establish clear roles, responsibilities, and accountabilities for AI initiatives, including appropriate segregation of duties.

Original implementation tip: The governance risk that causes the most silent damage is the ownership vacuum. I worked with a technology company where three separate teams claimed partial ownership of a production ML model. Data science owned the algorithm. Platform engineering owned the infrastructure. The business unit owned the use case. Nobody owned the model in production. When performance degraded, each team assumed another team was monitoring it. The model served degraded predictions for 11 weeks before a customer complaint triggered investigation. Fix this by creating a RACI matrix for every production AI system that names one individual, not a team, as the accountable party for model performance in production. One name. Not a distribution list.

## Domain 3: Decision-Making Risks

Two Priority 1 scenarios address how AI risk integrates into enterprise decision-making.

Risk integration gap occurs when organizations fail to integrate risk assessment and controls into the AI framework. Unidentified or unmitigated risks result, along with potential compliance violations and reputational damage. The control is mandatory risk and impact assessments: create and enforce a comprehensive policy mandating systematic identification, evaluation, and management of AI-related risks. Include quantitative model impact assessments with statistical analyses of threat prevalence and potential losses. Integrate these processes with existing framework protocols covering confidentiality, integrity, availability, compliance, contracts, and responsible AI principles.

AI model risk exposure results from outdated quantitative model risk management practices. The control is a quantitative risk model: develop and maintain up-to-date practices for AI model risk management, conduct impact assessments and statistical analyses to evaluate accuracy and reliability, address model metrics and acceptance criteria, and incorporate regular reviews of data, operational practices, and cybersecurity controls.

Original implementation tip: Most organizations attempt to integrate AI risk into their existing risk framework by adding a few AI scenarios to their enterprise risk register. This approach fails because the existing register was designed for risks that behave differently. AI risks are dynamic. A model that was within tolerance last quarter may be outside tolerance this quarter because the underlying data distribution shifted. Instead of simply adding AI rows to your existing register, create a parallel cadence of AI-specific risk reviews that feed into the enterprise register. Monthly AI risk reviews that update quarterly enterprise risk reports. This gives AI risks the attention frequency they require while maintaining integration with enterprise governance.

## Domain 4: People Risks

Three scenarios cover the human element of AI risk.

Resource misalignment (Priority 1) occurs when unclear resourcing requirements in the AI strategy lead to staffing inefficiencies. The control is staff planning: define and document human resource requirements, including recruitment, role profiles, training, retention strategy, and third-party involvement, in alignment with the AI strategy and roadmap.

Talent flight (Priority 1) results when poor development and retention of human talent produces AI solutions misaligned with organizational values. The control is talent alignment: establish HR processes to recruit, develop, and retain talent aligned with the AI strategy, including continuous professional development and performance evaluations.

Knowledge deficit (Priority 1) creates ineffective AI operations and poor incident response when IT knowledge is not retained and developed. The control is knowledge continuity: assign and document specific individuals to fulfill business-as-usual roles and sustainment functions. Ensure ongoing knowledge retention through formal knowledge management practices, continuous training, and documentation of key processes and incidents.

Original implementation tip: The knowledge deficit risk is particularly dangerous with AI systems because the knowledge required is specialized and often held by a single individual. I have seen organizations where one data scientist understood the feature engineering pipeline, and when that person left, nobody could retrain the model. The entire production system became fragile overnight. For every critical AI system, maintain a "bus factor" register. For each key knowledge area, list how many people can perform the function. If the number is one, you have a Priority 1 risk that requires immediate cross-training or documentation. Yeah, this sounds obvious. But count how many of your production AI systems depend on a single person's knowledge. The number will concern you.

## Domain 5: Architecture Risks

Architecture risks span seven scenarios across three priority levels.

Unexplainability (Priority 1) is the inability to understand or explain AI decisions due to missing functionality. The control is explainability by design: integrate explainability as a functional requirement in design, build, and testing phases. Ensure explanations are clear and accessible, with documentation of explainability features and traceability of decision-making processes.

Incompatibilities (Priority 1) cause operational issues from integration, scalability, and compatibility problems. The control is compatibility testing: develop testing procedures ensuring the AI model is compatible with the production environment, scalable to meet business needs, and integrated with other systems. Perform thorough compatibility testing across software, hardware, and network environments. Conduct scalability assessments including stress testing. Develop standardized integration protocols covering data formats, API usage, and security requirements.

Misaligned architecture (Priority 2) prevents unified automation when AI architecture is undefined. The control is architecture alignment: define and document an enterprise AI architecture including preferred technologies, design concepts, logging protocols, security controls, and monitoring requirements.

Segregation deficiency (Priority 2) creates security and data integrity losses in cloud or multi-tenant environments. The control is architectural segregation: define IT architecture principles enforcing segregation of AI system components and data from other infrastructure.

Unavailability (Priority 2) disrupts business operations due to insufficient AI system resilience. The control is high availability: define and monitor availability metrics, establish redundancy plans, and test for system reliability.

Ineffective security (Priority 3) results from failing to embed security by design. The control is security by design: incorporate security principles into the development methodology, ensuring all components adhere to established security standards.

License noncompliance (Priority 3) creates legal and financial exposure. The control is license management: establish a license management system ensuring appropriate licenses and timely renewals for all AI system components.

Original implementation tip: Explainability by design is the architecture control most frequently treated as an afterthought. Teams build complex ensemble models or deploy large language models, and only when a regulator or auditor asks "how does this model make decisions" do they realize explainability was never a requirement. Retrofitting explainability onto a deployed model is expensive and sometimes impossible. Add explainability to your definition of done for model development. If the development team cannot demonstrate how the model produces its outputs before deployment, the model does not deploy. This one requirement, enforced consistently, prevents an entire category of compliance and trust risks.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/547784213_3082409608585447_5872836174410763975_n.jpg?w=1024)

## Domain 6: Lifecycle Risks

This is the largest domain, spanning 10 scenarios, because the AI lifecycle from data to deployment contains the most failure points.

Poor hypothesis (Priority 1) produces unreliable outcomes from inadequate governance around hypothesis development. The control is hypothesis testing: establish governance controls requiring approval of hypotheses based on predefined criteria, with regular reviews for ongoing relevance.

Poor algorithms (Priority 1) leads to ineffective performance. The control is algorithmic controls: develop governance policies for algorithm development and maintenance, including validation and testing procedures with regular reviews.

Flawed logics (Priority 1) produces unreliable outputs from inaccurate model parameters. The control is logic validation: establish rigorous logic validation and testing procedures, with approval requirements for any changes to model logic.

Data accuracy failures (Priority 1) cause erroneous outputs. The control is data accuracy verification: develop and enforce data accuracy verification standards including validation, error detection, and correction before and during model use, with continuous monitoring and automated alerts.

Six Priority 2 scenarios complete this domain. Unallocated roles create regulatory and operational failures through unclear data governance responsibilities. The control is data ownership: establish roles including data owners and stewards with regular audits. Data corruption results from unintended interactions between AI and other systems. The control is data integrity monitoring: implement controls to monitor data interactions with automated alerts for corruption incidents. Integration failure occurs from corrupted data inputs or outputs between systems. The control is integration testing: develop strict testing procedures with continuous monitoring for data anomalies. Poor data results from inadequate governance over learning and production data. The control is data governance: enforce quality checks with documented standards and periodic audits. Incomplete inputs lead to incorrect outcomes. The control is data completeness control: implement validation processes with protocols for handling incomplete datasets.

At Priority 3, inaccurate results from models not reflecting underlying parameters are addressed by model validation: comprehensive validation protocols including sensitivity analysis and performance benchmarks.

Original implementation tip: The lifecycle risk that consistently surprises organizations is data accuracy failure during the transition from development to production. The training data has been cleaned, validated, and verified. The model performs beautifully in testing. Then in production, the live data feed introduces formats, edge cases, and quality issues that never appeared in the training set. I watched a fraud detection model go from 94% accuracy in testing to 71% in the first week of production because the live transaction data contained encoding inconsistencies that the training data had been cleaned of. Build a data reconciliation step between your training pipeline and your production pipeline. Compare distributions, formats, and quality metrics between the data the model was trained on and the data it receives in production. Do this before go-live and continuously afterward.

## Domain 7: Development Risks

Sixteen scenarios cover the development phase, making it the second largest domain.

At Priority 1, four scenarios demand immediate attention. Design flaw occurs when poor methodology is not consistently applied. The control is development standards: establish and maintain AI development standards integrated with broader development standards. Inaccurate model results from undefined model universe definition. The control is model universe: define and document the AI model universe including data sources, quality, transformations, and assumptions, updated regularly. Variable misalignment causes incorrect results from mistaking correlation for causality. The control is relationship modeling: establish quality controls ensuring relationships between variables are defined correctly, including interdependencies. Overfitting causes loss of reliability when models perform well on training data but poorly on new data. The control is overfitting mitigation: design algorithms for flexibility with documented testing and validation.

Learning bias (Priority 1) deserves special attention. Loss of accuracy and reliability occurs from data bias producing discriminatory outcomes. The control is bias mitigation: implement controls considering sensitivities across ethical, political, ethnic, racial, gender, and cultural groups, with documented evaluation processes and evidence of bias checks.

At Priority 2, five scenarios address operational development risks. To-be inaccuracy results from poor knowledge of desired processes. The control is to-be analysis: maintain documentation of user stories and end-to-end process flows with program sponsor approval. Insufficient segregation occurs when testing environments do not match production. The control is environment segregation: maintain separate development, QA/test, and production environments. Temporal misalignment causes accuracy loss when data time scales conflict. The control is synchronization verification: establish controls ensuring data source alignment with the AI system's time scale. Data duplication produces inflated insights from processing duplicate data. The control is duplication mitigation: implement file and data validation checks with documentation. AutoML issues create complexity and lack of transparency. The control is AutoML guides: develop guidelines for automated machine learning use with regular complexity assessments and explainability tool integration.

At Priority 3, six scenarios cover remaining development risks. As-is ignorance results from poor knowledge of current processes. The control is as-is analysis: document pre-automation process narratives during the design phase. Undefined controls create vulnerabilities. The control is a control matrix covering all key areas. Control gap occurs when controls are not implemented in the developed solution. The control is control testing to verify processes align with design. Weak traceability compromises logging effectiveness. The control is bot identification with unique identifiers. Improper testing results from insufficient go-live strategy. The control is testing execution with comprehensive documentation. User acceptance deficiency results from inadequate business input. The control is test approvals with documented feedback and sign-off.

Original implementation tip: Variable misalignment, the correlation-versus-causation problem, is the development risk I find most often in production AI systems. And it is rarely caught by automated testing because the model's statistical metrics look fine. A model might achieve high accuracy by using a variable that correlates with the target in training data but has no causal relationship. When the correlation breaks, which it eventually does, the model fails silently. The most effective countermeasure I have found is a mandatory "causal review" step in the development process where a domain expert, not a data scientist, reviews the feature set and challenges each variable's causal relationship to the outcome. Data scientists are trained to find patterns. Domain experts are trained to question whether those patterns make sense. You need both perspectives before deployment.

## Domain 8: Project Risks

Five scenarios cover project-level risks.

Operational misalignment (Priority 2) results from lacking strategic alignment between AI initiatives and organizational strategy. The control is a business case: establish a strategic alignment framework with formal approval and periodic review by stakeholders.

Problem mismatch (Priority 2) occurs when model design does not match the business problem. The control is iterative development: adopt approaches like Agile for continuous testing and refinement, with prototyping to identify mismatches early.

Management gap (Priority 2) results from poor project management methodology. The control is program management: implement project timelines, resource allocation, stakeholder engagement plans, and continuous alignment with business requirements.

Poor benefits (Priority 3) occurs when benefits management fails to track ROI. The control is impact value: develop a benefits management framework with metrics for short, medium, and long-term tracking.

Assurance deficit (Priority 3) results from lacking independent assurance. The control is assurance: engage an independent function to evaluate AI program setup, with regular reports on quality, costs, benefits, compliance, and internal control.

Original implementation tip: Problem mismatch is the project risk that wastes the most money. I worked with a retail organization that spent eight months building a demand forecasting model to solve what turned out to be a supply chain visibility problem. The model was technically excellent but solved the wrong problem. Their forecast accuracy improved by 15%, but the real issue was that they could not see inventory positions across warehouses in real time. The fix required a dashboard, not a model. Before approving any AI project, require the project team to answer one question in writing: "Why does this problem require machine learning, and what would the non-ML alternative look like?" If they cannot articulate why ML is necessary, there is a good chance a simpler solution would be more effective.

## Domain 9: Operations Risks

Nine scenarios cover the operational phase where most AI failures actually manifest.

Performance drift (Priority 2) is the operational risk with the highest real-world impact. Model accuracy degradation from data drift and concept drift occurs when stability checks are insufficient. The control is stability monitoring: implement model stability checks requiring ongoing validation, benchmarking, and performance evaluation to detect drift.

Resource laxity (Priority 2) results from inadequate control over IT resource usage given AI's unpredictable demands. The control is project monitoring: implement controls to monitor IT resource demands more closely than other systems.

Error oversight (Priority 2) leads to unauthorized changes and incidents from undetected errors. The control is incident management: establish a consistent approach with clear procedures, timely resolution, and integration with regular incident management.

Undetected error (Priority 2) causes delayed resolution from lacking procedures. The control is error resolution: perform timely exception processing with issue and performance monitoring.

Unsupported jobs (Priority 2) results from insufficient job monitoring. The control is job monitoring: monitor system jobs and interfaces ensuring completeness and timeliness.

Capacity issues (Priority 2) arise when availability and capacity management cannot meet evolving demand. The control is capacity management: implement availability and capacity management with scalability embedded in design.

At Priority 3, shadow AI is the scenario most organizations underestimate. Inability to ensure AI aligns with strategy and risk appetite occurs when the organization lacks an inventory of all AI solutions. The control is AI inventory: maintain a complete, up-to-date inventory of all AI platforms, solutions, and use cases, including dependencies and ownership.

IP loss (Priority 3) occurs when AI system intellectual property held by third parties is at risk. The control is IP protection: establish a repository of relevant IP, accessible in-house, secured with regular backups.

AI component blindness (Priority 3) results from lacking understanding of IT components and relationships. The control is configuration management: establish a configuration management database fed through change management.

Original implementation tip: Shadow AI is growing faster than most governance teams realize. Every time an employee uses ChatGPT to draft a customer response, builds a quick predictive model in a Jupyter notebook, or connects a third-party AI tool to company data through a browser extension, they create shadow AI. I conducted a shadow AI audit at a financial services firm last year. The governance team believed they had 12 AI systems in production. We found 47 AI tools and models being used across the organization, most without any risk assessment, data governance, or access controls. The 35 unknown systems included four that processed customer PII. Start your shadow AI inventory not by asking teams to self-report, which underestimates the problem, but by auditing network traffic, SaaS subscriptions, cloud resource usage, and API calls for AI-related activity.

## Domain 10: Monitoring Risks

Four scenarios address the monitoring function that keeps deployed AI systems safe.

Outcome blindness (Priority 1) occurs when AI system behavior is not monitored against business and ethical requirements. The control is outcome monitoring: implement regular review of AI system outcomes using data analytics to ensure performance aligns with requirements. Maintain audit trails and ensure controls operate at the same pace as monitored activities.

Monitoring ineffectiveness (Priority 1) reduces operational effectiveness from inadequate monitoring. The control is operational monitoring: develop a real-time monitoring and alerting framework to detect anomalies, establish KPIs and KRIs as the basis for effective monitoring, and trigger alerts followed by documented follow-ups.

Undetected issues (Priority 1) cause financial losses and compliance fines from lacking post-deployment monitoring. The control is post-deployment monitoring: develop a monitoring framework defining specific metrics, thresholds, and alerts. Implement automated tools for continuous real-time tracking. Define key performance indicators and review them regularly against business objectives.

Control override (Priority 2) leads to financial loss when automated stop/loss controls fail. The control is automated stop/loss: design controls to halt unintended AI behavior with an override process for exceptions, assessing exceptions against risk appetite and business impact.

Original implementation tip: The monitoring risk that catches organizations off guard is the gap between monitoring cadence and AI decision speed. I worked with an organization that monitored their AI system's output quality weekly. The system made 50,000 decisions per day. By the time they detected a quality degradation in their weekly review, the system had already made 350,000 decisions at reduced quality. Match your monitoring frequency to your decision frequency. If your model makes real-time decisions, you need real-time monitoring. If your model runs daily batch predictions, daily monitoring may suffice. But weekly monitoring for a real-time system is a control that exists on paper but provides no actual protection.

## Domain 11: Security Risks

Seven scenarios span security from Priority 1 through Priority 3.

Lack of auditability (Priority 1) prevents validation of AI outcomes. The control is auditability: securely store and ensure timely retrieval of data and algorithms, comply with data privacy regulations, prevent data context loss, and apply the vault principle.

Unauthorized access (Priority 2) leads to inappropriate changes to AI learning and processing data. The control is data access: securely configure AI input datasets to prevent unauthorized changes with completeness and accuracy checks.

At Priority 3, five scenarios address specific security concerns. Security breach results from inconsistent security management. The control is cyber security: apply a consistent approach integrated with regular security processes, aligned with ISO 27001. Malware attack affects AI environment integrity. The control is malware protection: implement protection systems and monitor patches, protecting self-learning components against malicious attacks. Data breach occurs from insecure handling of temporary files. The control is encryption: encrypt code, data storage, and network communications. Vulnerability blindness results from undetected security weaknesses. The control is vulnerability testing: conduct periodic penetration tests and red-team reviews.

Original implementation tip: The security risk unique to AI that most security teams miss is the attack surface created by the model itself. Traditional security teams protect the infrastructure around the model, the servers, networks, APIs, and databases. But the model is an attack surface too. An adversary who can query a production model thousands of times can extract information about the training data through model inversion attacks. They can find decision boundaries through systematic probing. They can manipulate outputs through carefully crafted inputs. Your security testing must include model-specific attack scenarios, not just infrastructure penetration testing. If your red team does not include someone who understands adversarial machine learning, your testing has a blind spot.

## Domain 12: Access Control Risks

Twelve scenarios cover access management for both human users and automated bots. All are Priority 3, but their aggregate effect is significant.

These scenarios cover compromised bot accounts, compromised user accounts, excessive bot access, excessive user access, inadequate account provisioning, inadequate access revocation, undetected bot access, undetected user access, excessive privileged access, segregation of duties conflicts, weak authentication, and unauthorized third-party access.

The controls follow a consistent pattern: bot control and user control for accountability, bot access authorization and user access authorization for least-privilege enforcement, account provisioning for formal approval processes, access revocation for timely deprovisioning, bot access review and user access review for periodic validation, privileged access authorization for restricting powerful accounts, access segregation for preventing conflicts, authentication for strong credential management, and third-party control for extending security standards to external users.

Original implementation tip: The access control risk specific to AI that most organizations handle poorly is bot account management. When a bot, an automated process, accesses systems, it typically uses a service account. These service accounts often accumulate privileges over time as the bot's functions expand, but nobody conducts the same periodic access reviews for bot accounts that they do for human accounts. I audited one organization where a bot account for a data preprocessing pipeline had accumulated database administrator privileges, access to the production model repository, and write access to the training data store. Nobody had reviewed the bot's access in 18 months. Treat bot accounts with the same access governance rigor as human accounts. Include them in quarterly access reviews. Apply least-privilege principles. Document and approve every privilege.

## Domain 13: Change Management Risks

Seven scenarios address how changes to AI systems introduce risk.

IT impact assessment (Priority 1) is the most critical. Disruptions to other IT services may occur from AI system changes with insufficient impact analysis. The control is IT impact assessment: mandate thorough impact analysis for all AI changes, focusing on effects on related IT services, requiring integration testing with documented results.

Inadequate ongoing testing (Priority 1) causes missed defects. The control is testing protocol: establish comprehensive testing protocols for ongoing AI validation with pre- and post-implementation tests executed by independent teams.

At Priority 2, undetected errors result from inadequate automated monitoring. The control is automated error monitoring: deploy tools that continuously validate the AI system after changes, detecting anomalies in real time.

Five Priority 3 scenarios cover unauthorized changes, untracked modifications, poor change control, and insufficient validations. Controls include formal change management processes, modification logging, change control procedures, and validation procedures requiring pre-deployment tests across functional, security, and performance criteria.

Original implementation tip: The change management risk specific to AI that organizations consistently underestimate is the cascading impact of retraining. When a model is retrained on new data, the outputs change. Sometimes subtly, sometimes dramatically. If downstream systems or business processes depend on the model's output characteristics, for example expected score ranges, output distributions, or decision thresholds, retraining can break those dependencies without triggering any traditional change management alerts. Treat model retraining as a change that requires the same impact assessment, testing, and approval as a code deployment. Because functionally, it is one.

## Domain 14: Third-Party and Business Continuity Risks

The final domain covers four third-party scenarios and five business continuity scenarios.

For third parties, black box solution (Priority 2) creates business disruption when the organization cannot understand the AI system's logic. The control is contract review: define intellectual property ownership, include escrow agreements, ensure right to audit, and outline roles and responsibilities. Third-party default (Priority 3) exposes the organization to lower control maturity. The control is due diligence: subject third parties to at least the same level of control as internal operations. Third-party dependency (Priority 3) creates concentration risk. The control is third-party segmentation: identify and categorize suppliers by criticality with contingency plans. Shadow third-party (Priority 3) results from lacking an updated vendor inventory. The control is third-party management: develop a comprehensive inventory integrated into risk and continuity planning.

For business continuity, inability to recover (Priority 1) causes prolonged disruptions when rollback mechanisms are absent. The control is roll-back: establish mechanisms to identify and recover the last known good AI state, with processes, algorithms, and cleansed data available for rapid retraining. Ineffective backups (Priority 1) results from inability to restore AI services. The control is backup restoration: implement appropriate backup and snapshot procedures, including frequent snapshots of learning data, with ability to roll back completely.

Ineffective fallback (Priority 2) results from lacking alternative processing facilities. The control is fallback facility: establish alternative processing capabilities with regular risk assessments. Fragility (Priority 3) and ineffective response (Priority 3) address business continuity planning and testing, with controls for continuity planning aligned with ISO 22301 and continuity testing through regular BCP simulations.

Original implementation tip: The business continuity risk most specific to AI is the inability to recover the model's learned state. Traditional systems can be restored from backups because their logic is deterministic. An AI model's "logic" is its trained weights, which are the product of specific training data processed in a specific sequence with specific hyperparameters. If you lose the trained model and do not have the exact training data, preprocessing pipeline, and training configuration documented and backed up, you cannot recreate it. I have seen an organization lose a production model to a storage failure and spend six weeks recreating it because they had backed up the model artifacts but not the training pipeline configuration. Back up everything: the model, the training data, the preprocessing code, the feature engineering pipeline, the hyperparameter configuration, and the training environment specification. Test restoration by actually rebuilding the model from backups at least annually.

## Implementation Tips

These four principles apply across all 14 domains and 100 scenarios.

First, prioritize by actual exposure, not by perceived sophistication. The scenarios rated Priority 1 in this taxonomy are not necessarily the most technically interesting. They are the ones that cause the most organizational damage when they materialize. Strategy deficiency, ownership vacuum, and compliance failure cause more real-world harm than adversarial machine learning attacks. Fund controls for Priority 1 scenarios before you invest in exotic defenses against lower-probability technical attacks.

Original implementation tip: When presenting this taxonomy to leadership, resist the temptation to lead with the technically impressive scenarios like adversarial attacks or model inversion. Lead with the governance and strategy scenarios that connect to business outcomes leadership already cares about. "We lack a defined owner for our production AI models" resonates more with a board than "we are vulnerable to model extraction attacks." Start with the risks they can feel, then build toward the ones they need to understand.

Second, map controls to your existing control framework. This taxonomy aligns to COBIT 2019 objectives across four domains: Evaluate, Direct and Monitor (EDM), Align, Plan and Organize (APO), Build, Acquire and Implement (BAI), and Deliver, Service and Support (DSS), plus Monitor, Evaluate and Assess (MEA). If your organization uses a different framework, map these controls to your existing structure. The worst outcome is creating a parallel AI control framework that nobody integrates into operational governance.

Original implementation tip: When mapping these controls to your existing framework, do not create 100 new control activities. Many of these AI controls are extensions of controls you already have. Data access controls for AI systems should be managed through the same access management processes you use for other systems. Change management for AI should follow the same change management framework with AI-specific additions. Identify which controls are genuinely new (explainability by design, bias mitigation, stability monitoring) and which are extensions of existing controls. New controls need new processes. Extensions need updated procedures. The distinction matters for implementation cost and adoption speed.

Third, document decisions and rationale, not just outcomes. For every control in this taxonomy, maintain evidence that demonstrates not just that the control exists, but why specific decisions were made. When an auditor or regulator asks why you accepted a particular residual risk, "because we assessed it and decided it was within tolerance" is insufficient. They need to see the assessment, the alternatives considered, and the governance approval.

Original implementation tip: Create a standard decision record template with five fields: the decision, the alternatives considered, the rationale for selection, the assumptions that must remain valid, and the conditions that would trigger reassessment. Use this template for every Priority 1 and Priority 2 control decision. It takes five minutes per decision and saves hours of reconstruction during audits. I have seen organizations that adopted this practice clear regulatory examinations in half the time of those that relied on informal documentation.

Fourth, reassess at a cadence that matches your risk velocity. AI risks change faster than traditional IT risks. Models degrade, data drifts, new attack techniques emerge, and regulations evolve. A taxonomy that is reviewed annually is a taxonomy that is wrong for 11 months of the year. Review Priority 1 controls quarterly, Priority 2 semi-annually, and Priority 3 annually at minimum. Update the taxonomy itself whenever a new risk scenario materializes that is not covered.

## References and Standards

This taxonomy draws from and aligns with the following authoritative frameworks.

ISO/IEC 27005:2022 for the information security risk management process structure.

ISO/IEC 23894:2023 for AI-specific risk management guidance.

ISO/IEC 42001:2023 for AI management system requirements covering governance, ethics, and accountability.

COBIT 2019 for IT governance and management objectives, providing the control mapping framework used throughout this taxonomy.

NIST AI RMF (AI 100-1) for the AI risk management lifecycle framework.

EU AI Act (Regulation 2024/1689) for risk-based regulatory requirements governing AI systems in EU markets.

ISO 22301 for business continuity management systems referenced in the continuity domain.

ISO/IEC 27001 for information security management systems referenced in the security domain.

MITRE ATLAS for the adversarial threat landscape specific to AI and machine learning systems.

FAIR (Factor Analysis of Information Risk) for quantitative risk analysis methodology when assessing the scenarios in this taxonomy.

## Making This Taxonomy Work

Organizations that treat this taxonomy as a reference document to satisfy an audit requirement will miss its value entirely. They will have a comprehensive list of 100 scenarios that nobody operationalizes, controls that exist in policy but not in practice, and a false sense of security that evaporates at the first real incident. The taxonomy becomes shelfware, and the organization remains exposed to the same risks it cataloged so carefully.

Organizations that treat this taxonomy as a living operational tool will use it differently. They will map their existing AI systems against these 100 scenarios to identify gaps. They will prioritize control implementation based on the priority ratings and their own risk appetite. They will assign named owners to each applicable control. They will review and update the taxonomy as new AI capabilities are deployed, new threats emerge, and new regulations take effect. Their risk conversations will be specific, traceable, and grounded in concrete scenarios rather than abstract categories.

A taxonomy that names 100 things that can go wrong is only useful if it drives 100 decisions about what to do right.

Which of these 14 domains has the biggest gaps in your organization right now? If you are honest with yourself, I suspect the answer is not the technical domains. It is strategy, governance, or people. Start there.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and globally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
