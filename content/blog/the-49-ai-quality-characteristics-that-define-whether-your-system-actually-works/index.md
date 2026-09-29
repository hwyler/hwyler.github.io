---
title: "The 49 AI Quality Characteristics That Define Whether Your System Actually Works"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-project-risks"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "hernan-huwyler"
  - "iso-25059"
  - "iso-31000"
  - "objectives-at-risk"
  - "technology"
---

## A Practitioner's Guide to ISO/IEC 25059

A model with 95% accuracy that nobody can explain, nobody can maintain, and nobody trusts is not a quality AI system. It is a liability waiting to surface.

I learned this the hard way. Three years ago, I helped deploy a classification model for a European insurer. The accuracy metrics were excellent. The data science team celebrated. Six weeks later, the project was in crisis. The model could not be updated without breaking downstream integrations (maintainability failure). Users did not understand why it made specific recommendations and stopped trusting it (transparency failure). The system consumed three times the expected cloud resources during peak periods (performance efficiency failure). And when a regulator asked how the model made decisions about claims, nobody could provide an adequate explanation (accountability failure).

The model worked. The system did not.

That distinction, between a model that produces correct outputs and a system that delivers quality across its full operational lifecycle, is exactly what ISO/IEC 25059:2023 addresses. This standard defines 49 quality characteristics for AI systems across 11 requirement domains. It builds on the established software quality model of ISO/IEC 25010 but adapts it for the specific challenges of AI: opacity, learned behavior, data dependency, drift, fairness, and the unique ways AI systems interact with human judgment.

This post walks through all 49 characteristics with practical implementation guidance for each. Use it as a checklist for AI system design, a framework for quality assurance, and a reference for identifying which characteristics create risk when they are absent.

## Why Software Quality Models Are Not Enough for AI

ISO/IEC 25010 is the standard quality model for software products and systems. It has served the industry well for conventional software. It defines characteristics like reliability, security, maintainability, and usability that apply to any software system.

AI systems need more.

A traditional software system does what its code tells it to do. If the code is correct, the system is correct. An AI system does what its training data and learned parameters tell it to do. Correctness is probabilistic, not deterministic. The system can be "correct" on average while failing catastrophically for specific populations or edge cases.

Three gaps in traditional software quality models become critical for AI.

First, transparency and explainability are not optional quality attributes for AI. They are functional requirements. A user who cannot understand why an AI system made a particular decision cannot verify it, trust it, or correct it. Traditional software quality models treat transparency as a nice-to-have. For AI, it is a prerequisite for accountability and regulatory compliance.

Second, AI systems degrade in ways traditional software does not. Data drift, concept drift, and model decay cause AI system quality to deteriorate over time even without any code changes. A quality model that only evaluates the system at deployment misses the ongoing quality challenges that define AI operations.

Third, AI systems create societal risks that traditional software rarely produces. Bias, discrimination, loss of autonomy, environmental impact, and ethical harms are quality concerns specific to AI that require explicit quality characteristics and measurement approaches.

ISO/IEC 25059 fills these gaps by extending the traditional quality model with AI-specific characteristics across every domain. The result is a comprehensive framework for evaluating whether an AI system is genuinely fit for purpose, not just whether it produces accurate outputs.

Original implementation tip: When I introduce ISO 25059 to organizations, the most common initial reaction is overwhelm. Forty-nine characteristics feels like an impossibly large quality surface to manage. The practical approach is to prioritize. Not every characteristic is equally relevant for every AI system. A customer-facing recommendation engine needs strong transparency, user controllability, and fairness characteristics. An internal process automation system needs strong reliability, maintainability, and robustness characteristics. Map the 49 characteristics to your specific system's risk profile and context of use. Identify the 10 to 15 that are most critical. Focus your quality assurance resources there. Then expand coverage over time.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/engaged-professional-at-a-coffee-strewn-workstation.png?w=1024)

## Domain 1: Functional Suitability

Four characteristics define whether the AI system does what it is supposed to do.

### Functional Completeness

The degree to which the system's functions cover all specified tasks and user objectives. The AI system provides all necessary functions for its intended purpose and fulfills all explicitly stated and implied user needs.

