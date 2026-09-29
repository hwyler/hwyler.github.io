---
title: "The 45 AI Threat Vectors That Your Security Team Probably Isn't Tracking"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-risk-management"
  - "ai-risks"
  - "ai-threat-model"
  - "artificial-intelligence"
  - "cybersecurity"
  - "fair"
  - "hernan-huwyler"
  - "iso-23894"
  - "iso-31000"
  - "mitre-atlas"
  - "security"
  - "stride-threat-model"
  - "technology"
  - "theat-modeling"
---

A Practitioner's Field Guide

Most AI threat models are incomplete. Not slightly incomplete. Fundamentally incomplete.

Last year I reviewed the threat model for a financial services company deploying a credit decisioning AI. Their security team had identified seven threat vectors. Seven. They covered the obvious ones: data breaches, unauthorized access, denial of service. They missed 38 others, including 15 that were specific to AI systems and had no equivalent in their traditional IT threat catalog.

Three months after deployment, the model started producing subtly biased outputs. Not because of an external attack. Because a data scientist on the team had inadvertently introduced a feature engineering flaw that created a proxy variable for a protected characteristic. It was a negligence threat, an internal one, and it was not on anyone's radar because the threat model only considered adversarial external actors.

This pattern repeats across almost every organization I work with. Security teams build threat models based on their experience with traditional systems. They focus on external attackers, malicious intent, and system-level exploits. They miss the internal negligence threats that cause the majority of real-world AI failures. They miss model-specific attack vectors that have no parallel in conventional cybersecurity. They miss the human and organizational threats that create the conditions for technical failures.

This post catalogs 45 distinct AI threat vectors organized across a two-dimensional taxonomy: intent (adversarial versus negligent) and target category (data, model, system, and human). Each vector includes a clear explanation, practical context, and implementation guidance. Use this as a working reference to audit the completeness of your own AI threat models.

## Why Traditional Threat Models Fail for AI

Traditional threat modeling frameworks like STRIDE, PASTA, and even MITRE ATT&CK were designed for conventional information systems. They handle network attacks, authentication bypasses, privilege escalation, and data exfiltration well. They were not designed for systems where the "logic" is learned from data rather than written in code, where the attack surface includes the training pipeline itself, and where some of the most damaging threats come from well-intentioned internal teams making honest mistakes.

AI systems introduce three categories of threat that traditional frameworks handle poorly.

First, the model itself is an attack surface. Traditional systems have deterministic logic. If you protect the infrastructure and the data, the system behaves as designed. AI models are different. An attacker can manipulate the model's behavior by carefully crafting inputs, without ever breaching the perimeter or accessing the infrastructure. They can extract sensitive training data by querying the model's API. They can clone the model's functionality through systematic probing. None of these attacks require the kind of infrastructure compromise that traditional threat models focus on.

Second, the training pipeline is a persistent vulnerability. Traditional systems are vulnerable during operation. AI systems are vulnerable during development. Poisoned training data, biased labels, flawed feature engineering, and compromised pre-trained models all introduce vulnerabilities before the system ever reaches production. By the time the model is deployed, the damage is already embedded in its weights.

Third, negligence threats cause more cumulative damage than adversarial threats. In traditional cybersecurity, the adversary is the primary concern. In AI, the internal team building and operating the system creates more risk through oversight, insufficient testing, poor documentation, and inadequate monitoring than external attackers do through deliberate exploitation. A threat model that only considers malicious actors misses the majority of the threat landscape.

Original implementation tip: When I first expanded an organization's AI threat model beyond traditional categories, the security team pushed back hard. "We already cover insider threats," they said. They did, but their insider threat model focused on malicious insiders who steal data or sabotage systems. It did not cover the data scientist who chooses features without considering proxy discrimination, the ML engineer who skips robustness testing under deadline pressure, or the architect who fails to build monitoring into the deployment pipeline. These are not insider "threats" in the traditional security sense. They are negligence risks that require fundamentally different controls. Treat them as separate categories in your threat model, not as subcategories of "insider threat."

## The Taxonomy Structure

This threat taxonomy organizes 45 vectors across two dimensions.

The first dimension is intent. Adversarial threats involve deliberate, intentional actions designed to compromise the AI system. Negligent threats involve unintentional actions or omissions that create vulnerabilities or cause harm. This distinction matters because adversarial and negligent threats require different controls. You defend against adversaries with detection, deterrence, and response. You defend against negligence with process, training, governance, and automation.

