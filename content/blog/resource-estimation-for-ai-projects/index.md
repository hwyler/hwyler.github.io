---
title: "Resource Estimation for AI Projects"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-cost"
  - "ai-deployment-costs"
  - "ai-development-cost"
  - "ai-project-costing"
  - "ai-roi-calculation"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "technology"
  - "total-cost-of-owership"
---

## The 15 Cost Categories for AI Budgets (And What They Actually Cost)

A Deloitte survey found that 52% of AI projects exceed their original budget. The overage isn't typically caused by one large unexpected expense. It's caused by dozens of cost categories that were never included in the original estimate.

Teams budget for the obvious items: cloud compute, software licenses, and data scientist salaries. Then they discover that data labeling costs more than model development. That integration with legacy systems takes three times longer than estimated. That compliance audits require external specialists nobody accounted for. That change management, the work of getting humans to actually use the AI system, was never budgeted at all.

AI project budgets fail because they're built around development costs and ignore the full lifecycle. A complete AI budget covers 15 cost categories spanning initial implementation and ongoing operations. This post walks through each one, explains what drives the cost, identifies where estimates most commonly go wrong, and provides the practical guidance needed to build budgets that survive contact with reality.

## Why AI Projects Are Uniquely Difficult to Budget

AI projects carry cost estimation challenges that traditional software projects don't. Three characteristics make AI budgeting harder.

First, model performance is uncertain until training is complete. A traditional software project can estimate development effort with reasonable confidence because the logic is deterministic. An AI project can't guarantee that the model will reach its accuracy target, which means the number of training iterations, the amount of additional data required, and the extent of architecture changes are all uncertain at planning time.

Second, data costs are difficult to predict because data quality problems aren't fully visible until data preparation begins. A dataset that looks adequate during feasibility assessment reveals gaps, inconsistencies, and labeling needs during actual preparation that can multiply the original data budget by two to five times.

Third, AI systems require ongoing operational spending that traditional software doesn't. Models need retraining. Monitoring systems need maintenance. Bias audits need repeating. Infrastructure costs scale with usage in ways that are difficult to forecast. The operational budget for an AI system in its second year often exceeds the development budget for its first year.

These characteristics mean that AI budgets need both more categories and larger contingency reserves than traditional technology budgets. Organizations that apply standard IT budgeting templates to AI projects systematically underestimate total cost.

Implementation tip: Build your AI budget in two sections: initial implementation costs (one-time expenses to build and deploy the system) and ongoing operational expenses (recurring costs to maintain, monitor, and improve the system). Present both sections to decision-makers together. Many AI projects get approved based on implementation costs alone, with operational costs disclosed later as "maintenance" that nobody initially planned for. A project that costs $400,000 to build and $200,000 per year to operate has a 3-year total cost of $1,000,000. If the business case was approved based on $400,000, the ROI calculation is fundamentally wrong. Present the full lifecycle cost from the beginning. Decision-makers who see the complete picture make better decisions than those who see only the first installment.

## Cost Category 1: Software Licensing

Software licensing covers the licenses for AI tools, platforms, and applications, including cloud-based services. This category includes machine learning frameworks, data processing platforms, model management tools, annotation platforms, monitoring dashboards, and any commercial AI APIs your system depends on.

What drives the cost: Licensing models vary significantly across vendors. Some charge per user, others per API call, others per compute hour, and others through annual enterprise agreements. A platform that appears affordable during proof of concept at low usage volumes may become expensive at production scale. Pricing tiers, overage charges, and minimum commitment terms all affect total cost.

Common estimation errors: Teams budget based on proof-of-concept usage rates and discover that production usage is 5x to 20x higher. They select tools during development without evaluating licensing costs at projected production volumes. They don't account for development environment licenses that duplicate production licenses.

What to include: List every software tool the project requires, its licensing model, its cost at projected usage volume, and its contract terms including minimum commitments and renewal pricing. Include development, staging, and production environment licenses separately.