This sounds basic. It is the characteristic most often violated in AI projects because teams focus on the model's prediction function and neglect the surrounding functions that make the prediction useful: data preprocessing, output formatting, error handling, user feedback mechanisms, and integration with downstream workflows.

To get this right, conduct rigorous requirements gathering that maps all user tasks to system functions. Validate coverage through user acceptance testing and traceability matrices that link requirements to implemented functions.

Original implementation tip: The functional completeness gap I find most often is the absence of a "decline to predict" function. Most AI systems are built to produce an output for every input. But there are inputs where the system should not produce a prediction because it does not have sufficient confidence, because the input falls outside its training distribution, or because the decision requires human judgment. Build the ability to abstain into your system. A credit scoring model that says "I cannot score this application with sufficient confidence, route to a human underwriter" is more functionally complete than one that produces a low-confidence score that a loan officer treats as definitive.

### Functional Correctness

The degree to which the AI system provides correct results with the needed degree of precision. Outputs and effects are accurate and yield the right result.

For AI systems, "correct" is probabilistic. A model with 90% accuracy is wrong 10% of the time. The question is not whether the system is perfect but whether its error rate falls within acceptable bounds for its application context, and whether errors are distributed fairly across populations.

Establish ground truth datasets and validate continuously against predefined accuracy metrics such as F1-score, precision, and recall. Use adversarial testing to challenge model outputs and expose weaknesses.

### Functional Appropriateness

The degree to which functions facilitate the accomplishment of specified tasks and objectives. Functions are suitable for the user's stated goals and context of use.

An AI system can be functionally complete and correct while still being inappropriate. A sentiment analysis model that classifies customer feedback into three categories (positive, negative, neutral) is functionally correct but functionally inappropriate if the customer service team needs to distinguish between 12 specific complaint types to route tickets effectively.

Conduct task analysis and user studies to ensure functions align with actual user goals and workflows. Prioritize features based on user value, not technical feasibility.

### Functional Adaptability

The degree to which the AI system can be adapted for different specified tasks and environments. The system can be modified or configured for new purposes or contexts.

AI systems that cannot adapt become obsolete quickly. Business requirements change, data distributions shift, and new use cases emerge. A system designed for a single, fixed purpose delivers diminishing value over time.

Design systems with configurable parameters and hooks for retraining. Use feature flags and modular architecture to enable adaptation to new tasks without full redevelopment.

Original implementation tip: Functional adaptability is the suitability characteristic that determines long-term ROI, and it is almost always underinvested in during initial development because the pressure is on delivering the first use case. I worked with a logistics company that built a demand forecasting model tightly coupled to a single product category. When they wanted to extend it to two additional categories, they discovered the data pipeline, feature engineering, and model architecture were all hard-coded for the original category. Extending took nearly as long as building from scratch. Build adaptability into the architecture from day one, even if you are deploying for a single use case. Parameterize data sources, feature definitions, and model configurations. The marginal cost during initial development is small. The cost of retrofitting adaptability later is enormous.

## Domain 2: Performance Efficiency

Three characteristics define whether the system uses resources appropriately.

### Time Behaviour

The degree to which response and processing times meet requirements. The system delivers results within required time constraints.

For AI systems, time behavior is more variable and harder to predict than for traditional software. Inference latency depends on model complexity, input size, hardware availability, and concurrent load. Training time depends on dataset size, model architecture, and compute resources.

Profile system components to identify bottlenecks. Set Service Level Objectives for latency and throughput. Optimize models through quantization, pruning, or distillation for target deployment environments.

### Resource Utilisation

The degree to which resource usage meets requirements. The system uses appropriate amounts of processing capacity, memory, and network bandwidth.

AI workloads consume significantly more resources than traditional applications. GPU costs for training, memory requirements for large models, and storage demands for training data can all exceed initial estimates.

Monitor compute, memory, and network usage during both inference and training. Right-size infrastructure and use auto-scaling. Prefer efficient model architectures for resource-constrained deployment environments.

### Capacity

The degree to which maximum limits of system parameters meet requirements. The system handles the specified maximum number of items, users, or data volume.

Perform load and stress testing to determine system limits across users, transactions, and data volume. Design architecture to scale horizontally. Build in rate limiting and graceful degradation so that exceeding capacity reduces performance rather than causing failure.

