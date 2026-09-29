---
title: "Practical Implementation Tips for an AI Fundamental Rights Taxonomy"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-impact-assessments"
  - "ai-projects"
  - "ai-risk-assessments"
  - "artificial-intelligence"
  - "business"
  - "data-protecion-impact-assessments-dpia-dpias"
  - "eu-ai-act"
  - "fria"
  - "frias"
  - "fundamental-right-impact-assessment"
  - "hernan-huwyler"
  - "technology"
---

### Most AI Impact Assessments Ignore Fundamental Rights Here's the Category Taxonomy to Fix That

Last year, I reviewed an AI impact assessment for a financial services firm deploying an automated credit scoring model. The document was 40 pages long. It covered model accuracy, data quality, and technical bias testing. It never once mentioned the right to equality and non-discrimination. It never assessed whether the system could deprive someone of due process. It treated fundamental rights like a footnote, not a foundation.

That firm is now dealing with a regulatory inquiry.

This pattern repeats across industries. Organizations build AI systems, run technical evaluations, and skip the part where they ask: which human rights could this system actually harm? The EU AI Act, the NIST AI Risk Management Framework, and ISO/IEC 42001 all point in the same direction. Fundamental rights impact assessment is becoming mandatory, not optional. Yet most teams lack a structured taxonomy to do it properly.

This post gives you that taxonomy. Ten fundamental rights categories, mapped to their causes of harm, technology exposures, and sector-specific risks. More importantly, I'll show you how to put it into practice so your impact assessments actually catch what matters.

## Understanding the Three-Dimensional AI Fundamental Rights Taxonomy

A fundamental rights taxonomy for AI is a structured classification system. It maps how specific AI technologies, deployed in specific sectors, can violate specific human rights. The taxonomy I use in practice operates across three dimensions, and understanding all three is what separates a real impact assessment from a checkbox exercise.

The first dimension is the rights themselves. Ten categories cover the full spectrum of rights that AI systems can affect: equality and non-discrimination, privacy, life and liberty, fair trial and due process, freedom of thought and expression, meaningful employment, protection against incitement to hatred, participation in public affairs, freedom of assembly, and enjoyment of scientific progress.

The second dimension is technology exposure. Different AI technologies create different risk profiles. Facial recognition creates different rights risks than a resume screening algorithm. A generative AI chatbot creates different risks than a predictive policing tool. You need to know which technologies trigger which rights concerns.

The third dimension is sector exposure. A healthcare organization deploying AI faces fundamentally different rights risks than a social media platform or a law enforcement agency. Sector context determines which rights violations are most likely and most severe.

The most common mistake I see is teams assessing only one dimension. They test for bias (one right) in one technology (one exposure) without considering the sector context. Build your assessment as a matrix. Every AI system should be scored across all ten rights categories, with technology type and sector context as modifiers. When I started using this three-dimensional approach with clients, we caught an average of three additional high-severity risks per assessment that single-dimension reviews missed.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/typing-on-laptop.png?w=1024)

## Stage 1: Protecting Individual Dignity Rights

Three rights form the foundation of individual dignity in the AI context: equality and non-discrimination, privacy, and life, liberty, and security of person.

Equality and non-discrimination is where most AI governance conversations start. Everyone has the right to be treated equally regardless of race, gender, social origin, or other protected grounds. The causes of harm here are well documented. Algorithmic systems ingest historically biased training data. They use proxy variables that correlate with protected characteristics. The result is automated segregation at scale.

What to assess: Your evaluation must examine both direct discriminatory programming (where systems explicitly treat groups differently) and indirect discrimination (where identical treatment produces different outcomes). The UN Human Rights Council has documented how training data incorporating historical biases perpetuates discrimination, and datasets recording only binary gender options exclude non-binary individuals entirely.

Technology exposures are concentrated in automated decision-making systems and facial recognition. Predictive policing tools have demonstrated racial bias through feedback loops. The COMPAS recidivism algorithm examined in State v. Loomis embedded historical criminal justice disparities. Facial recognition exhibits documented accuracy gaps across demographic groups, with higher error rates for darker-skinned individuals and women.

Sector exposures hit hardest in employment (automated resume screening), financial services (credit underwriting bias), and law enforcement (predictive profiling). But administrative decision-making in government, healthcare diagnostics, and educational admissions all carry significant risk.

I spent six months building what I thought was a thorough fairness testing protocol. It failed on the first real deployment because we only measured overall accuracy, not accuracy across demographic subgroups. Your equality assessment must include disaggregated performance metrics broken down by every protected characteristic relevant to your deployment context. Test for false positive rates and false negative rates separately. A system that denies 3% of loan applications overall but denies 12% of applications from a specific racial group has an equality problem that aggregate statistics completely hide.

Privacy is the second dignity right, and AI creates privacy harms that traditional data protection frameworks weren't designed to handle. The right protects against arbitrary interference with private life, family, home, and correspondence. AI systems violate this right throughout their lifecycle, from data collection through deployment.

What to assess: Generative AI systems create entirely new categories of privacy harm. They generate personal data about individuals based on inferences and correlations, enabling profiling for healthcare, benefits, and employment decisions without explicit data collection. The Italian data protection authority's enforcement action against ChatGPT directly addressed this issue.

Technology exposures include real-time facial recognition (biometric data without consent), large language models (scraping personal data from the open web), biometric systems (collecting data that cannot be changed if compromised), and IoT devices with always-on sensors in private spaces.

Sector exposures span healthcare (sensitive patient data), financial services (transaction histories), government (mass surveillance), social media (behavioral profiling at scale), and retail (consumer tracking across physical and digital environments).

The right to life, liberty, and security protects against AI outputs that incite violence, cause accidents, or induce mental distress. This is where AI governance intersects with physical safety.

