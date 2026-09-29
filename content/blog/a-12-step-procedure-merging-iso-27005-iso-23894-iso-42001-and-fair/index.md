---
title: "A 12-Step Procedure Merging ISO 27005, ISO 23894, ISO 42001, and FAIR"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-risk-assessments"
  - "ai-risk-management"
  - "ai-risks"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "iso-27005"
  - "risk-management"
  - "technology"
---

How to Build an AI Risk Assessment That Actually Protects Your Organization

Most AI risk assessments fail before they produce a single useful number.

I've reviewed dozens of them across financial services, healthcare, and technology companies. The pattern is almost always the same. A team fills out a qualitative risk matrix, assigns some red-yellow-green ratings, files the document, and moves on. Six months later, an AI system produces biased outputs in production, a regulator asks pointed questions, and nobody can trace a single risk decision back to a defensible analysis.

The problem is not a lack of frameworks. ISO 27005, ISO 23894, ISO 42001, and FAIR all offer strong foundations. The problem is that nobody shows risk managers how to combine them into one coherent, repeatable procedure that produces numbers leadership can actually use to make decisions.

This post walks through a 12-step AI risk assessment procedure that merges structured risk process, AI-specific principles, governance requirements, and quantitative rigor. Every step includes the practical guidance I wish someone had given me when I first tried to assess AI risks using nothing but a spreadsheet and good intentions.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/zurich_aerial.jpg?w=1024)

## Why You Need a Unified AI Risk Framework

Traditional cybersecurity risk assessment covers infrastructure, access controls, and data protection. That is necessary but insufficient for AI systems. AI introduces risks that sit outside the usual threat catalogs. Biased outputs, model drift, adversarial manipulation, opacity of decision-making, hallucinated content. These require their own vocabulary and their own assessment methods.

The procedure described here draws from four sources. ISO 27005 provides the structured risk management process. ISO 23894 adds AI-specific risk principles. ISO 42001 brings AI governance, ethics, and lifecycle management. FAIR supplies the quantitative engine that converts vague risk language into dollar ranges executives understand.

Original implementation tip: Do not try to run this procedure in isolation from your existing enterprise risk management program. The single most common failure I've seen is a standalone AI risk register that never connects to the organization's financial, operational, or compliance risk reporting. From day one, map your AI risk outputs to the same reporting structure your CFO and CRO already read. If they report in annualized loss exposure, you report in annualized loss exposure.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/image.png?w=1024)

## Stage 1: Scoping and Context Setting

### Step 1: Define the Project Objectives

Start with the business reason the AI system exists. This sounds obvious. But watch how many teams skip past it and jump straight to technical vulnerability scanning.

Define why the system is being built or deployed, who owns accountability across its lifecycle, and what business processes depend on it. Quantify the goals in measurable terms. Revenue growth targets, efficiency gains, cost reductions, time savings. "Reduce loan approval time by 40% without increasing default risk" is a useful objective. "Use AI to improve lending" is not.

Then define your protection requirements across three dimensions. For confidentiality, specify what intellectual property, personal data, or business information must stay protected. For integrity, state what data, models, and processes must remain accurate. For availability, define the uptime and performance levels required to support operations.

Layer on responsible AI commitments. What accuracy thresholds must the model meet? What are the acceptable performance ranges? What fairness and non-discrimination principles apply? When must a human step in?

Finally, record every compliance and legal obligation. Regulatory frameworks, sector rules, contractual commitments, and geographic considerations all belong here. A credit scoring model deployed across EU and US markets faces GDPR, the EU AI Act, the Equal Credit Opportunity Act, and likely several internal policies.

Original implementation tip: Write your risk appetite statement before you assess a single risk. I spent two years running assessments without a defined appetite, and every evaluation ended in the same argument. "Is this risk acceptable?" became a political debate instead of a comparison against a documented threshold. Set a clear number. "Residual annualized loss exposure must remain below $100k" gives your team a finish line. Without it, you are running a race with no tape.

### Step 2: Identify Assets

Build a complete inventory of everything that supports the AI system. This is not just a list of servers. It is a map of the entire ecosystem from development through deployment.