The second dimension is agent. External agents operate outside the organization's boundary, including hackers, competitors, nation-state actors, and third-party vendors. Internal agents operate within the organization, including developers, data scientists, architects, operators, and end users.

Within each combination of intent and agent, threats target one of four categories: data (the information the system processes and learns from), model (the learned representations, algorithms, and parameters), system (the infrastructure, APIs, and operational environment), and human (the people who build, operate, and interact with the system).

The result is a comprehensive matrix that surfaces threats most organizations overlook because they fall outside the traditional "external attacker targeting our infrastructure" frame.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/minimal-workspace-scene.png?w=1024)

## Adversarial External Threats: The Ones You Expect

This quadrant contains the threats most security teams already think about, plus several AI-specific vectors they likely do not.

### Data Threats from External Adversaries

Two vectors target the data layer from outside the organization.

Data exfiltration occurs when attackers extract sensitive data from the AI system, either during training or inference. This differs from traditional data theft because the AI model itself can leak data. An attacker who gains access to model outputs, gradients, or confidence scores can sometimes reconstruct training data without ever accessing the database directly. The model becomes an unintentional data disclosure channel.

Data poisoning occurs when attackers introduce malicious or corrupted data into the training dataset. This is uniquely dangerous because the corruption happens before the model is deployed. If an attacker can influence any data source that feeds into the training pipeline, whether through compromised public datasets, manipulated web scraping sources, or tampered third-party data feeds, they can embed biases or backdoors that persist through every subsequent version of the model until the poisoned data is identified and removed.

Data poisoning is the adversarial data threat I worry about most because it is the hardest to detect and the longest-lasting in impact. Traditional data validation checks look for obvious anomalies: missing values, out-of-range entries, format errors. Poisoned data is designed to look normal. The individual data points are plausible. The corruption is statistical, not syntactic. Defending against it requires comparing training data distributions across time windows to detect subtle shifts, validating training data provenance to verify that sources have not been compromised, and testing model behavior on held-out validation sets from trusted sources. If your training data comes from any source you do not fully control, you have exposure to this vector.

### Model Threats from External Adversaries

Six vectors target the model itself, and these are the threats most traditional security teams have the least experience with.

Deception involves crafting inputs designed to make the AI model produce incorrect predictions or classifications. Think of carefully modified images that cause a computer vision system to misclassify objects, or subtly altered text inputs that cause a natural language model to produce wrong outputs. The modifications are often imperceptible to humans but effective against the model.

Evasion is deception's cousin, focused specifically on bypassing detection or classification mechanisms. An attacker modifies malicious inputs to evade an AI-based security system, such as altering malware signatures to bypass AI-powered threat detection or modifying fraudulent transactions to avoid AI-based fraud scoring.

Exploitation targets weaknesses in the AI system's implementation rather than the model's learned behavior. Insecure APIs, poor input validation, missing authentication, and misconfigured endpoints are the entry points. This vector bridges traditional cybersecurity and AI-specific risk because the vulnerabilities are conventional but the assets being targeted (models, training pipelines, inference endpoints) are AI-specific.

Inversion attacks reverse-engineer the model to infer sensitive information about training data. By carefully analyzing the model's outputs across many queries, an attacker can deduce characteristics of the data the model was trained on. For models trained on medical records, financial data, or personal information, this vector directly threatens privacy even if the underlying database is perfectly secured.

Membership inference is related but distinct. Instead of reconstructing training data, the attacker determines whether a specific known data point was part of the training set. "Was this person's medical record used to train your diagnostic model?" is a question that, if answerable through the model's API, creates privacy and compliance exposure regardless of whether the attacker can reconstruct the full record.

Oracle attacks (also called model extraction or model stealing) involve an attacker querying the model extensively to understand its decision boundaries, then building a replica model that reproduces the original's behavior without access to the training data. The attacker essentially steals the intellectual property embedded in the model through its public-facing API.

Transfer learning attacks exploit vulnerabilities in pre-trained models or the transfer learning process itself. Many organizations build their AI systems on top of pre-trained foundation models. If the foundation model contains embedded vulnerabilities, biases, or backdoors, every downstream model inherits them. This vector is growing in importance as more organizations build on third-party foundation models they did not train and cannot fully audit.