Original implementation tip: The performance efficiency characteristic that catches organizations off guard is resource utilization during retraining, not during inference. Teams size their infrastructure for inference workloads and then discover that monthly retraining jobs require 10 times the compute resources. The retraining job competes with inference for GPU capacity, degrading production performance during the retraining window. Separate training and inference infrastructure, or schedule retraining during off-peak periods with dedicated resource allocation. Monitor resource utilization during both operational modes separately.

## Domain 3: Compatibility

Two characteristics define how the system coexists with its environment.

### Co-existence

The degree to which the AI system performs its functions while sharing a common environment and resources with other products. The system operates without negatively impacting other systems.

Test the AI system in a staging environment that mirrors production, including all other applications that share resources. Ensure the AI system does not monopolize shared CPU, memory, or network bandwidth during peak inference or training periods.

### Interoperability

The degree to which systems can exchange and use information. The AI system effectively communicates with other specified systems.

Adopt standard data formats like ONNX and PMML for model exchange, and standard API protocols like REST and gRPC for communication. Implement rigorous schema validation for all data exchanges. Use API gateways for consistent management of interfaces.

Original implementation tip: Interoperability failures are among the most common reasons AI projects fail during the transition from development to production. The model works perfectly in the data science team's environment but cannot consume data from the production pipeline because formats, schemas, or encoding conventions differ. Test interoperability between the development environment and the production environment early, ideally within the first two weeks of development. Discovering format mismatches at deployment is expensive. Discovering them during initial development is cheap.

## Domain 4: Usability

Seven characteristics define the human experience of interacting with the AI system. This is the largest traditional usability domain and includes two AI-specific additions: user controllability and transparency.

### Appropriateness Recognisability

The degree to which users can recognize whether the system is appropriate for their needs. The system's capabilities and limitations are clear to potential users.

Provide clear documentation of capabilities, limitations, and intended use cases. Create a Model Card or similar fact sheet that communicates what the system does, what it does not do, what data it was trained on, and where it performs well or poorly.

### Learnability

The degree to which the system enables users to learn how to use it effectively. The system supports users in acquiring operational knowledge.

Develop intuitive interfaces, comprehensive documentation, and interactive tutorials. Incorporate contextual help. Conduct usability testing to measure the learning curve across different user populations.

### Operability

The degree to which the system is easy to operate and control. User effort for operation is minimized.

Design clear and consistent interfaces and APIs. Provide effective error messages and status indicators. Automate complex operational tasks where possible.

### User Error Protection

The degree to which the system protects users against making errors. The system prevents, detects, and helps users recover from mistakes.

Implement input validation, confirmation dialogs for critical actions, and undo functionality. Use constraints to prevent invalid inputs. Guide users through complex tasks with clear step-by-step workflows.

### User Interface Aesthetics

The degree to which the interface enables pleasing interaction. The design is visually and interactively appealing.

Apply established design systems for visual consistency. Ensure a clean, uncluttered interface. Conduct user research on aesthetic perception to ensure the design supports rather than hinders the user's task.

### Accessibility

The degree to which the system can be used by people with the widest range of characteristics and capabilities. The system accommodates diverse user needs including disabilities.

Follow WCAG 2.1 guidelines. Test with screen readers, ensure keyboard navigation, provide alt text for images, and support high contrast modes. Accessibility is not optional. It is a quality requirement and increasingly a legal one.

### User Controllability (AI-Specific)

The degree to which users can control the AI system's behavior. Users can initiate, adjust, or stop the system's operations.

Provide settings to adjust system behavior such as confidence thresholds and filters. Allow users to start, stop, and correct operations. Ensure humans can always override AI decisions. This characteristic is directly tied to the EU AI Act's requirements for human oversight of high-risk AI systems.

### Transparency (AI-Specific)

The degree to which the system's functions, decisions, and outputs are understandable to the user. The system provides explanations for its behavior and results.

Implement Explainable AI techniques like LIME and SHAP to provide output explanations. Document the model's purpose, training data, and algorithms. Be explicit about the system's AI nature. Transparency is not a single feature. It is a quality that must be designed into every interaction between the system and its users.