Start with data assets. Distinguish between raw data and the specific training, validation, and test datasets derived from it. Then catalog model artifacts, including weights, embeddings, hyperparameters, and versioned configurations. Document the supporting infrastructure, from cloud services and GPU environments to orchestration pipelines and monitoring tools.

Do not overlook human assets. Developers, data annotators, ML engineers, auditors, and business owners all play roles in the system's lifecycle. Map them. Then identify all integration points, including APIs, dashboards, and downstream systems that consume model outputs.

Critically, assess external dependencies. Third-party datasets, open-source libraries, pre-trained models, credit bureau APIs, and partner services all introduce risk that sits outside your direct control.

Original implementation tip: Create a dependency map, not just an asset list. A flat inventory tells you what exists. A dependency map tells you what breaks when something fails. I once worked with a team that listed "scikit-learn" as an asset but never documented that three other internal systems consumed the same model's output via an unmonitored API. When the model degraded, the blast radius was four times what anyone expected. Draw the connections. Every one of them is a potential failure path.

## Stage 2: Threat and Vulnerability Discovery

### Step 3: Find Vulnerabilities

Examine four domains systematically. Data sources, model components, supporting architecture, and organizational processes.

For data, assess incompleteness, hidden bias, lack of sanitization, and susceptibility to poisoning. For model artifacts, look for opacity that limits explainability, exposure to evasion or inversion attacks, and reliance on unpatched open-source components. For infrastructure, check for exposed interfaces, weak access controls, and misconfigured environments. For processes, evaluate monitoring gaps, incident response readiness, and unclear ownership.

Tie every vulnerability directly to a specific asset from your inventory. "Training dataset underrepresents minority groups" connects to the training data asset. "Inference API lacks rate limiting" connects to the API asset. "Model ownership unclear between data science and IT operations" connects to the human assets and governance structure.

Original implementation tip: Most teams find technical vulnerabilities and miss organizational ones. In my experience, the highest-impact AI failures trace back to process gaps, not code flaws. Unclear ownership between data science and IT operations is the single most dangerous vulnerability I encounter. Neither team thinks they own the model in production. When drift happens, both teams point at each other. Assign one owner with documented accountability before you deploy anything.

### Step 4: Map Threats

Apply a structured taxonomy to identify who might exploit these vulnerabilities. MITRE ATLAS provides an AI-specific framework that covers adversarial machine learning techniques.

Categorize threat agents. Malicious outsiders include hackers, competitors, and organized cybercriminals. Malicious insiders exploit privileged access. Accidental insiders create exposure through negligence or misconfiguration. System failures include hardware malfunctions, software defects, and infrastructure outages.

For AI contexts, enumerate specific threat actions. Data poisoning during training. Adversarial inputs during inference. Model inversion or extraction that exposes sensitive training data. Prompt injection in generative systems. Output hallucinations that undermine accuracy. Misuse of generative capabilities for fraud.

Every threat must connect to at least one vulnerability you already documented. "External attacker sends adversarial queries" connects to "API lacks input validation." "Regulator investigates bias" connects to "training data underrepresents minority groups." If a threat has no corresponding vulnerability, either you missed a vulnerability or the threat is not relevant to this system.

Original implementation tip: Do not treat threat mapping as a one-time exercise. Threat landscapes for AI systems shift faster than for traditional IT. New adversarial techniques appear in academic papers months before they show up in the wild. Subscribe to MITRE ATLAS updates, follow ML security research, and refresh your threat catalog at least twice a year. I made the mistake of treating my first AI threat map as static. Within eight months, three new attack vectors had emerged that were not in my original catalog. Two of them were directly applicable to our deployed system.

## Stage 3: Scenario Construction

### Step 5: Build Scenarios

Combine actor, vulnerability, and asset into a single causal chain. Use a consistent structure. "Actor exploits vulnerability in asset, leading to impact."

Example: "An external attacker compromises the integrity of the credit scoring model by exploiting weak API input validation to generate unfairly high credit scores for fraudulent applicants."

Apply bow-tie analysis to each scenario. On the left side, define initiating events, precursors, and preconditions. What must be true for the attacker to succeed? On the right side, define consequences and impacts across confidentiality, integrity, availability, fairness, compliance, and business objectives. Identify existing controls on both sides, distinguishing prevention from mitigation.

