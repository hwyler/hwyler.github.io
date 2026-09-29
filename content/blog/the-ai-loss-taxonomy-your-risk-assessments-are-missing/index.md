---
title: "The AI Loss Taxonomy Your Risk Assessments Are Missing"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-models"
  - "ai-projects"
  - "ai-risk-assessment"
  - "ai-risk-management"
  - "ai-threat-assessments"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "iso-23894"
  - "iso-31000"
  - "technology"
---

### Incident Types and Direct Loss Categories That Define Real Exposure for AI Projects

Here is a question that reveals whether your AI risk program is mature or performative: Can you name the specific types of losses your AI systems could produce?

Not vague categories like "financial impact" or "reputational damage." Specific, measurable loss types with clear boundaries between them. The difference between a regulatory fine and a legal compensation payment. The difference between algorithm remediation costs and data regeneration costs. The difference between customer churn and business disruption.

I asked this question to the risk committee of a healthcare AI company two years ago. The room went quiet. They had a risk register with 20 AI risks, each rated on a five-point scale for likelihood and impact. But when I asked "what kind of impact?" nobody could decompose their generic "high impact" ratings into the specific loss types that would actually appear on a financial statement or in a regulatory action.

That gap matters. You cannot quantify what you cannot classify. And you cannot prioritize controls, calculate return on investment, or purchase appropriate insurance if you cannot distinguish between the types of losses your AI systems might generate.

This post provides two complementary taxonomies. The first catalogs 37 distinct AI-related incident types across eight categories, each classified by whether it creates internal losses (relevant to risk assessments) or external losses (relevant to impact assessments) or both. The second catalogs 15 direct loss types across five domains that map to specific financial line items. Together, they give you the vocabulary and structure to make your AI risk assessments financially precise.

## Why Generic Loss Categories Fail

Most AI risk assessments use three to five impact categories: financial, operational, reputational, regulatory, and strategic. These categories are so broad that they obscure more than they reveal.

When a risk assessment says an AI system has "high financial impact," does that mean the organization will pay regulatory fines? Lose customers? Write off a failed project? Pay for emergency model remediation? All of these are "financial impact," but they involve different stakeholders, different timescales, different control strategies, and different insurance coverage. Lumping them together makes the risk assessment useless for decision-making.

The same problem applies to incident classification. "AI bias" is not a single incident type. It manifests as biased outputs, unequal performance across groups, unfair discrimination, and lack of diversity in development teams. Each manifestation has different causes, different controls, and different loss profiles. Treating them as one incident type produces controls that are too generic to be effective.

The solution is granularity. Not complexity for its own sake, but sufficient decomposition to enable specific, actionable analysis. The taxonomies in this post provide that granularity.

Original implementation tip: When I first introduced a granular loss taxonomy to a financial services client, their initial reaction was that it added unnecessary complexity. They were managing 15 AI risks with five impact categories and felt that was sufficient. I asked them to take their highest-rated risk, "model produces biased outputs," and trace it to specific financial consequences. They identified regulatory fines quickly. Then I asked about legal compensation payments to affected customers, algorithm remediation costs for retraining the model, control remediation costs for fixing governance gaps found during investigation, customer churn from affected populations, and reputation damage from media coverage. The total potential exposure across these six loss types was four times their original "high impact" estimate. Granularity did not add complexity. It revealed exposure they had been underestimating.

## Part 1: AI-Related Incident Types

The incident taxonomy organizes 37 distinct incident types across eight categories. Each incident is classified as producing internal losses (considered in risk assessments), external losses (considered in impact assessments), or both.

This distinction matters for assessment methodology. Internal losses affect the organization directly through operational disruption, remediation costs, and control failures. External losses affect individuals, communities, or society through harm, discrimination, or rights violations. Many incidents produce both, requiring assessment from both perspectives.

### Category 1: Cognitive Degradation

Three incident types address AI's impact on human cognitive and decisional capacity.

