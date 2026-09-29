---
title: "The Risk and Compliance Automation Playbook"
date: 2026-03-12
tags: 
  - "ai-governance"
  - "ai-use-case-in-controls"
  - "ai-projects"
  - "artificial-intelligence"
  - "business"
  - "compliance-automation"
  - "compliance-performance"
  - "control-automation"
  - "hernan-huwyler"
  - "technology"
---

## From Manual Sampling to Monitoring 100% of Transactions

GRC data scattered across disconnected systems. Compliance controls that depend on slow, human-driven processes never built for scale. Audit preparation that turns into a quarterly fire drill. Risk assessments based on last quarter's data while threats evolve daily.

These aren't edge cases. They're the standard operating reality for most risk and compliance functions. A recent Thomson Reuters survey found that compliance professionals spend an average of 54% of their time on manual data collection and reporting activities rather than on analysis and decision-making. The tools have changed over the decades, from paper to spreadsheets to GRC platforms, but the fundamental model hasn't: humans gather data, humans check controls, humans write reports, and by the time the report is finished, the risk landscape has already shifted.

Automation changes this model fundamentally. Predictive models forecast risks by analyzing patterns across historical and real-time data streams. Autonomous agents execute predefined tasks and decisions based on model outputs and established business rules. Automated workflows connect models and agents to business processes for seamless, end-to-end task execution. And feedback loops improve accuracy and adapt to evolving threats continuously.

This post covers the complete automation engine for risk and compliance: how predictive risk models, autonomous agents, and automated workflows transform GRC from reactive reporting to proactive resilience, with practical implementation guidance for each component.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/silent-developer-at-work-1.png?w=1024)

## The Three Common Challenges Automation Solves

Three structural problems limit the effectiveness of traditional risk and compliance functions. Each problem has persisted because the available tools couldn't address it. Automation changes that equation.

The first problem is silos. GRC data is scattered across ERP systems, CRM platforms, IT asset management tools, HR systems, email, and unstructured documents. This fragmentation delays insights because assembling a complete risk picture requires manually extracting and reconciling data from multiple sources. It weakens accountability because no single system provides a comprehensive view of control performance. And it prevents the correlation analysis that identifies emerging risk patterns across organizational boundaries.

The second problem is manual processes. Compliance depends on human-driven controls: manual reviews, periodic sampling, scheduled assessments, and hand-compiled reports. These processes don't scale. When transaction volumes increase, the same team must review more cases with the same resources, which means either extending timelines or reducing coverage. Manual processes also introduce inconsistency, because different reviewers apply different judgment to similar cases, and latency, because issues discovered during a quarterly review have been accumulating for three months.

The third problem is reactive posture. Traditional GRC operates on a review-and-report cycle. Risks are identified after they materialize. Controls are tested after the control period ends. Compliance is verified after the fact. This reactive model was adequate when business moved at the speed of quarterly reporting. It's inadequate when threats evolve daily and regulatory expectations demand continuous compliance.

Automation addresses all three problems simultaneously. Integration eliminates silos by connecting data sources into unified risk profiles. Agents and workflows replace manual processes with automated, consistent, scalable execution. Real-time monitoring shifts compliance from periodic reporting to continuous validation.

Implementation tip: The most common mistake in GRC automation is attempting to automate everything at once. Organizations that try to build a comprehensive automation platform before demonstrating value in any single area spend months on architecture and integration without producing any operational improvement. Start with one high-impact use case, such as fraud detection, compliance reporting, or third-party risk monitoring, that has clearly quantifiable value. Run it as a contained project. Demonstrate ROI. Then expand from that success story to adjacent use cases. This approach builds organizational momentum, generates the performance data needed to justify larger investments, and reveals integration patterns that make subsequent automation projects faster.

## The Automation Engine: Models, Agents, Workflows, and Learning

The automation engine has four components. Each serves a distinct function, and together they create a self-improving system.

Predictive models forecast future risks by analyzing patterns in historical and real-time data streams. A model might predict vendor default probability based on financial indicators, payment patterns, and market conditions. It might predict fraud likelihood based on transaction characteristics, user behavior patterns, and temporal anomalies. It might predict control failures based on process complexity, staff workload, and historical failure rates. The model's output is a risk score or probability, not a decision.