What to assess: AI-generated deepfakes depicting individuals in compromising scenarios cause documented psychological harm including anxiety, depression, and suicidal ideation. The WHO has addressed AI chatbots providing harmful health advice, including suicide methods and eating disorder guidance. Wrongful arrests result from law enforcement reliance on inaccurate facial recognition matches.

When I conduct rights impact assessments for life and security, teams consistently underestimate mental health harms. They focus on physical safety because it's easier to quantify. Build a specific assessment category for psychological harm pathways. Ask: Can this system generate content about a real person without their consent? Can it provide health advice? Can it make detention or restriction decisions? If the answer to any of these is yes, you need a dedicated safety review that goes beyond technical accuracy testing. One client discovered their customer service chatbot was providing medical guidance it was never designed to give, simply because users asked health questions and the model generated plausible-sounding answers.

## Stage 2: Procedural and Due Process Rights

Fair trial and due process rights require that decisions significantly affecting civil rights are transparent, explainable, and subject to challenge. This right is under direct threat from opaque algorithmic systems.

What to assess: The core problem is "black box" decision-making. When an AI system determines judicial sentencing, welfare eligibility, or immigration status, the affected person must understand how the decision was reached and must have a meaningful way to challenge it. The Council of Europe's CEPEJ Ethical Charter on AI in Judicial Systems establishes that AI must not undermine fair trial guarantees.

Technology exposures center on automated decision-making systems that lack explainability, predictive policing tools where individuals cannot challenge data inputs, recidivism risk assessment algorithms (State v. Loomis, Ewert v. Canada), and risk scoring systems in child welfare and immigration.

Sector exposures concentrate in the judiciary (sentencing algorithms), public administration (automated welfare adjudication), law enforcement (predictive policing and investigative analytics), and regulatory enforcement.

What to put in place: Every AI system making or informing decisions about individuals' rights must include three elements. First, a plain-language explanation of how the system reaches its outputs. Second, a documented process for individuals to contest AI-influenced decisions. Third, a qualified human reviewer who understands the system's limitations and has genuine authority to override its recommendations.

Automation bias is the silent killer of due process rights. I've watched experienced case workers defer to an AI recommendation even when their professional judgment disagreed, because "the system said so." Your due process assessment must evaluate not just whether human oversight exists on paper, but whether it functions in practice. Run observational audits. Measure how often human reviewers override AI recommendations. If the override rate is below 5%, your human oversight is probably decorative. In one government agency I worked with, the override rate was 0.3%. The "human in the loop" was rubber-stamping every algorithmic output. We redesigned the workflow to present the human reviewer with the case facts before showing the AI recommendation, and the override rate rose to 14%.

## Stage 3: Expressive and Democratic Rights

Three rights protect the information environment and democratic participation: freedom of thought, conscience, and expression, the right to take part in public affairs, and freedom of assembly and association.

Freedom of expression faces twin threats from AI. Algorithmic censorship removes legitimate speech through automated content moderation that lacks contextual understanding. Simultaneously, recommendation algorithms create filter bubbles that limit exposure to diverse perspectives while amplifying sensational content. Large language models undertrained on lower-resource languages limit information access for billions of speakers.

The right to participate in public affairs is increasingly threatened by AI-enabled electoral interference. The Alan Turing Institute documented extensive AI influence operations in elections worldwide, including 24 smear campaigns and 14 voter targeting instances in the 2024 US election alone. Deepfakes of candidates making fabricated statements directly manipulate electoral outcomes, as occurred in the 2024 Bangladesh elections.

Freedom of assembly faces erosion through biometric mass surveillance in public spaces. When governments deploy facial recognition at protests, it creates a chilling effect that discourages citizens from exercising their right to organize. Predictive policing systems pre-emptively target potential gatherings and track organizers.

What to assess across all three rights: Map every pathway through which your AI system could suppress legitimate speech, manipulate political information, or identify individuals exercising assembly rights. This includes content moderation decisions, recommendation algorithm behavior, surveillance capabilities, and data sharing with government authorities.

Most organizations assess expression rights only through the lens of content moderation accuracy. That misses the bigger picture. Your assessment must include recommendation system behavior. I worked with a platform that had excellent content moderation (97% accuracy on policy violations) but whose recommendation algorithm systematically amplified divisive political content because it optimized for engagement. The moderation system was catching individual violations while the recommendation system was shaping the entire information environment. Assess both the removal function and the amplification function of your AI systems.

## Stage 4: Economic and Participation Rights

The right to meaningful employment and the right to enjoyment of scientific progress address AI's impact on livelihoods and equitable access to technological benefits.

Employment rights face pressure across the entire hiring lifecycle. Amazon's abandoned recruiting tool, which replicated past discrimination against women, is the most cited example. But the risks extend far beyond recruitment. AI-driven "bossware" enforces unrealistic productivity quotas through continuous surveillance. Video interview analysis tools use emotion recognition, a technology with no scientific validity for assessing job suitability, to screen candidates. Automated scheduling systems disadvantage workers with caregiving responsibilities.

What to assess: Map AI involvement at every stage, from job advertisement targeting through performance evaluation and termination. The ILO has documented how AI systems determining ad targeting exclude qualified candidates from even learning about opportunities based on demographic characteristics. High-paying job advertisements have been shown less frequently to women.

The right to scientific progress addresses the "AI divide." Benefits concentrate in wealthy nations and well-resourced organizations. Language limitations in AI systems exclude billions of speakers. Healthcare AI developed on populations from wealthy nations provides inferior performance for underrepresented communities. Educational systems lacking AI integration resources fall further behind.