Document the assumptions behind each scenario. Attacker capability, tool availability, detection reliability. Specify the triggers: system failure, intrusion attempt, data drift, human error. State the preconditions: access to training data, absence of monitoring, unpatched components.

Express consequences in business language. Financial loss, operational disruption, reputational damage, regulatory sanction, customer trust erosion. Tie each consequence back to the assets and objectives defined earlier.

Original implementation tip: Write scenarios in language that a non-technical board member can read and understand in thirty seconds. I learned this the hard way. My first set of scenarios included phrases like "adversarial perturbation of feature vectors in the latent space." The CISO nodded politely. The CFO checked her phone. The board moved on. Rewrite: "An attacker tricks the model into approving bad loans by feeding it manipulated applications." Same risk. Ten times the impact in the room.

## Stage 4: Quantitative Analysis

### Step 6: Estimate Impact

Identify loss categories covering primary and secondary effects. Primary losses include productivity disruption, detection and response costs, system replacement costs, and fines. Secondary losses capture reputation damage, customer trust erosion, competitive disadvantage, and long-term churn.

For AI systems, add specific categories. Discrimination claims from biased decisions. Fraudulent transactions from adversarial manipulation. Compliance breaches under emerging AI regulation. Loss of confidence in automated decision-making.

Quantify each loss using ranges, not point estimates. "Fraudulent loans cost $50k to $250k" is useful. "Fraudulent loans are a high impact risk" is not. Draw from historical incident data, industry breach reports, and calibrated expert judgment. When consulting experts, ask for ranges they are 90% confident contain the true value.

Original implementation tip: Calibrate your experts before you use their estimates. Most people are overconfident in narrow ranges and underconfident in wide ones. Run a quick calibration exercise. Ask your subject matter experts ten factual questions with numeric answers and have them provide 90% confidence intervals. If fewer than nine of their intervals contain the correct answer, they need calibration training. Uncalibrated estimates will sabotage your entire Monte Carlo simulation. I ran a full risk model once with uncalibrated inputs and the output was off by a factor of three compared to actual incident costs the following year.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/image-1.png?w=715)

### Step 7: Estimate Frequency

Break frequency into two components. Threat event frequency measures how often actors attempt to exploit a vulnerability. Vulnerability success probability measures how often those attempts succeed given current controls.

Gather threat event frequency from threat intelligence reports, organizational logs, industry attack databases, and internal incident history. Distinguish between automated probing, deliberate targeted attacks, and accidental internal events like misconfiguration or data drift.

Estimate vulnerability success probability by evaluating defensive controls. Patching practices, monitoring coverage, model robustness against adversarial input, incident response maturity. Use calibrated expert judgment when empirical data is thin.

Multiply them to get loss event frequency. Express as a range per year. "Adversarial inputs attempted 2 to 10 times per year, success probability 10% to 20%, loss event frequency 0.2 to 2 successful events per year."

Original implementation tip: Separate malicious frequency from accidental frequency. Data drift is not an attack. It is a certainty. Models degrade over time as the world changes. Treat drift-related scenarios with near-certain frequency estimates, not as low-probability events. I've seen teams assign "unlikely" ratings to model drift scenarios. Every single model drifts. The question is when and how badly, not whether it happens.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/image-2.png?w=687)

### Step 8: Model Risk

Run Monte Carlo simulations combining your frequency and impact distributions. Use at least 100,000 iterations for statistical stability. Each iteration produces a plausible annual loss outcome.

From the output, compute three key metrics. Expected loss (the average), which represents the long-term financial burden. Value at risk at the 90th or 95th percentile, which shows severe but plausible outcomes. Tail risk beyond those percentiles, which reveals catastrophic exposure.

Express everything in monetary terms. "Median annualized loss exposure is $125k. There is a 15% chance losses exceed $300k in a given year. Maximum simulated event is $550k." This language connects directly to business decisions.

Original implementation tip: Do not present simulation results without also presenting the input assumptions. Every Monte Carlo output is only as good as its inputs. When you brief leadership, show them the frequency ranges and loss ranges you fed in, the data sources behind those ranges, and the confidence level of your expert estimates. I once delivered a clean risk report with precise-looking numbers. The first question from the CRO was "Where did these numbers come from?" I did not have the input documentation ready. The entire presentation lost credibility. Now I include an assumptions appendix with every simulation output.