Original implementation tip: Of the seven usability characteristics, user controllability is the one most often missing from AI system designs, and it is the one regulators are asking about most frequently. I reviewed an AI system for a healthcare provider that provided diagnostic recommendations to physicians. The system had no mechanism for a physician to adjust the confidence threshold, no way to request an alternative recommendation, and no clear process for overriding the system's output when clinical judgment disagreed. The system treated every recommendation as a final answer rather than an input to human decision-making. When the EU AI Act's human oversight requirements were mapped against the system's capabilities, the gap was significant. Build controllability from the start. Provide clear controls for adjusting, overriding, and stopping AI behavior. Document how these controls work and verify that users know how to use them.

\[Suggested image placement: A visual showing all 11 quality domains arranged in a wheel or grid, with the number of characteristics per domain indicated, highlighting the AI-specific additions in a distinct color\]

## Domain 5: Reliability

Five characteristics define whether the system performs consistently and recovers from failures. This domain includes one critical AI-specific addition: robustness.

### Maturity

The degree to which the system meets reliability needs under normal operation. The system is stable with a low failure rate in its standard operating environment.

Establish a robust CI/CD pipeline with automated testing. Track mean time between failures. Use canary deployments to gradually roll out updates and catch stability issues before full deployment.

### Availability

The degree to which the system is operational and accessible when required. The system has minimal downtime.

Design for redundancy with failover mechanisms across availability zones. Monitor uptime and establish Service Level Agreements. Implement health checks and graceful degradation so that partial failures do not cause total outages.

### Fault Tolerance

The degree to which the system operates as intended despite hardware or software faults. The system continues functioning during component failures.

Build systems that handle component failures without total collapse. Use retries with exponential backoff, circuit breakers, and fallback mechanisms. Design stateless services where possible to simplify recovery.

### Recoverability

The degree to which the system can recover data and re-establish desired state after failure. The system restores service and data quickly.

Implement automated backup and restore procedures for models and data. Define and test a Disaster Recovery plan. Track mean time to recovery. Ensure recovery points are consistent, meaning the model, its configuration, and its data are all restored to the same point in time.

### Robustness (AI-Specific)

The degree to which the system functions correctly despite invalid inputs, stressful conditions, or adversarial attacks. The system maintains performance under perturbation.

This is the reliability characteristic most specific to AI and most critical for security. Test with noisy, out-of-distribution, and adversarial inputs. Use data augmentation, adversarial training, and defensive distillation to improve resilience. Monitor for data drift that degrades robustness over time.

Original implementation tip: Robustness is the reliability characteristic that creates the most direct link between quality and security. A model that is not robust against adversarial inputs is both a quality failure and a security vulnerability. Yet robustness testing is consistently treated as a security activity performed by the security team rather than a quality activity performed by the development team. This separation creates gaps. The security team tests for adversarial attacks. The development team tests for accuracy. Nobody tests for the space in between: inputs that are not adversarial but are unexpected, noisy, or from a different distribution than the training data. These "natural" robustness failures are more common than adversarial attacks and cause more cumulative damage. Include robustness testing in your development quality assurance process, not just in your security testing program.

## Domain 6: Security

Six characteristics define the system's security posture. This domain includes one AI-specific addition: intervenability.

### Confidentiality

The degree to which data are accessible only to those authorized. The system protects data from unauthorized disclosure.

Encrypt data at rest and in transit. Implement strict role-based access controls and the principle of least privilege. Anonymize or pseudonymize training data. Consider secure multi-party computation for sensitive applications.

### Integrity

The degree to which the system prevents unauthorized modification of data or functions. The system ensures data and system accuracy and completeness.

Use hashing and digital signatures to verify data and model artifacts have not been tampered with. Maintain an immutable audit trail. Validate inputs to prevent injection attacks, including adversarial inputs designed to manipulate model behavior.

### Non-repudiation

The degree to which actions can be proven to have taken place. The system provides evidence for transactions that cannot be denied later.

Implement secure logging and auditing for all significant actions and decisions. Use digital signatures to ensure actions can be attributed to a specific entity or user. For AI systems making consequential decisions, non-repudiation is essential for regulatory compliance and dispute resolution.

### Accountability

The degree to which actions can be traced to the entity that bears responsibility. The system enables assignment of responsibility.

Maintain clear ownership of models and system components. Establish audit trails that log system decisions, data sources, and user interactions. Define clear lines of responsibility for every component and every decision the system produces.