Implementation tip: Request production-scale pricing from every software vendor before including their tool in your budget. Development-tier pricing is designed to attract adoption. Production-tier pricing is where vendors capture value. The difference can be dramatic. One organization budgeted $2,400 per month for an AI platform based on the development tier pricing they saw during proof of concept. Production-tier pricing at their projected inference volume was $18,000 per month. That $15,600 monthly gap, discovered after the architecture was already built around the platform, created a budget shortfall that required either a vendor renegotiation or an architectural change. Request a formal quote at projected production volume during project planning, not after commitment to the platform.

## Cost Category 2: Data Acquisition

Data acquisition covers expenses for purchasing data from external sources and costs related to internal data collection and preparation. For many AI projects, data is the most expensive input, yet it's consistently one of the most underestimated budget categories.

What drives the cost: External data purchases vary from free public datasets to six-figure annual licensing agreements for specialized commercial data. Internal data collection costs include the staff time required to extract data from existing systems, the engineering effort to build data pipelines, and the operational cost of any new data collection processes that need to be established.

Common estimation errors: Teams assume that internal data is free because it already exists. Extracting, transforming, and validating internal data for AI use requires significant engineering effort. A dataset that exists in a production database requires pipeline development, format transformation, quality validation, and potentially anonymization before it's usable for model training. These preparation costs are data acquisition costs, even when no external purchase is involved.

What to include: External data purchase prices, internal data extraction engineering effort (estimated in person-hours), data pipeline development costs, and any ongoing data refresh costs for datasets that need periodic updating.

## Cost Category 3: Data Management

Data management covers the cost for data cleaning, labeling, and ongoing data management to ensure high-quality inputs for AI models. This category is separate from data acquisition because the work happens after data is obtained.

What drives the cost: Data cleaning effort depends on source data quality, which is usually worse than initial estimates suggest. Labeling costs depend on the volume of data requiring labels, the complexity of the labeling task, and whether labeling is done internally or outsourced to specialized services. Ongoing data management includes maintaining data quality over time, updating datasets as business conditions change, and managing data versioning across model iterations.

Common estimation errors: Data labeling is the single most underestimated line item in AI budgets. A natural language processing model might need 100,000 labeled text examples. At a commercial labeling rate of $0.05 to $0.50 per label depending on complexity, that's $5,000 to $50,000 for labeling alone. For specialized domains like medical imaging or legal document classification, labeling requires domain experts whose time costs significantly more. Teams that estimate labeling at zero because "we'll have internal staff do it" are still spending that money. They're spending it as opportunity cost of staff time diverted from other work.

What to include: Data cleaning effort (person-hours), labeling costs (internal staff time or external vendor fees), quality assurance for labeled data, data versioning infrastructure, and ongoing data refresh and maintenance effort.

Implementation tip: Get a labeling cost estimate from at least two external vendors, even if you plan to label data internally. The external quote provides a benchmark for the true cost of labeling effort. Internal labeling almost always takes longer and costs more than teams estimate because it competes with employees' primary responsibilities. If the external quote is $30,000 and your internal estimate is $5,000, your internal estimate is probably wrong. Either the volume estimate is too low, the per-label time estimate is too optimistic, or the complexity of the labeling task hasn't been fully understood. The external quote grounds your estimate in market reality.

## Cost Categories 4 and 5: Infrastructure and Cloud Services

Infrastructure costs cover investments in hardware, servers, storage, and networking equipment necessary to support AI development and deployment. Cloud services cover the costs for cloud computing resources, including storage, processing power, and associated service fees. These categories are closely related and often overlap, but they serve different budget functions.

Infrastructure costs tend to be capital expenditures with depreciation schedules. Cloud services tend to be operating expenditures with monthly billing. The mix between them depends on your deployment strategy: fully cloud-based, fully on-premises, or hybrid.