\[Suggested image: A sample Monte Carlo output distribution showing expected loss, VaR at 90th percentile, and tail risk\]

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/image-3.png?w=689)

## Stage 5: Decision and Action

### Step 9: Evaluate Risks

Compare simulation outputs to your defined risk appetite. If your median annualized loss exposure of $125k exceeds your $100k threshold, the risk is unacceptable. Period.

But financial tolerance is only half the evaluation. Assess each scenario against responsible AI principles. A bias-driven compliance risk may fall within financial tolerance but remain completely unacceptable on ethical and legal grounds. Evaluate fairness of outcomes, clarity of decision-making, and adherence to regulatory requirements with equal weight.

Rank scenarios by expected exposure, tail risk potential, and strategic relevance. Use risk matrices only as communication aids, never as decision tools. Identify which risks need mitigation, transfer, acceptance, or escalation to the board.

Estimate return on investment for each treatment option by comparing the AI system's anticipated benefits against expected losses and mitigation costs.

Original implementation tip: Never let a low-frequency bias scenario survive evaluation just because its expected annual cost is small. Regulators do not think in annualized loss exposure. They think in headlines. A single discriminatory outcome that affects a protected class can trigger enforcement action, class action lawsuits, and reputational damage that no Monte Carlo simulation adequately captures. Flag bias risks separately and route them to your ethics and compliance governance body regardless of their financial ranking.

### Step 10: Treat Risks

For each prioritized scenario, define specific treatment measures. Technical controls like web application firewalls and adversarial input detection. AI-specific treatments like bias audits, explainability tools, model cards, and access restrictions. Process improvements like retraining schedules and red-teaming programs.

Consider risk transfer through cybersecurity insurance or contractual arrangements. Evaluate avoidance by limiting AI scope or halting deployment in high-risk applications. Accept residual risk only when it falls within documented tolerance and only with governance sign-off.

Calculate ROI for each treatment. A $40k investment in adversarial input detection that reduces attack frequency by 80% and cuts annualized loss exposure from $125k to $25k delivers a return of 300%. That math gets budget approved.

Original implementation tip: Bundle your treatments and present them as a single investment package with a combined ROI. When I presented treatments individually, each one competed against unrelated budget priorities and half of them got cut. When I bundled adversarial defenses, bias auditing, and monitoring into one "AI risk control package" with a combined ROI of 300%, the CFO approved the entire package in one meeting. Frame treatment spending as insurance against quantified exposure, not as a cost center.

### Step 11: Integrate Decisions

Feed AI risk results into existing enterprise risk management structures. Use the same reporting language, the same dashboards, and the same meeting cadence as financial, cyber, and operational risk.

Connect residual risk levels to forward-looking business decisions. Product launch approvals, geographic expansion, pricing strategies, warranty terms, insurance negotiations. Leadership cannot make informed decisions about AI deployment if risk data lives in an isolated report that nobody reads.

Ensure escalation paths are clear. When residual exposure exceeds tolerance, the information must reach executive and board level through documented channels.

Original implementation tip: Present AI risk alongside other enterprise risks in the same board report. Do not create a separate AI risk briefing that competes for calendar time. The moment AI risk becomes "that other report," it loses executive attention. Integrate it. One page in the existing risk summary. Annualized loss exposure in the same column as cyber risk and fraud risk. That is how AI risk gets treated as a real business concern rather than a theoretical exercise.

## Stage 6: Continuous Monitoring

### Step 12: Monitor and Iterate

Establish continuous monitoring across technical, organizational, and process domains. Track model drift, emerging adversarial techniques, bias reappearance in outputs, and infrastructure changes. Build dashboards with automated alerts that trigger review when indicators exceed defined thresholds.

Recalibrate frequency and impact estimates quarterly. Use the latest operational data, incident records, and threat intelligence. Run Monte Carlo simulations again with updated inputs.

Red-team your AI systems on an ongoing basis. Simulate adversarial behavior, challenge existing controls, and find vulnerabilities before attackers do.

