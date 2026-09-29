---
title: "Managing AI Development and Deployment Projects"
date: 2026-03-13
tags: 
  - "ai-deployment"
  - "ai-development"
  - "ai-development-project"
  - "ai-prokect-risks"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "technology"
---

## The 10 Best Practices That Separate AI Projects That Ship From AI Projects That Stall

Managing AI development and deployment projects requires practices fundamentally different from traditional software project management. AI systems derive behavior from training data rather than human-written code. They exhibit opacity, drift, and emergent properties that deterministic software doesn't. A model that performs well during testing may degrade in production as real-world data evolves. A system that's technically accurate may still fail from a compliance, fairness, or adoption standpoint.

Most AI projects fail because the project was managed like ordinary software, governed too late, monitored too lightly, or deployed before the organization was ready to support it. Teams rush from prototype to launch, then discover that the data does not hold up, the model drifts in production, the vendor changes core behavior, users do not trust the output, or compliance asks questions nobody planned to answer. By then, delivery slows, confidence drops, and the business case gets harder to defend.

A strong AI project needs a management approach built for experimentation, risk, operational change, and continuous improvement. This post brings together the practical best practices from the material you provided, including governance, MLOps, risk-based lifecycle controls, third-party oversight, phased deployment, continuous monitoring, and value tracking. The goal is simple. Help teams build and deploy AI systems that actually work in the real world and keep working after launch.

This post covers the ten best practices that address these challenges: from governance structure through lifecycle management, MLOps implementation, regulatory compliance, third-party risk, phased deployment, human oversight, continuous monitoring, organizational literacy, and value measurement.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/data-center-technician.png?w=1024)

## Why AI Projects Require Different Management Than Software Projects

AI projects differ from conventional software development in ways that demand adapted management approaches. Three characteristics make traditional project management insufficient.

First, AI development is inherently experimental. Unlike software where requirements can be specified and development follows a predictable path, AI model performance cannot be guaranteed until training is complete and validation is run. A technically sound model may not achieve business objectives due to data limitations, feature interactions, or distribution mismatches. Project plans must account for this uncertainty rather than treating model development as a deterministic activity with fixed timelines.

Second, AI systems change after deployment without anyone modifying code. Data drift, concept drift, and population shifts cause model performance to degrade over time. A software application behaves the same on day 500 as on day 1. An AI model does not. This means deployment is the beginning of the maintenance lifecycle, not the end of the development lifecycle.

Third, AI systems create novel risk categories. Algorithmic bias, hallucination, adversarial vulnerability, training data leakage, and model opacity don't exist in traditional software. Managing these risks requires specialized controls that traditional project management frameworks don't include.

These three characteristics mean that success criteria, timeline expectations, governance structures, and post-deployment plans all need to be designed specifically for AI rather than adapted from software development templates.

Implementation tip: Build flexibility into every AI project plan by defining two types of milestones: fixed milestones (governance approvals, compliance checkpoints, deployment dates) and adaptive milestones (model performance targets, data quality thresholds, accuracy objectives). Fixed milestones maintain project structure and stakeholder accountability. Adaptive milestones acknowledge that model development is experimental and may require iteration. When a project plan treats accuracy targets as fixed milestones with hard deadlines, teams either compromise on validation rigor to meet the date or blow past the deadline repeatedly. When accuracy targets are adaptive milestones with defined evaluation criteria and go/no-go decision procedures, the project maintains momentum while accommodating the inherent uncertainty of model development.

## Best Practice 1: Establish Clear Governance and Accountability Structures

Effective AI project management begins with defined governance roles and decision rights. Organizations should build a structured AI management system aligned with ISO/IEC 42001, establishing clear accountability for each AI system through three distinct roles.

A business owner is accountable for outcomes and compliance. This person owns the business case, defines success metrics, and bears responsibility for the system's impact on users and the organization. A technical lead is responsible for model performance. This person owns model architecture decisions, training methodology, validation results, and technical documentation. A risk owner manages ongoing monitoring. This person owns post-deployment surveillance, drift detection, incident response, and the decision to retrain, roll back, or retire the system.

These three roles may be filled by different people or combined in smaller organizations, but the responsibilities must be explicitly assigned. Unassigned responsibilities don't get fulfilled.

Project managers should ensure that every AI initiative has documented approval gates, with an AI ethics or review board empowered to condition or reject use cases at key lifecycle stages. This governance structure should integrate with existing risk management frameworks rather than operate separately.