Employment rights assessments almost always focus on hiring bias and stop there. The fastest-growing risk area is algorithmic management, the systems that monitor, evaluate, and discipline workers after they're hired. When I assess employment AI, I now spend 60% of my time on post-hire systems. One logistics company I worked with had a fair hiring process but used an AI scheduling system that systematically gave fewer hours to workers who took sick days, effectively punishing people for using their benefits. The hiring assessment looked clean. The management system was causing real harm.

# Fundamental Rights Harms in AI Impact Assessments

### Detailed Harm Taxonomy for DPOs, CAIOs, and AI Risk Leaders

Fundamental rights impact assessments are becoming a core part of responsible AI governance in Europe. Under the EU AI Act, and in connection with data protection, product safety, consumer protection, employment, and anti-discrimination obligations, organizations need a structured way to identify how an AI use case could affect people in real life.

This is where Data Protection Officers and Chief AI Officers can create real value together. A strong DPO brings rigor on legality, necessity, proportionality, data governance, and the rights of individuals. A strong CAIO brings understanding of model design, deployment patterns, operating controls, testing methods, and technical failure modes. When they work in partnership, they help turn a fundamental rights impact assessment from a paper exercise into a decision-making tool: one that can shape whether an AI system should be deployed, how it should be redesigned, what safeguards are needed, and when escalation is required.

In practice, a good assessment does not stop at asking whether a model is accurate or secure. It asks a broader question: **what kind of harm could this AI system cause to people, groups, or society, and under what conditions?** The categories below are the most important rights-based harm areas that should be considered in AI projects, especially where the use case affects employment, education, law enforcement, healthcare, access to services, public administration, or democratic participation.

The order below moves from individual equality and privacy harms into safety, justice, civic freedoms, work, democratic integrity, and broader access to the benefits of AI.

* * *

## 1\. Rights to Equality and Non-Discrimination

The right to equality and non-discrimination is engaged whenever an AI system can affect how people are treated, ranked, selected, excluded, or targeted. At its core, this right protects individuals from being disadvantaged because of protected characteristics such as race, ethnic origin, sex, gender identity, disability, religion, age, sexual orientation, or social origin. In AI contexts, the concern is not only overt discrimination. It is also the quieter, harder-to-detect form: systems that appear neutral but produce systematically worse outcomes for certain groups.

This harm usually arises when historical patterns of inequality are built into data, labels, workflows, or optimization goals. If a hiring model is trained on historical recruitment decisions from an organization that favored men for technical roles, the model may learn that gender-coded patterns are signals of success. If a lending model uses ZIP code, school attended, purchasing behavior, or digital activity as predictors, those variables may operate as proxies for race, income, disability, or migration status. If a healthcare model is trained mostly on data from higher-income populations, it may underperform for underserved communities. These are not edge cases. They are well-documented patterns in AI risk literature, including work by NIST, OECD, UNESCO, and standards bodies developing trustworthy AI guidance.

The harm becomes more serious when the system is used at scale, in repeated decision-making, or in contexts with major life consequences. That includes employment screening, access to credit, insurance pricing, benefits eligibility, housing decisions, school admissions, fraud flags, policing, and sentencing support. In these use cases, even a modest disparity can become a systematic barrier when it affects thousands or millions of people.

Discrimination in AI can be direct or indirect. Direct discrimination happens when a system explicitly uses a protected characteristic in a way that produces unequal treatment without lawful justification. Indirect discrimination is more common and often more difficult to detect. It happens when the same model rule is applied to everyone, but in reality it disproportionately harms a protected group. A resume screen that penalizes non-linear work histories may affect women with caregiving gaps more than men. An interview scoring tool that rewards eye contact or tone may disadvantage autistic candidates or people from different cultural backgrounds. A fraud model that flags certain neighborhoods may disproportionately burden racialized communities.

The causes of these harms are usually cumulative rather than isolated. They include biased historical data, poor sampling, low representation of minority groups, simplistic labels, inaccurate or outdated records, weak feature selection, use of proxies, narrow performance metrics, and development teams that lack diversity of perspective. Another common cause is overreliance on aggregate accuracy. A model can look strong overall while performing badly for particular subgroups. This is why disaggregated testing matters.

Technology exposures are especially high for automated decision systems, facial recognition, emotion recognition, hiring tools, credit scoring models, fraud analytics, content moderation systems, and predictive systems used in law enforcement or public administration. Facial recognition deserves particular attention because multiple independent studies, including research from NIST, have shown differential error rates across demographic groups, especially where datasets or evaluation conditions are not representative.

Sector exposure is also high in employment, financial services, law enforcement, education, healthcare, housing, insurance, and public sector eligibility decisions. The reason is simple: these are environments where AI outputs shape access to opportunity, mobility, liberty, income, and dignity.

This harm should be assessed as an impact whenever an AI system does any of the following: makes or supports decisions about people; scores or ranks individuals; segments users; predicts risk or trustworthiness; personalizes access to opportunities; verifies identity; or monitors behavior in ways that can affect treatment. The assessment should become more stringent when the model is used in high-volume contexts, where human review is limited, where the consequences are difficult to reverse, or where affected groups are already vulnerable.

Guidance for assessment should include at least the following questions. What decision is the model influencing? Who may be disadvantaged, directly or indirectly? Are protected characteristics used, inferred, or proxied? Is the training data representative of the population affected by deployment? Have subgroup error rates, false positives, false negatives, and calibration been tested? Is there meaningful human review, or just rubber-stamping? Can affected individuals challenge the outcome? Is there evidence that the model is less reliable in the social context where it will be used?

A mature organization should also go beyond technical fairness testing. It should examine whether the use case itself is appropriate. Some AI systems are not merely risky because they are imperfect; they are risky because the function they perform is inherently prone to injustice. Predictive profiling in policing is a strong example. Even where a model is statistically refined, it may still reinforce historical over-policing and convert past bias into future intervention.

* * *

## 2\. Right to Privacy