Autonomous agents execute predefined tasks and decisions based on model outputs and established business rules. An agent might automatically flag transactions with fraud scores above a defined threshold for human review. It might route high-risk vendor onboarding requests to senior compliance officers. It might generate compliance reports when triggered by calendar events or data completions. Agents operate within defined parameters and execute consistently regardless of volume.

Automated workflows connect models and agents to business processes for seamless, end-to-end task execution. A workflow might chain together data extraction from an ERP, risk scoring by a predictive model, alert generation by an agent, routing to a human reviewer, decision capture, and documentation update. Workflows ensure that the output of each component flows correctly to the next component without manual handoffs.

Feedback loops improve accuracy and adapt to evolving threats by routing outcome data back to the models. When a fraud detection model flags a transaction and a human reviewer confirms or rejects the flag, that decision feeds back into the model's training data. Over time, the model learns from reviewer decisions and improves its accuracy. This learning loop is what makes the automation engine progressively better rather than static.

Implementation tip: Design your automation engine with the feedback loop as a first-class component, not an afterthought. Many initial automation deployments capture model outputs and agent actions but don't systematically route outcome data back for model improvement. Without feedback loops, the models remain frozen at their initial training state while the environment evolves around them. Build the feedback mechanism into the workflow design from the start: when a human reviewer makes a decision about a model-flagged item, capture that decision in structured format (confirmed flag, rejected flag, escalated to investigation), and feed it into the model retraining pipeline on a defined cadence (monthly for high-volume use cases, quarterly for lower-volume ones).

## Predictive Risk in Workflows: Design, Develop, Deploy

Building predictive risk capabilities into operational workflows follows three phases.