What drives infrastructure costs: GPU hardware for model training is the largest infrastructure expense for organizations that train models on-premises. A single high-end GPU costs $10,000 to $40,000. Training large models may require clusters of multiple GPUs. Storage costs scale with dataset size and model artifact retention. Networking costs increase when training data must be transferred between locations.

What drives cloud costs: Compute instances for model training, GPU-accelerated instances for inference, data storage, data transfer between services, managed AI services (such as AutoML platforms or pre-trained model APIs), and monitoring and logging services. Cloud costs are variable, which makes them harder to predict but easier to adjust.

Common estimation errors: Teams estimate cloud costs based on training a model once. In practice, models are trained multiple times during development as architectures are adjusted, hyperparameters are tuned, and data issues are resolved. Ten training runs at the same cost means 10x the cloud compute budget. Production inference costs are estimated based on average load without accounting for peak usage periods. And teams frequently forget to include development and staging environment costs, which can equal 30-50% of production environment costs.

What to include: For infrastructure, list hardware purchases with depreciation schedules, installation costs, maintenance contracts, and physical space requirements. For cloud services, estimate training compute (multiply single-run cost by expected number of training iterations), inference compute at projected volume with peak load multiplier, storage for data and model artifacts, data transfer costs, and managed service fees.

Implementation tip: Run a 30-day cloud cost tracking exercise during proof of concept before projecting production costs. Most cloud providers offer detailed cost breakdowns that show exactly where money is being spent. Analyze this breakdown to identify the highest-cost components and estimate how they'll scale with production volumes. Cloud cost calculators provided by vendors tend to underestimate actual costs by 20-40% because they don't account for idle resources, failed experiments, and data transfer charges between services. Your own measured costs from the proof of concept phase, scaled by the ratio of proof-of-concept volume to projected production volume, produce a more realistic estimate.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/colorful-code-display.png?w=1024)

## Cost Category 6: Integration

Integration covers expenses for connecting the AI solution with existing systems and software within your organization. Integration is the category that most frequently exceeds its budget because the complexity of connecting AI outputs to existing business processes is difficult to assess until the work begins.

What drives the cost: The number and complexity of integration points determine the effort. Each integration point requires understanding both the AI system's output format and the receiving system's input requirements, building data transformation logic between them, handling error cases and fallback scenarios, and testing the integration under realistic conditions. Legacy systems with limited APIs, outdated documentation, or proprietary data formats increase integration costs substantially.

Common estimation errors: Teams estimate integration effort based on the number of systems to connect without assessing the complexity of each connection. Connecting to a modern REST API takes days. Connecting to a legacy system with a flat-file interface and batch processing windows takes weeks. The average effort per integration point varies by an order of magnitude depending on the target system.

What to include: Engineering effort for each integration point (estimated separately based on target system complexity), middleware or integration platform costs, testing effort for each integration, and ongoing maintenance for integrations as connected systems are updated.

Implementation tip: Identify every system the AI solution needs to communicate with during the feasibility phase, not during development. For each system, document: the interface type (API, database, file transfer, message queue), the interface documentation quality (complete, partial, nonexistent), the system owner and their availability for integration support, and any planned changes to the system during your project timeline. This inventory almost always reveals at least one integration point that's significantly more complex than initially assumed. Finding that complexity during planning adjusts the budget. Finding it during development adjusts the timeline.

## Cost Category 7: Personnel

Personnel covers salaries for internal team members such as data scientists, AI engineers, machine learning engineers, data engineers, and project managers. For most AI projects, personnel is the largest single cost category.

What drives the cost: AI talent commands premium compensation in most markets. Data scientists, ML engineers, and MLOps specialists have compensation ranges that exceed general software engineering roles by 20-40% in many geographies. The team composition varies by project phase: data engineers are heavily utilized during data preparation, data scientists during model development, ML engineers during deployment, and operations staff during production monitoring.