Addiction and digital wellness (external only) occurs when AI systems contribute to addictive behaviors and negative impacts on digital wellness. Recommendation algorithms that maximize engagement metrics can create patterns of compulsive use. AI-driven content curation that prioritizes emotional arousal over informational value degrades the quality of users' information environment. This is an external loss because the harm falls on users, not the organization, but regulatory attention to digital wellness is increasing, which creates secondary compliance exposure.

Loss of autonomy (internal and external) occurs when AI systems make decisions that diminish user control. This happens when automated decision-making replaces human judgment in contexts where individuals should retain meaningful choice. Internally, this manifests when employees lose the ability to exercise professional judgment because AI systems override their input. Externally, customers or citizens experience reduced agency in decisions affecting their lives, such as credit, employment, or healthcare.

Overreliance on AI (internal and external) occurs when users anthropomorphize, trust, or depend on AI systems beyond what the system's capabilities warrant. Internally, decision-makers who treat model outputs as infallible stop applying critical judgment. Externally, users develop inappropriate emotional or material dependencies on AI systems, or form expectations the system cannot meet.

Original implementation tip: Overreliance on AI is the cognitive degradation incident type that creates the most immediate organizational risk, and it is almost never included in AI risk assessments. I worked with a lending organization where loan officers had become so accustomed to following the AI's credit recommendations that they stopped reviewing the underlying data. When the model began producing anomalous scores due to a data pipeline issue, officers approved loans they would have questioned under manual review. The model was technically malfunctioning, but the actual failure was human. The loan officers had ceded their judgment to the system. The control is not technical. It is procedural: require documented human rationale for a sample of AI-supported decisions, and audit whether the rationale demonstrates independent judgment or simply restates the AI's recommendation.

### Category 2: Discrimination

Five incident types address unfair or unequal treatment produced by AI systems.

Bias in AI outputs (internal and external) occurs when models produce systematically biased predictions or recommendations. This is the broadest discrimination incident type and encompasses statistical bias embedded in model outputs that disadvantages specific groups.

Exposure to toxic content (external only) occurs when AI systems expose users to harmful, abusive, unsafe, or inappropriate content. Content recommendation systems, generative AI outputs, and AI-moderated platforms all carry this risk. The loss is borne by the affected users, but regulatory and reputational consequences flow back to the organization.

Lack of diversity in AI development (internal and external) occurs when homogeneous development teams build systems that reflect their own perspectives and blind spots. This is a root cause incident type. It does not produce harm directly but creates the conditions for bias, unfair discrimination, and unequal performance across groups.

Unequal performance across groups (internal and external) occurs when AI systems deliver different levels of accuracy, reliability, or quality for different user populations. A facial recognition system that works well for some skin tones and poorly for others. A speech recognition system that understands some accents and fails on others. The performance disparity itself is the incident, regardless of whether it results from intentional design or data limitations.

Unfair discrimination (internal and external) occurs when AI systems treat individuals or groups unfairly in consequential decisions. This goes beyond statistical bias in outputs to encompass the downstream effects: denied loans, rejected applications, misclassified individuals, or misrepresented groups.

Original implementation tip: The discrimination incident type that is hardest to detect is unequal performance across groups, because standard accuracy metrics can mask it completely. A model with 92% overall accuracy might have 97% accuracy for the majority population and 74% accuracy for a minority group. The aggregate metric looks fine. The disaggregated metrics reveal a serious problem. When I audit AI systems for discrimination risk, I require performance metrics disaggregated by every protected characteristic available in the data. If protected characteristics are not in the data, which is common, I require proxy analysis using correlated variables. The first time you disaggregate your model's performance metrics, you will almost certainly find disparities you did not know existed.

### Category 3: Disinformation Warfare

Three incident types address AI's role in the information environment.

Disinformation and influence at scale (internal and external) occurs when AI systems enable large-scale manipulation of public opinion. This includes using AI to generate convincing fake content, automate social media manipulation, or conduct targeted influence campaigns. Internally, organizations face risk when their AI tools are misused for this purpose. Externally, society bears the cost of degraded public discourse.