### Authenticity

The degree to which the identity of a subject or resource can be proved. The system verifies that entities are genuine.

Implement strong authentication mechanisms including multi-factor authentication for system access. Verify the provenance of training data and model packages to prevent tampering or supply chain attacks. For AI systems, authenticity extends beyond user identity to include data authenticity and model authenticity.

### Intervenability (AI-Specific)

The degree to which the system allows human intervention in its operation. Authorized humans can oversee and interrupt the system's functions.

Design human-in-the-loop processes for critical decisions. Provide clear interfaces for oversight, intervention, and manual override. Ensure the system can be paused or stopped safely at any point without data loss or inconsistent state. This characteristic is a direct requirement of the EU AI Act for high-risk AI systems.

Original implementation tip: Accountability and intervenability work together and fail together. An AI system that logs every decision (accountability) but provides no mechanism for a human to intervene when they see a problematic pattern in those logs (intervenability) creates awareness without agency. A system that allows human override (intervenability) but does not log who overrode which decision and why (accountability) creates agency without traceability. Design these two characteristics as a pair. The logging system should inform the intervention interface, and every intervention should be logged with the rationale for the override.

## Domain 7: Maintainability

Five characteristics define whether the system can be changed, fixed, and improved over time.

### Modularity

The degree to which the system is composed of discrete components where changes to one have minimal impact on others.

Architect as loosely coupled components: separate data processing, training, and inference services. Use well-defined interfaces between components. This enables updating one component without risking the stability of others.

### Reusability

The degree to which components can be used in more than one system or context.

Develop and package model components, feature pipelines, and datasets as reusable assets. Create shared libraries with clear documentation. Use containerization to make components portable across environments.

### Analyzability

The degree to which the impact of an intended change can be assessed. The system can be diagnosed for deficiencies or failure causes.

Implement comprehensive logging and monitoring for all components. Use distributed tracing to follow requests through the system. Maintain detailed documentation of architecture and data lineage so that when something fails, the cause can be traced efficiently.

### Modifiability

The degree to which the system can be changed without introducing defects or degrading quality.

Write clean, well-documented code. Avoid tight coupling. Use version control for all artifacts including code, data, and models. Implement feature toggles for controlled rollout of changes.

### Testability

The degree to which test criteria can be established and tests can be performed effectively.

Design systems with testing in mind from the start. Create isolated test environments. Automate unit, integration, and regression tests for both models and code. Monitor test coverage and maintain it as the system evolves.

Original implementation tip: Analyzability is the maintainability characteristic that determines how quickly you can respond to AI incidents, and it is the one most organizations invest in only after their first major incident. When a model starts producing unexpected outputs in production, the first question is always "what changed?" Without comprehensive data lineage, model versioning, and input/output logging, answering that question can take days. With them, it takes minutes. Build analyzability into your system before you need it. The cost of implementing logging, tracing, and lineage tracking during initial development is a fraction of the cost of retrofitting them during a production incident investigation.

## Domain 8: Portability

Three characteristics define how the system moves between environments.

### Installability

The degree to which the system can be successfully deployed and removed in a specified environment.

Package using standard tools like Docker containers, Helm charts, or pip packages. Automate deployment scripts. Provide clear installation documentation and dependency lists. AI systems often have complex dependency chains that make installation significantly harder than traditional software.

### Replaceability

The degree to which the system can substitute for another product in the same environment.

Adopt standard interfaces and protocols to avoid vendor lock-in. Ensure data and models are exportable in standard formats. Document APIs and dependencies thoroughly so that replacement is feasible when needed.

### Adaptability

The degree to which the system can be adapted for different environments without custom modification.

Use configuration files to manage environment-specific parameters. Avoid hard-coding values. Design the system to be environment-agnostic, sourcing configuration externally. Follow the Twelve-Factor App methodology for environment-independent design.

Original implementation tip: Portability characteristics collectively determine your vendor lock-in risk. I worked with an organization that deployed an AI system on a single cloud provider's proprietary ML platform, using provider-specific data formats, training APIs, and deployment tools. When they needed to move to a multi-cloud architecture for resilience, the migration cost exceeded the original development cost. The system scored zero on all three portability characteristics. Before committing to a platform, evaluate your system against these three characteristics. If you score poorly on all three, you have accepted significant lock-in risk. Make that acceptance explicit and documented rather than accidental and discovered later.