The right to privacy protects people against arbitrary or unlawful interference with their private life, family life, home, correspondence, and personal data. In AI, privacy harms often arise long before the model is put into production. They begin with how data is collected, scraped, labeled, stored, shared, retained, inferred, and reused across the AI lifecycle.

A common pattern is that AI development rewards data maximization while privacy law requires necessity and proportionality. Teams want more data because more data can improve model performance. But collecting everything that is available is not the same as collecting what is lawful, fair, or necessary. This tension is especially visible in large-scale scraping, biometric processing, customer analytics, behavioral profiling, and generative AI training.

Privacy harm occurs when personal data is collected without a valid legal basis, when people are unaware their data is being used, when the data collected is excessive for the purpose, when sensitive data is processed without sufficient justification, when inferences reveal intimate information, or when weak security exposes personal information to unauthorized access. It also occurs when AI systems generate or reconstruct personal data about people, including people who never directly engaged with the system.

This is particularly important for generative AI. Large models trained on internet-scale data can absorb personal information from websites, forums, code repositories, public records, or social platforms. In some cases, they may reproduce personal details, create profiles, or infer characteristics such as health conditions, political views, sexual orientation, or financial distress. Privacy risk is no longer limited to what was directly collected. It also extends to what the model can infer or regenerate.

Validated guidance from GDPR, ISO/IEC 27701, and other privacy frameworks makes clear that organizations should assess privacy across the full AI lifecycle: collection, preparation, training, validation, deployment, monitoring, and decommissioning. The privacy question is not only whether data is personal. It is also whether a person can be affected through identification, re-identification, singling out, correlation, or profiling.

Technology exposures are high in facial recognition, biometric identification, generative AI, recommendation systems, personalization engines, digital assistants, connected devices, and internet-of-things environments. Real-time or remote biometric systems create especially severe exposure because they can identify or track people without meaningful awareness or consent. Always-on devices in homes, cars, or workplaces can also create continuous data capture in spaces where people reasonably expect privacy.

Sector exposure is high wherever personal data is central to the service. Healthcare processes highly sensitive medical and genetic data. Financial services use transaction patterns, identity records, and risk indicators. Government often processes personal data under conditions of unequal power, where individuals cannot meaningfully opt out. Social media and digital platforms aggregate behavior at scale and can infer highly intimate traits. Retail and marketing environments now blend online and offline tracking to build detailed consumer profiles.

This harm should be assessed as an impact whenever an AI system uses personal data, biometrics, behavioral data, communications data, location data, special category data, or inferred sensitive attributes. It is especially important where data is scraped from public or semi-public sources, where the use was not reasonably expected by individuals, where the model can infer sensitive characteristics, where retention periods are unclear, or where security weaknesses could expose data to attack.

Assessment guidance should include the legal basis for processing, purpose limitation, data minimization, transparency to individuals, data subject rights, retention controls, security measures, and international transfers. But it should also go further. Can the model memorize data? Can prompts or adversarial queries extract personal information? Are synthetic outputs capable of revealing real people? Are vendors using training data in ways the organization cannot verify? Has the team assessed whether the same outcome could be achieved with less intrusive data?

For DPOs and CAIOs, privacy in AI is best approached as a design issue, not just a notice issue. If a use case depends on excessive surveillance, speculative inference, or broad scraping to function, then the problem may not be solved by better wording in a privacy notice. It may require redesign, tighter scope, stronger filters, or a decision not to proceed.

* * *

## 3\. Right to Life, Liberty, and Security of Person

This category covers some of the most serious harms in AI. It includes threats to physical safety, wrongful deprivation of liberty, severe psychological harm, and AI outputs that put a person’s health or security at risk. It also overlaps with the right to health, especially where AI is used in medical, mental health, policing, border, or security settings.

The right is affected when AI systems make or influence decisions that can lead to injury, detention, violence, self-harm, or profound mental distress. This can happen through direct system failure, misleading outputs, unsafe automation, malicious misuse, or overreliance on model recommendations in high-stakes environments.

In healthcare, the risk may come from incorrect diagnostic support, unsafe triage prioritization, poor treatment recommendations, or chatbots that provide harmful advice. The World Health Organization has repeatedly highlighted the need for safety, oversight, and validation in health AI because inaccurate outputs can directly affect patient outcomes. In law enforcement, the risk may come from false identification, unreliable threat scoring, or predictive systems that lead to wrongful stops, arrests, or detention. In digital environments, deepfakes and cloned voices can be used to harass, extort, humiliate, or psychologically destabilize individuals.

Mental harm is part of this category, and it should not be treated as secondary. AI-generated non-consensual intimate imagery, impersonation, coordinated harassment, and synthetic abuse can cause severe anxiety, depression, fear, reputational damage, and social isolation. Women and girls are disproportionately affected by sexually explicit deepfake abuse, but the broader pattern is relevant to anyone targeted by synthetic media or AI-enabled intimidation.

Technology exposures are high for deepfake tools, voice cloning, facial recognition in policing, autonomous systems, health chatbots, decision support in clinical settings, predictive detention tools, and AI-enabled security platforms. Any system that can affect physical intervention, medical treatment, liberty deprivation, or high-intensity psychological harm should be treated as high exposure.

Sector exposure is highest in healthcare, law enforcement, border control, social media, defense, security, and public administration where the output can trigger enforcement action. But the risk also appears in consumer settings. A wellness chatbot, a child safety tool, or a home assistant can still create real harm if users reasonably rely on it for sensitive guidance.

This harm should be assessed as an impact whenever AI can materially influence a person’s bodily safety, mental health, access to medical care, movement, detention, or exposure to violence. It should also be assessed where the AI output may be weaponized by third parties, such as impersonation tools, synthetic image generators, or systems capable of producing harmful instructions.