False or misleading information (internal and external) occurs when AI systems generate or spread incorrect or deceptive information. This includes hallucination in large language models, inaccurate summaries, fabricated citations, and confidently stated falsehoods. Unlike deliberate disinformation, this often results from model limitations rather than malicious intent, but the impact on users who rely on the information is the same.

Pollution of information ecosystem (external only) occurs when AI-generated misinformation accumulates at sufficient scale to undermine shared reality. Filter bubbles, echo chambers, and the displacement of human-created content by AI-generated content of unknown reliability all contribute to this systemic effect.

Original implementation tip: False or misleading information is the disinformation incident type with the most immediate organizational liability, particularly for companies deploying generative AI in customer-facing applications. I advised a professional services firm that deployed a generative AI assistant to help clients navigate regulatory requirements. Within the first month, the assistant fabricated a regulation that did not exist and cited it confidently to a client. The client made a business decision based on the fabricated guidance. The firm's liability exposure from that single incident exceeded the entire annual budget for their AI program. The control that would have prevented this is output verification: for any generative AI system providing factual information to external users, implement a verification layer that checks generated claims against an authoritative source before presenting them. This adds latency and cost. It also prevents lawsuits.

### Category 4: Economic Displacement

Nine incident types address AI's macroeconomic and organizational effects, making this the largest incident category.

Changes in employment patterns (internal and external) covers reduced quality of employment and increased exploitation of workers as AI reshapes job roles. Competitive dynamics (internal only) addresses the organizational risk from racing to deploy AI systems before they are safe, a pattern that increases the probability of releasing error-prone systems. Disruption of traditional industries (internal and external) covers economic instability when AI displaces established business models.

Economic and cultural devaluation of human effort (internal and external) occurs when AI-generated output reduces the perceived or actual value of human-created work. This affects pricing, employment, and professional identity across creative, analytical, and service industries.

Environmental harm (external only) covers the energy consumption, water usage, and carbon emissions from training and operating large AI systems. Governance failure (internal and external) occurs when regulatory frameworks cannot keep pace with AI development, creating gaps in oversight.

Increased inequality and decline in employment quality (internal and external) addresses the broader societal pattern of AI benefits accruing to capital owners while labor bears displacement costs. Job displacement and economic disruption (internal and external) covers direct job losses and industry disruption. Power centralization and unfair distribution of benefits (external only) addresses the concentration of AI capabilities and their economic benefits among a small number of organizations.

Original implementation tip: Of the nine economic displacement incident types, governance failure is the one that creates the most direct and immediate organizational risk, because it applies to every organization deploying AI, regardless of industry or scale. Governance failure is not just about regulators failing to keep pace with technology. It is also about your organization failing to build internal governance that compensates for regulatory gaps. I worked with a technology company that was deploying AI across 14 use cases with no centralized governance body, no standardized risk assessment process, and no consistent documentation requirements. Each team made independent decisions about model deployment, monitoring, and retirement. When the EU AI Act requirements became concrete, the company had no way to determine which of their systems qualified as high-risk, what documentation existed for each system, or who was accountable for compliance. They spent 11 months and significant resources building governance retroactively that would have cost a fraction to build proactively. If your organization deploys AI and does not have a governance framework, this is your highest-priority incident type to address. Not because governance failure is the most dramatic risk, but because its absence makes every other risk harder to manage.

### Category 5: Exploitation

Two incident types address deliberate misuse of AI for harm.

AI weaponization (external only) covers the use of AI systems to develop cyber weapons or tools capable of mass harm. This is primarily a societal risk but creates organizational exposure when an organization's AI tools or models are repurposed for weaponization by third parties.

Fraud, scams, and targeted manipulation (external only) covers the use of AI to conduct fraud, run scams, or manipulate individuals through personalized deception. AI-generated deepfake voices used in CEO fraud, AI-crafted phishing messages personalized from scraped data, and AI-assisted identity theft all fall here.

### Category 6: Malicious Actors and Misinformation

Three incident types address AI-enabled attacks and synthetic media.

AI-powered phishing and social engineering (external only) covers the use of AI to create sophisticated, personalized phishing attacks and social engineering campaigns. AI enables attackers to generate convincing communications at scale, personalized to each target using publicly available information.