Of these six model-level threats, oracle attacks and transfer learning attacks are the two most underestimated. Oracle attacks are underestimated because organizations assume their model's logic is protected by keeping the code proprietary. It is not. If the model is accessible through an API, its behavior can be replicated through systematic querying. Rate limiting helps but does not eliminate the risk. Transfer learning attacks are underestimated because organizations treat pre-trained foundation models as trusted components without verifying what is in them. I worked with a team that fine-tuned a publicly available language model for customer service automation. Nobody audited the base model for embedded biases or vulnerabilities. The assumption was "it's from a reputable provider, so it's safe." That assumption is not supportable. If you use pre-trained models, document your trust assumptions about those models explicitly, test for bias and adversarial vulnerability in the fine-tuned model, and include the base model in your threat surface.

### System Threats from External Adversaries

Eight vectors target the infrastructure and operational environment.

Advanced persistent threats involve state actors or organized crime groups using sophisticated tools to compromise the AI system over an extended period. These are the most resource-intensive attacks and typically target high-value AI systems in critical infrastructure, financial services, or defense applications.

API-based attacks exploit vulnerabilities in the APIs used to interact with the AI system. This includes injecting malicious data through API endpoints, exploiting authentication weaknesses, or abusing API rate limits to conduct model extraction.

Denial of service overwhelms the AI system with excessive traffic or resource demands. AI systems can be particularly vulnerable because inference workloads on complex models consume significant computational resources, making resource exhaustion attacks more efficient than against simpler services.

Model freezing attacks target the AI system's update mechanism, preventing the model from receiving updates. A model that cannot be updated remains vulnerable to known threats and cannot adapt to data drift, effectively turning a dynamic system into a static one.

Model parameter poisoning introduces malicious updates or perturbations directly into the model's parameters (weights, biases) rather than through training data. This vector is particularly relevant for federated learning systems where multiple parties contribute model updates.

Poorly designed APIs represent a threat vector that straddles adversarial and negligent categories. While the design flaw is internal, external attackers exploit it. Insecure API design that exposes model internals, lacks input validation, or provides excessive information in error messages creates the conditions for multiple other attacks.

Side-channel attacks exploit non-functional characteristics of the AI system, such as timing differences in inference responses, power consumption patterns during computation, or electromagnetic emissions, to extract information about the model or its data. These attacks do not target the model's logic directly but extract information through observable physical or computational characteristics.

Supply chain compromise involves attackers tampering with hardware, software components, or third-party services in the AI system's supply chain. Compromised ML libraries, poisoned pre-trained models distributed through public repositories, or tampered GPU firmware all fall into this category.

Supply chain compromise is the system-level external threat I spent the most time helping organizations address last year. The AI supply chain is broader and less controlled than most organizations realize. A typical ML pipeline might include open-source libraries (PyTorch, TensorFlow, scikit-learn), pre-trained models from public repositories (Hugging Face, GitHub), data from third-party providers, cloud services for training and inference, and container images from public registries. Each component is a potential entry point. The most practical defense is maintaining a software bill of materials (SBOM) for your AI systems that includes not just code dependencies but also model provenance, training data sources, and infrastructure components. When a vulnerability is discovered in any component, the SBOM tells you immediately which AI systems are affected. Without it, you are guessing.

### Human Threats from External Adversaries

One vector targets the human element from outside.

Social engineering involves attackers manipulating developers, data scientists, or users into revealing sensitive information or interacting with the AI system in ways that compromise security. AI teams are often targeted because they have access to valuable IP (models, training data, feature engineering pipelines) and may not have received the same security awareness training as traditional IT staff. A data scientist who shares a model architecture diagram on a conference poster may not realize they have disclosed information useful for a model extraction attack.

## Adversarial Internal Threats: The Ones You Underestimate

This quadrant contains only two vectors, but both are high-impact.

### Human Threats from Internal Adversaries

Data sabotage occurs when insiders intentionally alter or destroy data used for training or inference. Unlike external data poisoning, an insider has legitimate access to data systems and can make changes that appear routine. A disgruntled data engineer who subtly modifies preprocessing scripts or alters label distributions can compromise model performance in ways that are extremely difficult to trace.