The assessment should ask: What is the worst credible failure mode? Could a person be injured, detained, denied care, or psychologically harmed? Is the system used in a context where users are vulnerable or likely to rely heavily on outputs? Is there robust human oversight by qualified personnel? Are unsafe outputs tested, red-teamed, and blocked? Can the system refuse dangerous requests reliably? Is there incident response for harms that emerge after deployment?

For technical teams, this is where safety-by-design becomes essential. For governance teams, it is where escalation thresholds must be clear. If an AI use case can affect life, liberty, or personal security, its impact assessment should be treated as a serious control process, not a checklist.

* * *

## 4\. Right to a Fair Trial and Due Process

The right to a fair trial and due process protects people from opaque, arbitrary, or unchallengeable decision-making in matters that affect their rights and obligations. In AI, this harm emerges when systems influence legal, quasi-legal, or administrative decisions in ways that reduce transparency, weaken the ability to contest outcomes, or displace independent judgment.

This is not limited to courts. It includes any setting where AI materially affects a decision about benefits, immigration status, child protection, licensing, tax enforcement, parole, bail, sentencing, investigations, or regulatory action. If a person cannot understand how a decision affecting them was reached, cannot challenge it meaningfully, or cannot obtain review by a competent human authority, due process concerns arise.

The problem is often described as opacity, but the real issue is procedural fairness. A model may be technically explainable in a narrow sense and still fail due process if the explanation is not meaningful to the affected person, if the decision-maker cannot evaluate the output critically, or if there is no practical path to review and remedy.

Causes of harm include black-box models used in adjudicative settings, poor data quality, coding or design errors, hidden assumptions in labels and thresholds, weak governance over evidentiary use, and automation bias among human operators. Automation bias is especially important. If judges, officers, caseworkers, or administrators place undue trust in an AI output because it looks scientific or objective, then nominal human oversight may not be meaningful in practice.

A separate issue is the use of probabilistic tools to make individualized decisions. Risk scores for recidivism, fraud, welfare abuse, or child welfare may be statistically framed but still produce unfair outcomes when they substitute group-level probability for individual evidence. This is one of the core reasons why due process analysis should not stop at accuracy.

Technology exposures are high for automated decision systems, recidivism and risk scoring tools, predictive policing, facial recognition used for suspect identification, and AI used in document review, evidence triage, or legal research where it shapes legal judgment. Facial recognition is particularly sensitive because false matches can affect arrests and prosecutions, while the confidence or authority attached to the technology can mislead decision-makers.

Sector exposure is highest in judiciary and legal systems, law enforcement, immigration, welfare administration, tax and licensing authorities, and other forms of public administration. In these settings, AI can alter not only outcomes but the fairness of the process itself.

This harm should be assessed as an impact whenever AI is used to support or make determinations that affect legal status, liberty, access to state benefits, family integrity, or enforcement action. It should also be assessed whenever AI outputs are likely to be treated as evidence or as a major input into a formal decision.

The right questions include: Is the AI system making, recommending, or materially shaping a consequential decision? Can the decision-maker explain the role the AI played? Can the individual know that AI was involved? Can they challenge the outcome, the data, and the reasoning? Is the model valid for this specific legal context? Has the organization evaluated whether using AI in this setting is proportionate at all?

From a governance perspective, due process often requires more than human review. It requires **meaningful** human review by someone competent, independent enough to question the output, and empowered to depart from it.

* * *

## 5\. Right to Freedom of Thought, Conscience, and Expression

This right protects people’s ability to hold opinions without interference and to seek, receive, and share information and ideas. AI can affect this right in two opposite but equally important ways. It can suppress legitimate speech, and it can flood the information environment with manipulative, false, or abusive content in ways that distort public discourse.

The first risk comes from automated content moderation, filtering, ranking, and takedown systems. These tools are often deployed at scale and under time pressure. They struggle with context, irony, political nuance, minority dialects, reclaimed language, and cultural variation. As a result, they may over-remove legitimate speech, especially from already marginalized communities. This can include political dissent, religious expression, journalism, activism, or speech in low-resource languages.

The second risk comes from recommendation and personalization systems that shape what people see, what they do not see, and how they form opinions. These systems may create filter bubbles, reinforce extreme content, amplify outrage, or privilege engagement over reliability. They do not need to censor directly to interfere with expression. They can distort the conditions under which expression and information exchange happen.

Generative AI adds a further layer. Language models, chatbots, and synthetic media tools can produce biased answers, censor certain viewpoints inconsistently, hallucinate information, or generate persuasive falsehoods at volume. At the same time, people increasingly use these systems as gateways to knowledge. That means design choices about prompts, retrieval, ranking, safety filters, and language support now have real implications for access to information.

The right is also affected by surveillance technologies that create a chilling effect. If people believe they will be identified and tracked for attending a protest, posting criticism, or joining a religious gathering, they may self-censor even without direct enforcement. That is one reason why freedom of expression and privacy often need to be assessed together.

Technology exposures are high for content moderation systems, recommender systems, search and ranking algorithms, chatbots, large language models, translation tools, facial recognition, and synthetic media generation. Moderation systems create risk because they cannot reliably understand context at scale. Recommendation systems create risk because they shape visibility and attention, often through optimization goals that are not aligned with pluralism or truth.

Sector exposure is high in social media, news and media, education, government surveillance, and platform businesses that mediate communications. Educational settings also matter because filtering and AI-assisted learning systems can influence what students encounter during formative periods.

This harm should be assessed whenever AI determines visibility, reach, ranking, takedown, amplification, personalization, searchability, or information access. It should also be assessed where systems monitor individuals in ways that may chill speech, or where language coverage and moderation quality are uneven across groups.

A robust assessment should ask: Could the system unfairly suppress lawful expression? Does it work equally across languages and communities? Are moderation standards clear and appealable? Does personalization narrow information diversity? Could the system be used to manipulate users or discourage dissent? Are users aware when AI has shaped what they see?