Common estimation errors: Teams budget for the number of people needed during peak development but don't account for the full project duration. A data scientist who's needed for 3 months of model development is still partially allocated during the 2 months of data preparation that precede it and the 2 months of deployment that follow. Personnel costs should reflect the actual allocation percentage across the full timeline, not just the peak utilization period.

What to include: Salary costs for each team member, prorated by their allocation percentage to the project, for the full project duration including post-deployment support. Include benefits, taxes, and overhead multipliers. Budget separately for any new hires required, including recruitment costs and ramp-up time during which the new hire is learning rather than contributing at full capacity.

## Cost Category 8: Contractors and Consultants

Contractor and consultant fees cover external experts such as AI consultants, data specialists, or software developers brought in to supplement internal capabilities.

What drives the cost: Daily or hourly rates for specialized AI expertise range from $150 to $500+ per hour depending on specialization and geography. Common external engagements include: AI strategy consulting during planning, specialized model development for domains where internal expertise is insufficient, security and red-team assessments, bias audits requiring independent evaluation, and regulatory compliance advisory services.

Common estimation errors: Teams budget for the initial consulting engagement without accounting for follow-up work. An AI strategy consultant who spends 3 weeks on initial planning often needs to return for 1 week during pilot evaluation and another week during production readiness review. Engagement extensions and follow-up work typically add 30-50% to the original contractor budget.

What to include: Contractor daily rates, estimated engagement duration, travel expenses if applicable, and a buffer for engagement extensions. For ongoing relationships such as managed service providers, include the full contract value over the budget period.

Implementation tip: For personnel and contractor costs combined, map the staffing profile across the full project timeline as a chart showing headcount or cost by month. This visualization reveals staffing gaps (months where critical roles are unallocated) and staffing peaks (months where costs spike due to overlapping phases). It also reveals the cost of delays. If the project timeline extends by two months, the staffing chart shows exactly what those two months cost in personnel and contractor spend. This number is often large enough to justify investment in preventing delays, such as more thorough feasibility assessment or better data preparation, which might seem expensive in isolation but are cheap compared to the per-month cost of timeline extension.

## Cost Categories 9 and 10: Training and Maintenance

Training and development covers the cost for programs and resources to upskill your team on AI technologies and tools. Maintenance and support covers costs for future software maintenance, updates, and technical support.

Training costs include formal course fees, conference attendance, certification programs, and the productive time lost while employees are learning rather than working. AI tools and platforms change rapidly, which means training is not a one-time expense. Budget for initial training during project onboarding and ongoing training as tools evolve.