Use of AI for social engineering (external only) is a related but broader category covering all uses of AI to manipulate human behavior for unauthorized access or information disclosure.

Deepfakes and AI-generated content (external only) covers AI-generated synthetic media used to spread misinformation, impersonate individuals, or manipulate public opinion. This includes fake video, audio, images, and text that are increasingly difficult to distinguish from authentic content.

### Category 7: Privacy Infringement

Five incident types address AI's impact on personal data and privacy.

AI system security vulnerabilities and attacks (external only) covers exploitation of vulnerabilities in AI systems leading to unauthorized access, data breaches, or system manipulation causing unsafe outputs.

Collection of personal data (external only) covers AI systems that collect personal data without adequate consent. This includes passive data collection through AI-powered sensors, inference of personal characteristics from behavioral data, and collection that exceeds stated purposes.

Compromise of privacy (external only) occurs when AI systems memorize and leak sensitive personal data, or infer private information about individuals without consent. This is distinct from data breaches because the privacy compromise occurs through the model's normal operation, not through a security failure.

Data breaches and unauthorized access (external only) covers traditional security incidents applied to AI contexts, including unauthorized access to training data, model weights, or inference logs containing personal information.

Surveillance and monitoring (external only) covers AI-powered surveillance that erodes trust and creates unease among individuals and communities. Facial recognition in public spaces, behavioral monitoring in workplaces, and predictive policing systems all carry this risk.

Original implementation tip: Compromise of privacy is the privacy incident type that is most specific to AI and least covered by traditional privacy controls. A large language model can memorize and reproduce fragments of its training data, including personal information, in its outputs. This is not a data breach in the traditional sense. No attacker exploited a vulnerability. The model simply learned its training data too well and reproduces it when prompted in certain ways. Traditional privacy controls focus on securing data at rest and in transit. They do not address data that is encoded in model weights. The control for this risk is differential privacy during training (adding noise to prevent memorization of individual data points) combined with output filtering that detects and blocks personal information in model responses. If your AI system was trained on data containing personal information, this incident type applies to you.

### Category 8: Value Misalignment

Seven incident types address fundamental alignment between AI systems and human values.

AI possessing dangerous capabilities (external only) covers AI systems that develop or access capabilities increasing their potential for mass harm. This is an emerging and contested risk category, but it is increasingly relevant as AI systems become more capable.

AI pursuing its own goals in conflict with human goals (external only) covers AI systems acting contrary to the intentions of their designers or users. This ranges from reward hacking in reinforcement learning systems (achieving the stated objective through unintended means) to more speculative scenarios of advanced AI systems developing emergent goals.

AI system reliability and maintainability (internal and external) covers systems that are not reliable or maintainable, leading to errors and failures with significant consequences. This is particularly critical in applications requiring moral reasoning or operating in safety-critical environments.

Lack of accountability (internal and external) occurs when AI decision-making processes have no clear accountable party, leading to situations where harmful outcomes cannot be attributed, corrected, or prevented from recurring.

Lack of capability or robustness (internal and external) covers AI systems that fail under varying conditions. A model that works in testing but fails in production, a system that degrades when input distributions shift, or an application that produces errors under edge cases all represent this incident type.

Lack of explainability (internal and external) occurs when AI systems cannot explain their decisions to stakeholders who need to understand them, whether those stakeholders are regulators, affected individuals, or internal decision-makers.

Lack of transparency or interpretability (internal and external) covers broader challenges in understanding AI decision-making processes, leading to difficulty enforcing compliance, holding actors accountable, and identifying errors.

Original implementation tip: The value misalignment incident type I find most practically relevant for organizations today, the one that is neither speculative nor distant, is lack of accountability. Every AI failure I have investigated has had an accountability gap at its root. Not the absence of a responsible person in an organizational chart, but the absence of a person who knew they were responsible, had the authority to act, and had the information needed to act in time. The control is deceptively simple: for every production AI system, publish an accountability card that names the individual accountable for model performance, the individual accountable for data quality, the individual accountable for compliance, and the individual accountable for incident response. Post these accountability cards where the operations team can see them. Update them when people change roles. Test them by calling the named individuals during a tabletop exercise and verifying they know they are accountable and know what to do.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/professional-man-at-modern-workspace.png?w=1024)