Update the risk register every quarter with residual risk levels, treatment outcomes, and any new scenarios identified through monitoring or incident review. Feed insights back into Step 1 to close the loop.

Original implementation tip: Automate your drift detection and bias monitoring from the start. Manual quarterly reviews miss problems that emerge between review cycles. I worked with a team that relied on quarterly manual checks. The model drifted significantly in month two, produced biased outputs for six weeks before anyone noticed, and generated three customer complaints that reached the regulator. An automated monitoring pipeline with real-time alerts would have caught the drift within days. The cost of automated monitoring was less than 10% of the cost of the resulting regulatory response.

## Cross-Cutting Tips That Apply Across Every Stage

These four principles apply throughout the entire procedure, regardless of which step you are executing.

Original implementation tip on documentation: Record every decision, assumption, and data source as you go. Do not plan to "document it later." Later never comes. I have inherited risk assessments where the simulation outputs existed but the input assumptions were lost. The entire assessment had to be re-run from scratch because nobody could defend the original numbers. Use a decision log that captures date, participants, inputs, outputs, and rationale for every significant choice.

Original implementation tip on role clarity: Assign a single accountable owner for each step using a RACI framework. In practice, the most common dysfunction is a step where everyone is "consulted" and nobody is "accountable." Vulnerability identification is the step where this breaks down most often. Data scientists think it is a security team responsibility. The security team thinks it is a data science responsibility. Neither team does it. Name one person. Make them answer for the output.

Original implementation tip on calibration consistency: Use the same calibration method for all expert estimates throughout the assessment. If your impact experts are calibrated using one method and your frequency experts use a different method (or none at all), your Monte Carlo inputs will carry inconsistent levels of confidence. Standardize your calibration training and apply it to every subject matter expert who contributes ranges to the model.

Original implementation tip on governance integration: Treat the completed risk assessment as a living document with a defined review cycle, not as a project deliverable that gets filed. Assign a review owner, set calendar reminders for quarterly updates, and tie the review cycle to your organization's existing governance meeting schedule. Risk assessments that are not reviewed within 90 days of completion begin to decay in accuracy and relevance.

## References and Standards

The procedure described in this post draws from and aligns with the following standards and frameworks:

ISO/IEC 27005:2022, Information security, cybersecurity and privacy protection, providing guidance on managing information security risks.

ISO/IEC 23894:2023, Information technology, Artificial intelligence, providing guidance on risk management specific to AI systems.

ISO/IEC 42001:2023, Information technology, Artificial intelligence, setting requirements for establishing, implementing, maintaining, and improving an AI management system.

The FAIR (Factor Analysis of Information Risk) framework, providing a quantitative model for information risk analysis.

MITRE ATLAS (Adversarial Threat Landscape for AI Systems), offering a knowledge base of adversarial tactics and techniques against AI.

EU AI Act (Regulation 2024/1689), establishing harmonized rules on artificial intelligence.

NIST AI Risk Management Framework (AI 100-1), providing guidance for managing risks associated with AI systems.

NIST SP 800-30 Rev. 1, Guide for Conducting Risk Assessments, offering a foundational risk assessment methodology.

Equal Credit Opportunity Act (ECOA) and related fair lending regulations, governing non-discrimination in credit decisions.

GDPR (Regulation 2016/679), governing the protection of personal data in the European Union.

## The Difference Between Compliance Theater and Real Risk Management

Organizations that treat this procedure as a compliance artifact will fill out templates, generate reports that collect dust, and discover their actual risk exposure only after an incident forces them to confront it. They will spend more on incident response and regulatory fines than they would have spent on proper assessment and treatment. Their AI systems will carry hidden risks that leadership never sees until the damage is done.

Organizations that treat this procedure as a living operational tool will know their annualized loss exposure in dollar terms, defend their deployment decisions with traceable analysis, and catch model drift and emerging threats before they become incidents. They will integrate AI risk into the same governance structures that manage every other business risk, and their leadership will make AI investment decisions with the same rigor they apply to financial and operational planning.

The risk assessment procedure is not a document you complete. It is a discipline you practice.

What step in your current AI risk assessment process would benefit most from the quantitative rigor described here? That is probably the step where your biggest blind spot lives.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and globally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