Subversion involves authorized developers or contractors intentionally sabotaging, exfiltrating, or manipulating the AI system. This goes beyond data sabotage to include embedding backdoors in model code, exfiltrating trained model weights for competitors, or introducing vulnerabilities that can later be exploited. The insider's authorized access makes traditional perimeter defenses irrelevant.

Internal adversarial threats against AI systems are harder to detect than their equivalents in traditional IT for one specific reason: the normal behavior of an AI developer already includes activities that would be flagged as suspicious in other contexts. A data scientist routinely downloads large datasets, modifies data processing logic, changes model parameters, and deploys updated models. These are their job functions. Distinguishing between a legitimate model update and a sabotage event requires understanding what the model should be doing, not just what the developer is doing. The most effective control I have found is mandatory peer review for all changes to training data, feature engineering code, and model parameters before they reach production. Not automated testing, though that helps too. Human review by a second qualified person who can assess whether the change makes sense in context. This catches both intentional sabotage and unintentional errors.

## Negligent External Threats: Your Vendors and Dependencies

This quadrant covers unintentional risks introduced by parties outside your organization.

### Human Threats from External Negligence

Supply chain negligence occurs when third-party vendors introduce vulnerabilities through insecure libraries, dependencies, or tools used during AI system development, deployment, or maintenance. Unlike supply chain compromise (which is intentional), this vector reflects genuine negligence: a vendor fails to patch a library, releases an update with a security flaw, or provides tooling that does not meet security standards. The impact on your AI system is the same whether the vulnerability was introduced deliberately or carelessly.

Third-party data risk arises when organizations rely on external data sources that may be of poor quality, biased, or inadvertently altered. The third party is not acting maliciously. They simply do not maintain the data quality standards your model requires. Training on degraded external data produces degraded model performance, and the organization consuming the data may not detect the quality decline until outputs start failing.

### System Threats from External Negligence

Outdated dependencies represent the use of unsupported software libraries in AI systems that introduce known, exploitable vulnerabilities. This is technically a negligence issue, an external provider stops maintaining a library, but the security impact is the same as an adversarial exploit because attackers actively scan for systems using deprecated dependencies.

Third-party data risk is the negligent external threat I encounter most frequently in practice. Organizations build models on external data feeds and assume the data quality will remain stable. It does not. I worked with a company whose fraud detection model degraded over four months because a third-party transaction data provider changed their data formatting without notification. The change was minor, a modification to how categorical fields were encoded, but it silently corrupted the feature engineering pipeline. The model's accuracy dropped from 91% to 78% before anyone noticed. The fix was straightforward but the damage was done. For every external data dependency, establish a data quality SLA with the provider that specifies format, completeness, timeliness, and quality metrics. Monitor incoming data against those SLAs automatically. When a deviation occurs, alert before the data enters your training pipeline, not after your model degrades.

## Negligent Internal Threats: Where Most AI Failures Actually Originate

This is the largest quadrant in the taxonomy, containing 24 of the 45 vectors. That distribution is not an accident. It reflects reality. The majority of AI failures in production stem from internal negligence, not external attacks.

### Data Threats from Internal Negligence

Two vectors target the data layer through internal oversight.

Inaccurate data labeling occurs when developers fail to properly label training data during preparation. Labels are the ground truth the model learns from. If a medical imaging dataset contains mislabeled scans, the model learns to associate the wrong visual patterns with the wrong diagnoses. Unlike external data poisoning, this is not malicious. It is the predictable result of insufficient quality assurance in the annotation process, often driven by time pressure, undertrained annotators, or ambiguous labeling guidelines.

Bias in data occurs when data scientists or developers incorporate biased data during training, producing discriminatory or unfair outputs. This can result from historical bias embedded in the data itself (past lending decisions that reflected discriminatory practices), selection bias in how data was collected (underrepresenting certain populations), or measurement bias in how variables were recorded. The developers are not trying to create discriminatory outcomes. They are training on data that reflects existing inequities.

Bias in data is the negligent data threat with the highest regulatory and reputational impact. It is also the one where I see the most dangerous misconception. Teams believe that removing protected characteristics like race or gender from the training data eliminates bias. It does not. Other variables in the dataset frequently serve as proxies for protected characteristics. Zip code correlates with race. Job title correlates with gender. Part-time employment status correlates with caregiving responsibilities. Removing the protected characteristic while leaving the proxy variables in the feature set gives the appearance of fairness while producing the same discriminatory outcomes. The effective control is to test model outputs for disparate impact across protected groups, regardless of whether protected characteristics appear in the input features. Test the outputs, not the inputs.