For DPOs and CAIOs, the practical challenge is to connect policy principles to product mechanics. The risk often sits not in one model but in the interaction between classifiers, ranking systems, policy rules, user reporting, and engagement optimization.

* * *

## 6\. Right to Meaningful Employment

The right to meaningful employment includes access to work, free choice of employment, fair conditions, dignity at work, and protection from unjust exclusion or oppressive working conditions. AI can affect this right across the full employment lifecycle: job advertising, sourcing, screening, interviewing, hiring, task allocation, scheduling, productivity monitoring, promotion, discipline, and termination.

The most visible harms arise in hiring. Resume screening tools can replicate historical bias. Targeted job advertising can quietly direct better opportunities away from certain groups. Interview analysis tools may claim to infer personality, engagement, truthfulness, or emotional traits from facial expressions or speech patterns, despite serious scientific concerns about the validity of those inferences. Several regulators and expert bodies have questioned or criticized these techniques, especially where they are used to make consequential employment decisions.

But employment harm does not end after hiring. AI-driven workforce management can create invasive monitoring and reduce worker autonomy. Systems that track keystrokes, location, calls, delivery speed, idle time, or customer ratings may produce relentless surveillance and unrealistic productivity demands. In gig economy settings, workers may be managed, penalized, or removed by algorithm with little explanation and limited recourse. The individual may not know why they lost hours, pay, visibility, or access to the platform.

Causes of harm include biased historical employee data, use of unreliable behavioral proxies, weak validation, poor accommodation design for disability, one-size-fits-all productivity metrics, and fully automated management practices. Another common cause is the mismatch between system design and the social reality of work. A scheduling model may optimize attendance consistency while disadvantaging workers with caregiving duties. A performance model may reward measurable digital activity rather than substantive contribution.

Technology exposures are high for CV and application screening, skill assessment engines, video interview analysis, biometric attendance systems, worker monitoring tools, scheduling systems, and automated performance management platforms. Surveillance and monitoring tools deserve special attention because they create both privacy and labor rights concerns at the same time.

Sector exposure is broad because human resources functions exist in every industry. Risks are especially high in large-scale recruitment, customer operations, logistics, call centers, warehousing, retail, transportation, and platform or gig work. Professional licensing and credentialing can also affect a person’s ability to access their chosen profession and should not be overlooked.

This harm should be assessed as an impact whenever AI influences access to job opportunities, candidate ranking, hiring decisions, workplace monitoring, scheduling, pay, promotion, discipline, termination, or labor organizing conditions. It should also be assessed where workers have little bargaining power or where the employer’s system effectively determines livelihood.

The assessment should ask: Does the system affect who gets a chance to work, to keep working, or to progress at work? Is there evidence of bias in ads, screening, or scoring? Are disability accommodations built into the process? Is any claimed behavioral inference scientifically valid? Are workers informed about the system? Can they contest ratings or discipline? Is surveillance proportionate to the stated purpose?

DPOs, CAIOs, HR, and legal teams should work together here. Employment AI often fails not because the algorithm is advanced, but because the governance surrounding it is weak, the evidence base is thin, and the power imbalance is high.

* * *

## 7\. Right to Protection Against Incitement to Hatred

This right protects people and groups from advocacy of national, racial, or religious hatred that constitutes incitement to discrimination, hostility, or violence. AI changes the scale, speed, and sophistication with which hateful content can be produced, tailored, translated, and amplified.

Generative AI has lowered the cost of producing propaganda, conspiracy narratives, abuse, and extremist messaging. A malicious actor can now create text, images, audio, and video that appear coordinated, localized, and persuasive without the staffing and time that older influence campaigns required. Deepfakes can be used to fabricate inflammatory events or statements. Language models can generate hateful narratives in many styles. Translation systems can adapt those narratives across geographies. Bot networks can distribute them in a way that simulates public support.

The harm is not limited to intentionally malicious systems. AI systems can also amplify hatred through optimization choices. Recommendation engines tuned for engagement may favor divisive, shocking, or identity-based hostility because it drives reaction. Weak moderation tools may miss coded hate speech, or they may be manipulated to allow coordinated campaigns to spread faster than human review can respond.

This category should also include the role of AI in radicalization pathways. Recommender systems can repeatedly direct users toward more extreme content. Conversational systems can be manipulated into generating extremist narratives. Micro-targeting can identify vulnerable audiences and match messaging to their fears, grievances, or identity markers.

Technology exposures are high for generative AI, deepfake systems, recommender systems, social bots, multilingual content generation tools, and conversational AI. The risk is especially pronounced when the system can produce tailored messaging, adapt to user response, or optimize distribution based on engagement.

Sector exposure is highest in social media, media distribution, gaming communities, online forums, messaging ecosystems, and political communication environments. But any business operating user-generated content services or recommendation systems should consider this harm.

This harm should be assessed whenever a system can create, translate, personalize, rank, or amplify content that may target protected groups. It should also be assessed where moderation controls are weak, where the system can be repurposed by external actors, or where the social context is already polarized or conflict-prone.

Assessment guidance should include: Can the system generate or spread hateful content at scale? Can it be jailbroken or fine-tuned for extremist narratives? Does the platform amplify hostility through engagement optimization? Are there robust abuse detection, rate limits, provenance tools, and escalation channels? Are moderators equipped to handle multilingual and coded forms of hate?

This is an area where technical controls and societal context matter equally. A system that is relatively safe in one market may create much greater risk in another with active ethnic tension, election volatility, or weak moderation capacity.

* * *

## 8\. Right to Take Part in Public Affairs