## Part 2: Direct Loss Types

The incident taxonomy tells you what can happen. The direct loss taxonomy tells you what it costs. These 15 loss types map to specific financial line items that appear in budgets, financial statements, and insurance claims. They give your risk quantification the precision needed for credible Monte Carlo simulation and ROI analysis.

Five domains organize the 15 loss types.

### Domain 1: Compliance Losses

Four loss types address the financial consequences of regulatory and legal exposure.

Regulatory fines cover penalties for violating AI regulations like the EU AI Act, privacy laws like GDPR, or sector-specific requirements. They also cover sanctions for data breaches, discriminatory outcomes, or copyright infringements produced by AI systems. These are typically the most visible AI losses because they are public, quantifiable, and reported.

Legal compensations cover settlement payments to affected parties for harm caused by AI malfunctions or decisions. This includes attorney fees and court costs for defending lawsuits from individuals or groups. Unlike regulatory fines, which are imposed by authorities, legal compensations arise from private litigation. They can be larger than fines and take longer to resolve.

Contractual credits cover service credits issued to customers when AI performance falls below guaranteed levels. Refunds and discounts applied for missed availability or accuracy commitments. These losses are often overlooked in risk assessments because they are managed by commercial teams, not risk teams, but they can be significant for organizations selling AI-powered services.

Legal response costs cover external legal counsel fees for investigating and responding to AI-related claims, as well as internal legal team costs for compliance reviews and regulatory correspondence. These costs are incurred regardless of whether the organization is ultimately found liable.

Control remediation covers costs to fix governance gaps identified in failed AI audits. This includes documentation, implementation, and certification expenses for new compliance controls and frameworks. This loss type often surprises organizations because it represents the cost of building governance they should have built proactively.

Original implementation tip: When estimating compliance losses for risk quantification, the most common error is using historical fine amounts as the basis for estimates. Historical data underestimates future exposure for two reasons. First, AI-specific regulations like the EU AI Act establish fine structures that far exceed previous penalties: up to 35 million euros or 7% of global annual turnover for certain violations. Second, regulatory enforcement of AI is in its early stages. The fines imposed in 2025 and 2026 will set precedents that do not yet exist in historical data. For AI compliance loss estimation, use the maximum penalty structures defined in applicable regulations as the upper bound of your range, not historical fine amounts. Your calibrated experts should estimate the probability of enforcement action and the likely penalty within the regulatory range, but the range itself should reflect the legal maximum, not past experience.

### Domain 2: IT/Technical Losses

Three loss types address the costs of technical remediation and infrastructure.

Data regeneration covers costs to rebuild training datasets when data becomes corrupted, poisoned, or drifted beyond usability. This includes expenses for new data collection, labeling, cleaning, and validation. Data regeneration is expensive because high-quality training data is the most time-consuming and labor-intensive component of AI development. Rebuilding a corrupted training dataset can take months and cost more than the original data preparation.

Algorithm remediation covers engineering costs to retrain models that produce biased or inaccurate predictions. This includes compute resources for retraining, testing expenses for validation, and the data science team time required to diagnose the root cause, design the fix, and verify the corrected model's performance. For complex models, remediation can require multiple retraining cycles.

Infrastructure overruns cover unexpected cloud computing and storage costs from inefficient AI resource usage. Emergency scaling expenses when systems face performance bottlenecks or capacity issues. AI workloads are computationally intensive and unpredictable. A model retraining job that runs longer than expected, a sudden spike in inference requests, or an unoptimized training pipeline can generate infrastructure costs that significantly exceed budget.