### Model Threats from Internal Negligence

Five vectors target the model through internal oversight.

Data and model drift occurs when developers fail to account for changes in data distribution or underlying concepts over time. A model trained on data from 2022 may not perform well on data from 2025 if customer behavior, market conditions, or the relationships between variables have shifted. This is not a one-time risk. It is an ongoing degradation that accelerates the longer a model operates without retraining or recalibration.

Feature engineering flaws result from unintentionally introducing vulnerabilities through poor feature selection. Selecting features that are easily manipulated by adversaries, including features that leak future information (data leakage), or failing to consider how feature distributions might shift in production all fall into this category.

Overfitting occurs when developers create models that fit too closely to the training data, learning noise and idiosyncrasies rather than genuine patterns. An overfit model shows excellent performance in testing and poor performance in production. From a security perspective, an overfit model is also more predictable to an adversary who understands its training data, making it easier to craft adversarial inputs.

Overfitting to noise is a specific variant where the model learns from irrelevant data rather than meaningful signal. The model performs well on training metrics but produces unreliable results in real-world deployment because it has memorized artifacts in the training data rather than learning the underlying relationship.

Unexplainability results when developers create AI systems too complex and opaque to understand or explain. This is a threat vector because opacity prevents detection of errors, biases, and vulnerabilities. A model whose decisions cannot be explained cannot be audited, cannot be debugged when it fails, and cannot satisfy regulatory requirements for explainability. Opacity does not cause harm directly, but it creates the conditions under which every other threat vector becomes harder to detect and address.

Data and model drift is the negligent model threat that causes the most cumulative financial damage because it is slow, silent, and continuous. I have never worked with an organization that detected drift proactively on their first AI deployment. They always detected it reactively, after business outcomes degraded enough for someone to notice. The detection lag ranged from three weeks to nine months depending on how closely business stakeholders monitored the model's downstream effects. The fix is statistical monitoring of input feature distributions and output prediction distributions, compared against baseline distributions from the training period. When statistical tests detect a significant shift, trigger an alert. Do not wait for business outcome metrics to degrade, because by then the model has been making suboptimal decisions for weeks or months. Population Stability Index (PSI) is a good starting metric. Monitor it weekly at minimum for production models.

### Human Threats from Internal Negligence

This is the richest subcategory in the entire taxonomy, containing 12 vectors. Each represents a different way that well-intentioned people create AI risk through oversight, insufficient skill, or organizational failure.

Inadequate documentation occurs when teams provide insufficient documentation for AI models, data sources, and decision-making processes. Without documentation, models cannot be maintained by anyone other than their original developer, security reviews cannot assess the system's design assumptions, and regulatory compliance cannot be demonstrated.

Inadequate monitoring results from failing to build proper monitoring mechanisms to detect anomalies, adversarial activity, or model degradation in real time. An unmonitored model is a model whose failures go undetected until they manifest as business losses, customer complaints, or regulatory actions.

Inadequate maintenance occurs when teams fail to regularly update and maintain AI models, leaving them vulnerable to known attacks, data drift, and exploits as the system ages. Models, like all software, require ongoing maintenance. Unlike traditional software, model maintenance includes retraining, recalibration, and feature re-evaluation in addition to patching.

Inadequate testing results from failing to sufficiently test and validate models before deployment. This includes insufficient unit testing of data pipelines, absence of adversarial robustness testing, incomplete validation against held-out datasets, and failure to test for bias and fairness.

Inadequate training affects end-users and operators who receive insufficient instruction on how to interact with or manage AI systems. A model that is technically sound can still produce harmful outcomes if the humans using it do not understand its limitations, do not know when to override its recommendations, or cannot recognize when its outputs are unreliable.

Insecure design results from architects or developers failing to build secure AI systems from the start. This includes objective functions susceptible to manipulation, model architectures that leak information through their outputs, and deployment configurations that expose internal model details.

Insider threat (unintentional) covers authorized team members who inadvertently cause harm. A developer who accidentally pushes a model trained on test data to production. A data engineer who modifies a preprocessing script that breaks feature normalization. An operations team member who changes a configuration parameter without understanding its downstream effects.