Implementation tip: The governance structure must have the authority to stop a project, not just review it. Many AI governance boards operate as advisory bodies that provide recommendations but lack enforcement power. When the governance board recommends against deployment but the business sponsor overrides the recommendation, governance becomes performative. Grant your governance structure explicit authority over three decisions: use case approval (can we build this), deployment approval (can we launch this), and continuation approval (should we keep running this). Without authority over these three gates, governance provides commentary rather than control.

## Best Practice 2: Implement Risk-Based Lifecycle Management

Organizations should adopt a risk-based approach that applies governance intensity proportional to potential harm. A low-risk internal productivity tool doesn't need the same oversight as a high-risk system making decisions about individuals' access to credit, healthcare, or employment.

The AI lifecycle should include five structured phases, each with documented governance decision points.

Business case identification defines the problem, expected value, and success metrics before technical work begins. This phase prevents the common failure of building solutions before confirming they solve the right problem.

Design and data preparation assesses data availability, quality, and potential bias. This phase documents data provenance and identifies representativeness gaps before model development commits to specific data sources.

Development and testing evaluates model performance, fairness, and robustness against defined criteria. This phase produces the validation evidence that supports deployment decisions.

Deployment ensures that integration, monitoring, and compliance controls are in place before the system goes live. This phase confirms operational readiness, not just model readiness.

Ongoing monitoring tracks drift, performance degradation, and emerging risks continuously after deployment. This phase maintains the system's trustworthiness over time rather than assuming that deployment-time performance persists.