Design begins by identifying quantifiable risks and required data sources from your existing ERP, CRM, and IT systems. Not all risks are suitable for predictive modeling. Suitable risks have three characteristics: they occur frequently enough to provide training data, they have measurable outcomes (the risk either materialized or it didn't), and relevant predictor variables are captured in existing systems. Fraud in accounts payable, vendor default, customer churn, and IT security incidents typically meet all three criteria. Strategic risks, reputational risks, and emerging regulatory risks typically don't, because they lack sufficient historical frequency and structured predictor data.

What to do during design: Map each candidate risk to the specific data fields that would serve as predictor variables. For vendor default risk, predictors might include days payable outstanding trends, financial statement ratios, industry sector, geographic location, contract tenure, and recent news sentiment. Verify that each data field is available, accessible, and of sufficient quality. Gaps identified during design are addressed before development begins.

Develop involves training models on historical data to establish baselines and validating predictive accuracy against known outcomes. Use historical cases where the risk either materialized or didn't to train the model. Split data into training and testing sets. Validate that the model's predictions on the test set align with actual outcomes. Establish performance baselines: what accuracy, precision, and recall does the model achieve? How does this compare to the current manual risk assessment process?

What to do during development: Run the predictive model in parallel with the existing manual process for at least one full business cycle. Compare the model's predictions against the manual assessments and against actual outcomes. This parallel run produces the evidence needed to determine whether the model improves on existing processes and builds stakeholder confidence before any operational dependency on the model is established.

Deploy means embedding lightweight agents within workflows to monitor live data and trigger alerts based on model scores. The model produces risk scores continuously. Agents evaluate those scores against defined thresholds and trigger appropriate responses: routing high-risk items to human reviewers, generating alerts for medium-risk items, and auto-approving low-risk items (where business rules permit). The deployment must include monitoring that tracks model performance on production data continuously.

Implementation tip: The "lightweight agents" approach to deployment is critical for initial adoption. Heavy agents that make complex autonomous decisions face organizational resistance and regulatory scrutiny. Lightweight agents that flag, route, and alert leave decision authority with humans while eliminating the manual data gathering and case compilation that consumes most of the cycle time. Start with agents that prepare decision packages for human reviewers rather than agents that make decisions autonomously. This approach captures 70-80% of the efficiency gain while maintaining the human oversight that regulators and internal stakeholders expect.

## Autonomous Compliance Controls

Compliance automation follows a six-step operational cycle: map, monitor, self-learn, alert, report, and escalate.

Map links specific laws and regulations (GDPR, SOX, ISO standards) to internal controls. This mapping creates the reference framework that agents use to evaluate compliance. Each regulation is decomposed into specific requirements. Each requirement is linked to one or more internal controls. Each control is defined with measurable attributes that agents can evaluate: completion status, timeliness, evidence availability, and control effectiveness indicators.

Monitor runs continuously. Agents scan workflows for policy breaches in real time. Unlike periodic compliance testing that samples a subset of transactions, automated monitoring evaluates every transaction against applicable control requirements. This shifts the compliance model from statistical sampling (testing 25 of 10,000 transactions) to population testing (evaluating all 10,000 transactions). The coverage improvement is dramatic and directly addresses one of the most persistent limitations of traditional compliance programs.

Self-learn adjusts control parameters in response to new compliance rules. When regulations change, the mapping is updated and agents adjust their monitoring criteria accordingly. Machine learning capabilities enable agents to identify emerging patterns that indicate new compliance risks before those patterns are explicitly coded as rules.

Alert instantly flags deviations or control failures for human review. Alert design matters: too many alerts cause alert fatigue and get ignored. Too few alerts miss genuine issues. Set alert thresholds through calibration against historical deviation data. Categorize alerts by severity to ensure that critical issues receive immediate attention while minor deviations are queued for periodic review.

Report generates real-time evidence of control performance for audits. Instead of compiling audit evidence manually before each audit cycle, the automation engine produces continuous documentation of control execution, test results, and exception handling. Audit readiness becomes a persistent state rather than a periodic project.

Escalate routes high-risk breaches to compliance officers with full context. The escalation includes the specific control that failed, the transaction or process affected, the severity assessment, the regulatory implications, and the recommended response. This context enables faster, better-informed human decisions.

Implementation tip: The self-learning capability requires careful governance. Agents that adjust their own monitoring parameters without human oversight can drift toward configurations that reduce alert volume (because fewer alerts means less work for the downstream review process) rather than configurations that maximize compliance coverage. Implement a change control process for agent parameter modifications: all self-learned adjustments should be logged, reviewed monthly by a compliance officer, and approved or reversed. This governance layer ensures that self-learning improves compliance detection rather than quietly reducing it.

## The Continuous Audit Transformation

Automation enables a fundamental shift in audit methodology: from manual sampling of selected transactions to monitoring 100% of process transactions continuously.

For operational auditing, continuous monitoring detects process deviations, control failures, and efficiency anomalies across every transaction in real time. An accounts payable automation that evaluates every invoice against approval authority limits, vendor verification status, and duplicate payment indicators catches issues that sampling-based audits statistically miss.

For financial auditing, continuous monitoring enables real-time detection of fraud, errors, and SOX control deviations. Journal entry testing that traditionally sampled 50 entries per quarter can evaluate every entry continuously against established criteria: unusual amounts, unusual accounts, unusual timing, and unusual users.

The shift from sampling to population monitoring doesn't eliminate the need for human judgment. It redirects human attention from data gathering and routine testing toward investigating the exceptions and anomalies that automated monitoring identifies. Auditors spend less time looking for problems and more time understanding and resolving the problems that automation has already found.

Implementation tip: The transition to continuous auditing requires recalibrating what "normal" looks like. Traditional audits accept a certain volume of exceptions as expected in any business process. Continuous monitoring of 100% of transactions will surface exception volumes that appear alarming compared to sampling-based testing simply because the monitoring scope is larger. Before deploying continuous audit monitoring, establish baseline exception rates from a representative period. Use these baselines to set alert thresholds that distinguish genuine anomalies from normal business variation. Without calibrated baselines, the monitoring system produces overwhelming alert volumes that desensitize reviewers and undermine the value of continuous coverage.

## Integration First: Connecting Systems for Unified Risk Intelligence

Automation requires integration. Models need data from multiple sources. Agents need to act across multiple systems. Dashboards need to aggregate information from the entire enterprise.

Two integration priorities establish the foundation.

Use APIs and middleware to connect disparate systems, enabling agents to act across the entire enterprise. API-based integration provides real-time data access and bidirectional communication between systems. When an agent needs to verify a vendor's financial status before approving a payment, it queries the vendor management system through an API, retrieves the current risk score, evaluates it against the approval threshold, and either processes the payment or routes it for review. This entire sequence executes in seconds without human involvement.

Integrate structured data (from ERP and CRM systems) and unstructured data (from email, logs, documents) to create comprehensive risk profiles. Most risk-relevant information exists in unstructured formats: incident reports, audit findings, customer complaints, regulatory correspondence, and internal communications. NLP capabilities extract structured data from these unstructured sources, enabling models to incorporate information that traditional GRC systems can't process.

Unified dashboards provide the visualization layer.

Consolidation: Agents aggregate risk, compliance, and audit data automatically from all connected systems.

Visualization: Dashboards display real-time key risk indicators, showing current status rather than last quarter's status.

Action: Alerts are routed to decision-makers in context, accompanied by the data and analysis needed to make informed decisions quickly.

Foresight: Dashboards showcase predictive trends, not just historical performance. Instead of showing that vendor payment delays increased last quarter, the dashboard shows that the model predicts a 40% probability of supply chain disruption in the next 60 days based on current vendor risk indicators.

Implementation tip: Start integration with the two or three systems that contain the highest-value risk data, not with a comprehensive integration of every system in the enterprise. For most organizations, the ERP (financial transaction data), the HRIS (people data), and the IT asset management system (technology risk data) provide the foundation for the majority of automated risk and compliance monitoring. Expanding to additional systems (CRM, contract management, project management) adds value incrementally. Each integration should be justified by a specific automation use case that depends on the data that integration provides.

## Automating Specific GRC Functions

Four GRC functions demonstrate the practical application of automation.

Automating third-party risk covers the complete vendor lifecycle. Onboarding automation handles due diligence questionnaire distribution, response collection, initial risk tiering based on predefined criteria, and documentation management. Monitoring automation continuously scans for vendor security incidents, financial distress indicators, regulatory actions, and news events that affect risk profiles. Offboarding automation ensures that data is sanitized, access is revoked, and contractual obligations are fulfilled when vendor relationships end.

Accelerating legal review applies automation to contract analysis. Compare: AI identifies non-standard or missing clauses by comparing each contract against a library of standard clause templates. Detect: The system flags missing confidentiality or liability clauses instantly. Alert: Agents check for regulatory compliance updates that affect contract terms. Track: High-risk contracts are automatically routed to legal experts for human review. This automation doesn't replace legal judgment. It eliminates the manual scanning that consumes most of the contract review cycle and ensures that every contract receives consistent evaluation against current standards.

Future-proofing controls uses scenario simulation to test organizational resilience. Automate the modeling of supply chain disruption impacts, major cybersecurity breach scenarios, sudden regulatory changes, key personnel loss effects, economic downturn financial impacts, and third-party vendor failure consequences. These simulations, run regularly against current data, provide early warning of emerging vulnerabilities and enable proactive control adjustments.

Audit readiness transforms preparation from a periodic scramble into a persistent state. When compliance monitoring, control testing, and evidence collection operate continuously, the organization is always audit-ready. The audit becomes a review of the monitoring system's outputs rather than an independent re-creation of compliance evidence.

Implementation tip: Contract review automation delivers among the fastest ROI of any GRC automation use case because it addresses a high-volume, time-intensive process with clearly measurable efficiency gains. A legal team that manually reviews 200 contracts per quarter, spending an average of 90 minutes per contract, dedicates 300 hours quarterly to review. Automation that handles initial clause comparison and flags only the contracts requiring legal attention typically reduces human review time by 60-70%, redirecting 180-210 hours per quarter to higher-value legal work. Start contract review automation with a specific contract type (vendor agreements, NDAs, or service contracts) and expand to additional types after demonstrating accuracy and efficiency gains.

## Human Oversight: Calibrating Automation to Risk Exposure

Not every GRC process should be fully automated. The appropriate level of automation depends on the confidence level in the automation's outputs and the risk exposure of the decisions being automated.

The oversight framework operates along two axes.

The vertical axis represents risk exposure, from low to high. Low-risk decisions (routine data validation, standard report generation) tolerate higher automation. High-risk decisions (regulatory filings, fraud determination, compliance enforcement) require more human involvement.

The horizontal axis represents automation confidence, from low to high. Early-stage automation with limited training data and unproven models warrants more human oversight. Mature automation with extensive validation and demonstrated accuracy warrants less oversight.

Four quadrants emerge from these axes.

Human-led with low automation and high risk exposure: The human makes the decision. The automation provides data and analysis to support the decision. Example: Determining the response to a major compliance breach.

Human-verified with high automation and high risk exposure: The automation makes a recommendation. A human reviews and approves or rejects. Example: Flagging potentially fraudulent transactions for investigator review.

Monitor with low automation and low risk exposure: Humans observe automated outputs periodically to verify the automation is functioning correctly. Example: Automated generation of routine compliance reports.

Automate with high automation and low risk exposure: The automation operates independently with periodic human audit. Example: Automated data quality checks on incoming vendor data feeds.

Implementation tip: Review the placement of each automated process on the oversight framework annually. As automation matures and confidence increases, processes can move from human-led to human-verified, or from human-verified to monitored. As risk exposure changes due to regulatory developments or business model shifts, processes may need to move in the opposite direction. The framework should be dynamic, not static. An automation that was appropriately placed in the "monitor" quadrant when transaction volumes were low may need to move to "human-verified" when the same automation begins handling higher-value transactions. Document the rationale for each placement and review it as conditions change.

## Team Preparation and Implementation Approach

Automation adoption requires organizational preparation across three dimensions: team capability, governance structure, and implementation methodology.

Team preparation starts with establishing a center of excellence for AI adoption. This cross-functional group provides expertise, governance, and support for automation initiatives across the organization. It doesn't build every automation. It establishes standards, provides technical guidance, reviews proposed automations for risk and compliance implications, and shares lessons learned.

Train business users through citizen developer programs that enable compliance officers, auditors, and risk managers to build basic automated workflows without deep technical expertise. Low-code platforms connect with ERP and CRM data, enable configuration of alerts for breaches or anomalies, and support template-based automation that can be expanded for multi-department coverage.

Promote cross-functional collaboration between AI/IT teams, business process owners, and audit functions. Automation that's built by IT without business input doesn't address the right problems. Automation that's designed by business without IT input doesn't integrate properly. Automation that's deployed without audit input doesn't meet evidence and governance requirements.

Celebrate and showcase early wins to build momentum. The first successful automation project generates the organizational energy needed to fund and staff subsequent projects. Capture quantified ROI results from early projects and present them to stakeholders considering automation for their own functions.

The implementation follows an automation sprint methodology with three phases.

Identify: Select a high-impact use case, unify key data sources, define success metrics.

Develop and pilot: Run in parallel with manual processes, measure performance against baseline, gather feedback from end users.

Scale: Expand to adjacent use cases, enforce ongoing assurance, adjust and mature for sustainable deployment.

Implementation tip: Empower compliance officers to build workflows rather than treating them as passive consumers of automation built by technologists. Compliance officers understand the regulatory requirements, the control logic, and the exception handling that effective GRC automation must implement. When they can build and modify workflows themselves using low-code tools, the automation reflects actual compliance needs rather than a technologist's interpretation of those needs. The most effective GRC automation programs combine technical platform expertise (provided by the center of excellence or IT team) with business process expertise (provided by compliance officers and risk managers who build workflows within the platform). Training compliance professionals to use low-code automation tools is a high-ROI investment because it eliminates the translation layer between "what compliance needs" and "what IT builds."

## Recommendations for Risk and Compliance Automation

These principles apply across all automation components and use cases.

Implementation tip on starting with fraud, maintenance, or compliance reporting: These three use cases consistently deliver the fastest, most measurable ROI for initial GRC automation projects. Fraud detection benefits from automation because it requires high-speed, high-volume pattern recognition that humans can't perform at scale. Predictive maintenance benefits because the sensor data and failure patterns exist in structured formats ready for modeling. Compliance reporting benefits because it's the most time-intensive manual activity in most GRC functions and automation can reduce reporting effort by 70-80%. Pick the one that's most painful in your organization and make it your first project.

Implementation tip on measuring automation ROI: Quantify automation ROI across four dimensions. Cost reduction: the personnel hours and third-party expenses eliminated or redirected by automation. Resilience improvement: the reduction in mean time to detect issues, measured before and after automation deployment. Accountability strengthening: the increase in control coverage (percentage of transactions monitored) and evidence completeness (percentage of controls with automated evidence collection). Trust protection: the reduction in compliance findings, audit exceptions, and risk incidents attributable to improved monitoring and faster response. Present all four dimensions to stakeholders. Cost reduction alone undervalues automation because it misses the risk reduction benefits. Risk reduction alone undervalues automation because it misses the efficiency gains.

Implementation tip on sustainable deployment: Automation is not a one-time project. It's an ongoing operational capability that requires maintenance, monitoring, and continuous improvement. Budget for ongoing automation operations at 20-25% of the initial automation development investment annually. This covers model retraining, agent reconfiguration as regulations change, workflow updates as business processes evolve, and monitoring of automation performance against defined thresholds. Automation that's deployed and then left unattended degrades just like any other AI system, through data drift, process changes, and regulatory evolution that the static automation doesn't accommodate.

Implementation tip on the relationship between automation and human expertise: Automation eliminates routine GRC work. It does not eliminate the need for GRC expertise. It redirects that expertise from data gathering and report compilation toward judgment, investigation, stakeholder engagement, and strategic risk management. The most effective GRC automation programs explicitly redefine job roles after automation is deployed, documenting what each role no longer does (manual data collection, routine testing, report compilation) and what each role now focuses on (exception investigation, risk analysis, control design, stakeholder advisory). Without this role redefinition, automated processes coexist with manual processes that haven't been discontinued, and the efficiency gains never materialize.

## Key References and Authoritative Frameworks

Your risk and compliance automation practice should align with these established standards:

- ISO/IEC 42001:2023, AI Management System (governance requirements for automated AI systems)

- ISO/IEC 23894:2023, AI Risk Management (risk framework for automated risk systems)

- ISO 31000:2018, Risk Management (foundational risk framework)

- COSO ERM Framework (enterprise risk management for automated environments)

- ISACA COBIT 2019 (IT governance for automated GRC processes)

- NIST AI Risk Management Framework (governance of AI-based automation)

- EU AI Act (requirements for automated decision-making systems)

- IIA Global Internal Audit Standards (continuous auditing methodology)

- ISO 27001:2022 (security requirements for automated systems)

- SOX Section 404 (internal control requirements applicable to automated controls)

- NIST SP 800-53 (security controls for automated information systems)

- GDPR Articles 22 and 35 (automated decision-making and DPIA requirements)

If you automate risk and compliance processes without changing the underlying operational model, you'll produce faster reports about the same problems, generate more alerts that the same understaffed team can't handle, and create a digital version of the same reactive cycle that manual processes followed. The automation will produce efficiency gains. It won't produce transformation. And the gap between what your GRC function can do and what evolving threats and regulations demand will continue to widen.

When you design automation as a complete engine, with predictive models feeding autonomous agents that execute through automated workflows with continuous feedback loops, integrated across enterprise systems and governed by calibrated human oversight, you create a GRC capability that scales with transaction volume, adapts to regulatory changes, detects threats in real time, and produces audit-ready evidence continuously. The compliance function moves from telling the organization what went wrong last quarter to preventing problems from materializing this minute.

Automate risk and compliance to cut costs, sustain resilience, prove accountability, and protect long-term trust. That's the mandate. The tools exist. The question is whether your organization will use them.

What's the single most time-consuming manual process in your GRC function today? Start designing its automation this quarter.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