Original implementation tip: Algorithm remediation is the technical loss type most consistently underestimated in risk assessments. Teams estimate the compute cost of retraining but forget the human costs: the data science team time to diagnose the root cause (which can take weeks for complex model failures), the opportunity cost of pulling those data scientists off other projects, the testing and validation time for the remediated model, and the business cost of operating with a degraded model during the remediation period. When I help organizations estimate algorithm remediation costs, I use a formula that includes compute costs (typically the smallest component), data science team labor at fully loaded cost for the estimated remediation duration, lost productivity for the business processes that depend on the model during remediation, and any expedited procurement costs for additional compute resources or external expertise. The total is typically three to five times the compute cost alone.

### Domain 3: Operational Losses

Five loss types address the business impact of AI failures on operations.

Decision errors cover financial losses from incorrect AI-driven business decisions made at scale. This includes costs of resource misallocation in operations, investments, or strategic planning based on flawed AI recommendations. The defining characteristic of decision error losses is scale. An AI system making thousands of decisions per day can accumulate significant losses before the error pattern is detected.

Operational inefficiency covers manual intervention costs when staff must correct or override AI outputs. Lost productivity from rework and staff time diverted to address AI failures. This loss type captures the ongoing drag on organizational performance that occurs when an AI system works poorly but not badly enough to take offline.

Development waste covers write-offs of failed AI projects that never reach production deployment. Sunk costs in licenses, development efforts, and procurement that yield no value. Industry estimates suggest that between 60% and 85% of AI projects fail to reach production. Each failed project represents development waste that should be included in the organization's AI loss profile.

Business disruption covers revenue loss during downtime when AI-dependent processes stop functioning. Emergency replacement costs and lost transactions from service interruptions. This loss type is particularly relevant for organizations where AI systems sit in the critical path of revenue-generating processes.

Provider switching covers contract termination fees and cancellation penalties with current AI vendors. Migration costs, integration expenses, and negotiation time for new provider onboarding. This loss type is often triggered by other incidents, such as a vendor's quality declining, a security breach at the vendor, or a strategic decision to reduce vendor dependency, but the switching costs themselves represent a distinct financial impact.

Original implementation tip: Development waste is the operational loss type with the highest aggregate financial impact across most organizations I work with, and it is almost never included in AI risk assessments because it is treated as a project management issue rather than a risk management issue. When I aggregate the fully loaded costs of failed AI projects across an organization, including salaries, compute resources, license fees, and opportunity costs, the total frequently exceeds the organization's estimated exposure from all other AI risk scenarios combined. Include development waste in your loss taxonomy. Estimate it by multiplying the average fully loaded cost of an AI project by the historical failure rate. If you do not track your AI project failure rate, start. That number alone will change how your organization evaluates AI investments.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/urban-tech-fusion.png?w=1024)

### Domain 4: Revenue Losses

Two loss types address top-line financial impact.

Customer churn covers lost revenue from customers leaving after negative AI experiences or failures. Acquisition costs for replacing churned clients and margin erosion from retention efforts. This loss type has a compounding effect because the cost of acquiring a new customer is typically several times the cost of retaining an existing one.

Reputation damage covers brand value decline and crisis management costs following publicized AI incidents. Lost business opportunities and reduced market position from negative media coverage. This is the loss type most organizations acknowledge but least effectively quantify.

Original implementation tip: Reputation damage is the loss type I spent the most time helping organizations quantify, because it is the one where calibrated estimation is most valuable and most difficult. The approach that works is decomposition. Do not try to estimate "reputation damage" directly. Instead, estimate its measurable downstream effects. How many deals in the pipeline would be delayed or lost? (Estimate the pipeline value at risk.) How much would customer acquisition costs increase, and for how long? (Estimate the increment times the acquisition volume times the duration.) How much additional spending on PR and crisis management would be required? (Get a range from your communications team.) What revenue from existing contracts would be at risk of non-renewal? (Estimate the percentage of contracts with reputation-sensitive renewal decisions.) Add these components together. The total is more defensible than any direct estimate of "reputation damage" and more useful for risk quantification.

## Connecting Incidents to Losses: The Traceability Requirement

The two taxonomies in this post are designed to work together. Each incident type produces one or more direct loss types. Mapping these connections creates the traceability needed for effective risk quantification.