## Domain 9: Quality in Use

This is the most expansive domain, containing 14 characteristics that evaluate the system's quality from the perspective of actual use by real users in real contexts. Several of these characteristics are specific to AI and address societal and ethical dimensions that have no equivalent in traditional software quality models.

### Effectiveness

The degree to which accurate and complete results are achieved. The system helps users achieve specified goals with precision and comprehensiveness.

Define clear metrics for accuracy and completeness aligned to user goals, not just model performance metrics. Implement robust validation and user acceptance testing. Track task success rates to measure real-world effectiveness.

### Efficiency

The degree to which results are achieved with appropriate resources. The system minimizes user time, effort, and resource expenditure.

Measure time-on-task and steps to completion for key user journeys. Optimize workflows and system performance to reduce user effort. Efficiency in the quality-in-use sense is about the user's experience, not the system's computational efficiency.

### Usefulness

The degree to which the system is capable of achieving specified goals. The system serves a practical purpose and delivers tangible benefits.

Conduct task analysis and user research to ensure the system solves a real problem. Prioritize features that deliver the highest value. Continuously validate usefulness through feedback and usage metrics.

### Trust

The degree to which users have confidence that the system will behave as intended. The system is reliable, dependable, and predictable.

Design for reliability, transparency, and fairness. Provide explanations for outputs and allow human oversight. Be clear about system limitations to build appropriate trust, not excessive trust that leads to overreliance.

### Pleasure

The degree to which users obtain satisfaction from using the system. The experience is positive and enjoyable.

Apply user-centered design principles. Conduct usability testing to identify and eliminate frustration points. Reward user actions positively through clear feedback and smooth interactions.

### Comfort

The degree to which users are satisfied with physical comfort during interaction. The system minimizes physical strain such as eye fatigue or repetitive stress.

Design interfaces that adhere to ergonomic principles. Ensure readable text, comfortable interaction patterns, and support for assistive technologies.

### Transparency in Use

The degree to which users can understand the system's functions, decisions, and outputs in practice. The system provides clarity on operations and reasoning.

This extends the usability transparency characteristic into actual use contexts. Implement Explainable AI techniques suitable for end-users, such as natural language explanations rather than technical feature importance scores. Ensure explanations are actionable and understandable by non-technical users.

### Economic Risk Mitigation

The degree to which the system mitigates potential economic risks. The system protects users and stakeholders from financial loss and wasted investment.

Conduct cost-benefit and ROI analyses. Implement safeguards against errors that could lead to significant financial loss. Ensure transparency in automated financial decisions. This characteristic is particularly relevant for AI systems that make or influence financial decisions at scale.

### Health and Safety Risk Mitigation

The degree to which the system mitigates health and safety risks. The system prioritizes human well-being above all else.

Perform rigorous risk assessments such as Failure Mode and Effects Analysis for safety-critical applications. Implement fail-safes, human-in-the-loop controls, and continuous monitoring for hazardous situations. Comply with relevant safety standards such as IEC 61508 for functional safety.

### Environment Risk Mitigation

The degree to which the system mitigates environmental risks. The system minimizes negative environmental impacts.

Monitor and optimize computational efficiency and energy footprint. Prefer cloud regions powered by renewable energy. Consider the full lifecycle environmental impact including training, inference, and data storage.

### Societal and Ethical Risk Mitigation

The degree to which the system mitigates societal and ethical risks. The system avoids causing harm, promotes fairness, and upholds ethical principles.

Establish an AI Ethics board and guidelines. Proactively test for and mitigate biases. Ensure fairness, accountability, and transparency throughout the AI lifecycle. Conduct impact assessments for high-risk applications.

### Context Completeness

The degree to which the system can achieve goals in all specified contexts of use. The system functions effectively across all intended situations, environments, and user profiles.

Identify and test all specified contexts during development. Use diverse datasets that represent all intended environments and user groups. Monitor for context drift in production where the system encounters situations outside its training distribution.

### Flexibility

The degree to which the system can achieve goals in contexts beyond those initially specified. The system adapts to unanticipated situations.