The right to take part in public affairs protects democratic participation, including voting, campaigning, public debate, and engagement with civic institutions. AI can undermine this right by manipulating voters, polluting the information environment, suppressing participation, or weakening trust in authentic public communication.

The most visible threat is synthetic political deception. Deepfakes can depict candidates saying or doing things that never happened. AI-generated audio can imitate officials. Fake news sites can be populated at scale with fabricated or misleading political content. During election periods, these techniques can distort voter perception at exactly the moment when reliable information matters most.

Another major concern is micro-targeting. AI-enabled profiling can identify likely voters, persuadable audiences, disengaged groups, or psychologically vulnerable individuals and then deliver tailored messages designed not to inform, but to manipulate. The message a person receives may be invisible to everyone else, making public accountability harder. This affects the fairness and openness of democratic debate.

Recommendation systems and ranking algorithms also shape democratic participation. They influence what political content is seen, what is ignored, what trends, and what disappears into low visibility. Bot networks and automated engagement systems can create false impressions of consensus or momentum. Even parody and satire become harder to evaluate when synthetic content is realistic enough to confuse origin, intention, or authenticity.

Technology exposures are high for generative AI, deepfakes, micro-targeting systems, social media ranking algorithms, automated accounts, and political advertising infrastructure. The risk rises when content can be generated quickly, personalized deeply, and distributed widely.

Sector exposure is high in political campaigns, government and election administration, media, advertising technology, social media platforms, and civil society information ecosystems. Election authorities also face AI-related operational threats, including misinformation about voting procedures, locations, or eligibility.

This harm should be assessed whenever AI is used in political communication, public information delivery, voter targeting, campaign analytics, content ranking related to civic discourse, or election administration. It should also be assessed where the use case can degrade trust in authentic media or democratic institutions.

Assessment questions should include: Can the system fabricate political content or impersonate public figures? Can it target voters in a manipulative or opaque manner? Could it suppress turnout through misinformation? Does it affect visibility of political information? Are provenance and disclosure mechanisms in place? Is there a heightened election-period control framework?

For organizations outside politics, this category may still matter. A consumer platform, ad-tech provider, cloud host, or foundation model provider may become part of a democratic harm chain even if its primary business is not electoral.

* * *

## 9\. Right to Freedom of Assembly and Association

This right protects people’s ability to gather peacefully, organize, join groups, form associations, and participate in collective action. AI can interfere with this right by identifying organizers, tracking participants, suppressing organizing activity, or creating fear that discourages participation.

The most direct threat comes from biometric surveillance in public and quasi-public spaces. Facial recognition, gait analysis, or other identification systems can be used to monitor people attending protests, union meetings, political gatherings, religious events, or community organizing sessions. Even where the system is not used to arrest or sanction people immediately, the existence of surveillance records can create a chilling effect. People may decide not to attend at all.

Predictive systems create another layer of harm. If authorities or private actors use AI to identify likely organizers, anticipate gatherings, or monitor communication patterns for “risk,” they may disrupt assembly before it begins. Social media systems can also interfere when content moderation removes event pages, de-ranks organizing posts, or limits the reach of association-related communications.

The right is increasingly exercised in digital spaces as well as physical ones. Group chats, event pages, community forums, labor organizing platforms, and digital campaigns are all part of modern association. AI systems that govern visibility, recommendation, takedown, or threat scoring can therefore influence whether people are able to associate effectively.

Technology exposures are high for facial recognition, biometric surveillance, predictive policing, communication surveillance, social media moderation systems, recommendation engines, and automated threat assessment tools. The risk is highest where these systems are used around protests, political activity, labor organizing, or civil society action.

Sector exposure is high in law enforcement, government, educational institutions, employer monitoring systems, and major digital platforms. Employers should pay particular attention where AI tools are used to monitor worker communications or identify union activity. Educational institutions should do the same where student organizing may be chilled by surveillance or analytics.

This harm should be assessed whenever AI can identify, monitor, predict, suppress, or discourage collective action or group membership. It should also be assessed when the system processes communications or location patterns in ways that reveal association networks.

Useful assessment questions include: Could individuals be identified at a gathering? Are people aware of the surveillance? Is there a lawful and proportionate basis for using the system in this context? Could the tool be used to map social or political networks? Does moderation interfere with organizing activity? Are safeguards in place against mission creep?

For DPOs and CAIOs, the key issue is often not one isolated model but the accumulation of signals: identity, location, communications, watchlists, and behavioral analytics combined into a profile of collective behavior.

* * *

## 10\. Right to Enjoyment of Scientific Progress

This right is sometimes overlooked in AI governance, but it matters greatly. It protects people’s ability to benefit from scientific and technological progress and to participate in it. In AI, this right is implicated when the benefits of innovation are concentrated among already advantaged groups while other communities are excluded from access, participation, or meaningful influence over development.

The harm here is not always a direct injury in the classic sense. Often it is a structural harm: unequal access to AI tools, unequal performance across languages and populations, unequal opportunity to contribute to research and innovation, and unequal distribution of economic gains. If AI systems are built mainly for wealthy markets, dominant languages, and highly connected users, then the benefits of AI will reinforce existing inequalities rather than reduce them.

One part of this issue is the global AI divide. High-performance AI systems often require large amounts of capital, compute, data, and specialized talent. That means advanced AI capacity is concentrated in a small number of countries and companies. Developing economies may contribute data and labor to the AI value chain but receive fewer of the benefits. This concern has been raised in international development and digital cooperation discussions for several years.

Another part is linguistic and cultural exclusion. Models trained primarily on English and other high-resource languages can perform poorly for minority languages or local contexts. This affects access to information, education, healthcare support, civic tools, and productivity applications. It also affects whether communities can shape AI to reflect their own needs and realities.