Higher-risk applications require more rigorous validation and oversight at each phase. A classification system for AI risk levels (following the EU AI Act's risk tiers or an internal equivalent) determines the governance intensity applied at each gate.

Implementation tip: Conduct regulatory classification during the planning phase, not after development. Discovering that a system falls under high-risk classification after months of development typically requires redesign and delays deployment. By early 2026, over 72 countries have launched more than 1,000 AI policy initiatives, with the EU AI Act imposing fines up to 35 million euros or 7% of global turnover for non-compliance. Map your AI systems against applicable regulations based on where systems are developed, deployed, and whose data they process. Use ISO 42001 as a common governance layer that can be mapped to multiple regional requirements, reducing duplication while maintaining defensibility across jurisdictions.

## Best Practice 3: Adopt MLOps for Scalable, Reproducible AI Operations

MLOps extends DevOps principles to machine learning, providing a structured approach to AI deployment that addresses the scalability, reproducibility, and governance challenges that manual AI operations can't handle at scale.

Five MLOps components deliver measurable operational improvements.

Data engineering forms the foundation. Tools like Apache Airflow, Apache Kafka, and Apache Spark automate data collection, preprocessing, and feature engineering. Published studies indicate these practices can reduce data preparation time by up to 30% and improve data quality by 25%.

Model development with version control and experiment tracking ensures reproducibility. Tools like Git, DVC (Data Version Control), and MLflow enable teams to track every experiment, reproduce results, and manage model iterations systematically. Organizations using these practices have reported a 40% reduction in time spent on experiment management. Currently, 89% of organizations use version control for ML models, leading to a 41% improvement in model reproducibility.

CI/CD pipelines automate model testing and deployment. Automated pipelines continuously check model accuracy, latency, resource usage, and data drift on each deployment, with thresholds and alerts. Published data suggests CI/CD implementation can reduce deployment time by up to 70% and decrease production errors by 60%.

Model serving and monitoring maintains production performance. Efficient serving infrastructure (Kubernetes, TensorFlow Serving) and continuous monitoring tools (Prometheus, Grafana) detect degradation early. Published studies indicate robust monitoring can reduce model performance degradation by up to 35% and improve mean time to resolution by 50%.

Governance and security integration builds compliance into the pipeline. Regulatory compliance checks, model security against adversarial attacks, and bias monitoring run as automated steps in the deployment process rather than as manual reviews after the fact. Organizations report a 45% reduction in compliance-related incidents and a 30% improvement in model robustness from these practices.

Implementation tip: Start MLOps adoption with version control for models, data, and configurations. This single practice, which costs minimal effort to implement, addresses the reproducibility crisis that undermines trust in AI systems. When a model in production behaves differently than expected, version control enables the team to identify exactly which model version is running, which data it was trained on, which configuration produced it, and what changed between the current and previous versions. Without version control, diagnosis relies on individual memory and informal records, which degrade rapidly as time passes and team members change. Version control is the foundation upon which every other MLOps practice builds.

## Best Practice 4: Build Modular Pipelines With Automated Testing

Two MLOps practices deserve individual attention because they produce the largest operational impact: modular pipeline design and automated testing.

Modular pipelines decompose the AI workflow into independent, reusable components: data ingestion, preprocessing, feature engineering, model training, validation, deployment, and monitoring. Each module can be developed, tested, updated, and debugged independently. Organizations using modular pipelines have reported a 28% reduction in model deployment time, improved collaboration across teams, and a 45% decrease in code duplication.

Modularity also enables component-level reuse across projects. A data quality validation module built for one AI system can serve every subsequent system that uses similar data types. This compounding value accelerates each successive AI project.

Automated testing extends beyond traditional software testing to include data validation, model performance testing, fairness testing, and drift detection. Comprehensive automated testing has been shown to reduce production incidents by 37% and detect data drift issues before they impact model performance.

What to automate: Data integrity tests verify that incoming data matches expected schemas, ranges, and distributions. Model performance tests run the model against a standard validation dataset after every update and compare results against acceptance thresholds. Fairness tests compute demographic performance metrics and flag disparities exceeding defined limits. Integration tests verify that model outputs flow correctly to downstream systems. These tests should run automatically in the CI/CD pipeline, blocking deployment when any test fails.

Implementation tip: The testing practice with the highest return is automated data validation at pipeline ingestion. Most AI production failures originate from data problems, not model problems: unexpected null values, changed field formats, shifted distributions, and corrupted data feeds. An automated data validation step that runs before every model training and inference cycle catches these problems at their source. Build validation rules for every input field: acceptable ranges, expected data types, maximum null rates, and distribution similarity to training data. When any rule is violated, the pipeline pauses and alerts the data engineering team. This single control prevents the cascade where bad data produces bad predictions that produce bad business decisions before anyone notices the data quality degradation.

## Best Practice 5: Manage Third-Party and Embedded AI Rigorously

Most organizations acquire more AI capabilities than they build. AI is embedded in vendor software ranging from procurement platforms to human resources systems, CRM tools, and enterprise resource planning systems. Each embedded AI component carries risks that the organization remains accountable for regardless of who built it.

Third-party AI management requires four disciplines.

Due diligence on vendor development practices and training data. Before procurement, evaluate the vendor's model development methodology, training data provenance, bias testing practices, and performance validation approach. Request model cards or equivalent documentation for every AI component embedded in vendor software.

Contractual provisions for transparency, liability allocation, and update notifications. Contracts should specify the vendor's obligations regarding performance metrics, fairness standards, explainability requirements, drift management, and change notification procedures. Liability for AI-related harms should be explicitly allocated, and vendor obligations should include regular compliance audits.

Monitoring vendor systems post-deployment for drift or changes. Vendor AI components change when the vendor retrains models or updates algorithms, often without customer notification. Build independent monitoring that tracks vendor AI performance on your data and your use case, detecting degradation regardless of whether the vendor reports it.

Exit strategies addressing data portability. Before signing a contract, understand what happens to your data, your configurations, and any custom model components if the relationship ends. Data portability terms negotiated before commitment are always more favorable than those negotiated during exit.

Shadow AI requires specific attention. When employees adopt AI tools outside formal channels, using personal ChatGPT accounts for work tasks, connecting unauthorized AI plugins to enterprise systems, or using AI-powered browser extensions that process company data, they create unmanaged risk. Detection mechanisms, clear acceptable use policies, and approved alternatives that meet security requirements address shadow AI more effectively than prohibition alone.

Implementation tip: Build a third-party AI inventory that catalogs every vendor AI component operating in your environment, including AI embedded in SaaS platforms that may not be marketed as "AI products." Many organizations discover during their first inventory that they have 3-5 times more third-party AI components than they knew about, because AI features were added to existing vendor products through routine software updates. Review the release notes and feature updates from your top 20 software vendors for the past 18 months. Many will have added AI-powered features (smart recommendations, automated classification, predictive analytics, chatbot capabilities) without prominently labeling them as AI. Each of these features is a third-party AI component that should be governed accordingly.

## Best Practice 6: Adopt Phased Implementation With Clear Metrics

Successful AI adoption follows a staged approach rather than attempting comprehensive deployment at once. Three phases build capability and confidence progressively.

Phase 1 automates repetitive administrative work to build trust and demonstrate quick wins. Targets include data entry automation, report generation, document processing, and routine classification tasks. These applications have well-defined inputs and outputs, clear success metrics, and low risk if they underperform. Success in Phase 1 generates the organizational support needed for more ambitious deployments.

Phase 2 adds predictive analytics for decision support, using historical data to forecast trends, identify risks, and optimize resource allocation. This phase introduces AI into decision-making processes but maintains human judgment as the final authority. Success metrics shift from efficiency (time saved) to effectiveness (prediction accuracy, forecast reliability, decision quality improvement).

Phase 3 deploys AI-powered optimization with intelligent matching, automated responses, and autonomous decision-making for appropriate use cases. This phase requires the most robust governance, monitoring, and human oversight mechanisms because the AI system is taking or heavily influencing consequential actions.

Each phase should have defined success metrics measured against baselines established before deployment: time saved on reporting, improved forecast accuracy, reduced administrative burden, error reduction, or customer satisfaction improvement.

Implementation tip: Define the metrics for each phase before beginning the phase, and measure against a baseline established from the current manual or non-AI process. Without a baseline, improvement claims are unverifiable. "The AI system processes documents in 3 minutes" sounds impressive until you learn that the manual process took 4 minutes. The improvement is real but marginal. Baselines enable honest ROI calculation: "The AI system processes documents in 3 minutes versus the manual process average of 47 minutes, representing a 94% reduction in processing time across approximately 400 documents per month, saving an estimated 293 hours monthly." This specificity supports investment decisions, demonstrates value to stakeholders, and provides the evidence base for scaling to subsequent phases.

## Best Practice 7: Integrate Human Oversight and Escalation Pathways

Despite AI's capabilities, human judgment remains critical for high-risk decisions. Best practice requires documented human oversight mechanisms with defined triggers and response procedures.

Human-in-the-loop processes ensure that consequential decisions receive human review before action. The design of human oversight matters as much as its presence. If the human reviewer sees the AI's recommendation before reviewing the case independently, automation bias may cause them to defer to the AI even when their own judgment disagrees. If the reviewer is presented with the case facts first and asked for their independent assessment before seeing the AI recommendation, the oversight is more genuine.

Escalation pathways define what happens when problems are discovered. When bias is detected, who gets notified, within what timeframe, and with what authority to act? When the model produces unexpected outputs, who investigates, and what actions can they take (pause the system, retrain the model, roll back to a previous version, shut down)? When a user reports that the AI system produced a harmful output, what's the response procedure?

These pathways should be documented before deployment, tested through tabletop exercises, and verified through periodic review of escalation logs.

Implementation tip: Measure the actual override rate for human-in-the-loop processes. If the AI makes 10,000 recommendations per month and human reviewers override 12 of them (0.12% override rate), the human oversight may be functionally nonexistent. Reviewers may be rubber-stamping AI outputs because of time pressure, automation bias, or insufficient training. Published research consistently shows that human oversight degrades when reviewers process high volumes of AI outputs without adequate time, training, or incentive to exercise independent judgment. If your override rate is below 2-3%, investigate whether the low rate reflects genuine agreement (the AI is consistently correct) or passive acceptance (reviewers aren't actively evaluating). Analyze override patterns: do overrides come from specific reviewers while others never override? Does the override rate vary with workload? These patterns distinguish active oversight from passive compliance.

## Best Practice 8: Monitor Continuously and Plan for Change

AI systems require ongoing monitoring because model performance degrades as real-world conditions change. Four types of drift require continuous surveillance.

Data drift occurs when the statistical properties of production inputs diverge from training data. The model receives inputs it wasn't trained to handle.

Concept drift occurs when the relationship between inputs and outcomes changes. What predicted customer churn in 2023 may not predict it in 2026 because customer behavior has evolved.

Model drift occurs when the model's predictions shift over time even without changes to the model itself, typically as a consequence of data drift or concept drift.

Performance degradation occurs when accuracy, fairness, or other performance metrics decline below acceptable thresholds.

When monitoring identifies issues, organizations need documented retraining and update procedures that include re-validation before deployment. This ensures that changes don't introduce new risks. The monitoring system should include defined thresholds for investigation, retraining, rollback, and retirement, with each threshold triggering a specific response procedure.

Cloud-native deployment enables dynamic scaling of monitoring and retraining operations. Published data indicates that cloud-native solutions have led to a 62% improvement in model training speed and an average cost reduction of 35% in ML infrastructure expenses.

Implementation tip: Build your monitoring system to detect problems in hours, not weeks. The most expensive monitoring failures are the slow ones, where performance degrades gradually over days or weeks without triggering any alert because each daily change is individually minor. Configure your monitoring to detect trends, not just threshold breaches. A model that drops 0.3 percentage points of accuracy per day doesn't breach a 5-point accuracy threshold for 16 days. Trend detection that flags sustained directional movement over 5-7 days catches the same problem in one-third the time. Trend-based alerts supplement threshold-based alerts and catch the gradual degradation that threshold alerts miss.

## Best Practice 9: Build AI Literacy Across the Organization

Effective AI governance depends on shared understanding across roles. Technical teams can't govern AI systems alone because they lack regulatory and business context. Business teams can't govern AI systems alone because they lack technical understanding. Governance requires both perspectives working together, which requires minimum AI literacy across the organization.

Four audience-specific literacy programs address different needs.

Executives need to understand strategic AI risk: what can go wrong at the organizational level, what the regulatory exposure looks like, and how to evaluate whether AI investments are delivering value.

Business managers need to understand how to propose use cases responsibly, how to evaluate whether AI is the right tool for a specific problem, and how to set realistic expectations for AI capabilities.

Operational staff need to understand how to interact with AI systems correctly, when to trust AI outputs, when to override them, and how to provide feedback that improves system performance.

Technical teams need to understand governance requirements, regulatory constraints, and ethical considerations that affect model design, testing, and deployment decisions. Technical excellence without governance understanding produces systems that work technically but fail regulatory or ethical standards.

Published data indicates that organizations considering ethical AI as a critical component of their AI operations increased from 54% in 2021 to 82% in 2023. Bias monitoring tools have led to a 39% reduction in biased outcomes in organizations that deploy them. These improvements require organizational literacy to sustain because tools alone don't create responsible AI culture.

Implementation tip: The most effective AI literacy investment is cross-functional workshop sessions where technical and business teams work through real scenarios together. A workshop where a data scientist explains a model card to a compliance officer, who then explains a regulatory requirement to the data scientist, produces more practical understanding than either person attending a separate training course. These workshops reveal the translation gaps between technical and business language that cause miscommunication in daily operations. Schedule quarterly cross-functional workshops covering a current AI system, its performance data, its governance documentation, and a hypothetical incident scenario. The shared experience of working through these materials together builds the mutual understanding that individual training cannot replicate.

## Best Practice 10: Measure Value, Not Just Compliance

While risk management is critical, successful AI programs also measure business value. A governance framework that prevents every possible risk but blocks every possible value creation isn't serving the organization. Balance requires measuring both dimensions.

Project managers should define success metrics that include both technical performance and business outcomes.

Technical metrics include accuracy, precision, recall, F1-score, latency, throughput, and resource utilization. These metrics confirm that the AI system functions correctly.

Business metrics include efficiency gains (time saved, manual effort reduced), revenue impact (increased conversion, reduced churn, optimized pricing), cost reduction (lower processing costs, reduced error remediation), and customer satisfaction (NPS improvement, resolution time reduction, service quality). These metrics confirm that the AI system creates value.

Organizations implementing MLOps practices have reduced model deployment time by an average of 63%, from 45 days to 17 days. AI technologies, enabled by effective operations practices, could boost labor productivity by 0.8% to 1.4% annually through 2030. These gains materialize only when organizations measure and optimize for business outcomes alongside technical performance.

Regularly evaluate the ROI of AI projects to guide future investments and technology decisions. A project that delivers strong technical performance but negative ROI may need scope adjustment, cost optimization, or retirement. A project that delivers modest technical performance but strong ROI may deserve additional investment to improve its technical foundation.

Implementation tip: Create a balanced scorecard for each AI system that tracks four quadrants: technical performance (model accuracy, latency, reliability), business impact (ROI, efficiency gains, revenue contribution), risk and compliance (bias metrics, regulatory compliance, incident rates), and user adoption (adoption rate, satisfaction scores, override rates). Review all four quadrants quarterly. A system that scores well in three quadrants but poorly in one has a specific, identifiable problem to address. A system that scores well in technical performance and compliance but poorly in business impact and user adoption is a well-governed system that nobody uses, which means it's not delivering value. The balanced view prevents the common pattern where technical teams celebrate model performance while business outcomes go unmeasured.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/modern-professional-in-a-sunny-co-working-space.png?w=1024)

## Implementation Tips for AI Project Management

These principles apply across all ten best practices.

Implementation tip on the prototype-to-production transition: The GreatAI framework, developed through design science research and evaluated with practitioners, identifies 33 specific best practices for transitioning AI from prototype to production. The research found that both ease of use and functionality are crucial factors for adopting deployment technologies. The most common failure point isn't building a working prototype. It's converting that prototype into a production system with proper data pipelines, monitoring, error handling, versioning, and governance. Budget the prototype-to-production transition as a separate project phase with its own timeline, resources, and success criteria. Teams that treat deployment as a simple step after development consistently underestimate the effort required.

Implementation tip on managing stakeholder expectations: AI projects have a unique expectation management challenge because stakeholders often have inflated expectations about AI capabilities drawn from media coverage and vendor marketing. Set expectations during the planning phase using concrete examples from comparable deployments, not abstract capability descriptions. "Our customer churn model is expected to identify 75-85% of customers likely to leave within 30 days, based on results from similar models in our industry" is a manageable expectation. "AI will predict customer churn" invites the assumption that the model will identify 100% of churning customers with certainty. The specificity of the first statement protects both the team and the stakeholder from the disappointment that vague promises create.

Implementation tip on documentation as a project deliverable: Treat documentation (model cards, risk assessments, compliance records, governance approvals) as project deliverables with the same status as code and model artifacts. Documentation completed as an afterthought after deployment is consistently lower quality than documentation completed as each phase concludes. Include documentation deliverables in your project plan with specific owners and due dates. Review documentation quality at each governance gate. A model that passes technical validation but lacks complete documentation should not proceed to deployment.

Implementation tip on the relationship between AI project management and organizational change: Every AI deployment changes how people work. Processes that were manual become automated. Decisions that were intuitive become data-driven. Roles that centered on data gathering shift toward analysis and judgment. These changes require active management. Published data on AI implementation consistently shows that the most common deployment failure mode isn't technical. It's adoption. Users who don't trust, understand, or know how to use the AI system revert to previous methods. Dedicate project management attention and budget to change management activities: user training, workflow redesign, communication, and adoption monitoring. Treat adoption rate as a first-class success metric alongside technical performance metrics.

## Key References and Authoritative Frameworks

Your AI project management practices should align with these established standards:

- ISO/IEC 42001:2023, AI Management System (governance, lifecycle, and performance evaluation)

- NIST AI Risk Management Framework 1.0, Govern-Map-Measure-Manage functions

- IIA AI Auditing Framework and 2024 IIA Standards

- EU AI Act (risk classification, compliance requirements, documentation obligations)

- ISO/IEC 5338, AI System Life Cycle Processes

- ISO/IEC 23894:2023, AI Risk Management

- MLOps frameworks and practices for automation, monitoring, reproducibility, and governance

- GreatAI and related deployment best-practice frameworks focused on prototype-to-production transition

- Internal PMO, change management, architecture review, security review, and product governance standards

- ETSI TS 104 008, Continuous Auditing-Based Conformity Assessment

- MLOps maturity model frameworks from Google, Microsoft, and AWS

- GreatAI Framework for prototype-to-production best practices (Visser, 2023)

- MLOps integration research (Sachdeva, 2024; Kabbay, 2024)

- PMBOK Guide adapted for AI project lifecycle management

- COBIT 2019 for IT governance of AI initiatives

If you manage AI projects using traditional software development practices, treating model development as deterministic, deployment as a one-time event, and post-deployment monitoring as optional, you will produce systems that work in testing environments and degrade in production. The model will drift without detection. The governance will exist without function. The business case will remain unverified because nobody measured the outcomes. And each failed project will make the next one harder to fund because the organization will have learned to distrust AI promises without learning the management practices that make AI promises deliverable.

When you apply AI-specific project management practices, building governance structures with real authority, implementing MLOps for reproducibility and scale, managing the AI lifecycle as a continuous process rather than a one-time project, integrating human oversight that functions rather than merely exists, and measuring business value alongside technical performance, you create the conditions for AI projects to deliver sustained value. The model gets built with proper validation. It gets deployed with proper monitoring. It gets maintained with proper governance. And it gets measured against the business outcomes that justified its creation.

An AI project managed like a software project is a project managed for its first 30 days. An AI project managed for its full lifecycle is a project managed for its full value.

Which of these ten best practices is weakest in your current AI project management approach? Strengthen that practice before your next AI initiative kicks off.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