Design with modular and adaptable architectures. Allow configuration and customization. Use techniques like transfer learning to enable adaptation to new contexts without full redevelopment.

Original implementation tip: The quality-in-use characteristics that organizations most consistently neglect are the four risk mitigation characteristics: economic, health and safety, environmental, and societal/ethical. These characteristics feel like "someone else's job." The AI development team focuses on effectiveness and efficiency. The compliance team handles economic risk. The safety team handles health and safety. Nobody owns environmental or societal risk mitigation as a quality characteristic of the AI system itself. But ISO 25059 places these squarely within the quality model. They are quality attributes of the system, not external governance requirements. Treat them as you would any other quality characteristic: define metrics, set targets, test against them, and monitor in production. The system's quality is incomplete without them.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/watermark-free-gemini_generated_image_fn28r6fn28r6fn28.png?w=1024)

## Using This Framework for Risk Identification

The 49 characteristics in ISO/IEC 25059 serve a dual purpose. They define what quality looks like for an AI system, and they identify where risk lives when quality is absent.

Every characteristic that scores poorly represents a risk. Low functional correctness means the system produces errors. Low robustness means the system is vulnerable to adversarial inputs. Low transparency means decisions cannot be explained to regulators. Low intervenability means humans cannot stop the system when it malfunctions.

Map this directly to your AI risk assessment. For each characteristic, ask three questions. How does our system perform against this characteristic? What is the consequence if this characteristic fails? What controls do we have in place to maintain this characteristic over time?

The answers populate your risk register with specific, measurable, and controllable risks rather than generic categories like "model risk" or "AI quality issues."

Original implementation tip: I use the 49 characteristics as a structured interview guide during AI risk assessments. For each production AI system, I walk through every characteristic with the development team, operations team, and business owner. Each conversation takes about two hours. The output is a quality profile for the system with a red/amber/green rating for each characteristic. Red-rated characteristics map directly to risks in the risk register. Amber-rated characteristics map to watch items with monitoring requirements. This approach produces a more comprehensive risk identification than any brainstorming-based approach I have used, because the characteristics serve as prompts that surface risks the team would not think of on their own. "How does your system handle invalid inputs?" (robustness) and "Can a user override the system's decision?" (intervenability) consistently uncover risks that open-ended risk identification sessions miss.

## Key References and Standards

This quality framework draws from and aligns with the following authoritative sources.

ISO/IEC 25059:2023 for the primary AI system quality model that defines the 49 characteristics described in this post.

ISO/IEC 25010:2023 for the foundational software product and system quality model that ISO 25059 extends.

ISO/IEC/IEEE 29148 for requirements engineering practices that support functional suitability assessment.

ISO 9241-210 for human-centered design principles that support usability assessment.

NIST AI RMF (AI 100-1) for the AI risk management framework that connects quality characteristics to risk management.

NIST AI 100-2 for adversarial machine learning guidance that supports robustness assessment.

EU AI Act (Regulation 2024/1689) for regulatory requirements that make several quality characteristics legally mandatory for high-risk AI systems.

W3C WCAG 2.1 for web accessibility guidelines that support the accessibility characteristic.

ISO/IEC 27001 for information security management standards that support security characteristics.

IEC 61508 for functional safety standards relevant to health and safety risk mitigation.

## The Difference Between Accurate and Good

Organizations that evaluate their AI systems only on accuracy metrics will continue deploying systems that work in testing and fail in production, that produce correct outputs nobody trusts, that cannot be maintained by anyone other than their original developer, and that create regulatory exposure because they cannot explain their decisions. High accuracy on a test set is one characteristic out of 49. Treating it as the only one that matters is how quality failures happen.

Organizations that evaluate their AI systems across the full quality model will build systems that are not only accurate but explainable, robust, maintainable, fair, controllable, and recoverable. They will catch quality gaps during development rather than discovering them through production incidents. They will satisfy regulatory requirements because the quality characteristics regulators care about, transparency, accountability, intervenability, fairness, were designed in from the start.

An AI system that scores well on one quality characteristic and poorly on 48 others is not a quality system. It is a model with infrastructure around it. The infrastructure is where quality lives or dies.

Which of the 49 characteristics is weakest in your most important AI system? If you cannot answer that question, start with the structured interview approach described above. Two hours will reveal gaps that months of operation have hidden.