Take a concrete example. The incident type "bias in AI outputs" (Discrimination category, internal and external) can produce the following direct losses: regulatory fines (if the bias violates the EU AI Act or fair lending laws), legal compensations (if affected individuals or groups file lawsuits), algorithm remediation (costs to diagnose and fix the biased model), control remediation (costs to build governance controls that should have prevented the bias), customer churn (if the affected population includes customers who leave), and reputation damage (if the bias becomes public).

Each of these loss types has a different magnitude, different timing, and different probability. Regulatory fines are large but require a regulatory investigation, which may take months. Legal compensations can exceed fines but require plaintiffs to organize and file. Algorithm remediation costs are incurred immediately but are typically the smallest component. Reputation damage may or may not materialize depending on media attention.

Without this incident-to-loss mapping, your risk quantification combines everything into a single "impact" number that is neither precise enough for Monte Carlo simulation nor useful enough for control investment decisions.

Original implementation tip: Build an incident-to-loss mapping matrix for every AI system in your portfolio. Down the left side, list every applicable incident type from this taxonomy. Across the top, list every applicable direct loss type. In each cell, indicate whether the incident could produce that loss type, and if so, provide a rough magnitude range. This matrix becomes the foundation for your FAIR-based risk quantification. When you estimate the impact component of a risk scenario, you are not estimating a single number. You are estimating the aggregate of all applicable loss types for the specific incident. This granularity dramatically improves the quality of Monte Carlo simulation inputs and the credibility of the outputs.

## Internal Versus External: Why the Distinction Matters

The taxonomy classifies each incident type as producing internal losses, external losses, or both. This classification is not academic. It determines which assessment methodology applies.

Internal losses are costs borne by the organization. They are addressed through risk assessments that quantify exposure to the organization and inform control investment decisions. When you run a Monte Carlo simulation to calculate annualized loss exposure, you are modeling internal losses.

External losses are harms borne by individuals, communities, or society. They are addressed through impact assessments that evaluate potential harm to affected parties and inform responsible AI decisions. External losses may or may not create financial exposure for the organization (through fines, lawsuits, or reputation damage), but they matter independently because they represent real harm to real people.

Some incident types produce only internal losses. Competitive dynamics, for example, creates risk for the organization through unsafe AI deployment but does not directly harm external parties. Some produce only external losses. Surveillance and monitoring, for example, harms individuals and communities but may not create direct financial losses for the organization until it triggers regulatory action or public backlash.

Most incident types produce both. Bias in AI outputs, for example, creates internal losses through remediation costs and external losses through discriminatory harm to affected individuals.

Mature AI risk programs assess both dimensions for every applicable incident type. Immature programs assess only internal losses and are surprised when external harms generate regulatory, legal, or reputational consequences they did not anticipate.

Original implementation tip: The practical implication of the internal/external distinction is that you need two different assessment processes, and they should involve different people. Internal loss assessment is a financial exercise led by risk managers, using techniques like FAIR quantification and Monte Carlo simulation. External impact assessment is an ethical and societal exercise that should involve ethicists, affected community representatives, legal experts, and domain specialists, not just risk managers. I have seen organizations try to combine both assessments into a single process run by the risk team. The financial analysis crowds out the impact analysis every time. When a risk manager and an ethicist are in the same room, the conversation gravitates toward quantifiable financial exposure because that is what the risk manager knows how to discuss. Keep the assessments separate. Conduct them with different teams. Then combine the findings in a governance review where both perspectives inform the decision.

## Cross-Cutting Implementation Tips

Four principles apply across both taxonomies.

Use the incident taxonomy to audit your risk register. Take every risk in your current AI risk register and map it to the incident types in this taxonomy. If a risk in your register maps to multiple incident types, decompose it. If incident types in this taxonomy have no corresponding risk in your register, you have a gap. This audit typically reveals that existing risk registers are too coarse and miss 40% to 60% of applicable incident types.