Sector exposure is broad because AI increasingly affects competitiveness, service quality, and public value in every sector. Healthcare systems in lower-resource settings may not have access to advanced clinical AI. Education systems may not have equal access to AI-assisted learning. Agricultural communities may not benefit from climate and crop tools designed for industrialized farming. Small businesses may not be able to adopt AI at the pace of larger firms.

Technology exposures are high for large language models, proprietary foundation models, highly compute-intensive AI, and systems that depend on concentrated infrastructure or expensive licensing. Closed platforms can deepen dependency where users cannot adapt models to local languages, contexts, or public interest needs.

This harm should be assessed whenever a use case may systematically exclude certain populations from access to AI benefits, where language or infrastructure barriers are known, where the technology is likely to widen inequality, or where the organization’s deployment choices affect who can participate in innovation. It should also be assessed in international deployments, public sector contexts, and sectors with strong public interest dimensions such as health, education, agriculture, and finance.

Assessment guidance should ask: Who benefits from the system, and who is left out? Does the model work across relevant populations, languages, and contexts? Are there affordability, accessibility, literacy, or infrastructure barriers? Can local users adapt the technology to their needs? Does the deployment increase dependency on a small set of vendors without building local capacity?

For AI leaders, this category is a reminder that responsible AI is not only about avoiding harm from misuse. It is also about ensuring that the benefits of AI are shared fairly, accessibly, and inclusively.

* * *

# Why This Matters for EU AI Act Readiness

A fundamental rights impact assessment is most useful when it helps the organization make better decisions early: whether to proceed, how to redesign, what safeguards to add, which stakeholders to consult, and when executive or legal escalation is needed.

For the EU AI Act, that means moving beyond a narrow compliance interpretation. DPOs and CAIOs can jointly create a stronger practice by connecting legal obligations, technical reality, and operational governance. The DPO helps anchor legality, rights, and proportionality. The CAIO helps translate the actual behavior of models, data pipelines, and controls. Together, they can identify where an AI system may look acceptable in testing but still create serious rights impacts in context.

## Implementation Tips

These four principles apply across every rights category and every stage of your assessment.

Tip on maintaining the taxonomy over time: A fundamental rights taxonomy is worthless if it's completed once and filed away. Rights risks change as AI systems learn from new data, as deployment contexts shift, and as regulatory expectations evolve. Schedule quarterly taxonomy reviews for high-risk systems and annual reviews for everything else. I've seen organizations complete excellent initial assessments, then deploy a model update six months later that completely changed the risk profile because the training data was refreshed. Your taxonomy must be version-controlled and linked to your model lifecycle management process.

Tip on handling the "proportionality" judgment: Every rights assessment requires a proportionality determination. Is the AI system's benefit proportionate to its rights impact? This is where assessments break down, because proportionality is a judgment call, not a calculation. Create a proportionality panel with at least three perspectives: a domain expert who understands the business need, a rights specialist who understands the harm pathways, and someone representing affected communities. Never let proportionality decisions rest with a single individual or the team that built the system. I made this mistake early in my career. I let the product team determine proportionality for their own system. They concluded, predictably, that the benefits justified the risks. An independent review later disagreed.

Tip on documenting decisions: Document the "no" decisions as carefully as the "yes" decisions. When your assessment identifies a rights risk and the organization decides to proceed anyway, the reasoning behind that acceptance must be recorded in detail: who made the decision, what information they had, what mitigations were required, and what residual risk was accepted. This documentation protects the organization legally and creates institutional memory. In one regulatory inquiry I supported, the organization couldn't explain why they had accepted a known discrimination risk. The decision had been made verbally in a meeting with no minutes. That gap cost them months of remediation work and significant regulatory scrutiny.

Tip on technology-specific assessments: Resist the temptation to create a single generic assessment template for all AI technologies. Facial recognition, generative AI, automated decision-making systems, and recommendation algorithms each create fundamentally different rights risk profiles. Build technology-specific assessment modules that plug into your overall taxonomy framework. Your facial recognition module should automatically flag equality, privacy, assembly, and expression rights for detailed review. Your generative AI module should flag privacy, incitement, democratic participation, and life/security rights. Pre-mapping these connections reduces the chance that assessors miss critical pathways.

## References and Authoritative Frameworks

Your fundamental rights taxonomy should be anchored to established standards and regulatory requirements:

- EU AI Act, particularly the fundamental rights impact assessment requirements for high-risk AI systems

- NIST AI Risk Management Framework (AI RMF 1.0) and its companion playbook

- ISO/IEC 42001 (AI Management System) and ISO/IEC 23894 (AI Risk Management)

- UNESCO Recommendation on the Ethics of Artificial Intelligence

- OECD AI Principles and the OECD Framework for the Classification of AI Systems

- UN Guiding Principles on Business and Human Rights

- Council of Europe CEPEJ Ethical Charter on the Use of AI in Judicial Systems

- ILO guidelines on AI and worker rights

- The Rabat Plan of Action on prohibition of incitement

- GDPR and ISO/IEC 27701 for privacy-specific assessments

If you treat a fundamental rights taxonomy as a compliance artifact, something you produce for auditors and store in a shared drive, you will miss the risks that actually matter. The organizations I've seen face regulatory action, public backlash, and genuine human harm all had documentation. What they lacked was a living process that connected rights analysis to real deployment decisions.

When you treat the taxonomy as an operational tool, reviewed at every model update, referenced in every deployment decision, and owned by someone with authority to stop a launch, it becomes the single most valuable artifact in your AI governance program. It tells you what can go wrong before it goes wrong. It gives you the language to explain risks to executives who don't speak technical. It creates the evidentiary record that regulators and courts will eventually ask for.

The fundamental rights taxonomy for AI is the bridge between abstract ethical principles and concrete operational decisions. Build it well, keep it current, and give it teeth.

What's the first AI system in your organization that you'd run through this taxonomy? Start there, this week.