Insufficient access control results from poorly managed access permissions that allow unauthorized access to models, data, or systems. This is a process failure, not a technology failure. The tools to enforce access control exist. The organization simply has not implemented them with sufficient rigor for AI-specific assets.

Lack of governance occurs when organizations fail to establish proper governance frameworks for AI development and deployment. Without governance, teams operate independently, security practices are inconsistent, accountability is undefined, and risk accumulates without visibility.

Over-reliance on AI results from decision-makers depending on AI outputs without sufficient human oversight or fail-safes. When users treat AI predictions as infallible, they stop applying the human judgment that catches model errors. This vector is particularly dangerous in high-stakes domains like healthcare, criminal justice, and financial services.

Unclear AI accountability occurs when nobody is clearly defined as accountable for AI-related decisions, model performance, or security. When accountability is unclear, risks go unmanaged because everyone assumes someone else is responsible.

Of these 12 human negligence vectors, inadequate monitoring and unclear accountability are the two that create the most cascading damage. They amplify every other threat in the taxonomy. An adversarial attack against an inadequately monitored system succeeds for longer. Data drift in a system with no accountable owner goes unaddressed for months. Bias in a model that nobody monitors against fairness metrics persists indefinitely. If you can only address two human negligence vectors immediately, address these two. Assign a named individual, not a team, as accountable for each production AI system. Then build monitoring that runs at the same speed as the model's decision-making. Everything else becomes more manageable once you have visibility and ownership in place.

### System Threats from Internal Negligence

Five vectors target the system infrastructure through internal oversight.

Inadequate incident response results from failing to develop or implement effective response plans for AI-specific incidents. AI incidents differ from traditional IT incidents. A model producing biased outputs is not a "system down" event. It does not trigger the same alerts. It requires different diagnostic procedures and different remediation steps. If your incident response playbook does not include AI-specific scenarios, your response will be improvised when it matters most.

Inadequate logging results from insufficient logging and monitoring infrastructure that makes it difficult to detect, investigate, or respond to incidents. If you cannot see what the model received as input, what it produced as output, and how its behavior has changed over time, you cannot diagnose problems or provide evidence for regulatory investigations.

Insecure data storage results from failing to implement secure storage for AI-specific data assets. Training data, model weights, feature engineering code, and hyperparameter configurations all contain sensitive intellectual property and potentially personal data. Storing them with the same (or lesser) security controls as general-purpose data creates exposure.

Insufficient redundancy results from failing to build AI systems with adequate fail-safes. A single point of failure in the model serving infrastructure, the data pipeline, or the monitoring system can take down the entire AI capability. AI systems often have complex dependency chains that create hidden single points of failure.

Misconfiguration results from incorrectly configuring security settings, environments, or system components. Cloud environment misconfigurations, exposed model endpoints, overly permissive IAM roles, and unencrypted data storage are the most common variants.

Inadequate incident response for AI systems is the system-level negligence threat I have spent the most time remediating. Traditional incident response plans categorize incidents by severity and system type, but they almost never include AI-specific incident categories. What do you do when a model starts producing outputs that are statistically different from its validation period behavior? What do you do when a fairness audit reveals disparate impact? What do you do when you discover that training data was contaminated three months ago and every model version since then is potentially compromised? These are AI incidents that require AI-specific response procedures. Build an AI incident response appendix for your existing plan. Include at minimum: model rollback procedures, retraining triggers, bias investigation protocols, adversarial attack containment steps, and stakeholder notification procedures. Then tabletop exercise these scenarios. The first time you run through an AI incident scenario, you will discover gaps in your response capability that are fixable before a real incident occurs.

## Cross-Cutting Implementation Tips

These apply across all four quadrants of the threat taxonomy.

Assess your taxonomy coverage quarterly. AI threat vectors evolve as attack research advances, new model architectures emerge, and regulatory requirements expand. A taxonomy that was comprehensive six months ago may have gaps today. Assign someone to monitor AI security research (MITRE ATLAS updates, conference proceedings from NeurIPS and USENIX Security, regulatory guidance from NIST and the EU AI Office) and flag new vectors that should be added.