What to include for training: Course and certification fees per team member, conference and event costs, internal training development costs (if you're creating custom training materials), and productive time allocation for learning (estimate the hours each team member will spend in training and multiply by their hourly cost).

Maintenance costs include software updates, bug fixes, model retraining, infrastructure patching, and technical support contracts. For AI systems, maintenance is more intensive than for traditional software because models degrade over time and require periodic retraining, monitoring systems need ongoing calibration, and the AI technology landscape evolves rapidly, requiring regular platform and library updates.

What to include for maintenance: Annual software maintenance fees (typically 15-22% of license cost), model retraining costs (compute, data, and personnel per retraining cycle multiplied by expected annual frequency), infrastructure maintenance and patching effort, and vendor technical support contract costs.

Implementation tip: Estimate maintenance costs as a percentage of total initial implementation cost and validate that percentage against industry benchmarks. For AI systems, annual maintenance costs typically run between 20% and 35% of the initial implementation investment. A system that costs $500,000 to build will likely cost $100,000 to $175,000 per year to maintain. If your maintenance estimate is significantly below this range, scrutinize it. The most common maintenance cost omission is model retraining. A model that needs quarterly retraining at $15,000 per cycle adds $60,000 annually that many budgets miss entirely. If your maintenance estimate is significantly above this range, evaluate whether the system is too complex for its value proposition.

## Cost Categories 11 and 12: Compliance and Testing

Compliance and security covers costs for ensuring that AI systems meet regulatory requirements and for robust security measures. This includes bias audits, certifications, regulatory filings, and security assessments. Testing and validation covers costs for testing AI models to ensure accuracy, reliability, and alignment with business objectives.

Compliance costs vary dramatically based on the risk level of the AI system and the regulatory jurisdictions where it operates. A low-risk internal productivity tool may require minimal compliance investment. A high-risk AI system making decisions about individuals under the EU AI Act requires impact assessments, conformity assessments, and ongoing monitoring that can cost $50,000 to $200,000 or more.

What to include for compliance: External bias audit fees (typically $20,000-$75,000 per audit depending on system complexity), certification costs for applicable standards (ISO 42001, SOC 2, etc.), legal review of AI-specific regulatory requirements, data protection impact assessment costs, and ongoing compliance monitoring effort.

Testing costs include the effort for functional testing, performance testing, security testing, fairness testing, and user acceptance testing. AI systems require more extensive testing than traditional software because model behavior must be validated across diverse input scenarios, demographic subgroups, and edge cases.

What to include for testing: Internal testing effort (person-hours across all testing phases), external penetration testing and red-team assessment fees, test data creation or acquisition costs, testing infrastructure costs (separate environments that mirror production), and user acceptance testing coordination effort.

Implementation tip: Budget for at least two rounds of bias auditing: one before initial deployment and one six months after deployment. Pre-deployment audits assess the model on test data. Post-deployment audits assess the model on actual production data, which frequently reveals fairness issues that test data didn't capture. Many organizations budget for the initial audit and treat it as a completed task. Regulatory frameworks including the EU AI Act require ongoing bias monitoring, not one-time assessment. The post-deployment audit often costs less than the initial audit because the methodology is established, but it must be explicitly budgeted or it won't happen.

## Cost Categories 13, 14, and 15: R&D, Change Management, and Contingency

Research and development covers costs for experimenting with new AI models or technologies. Not every AI project requires dedicated R&D spend. But projects that involve novel applications, emerging model architectures, or unproven techniques should budget for experimentation that may not directly produce production features.

What to include: Dedicated research time for team members exploring alternative approaches, compute costs for experimental model training, and prototype development costs for testing new capabilities before committing to production implementation.

Change management covers the cost of managing organizational change and communicating AI project developments to stakeholders. This category is budgeted by fewer than 30% of AI projects despite being cited as a top-three success factor for AI adoption.

What to include: Internal communications development (materials explaining the AI system, its purpose, and its impact on roles), stakeholder engagement effort (meetings, presentations, feedback sessions), workflow redesign and documentation updates, and any organizational restructuring costs associated with AI-driven process changes.

Contingency reserve is a fund for covering unexpected costs or project overruns. Given the inherent uncertainty in AI project budgets, contingency is not optional.

What to include: A contingency percentage applied to the total project budget. For AI projects with well-defined requirements and proven technology approaches, 15-20% contingency is reasonable. For projects involving novel approaches, uncertain data availability, or complex integrations, 25-35% contingency is appropriate. Consider whether cyber insurance policies should be included as part of the contingency strategy, particularly for AI systems that process sensitive data or make consequential decisions.

Implementation tip: Change management is the budget category that most directly affects whether the AI system delivers its projected value. A system that works technically but isn't adopted by users delivers zero value. Change management investment, including user training, stakeholder communication, and workflow adaptation support, directly drives adoption rates. Yet change management is typically the first line item cut when budgets are squeezed. Protect it. Industry data consistently shows that AI projects with dedicated change management budgets achieve 2x to 3x higher user adoption rates than projects without them. If your budget comes under pressure, cut contingency before cutting change management. A smaller reserve with high adoption beats a larger reserve with a system nobody uses.

## Tips for AI Resource Estimation

These principles apply across all 15 cost categories.

Implementation tip on the difference between estimates and commitments: Present your AI budget as a range, not a single number. Provide a best-case estimate (everything goes according to plan), an expected-case estimate (normal challenges and moderate scope adjustments), and a worst-case estimate (significant technical challenges, data issues, or timeline extensions). Decision-makers who see a range understand the uncertainty inherent in AI projects. Decision-makers who see a single number treat it as a commitment and react negatively to any variance. The expected-case estimate should be your primary planning number. The worst-case estimate should inform your contingency reserve. The best-case estimate should be treated as unlikely but possible.

Implementation tip on tracking actual costs against budget: Track actual spending against budget at the category level monthly, not just at the total project level. Total project spending can appear on track while individual categories are significantly over or under budget. If data management is 200% over budget and infrastructure is 50% under budget, the total may look fine, but the data management overage signals a problem that needs attention. Category-level tracking reveals where estimate accuracy was poor, enabling better estimates on future projects. It also enables mid-project reallocation: if one category is running under budget, those funds can be formally reallocated to categories running over, rather than allowing overspending to accumulate without acknowledgment.

Implementation tip on the ongoing operational budget: Build the operational budget as a separate, recurring annual document, not as a line item in the project budget. The project budget covers implementation and ends at deployment. The operational budget covers the system's ongoing costs and starts at deployment. These are different financial instruments with different approval processes and different ownership. The project sponsor approves the project budget. The system owner or business line leader approves the operational budget. If the operational budget doesn't have its own owner and approval process, operational costs either get absorbed into general IT overhead without visibility or get neglected until the system degrades from inadequate maintenance.

Implementation tip on validating estimates with comparable projects: Before finalizing your budget, identify two or three comparable AI projects, either within your organization or documented in industry case studies, and compare your estimates against their actual costs. Significant deviations in any category should trigger investigation. If comparable projects spent 25% of their budget on data management and your estimate allocates 8%, either your project has genuinely simpler data requirements or your estimate is unrealistic. This benchmarking step takes a few hours and has repeatedly caught estimation errors that would have caused budget overruns.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/publithings_seo_a_man_showing_off_a_powerful_processor_with_the_d8b945bf-4d5c-455f-b33d-0c4427d2fa7e-768x384.png.webp?w=768)