Original implementation tip: When I conduct this audit with organizations, the most common gaps are in the cognitive degradation and value misalignment categories. Risk teams are comfortable identifying bias, security, and privacy risks. They are much less comfortable identifying risks related to overreliance on AI, loss of autonomy, lack of explainability, or accountability gaps. These "softer" incident types are not soft in their consequences. Lack of accountability contributed to more AI incidents I have investigated than any specific technical failure. Include the full taxonomy in your audit, not just the categories that feel comfortable.

Use the direct loss taxonomy to improve your quantification. For every risk scenario you quantify, decompose the impact into the specific direct loss types that apply. Estimate each loss type separately using calibrated ranges. Then aggregate them for the total impact distribution. This produces more accurate estimates than a single "impact" range because subject matter experts can estimate specific loss types more credibly than they can estimate total impact.

Original implementation tip: When conducting estimation workshops, present loss types one at a time, not all at once. Ask experts to estimate regulatory fine exposure, then legal compensation exposure, then algorithm remediation costs, then customer churn impact, and so on. This prevents anchoring, where the first estimate influences all subsequent estimates, and produces wider, more honest ranges. The first time I tried this approach, the aggregate impact estimate was 2.3 times higher than the single "total impact" estimate the same experts had provided before decomposition. Decomposition reveals exposure that aggregation hides.

Update both taxonomies as the AI landscape evolves. New incident types emerge as AI capabilities expand. Generative AI created incident types like hallucination and prompt injection that did not exist five years ago. Autonomous agents will create new incident types that do not exist today. Review and update your taxonomies at least annually, and whenever a significant new AI capability is deployed within your organization.

Align your taxonomy with regulatory requirements. The EU AI Act, NIST AI RMF, ISO 42001, and ISO 23894 each reference specific types of AI-related harms and losses. Map your taxonomy to the categories used by the regulations that apply to your organization. This ensures that your risk assessments address every category a regulator will ask about and that your documentation uses consistent terminology.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/some-photos-of-googles-new-ironwood-tpu-based-ai-superpods-v0-lhuqos1mfxzf1.webp?w=1024)

## Key References and Standards

This loss taxonomy draws from and aligns with the following authoritative frameworks.

ISO/IEC 42001:2023 for AI management system requirements covering governance and accountability for AI-related incidents and losses.

ISO/IEC 23894:2023 for AI risk management guidance, including classification of AI-specific risks and impacts.

ISO/IEC 27005:2022 for the information security risk management process, including loss event classification.

EU AI Act (Regulation 2024/1689) for the regulatory framework defining prohibited practices, high-risk requirements, and penalty structures for AI systems.

NIST AI RMF (AI 100-1) for the AI risk management lifecycle including harm categorization.

FAIR (Factor Analysis of Information Risk) for quantitative loss modeling taxonomy and methodology.

OECD AI Principles for the international framework addressing AI-related societal impacts.

UNESCO Recommendation on the Ethics of Artificial Intelligence for the broader ethical framework covering cognitive, social, and economic impacts.

MIT AI Risk Repository for the comprehensive academic catalog of AI risk incident types that informed several categories in this taxonomy.

## Making These Taxonomies Operational

Organizations that file these taxonomies as reference documents will continue making the same mistakes. Their risk assessments will use generic impact categories that obscure actual exposure. Their incident response plans will not cover incident types they have not named. Their loss estimates will undercount by factors of two to five because they have not decomposed generic "impact" into specific loss types. When an AI incident occurs, they will discover that they cannot quantify their exposure because they never built the vocabulary to describe it precisely.

Organizations that operationalize these taxonomies will build risk assessments that distinguish between 37 distinct incident types and 15 direct loss categories. They will estimate exposure with the granularity needed for credible Monte Carlo simulation. They will map incidents to losses to controls, creating traceability that survives regulatory scrutiny. Their boards will understand AI risk in specific financial terms because the risk team can articulate exactly what kinds of costs would appear and on which financial lines.

The precision of your AI risk management cannot exceed the precision of your loss taxonomy. Name the losses specifically, or accept that your risk numbers are wrong.

Which loss types in this taxonomy are missing from your current AI risk assessments? Start with the ones you have never estimated. Those are where your biggest quantification gaps live.