Original implementation tip: When reviewing your taxonomy coverage, do not just ask "have any new threat vectors emerged?" Also ask "have any of our existing vectors changed in severity or likelihood?" The relative importance of threat vectors shifts as your AI systems mature. Early in deployment, development negligence threats (inadequate testing, insecure design) are most relevant because the system is new and untested. Six months into production, operational negligence threats (inadequate monitoring, data drift, inadequate maintenance) become dominant. Twelve months in, adversarial threats increase as your AI system becomes a known, valuable target. Reassess priority rankings at each quarterly review.

Balance adversarial and negligence controls in your budget. Security teams naturally gravitate toward adversarial controls because they are more dramatic and more familiar. Adversarial robustness testing, penetration testing, red-teaming: these feel like "real" security work. Process controls, governance frameworks, training programs, and documentation standards feel like bureaucracy. In practice, the negligence controls prevent more incidents.

Original implementation tip: I track a simple metric with every organization I advise: the ratio of AI incidents caused by adversarial action versus negligence. Across 14 organizations over three years, the ratio has consistently been approximately 15% adversarial and 85% negligence. Yet budget allocation for adversarial controls versus negligence controls is typically inverted: 60-70% on adversarial defenses and 30-40% on process and governance. Reallocate to match the actual threat distribution. This does not mean reducing adversarial defenses. It means increasing investment in monitoring, documentation, testing processes, training, and governance until the budget reflects where incidents actually originate.

Map each vector to specific assets and controls. A threat vector without a corresponding asset mapping tells you what could happen but not where it could happen to you. A threat vector without a corresponding control tells you what to worry about but not what to do. For each vector in this taxonomy that applies to your AI systems, document three things: which specific assets are exposed, which controls currently mitigate the vector, and what residual exposure remains.

The most effective way I have found to operationalize a threat taxonomy is to create a traceability matrix with four columns: threat vector, exposed assets, current controls, and residual risk rating. Populate this matrix for every production AI system. When a new asset is deployed, add rows. When a new threat vector is identified, add rows. When a control is implemented or modified, update the current controls column and reassess residual risk. This matrix becomes the working document for your AI security program. It tells you at any point what threats you have addressed and what gaps remain. Without it, the taxonomy is an intellectual exercise. With it, the taxonomy drives action.

## Key References and Standards

This threat taxonomy draws from and aligns with the following authoritative frameworks.

MITRE ATLAS (Adversarial Threat Landscape for Artificial Intelligence Systems) provides the primary reference taxonomy for AI-specific adversarial threats.

NIST AI RMF (AI 100-1) provides the risk management framework for identifying and addressing AI threats across the lifecycle.

ISO/IEC 27005:2022 provides the information security risk management process for integrating AI threats into enterprise risk assessment.

ISO/IEC 23894:2023 provides AI-specific risk management guidance including threat identification.

ISO/IEC 42001:2023 provides AI management system requirements for governance of the threat landscape.

OWASP Machine Learning Security Top 10 provides a practitioner-focused list of common ML security threats.

EU AI Act (Regulation 2024/1689) establishes regulatory requirements that make several of these threat vectors compliance-relevant.

NIST SP 800-30 Rev. 1 provides guidance on threat identification and risk assessment methodology.

ENISA Threat Landscape for AI provides European regulatory perspective on AI-specific threats.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/modern-office-meeting-with-colorful-glass-panes.png?w=1024)

## Using This Taxonomy to Find Your Gaps

Organizations that treat this taxonomy as a reference list will read it, nod, and return to their existing threat models unchanged. They will continue to overweight adversarial external threats because those threats are familiar and dramatic. They will continue to underweight internal negligence threats because those threats feel mundane and uncomfortable to discuss. When an AI failure occurs, and it will, they will discover that the vector was sitting in a taxonomy they read but never operationalized.

Organizations that treat this taxonomy as an audit tool will do something different. They will take each of their production AI systems and map every applicable threat vector to the specific assets, existing controls, and residual risk for that system. They will discover gaps, mostly in the negligent internal quadrant, and they will prioritize closing them. They will update their incident response plans to include AI-specific scenarios. They will build monitoring that catches negligence-driven failures before they reach customers. They will assign accountability for each production model to a named individual who cannot hide behind a team name.

The threat your AI system faces tomorrow is almost certainly already in this taxonomy. The question is whether you have mapped it to your assets, built controls for it, and assigned someone to watch for it.

Which quadrant of this taxonomy has the least coverage in your current AI threat model? For most organizations, the answer is negligent internal. That is where your biggest gap probably lives.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and globally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