## AI Costing References

Your AI resource estimation should align with these established standards and guidelines:

- ISO/IEC 42001:2023, AI Management System (resource planning and allocation requirements)

- ISO/IEC 5338, AI System Life Cycle Processes (resource estimation across lifecycle stages)

- NIST AI Risk Management Framework (resource requirements for risk management functions)

- EU AI Act, Article 9 and Annex IV (documentation and compliance cost requirements for high-risk systems)

- PMBOK Guide for cost estimation and budget management methodology

- COBIT 2019 for IT governance alignment of AI investment decisions

- ISO/IEC 27001:2022 (security investment requirements for AI systems)

- FinOps Foundation guidance for cloud cost management and optimization

- Gartner TCO models for AI and machine learning systems

- ISO/IEC 25010 for quality-related testing and validation cost planning

If you build your AI budget around development costs alone, presenting a number that covers building the system but ignores operating it, you will either face an unpleasant budget conversation six months after deployment or quietly underfund the operational activities that keep the system safe, accurate, and compliant. Underfunded monitoring misses model drift. Underfunded maintenance allows technical debt to accumulate. Underfunded compliance skips the audits that regulations require. The system runs, but the risks compound silently until an incident forces attention and the cost of remediation far exceeds what proper budgeting would have required.

When you estimate resources across all 15 cost categories, present full lifecycle costs honestly, track actual spending against estimates at the category level, and maintain a separate operational budget that's reviewed and approved annually, you create financial visibility that supports good decisions. Decision-makers who understand the true cost of an AI system can evaluate its ROI honestly, prioritize investments rationally, and allocate resources where they generate the most value. An AI budget that tells the full truth is an AI project's strongest foundation.

An AI project funded for development but not for operations is a project funded to start but not to succeed.

Which of the 15 cost categories is missing from your current AI project budget? Add it before the next budget review.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and globally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
