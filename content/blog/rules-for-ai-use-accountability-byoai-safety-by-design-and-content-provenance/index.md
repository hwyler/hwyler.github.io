---
title: "Rules for AI Use, Accountability, BYOAI, Safety by Design, and Content Provenance"
date: 2026-03-16
tags: 
  - "ai"
  - "ai-governance-policy"
  - "ai-policy"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "bring-your-own-ai-algorithm-byoai"
  - "bring-your-own-algorithm-byoai"
  - "business"
  - "content-provenance-provenance"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "technology"
---

Organizations have zero or one AI policy. They need six.

A single "AI policy" that tries to cover governance, acceptable use, content provenance, employee-owned AI tools, safety requirements, and vendor management in one document produces a policy that's too broad to be actionable and too long to be read. Different audiences need different policies. The board needs a governance policy that defines oversight responsibilities. Employees need an acceptable use policy that defines what they can and cannot do with AI. Development teams need a safety-by-design policy that defines how AI systems must be built. And the organization needs content provenance, BYOAI, and accountability policies that address specific risk categories that cross-cutting documents handle poorly.

A strong AI policy stack is more structured. It defines who can use AI, for what, with what data, under what oversight, with what reporting and escalation, and how the organization proves accountability over time. This post turns the material you shared into a practical AI governance policy playbook.

ISO 38507:2022 establishes that the governing body takes full responsibility for the use of AI systems within the organization. That responsibility is discharged through policies that are specific enough to be followed, enforceable enough to matter, and comprehensive enough to cover the risk landscape. A single aspirational document doesn't meet any of these requirements.

This post covers six AI policies that together constitute a complete governance framework: the AI governance policy, the maintaining accountability framework, the acceptable use policy, the content provenance policy, the bring-your-own-AI policy, and the AI safety-by-design policy. For each policy, it covers what the policy must contain, who it applies to, and the specific provisions that make it operational rather than decorative.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/0115f641-3c8b-4ab1-9030-141225dba25f.png?w=1024)

## Policy 1: AI Governance Policy

The AI governance policy is the master document that establishes ethical guidelines, security protocols, and strategic objectives for AI integration across the organization. It defines the organizational framework within which all other AI policies operate.

Seven provisions define a complete AI governance policy.

Scope and applicability. Define the intended users, including employees, contractors, and vendors interacting with AI tools. Clearly state the policy's scope, applying it to all AI-related activities including past, present, and future projects. The scope statement determines who is bound by the policy and what activities it covers. A scope statement that covers only "AI projects initiated by the IT department" leaves unaddressed the AI tools that marketing adopted through a SaaS vendor, the AI features embedded in the HR platform, and the generative AI tools that individual employees use for daily productivity.

The scope should explicitly cover three categories of AI use: AI systems the organization develops internally, AI capabilities embedded in third-party software the organization uses, and AI tools that individual employees access independently (covered in more detail by the BYOAI policy).

Approved and restricted use cases. Define approved and restricted use cases for AI tools based on tasks, including nuances for conditional use. This provision creates a three-tier classification. Approved use cases are those evaluated and cleared for AI application: research assistance, document summarization, code generation with human review, data analysis support. Conditional use cases are approved only under specific conditions: client-facing content generation requires human review before delivery, AI-assisted decision-making requires documented human approval, AI processing of personal data requires prior privacy impact assessment. Restricted use cases are prohibited regardless of potential efficiency gains: autonomous decision-making without human oversight, processing of classified or privileged information through unapproved AI tools, using AI to generate content that impersonates real individuals.

Human oversight requirements. Emphasize that AI assists human judgment rather than replacing it. Require human review for AI-generated outputs before they influence decisions, reach customers, or create legal obligations. The policy should specify which categories of AI output require human review (all external communications, all decisions affecting individuals, all financial calculations) and which can be used without review (internal research notes, personal productivity assistance, data formatting).

Transparency obligations. Include explicit transparency requirements about AI use. In client agreements, disclose when AI tools are used in delivering services. In internal processes, document when AI influences decisions that affect employees. In external communications, identify content that was generated or substantially modified by AI. Transparency builds trust with clients, employees, and regulators, all of whom increasingly expect to know when they're receiving AI-generated work product.

Data security standards. Outline data security standards for approved AI tools. Specify minimum requirements such as SOC 2 Type 2 certification, zero-retention API configurations (where the AI provider does not retain input data after processing), encryption in transit and at rest, and data residency requirements. These standards should be non-negotiable for any AI tool that processes organizational data. Tools that don't meet these standards should not be approved regardless of their capabilities.

Incident reporting and escalation. Establish reporting procedures for AI tool malfunctions, data breaches, or violations of policy. Detail escalation protocols for addressing erroneous AI outputs, including consequences for violations up to termination. The reporting procedures should specify what constitutes a reportable incident (any AI output used in a decision that turns out to be incorrect, any suspected data exposure through an AI tool, any observed use of AI tools in violation of the acceptable use policy), who receives reports, what timeline applies for reporting, and what investigation process follows.

Employee acknowledgment. Require employees to acknowledge the policy and agree to compliance with [responsible AI](https://hernanhuwyler.wordpress.com/2026/03/16/responsible-ai-policy-categories/) use guidelines. This acknowledgment should be renewed annually and after any significant policy update. Acknowledgment without training is insufficient. Employees should receive training on what the policy requires before they're asked to acknowledge it.

Continuous monitoring and updates. Continuously monitor AI developments and adjust the policy to mitigate emerging risks. The AI capability landscape, the regulatory environment, and the threat landscape all change faster than annual policy review cycles can accommodate. Designate someone responsible for monitoring AI developments (new capabilities, new regulations, new threats, new vendor practices) and triggering policy updates when changes warrant them.

Implementation tip: When defining approved and restricted use cases, be specific about the nuances of conditional use. "AI may be used for research" is too broad. "AI may be used for preliminary legal research using approved tools (listed in Appendix A), provided that all citations are independently verified against primary sources before inclusion in any work product, and that no client-confidential information is included in prompts to any AI tool" is specific enough to follow and specific enough to enforce. Every conditional use case should specify the condition, the verification requirement, and the data handling restriction. Conditions that aren't specific enough to verify aren't conditions. They're suggestions.

## Policy 2: Maintaining Accountability (ISO 38507:2022 Alignment)

Accountability governance ensures that the governing body, typically the board of directors or executive committee, takes full responsibility for AI use within the organization. ISO 38507:2022 provides the framework for governance of IT, including AI, that defines how the governing body exercises its accountability.

Ten provisions operationalize AI accountability governance.

Avoid anthropomorphizing AI. The governing body and organizational leadership must understand AI's limitations and not attribute human characteristics to it. AI systems don't "understand," "decide," or "think" in the human sense. They process inputs according to learned patterns and produce outputs. When leadership attributes human capabilities to AI systems, they overestimate the system's reliability and underestimate the need for human oversight. Training for board members and executives should cover what AI actually does versus what marketing language implies it does.

Include AI in existing governance frameworks. Avoid creating separate AI governance structures that operate independently from existing corporate governance. AI should be included in the scope of existing governance frameworks for technology, risk, compliance, and ethics. Separate AI governance structures create oversight gaps because risks that span AI and non-AI systems fall between governance bodies. Integrated governance ensures that AI risks are assessed alongside and in proportion to other organizational risks.

Review and update governance mechanisms. Ensure governance mechanisms are fit for AI's specific applications. Traditional IT governance assumes deterministic systems with predictable behavior. AI governance must account for probabilistic outputs, model drift, data dependency, and emergent behavior that traditional governance wasn't designed to address. Review governance mechanisms annually to verify they remain adequate for the AI capabilities the organization deploys.

Strengthen oversight with specialized committees. Create subcommittees or advisory bodies focused specifically on AI strategy, AI risk, and AI ethics. These bodies don't replace existing governance structures. They provide specialized expertise that general governance committees may lack. An AI ethics advisory board that includes ethicists, domain experts, and affected community representatives provides perspective that a board of directors composed primarily of business executives cannot replicate.

Report on AI governance practices. Report to stakeholders regularly on AI governance practices to demonstrate accountability and transparency. Reporting should cover which AI systems are in operation, how they are governed, what risks have been identified and mitigated, what incidents have occurred and how they were handled, and what governance improvements have been made. Annual AI governance reports, whether published publicly or provided to regulators and key stakeholders, create accountability through visibility.

Increase review frequency. Increase the frequency of IT and AI system reviews to stay current on technological developments. Annual reviews are insufficient for a technology that changes quarterly. Quarterly reviews of AI system performance, risk status, and compliance posture keep governance current. Monthly monitoring of AI developments (new regulations, new threats, new vendor practices) keeps the governance framework informed between formal reviews.

Represent staff concerns. Ensure staff concerns related to AI, including safety, training, job impact, and working conditions, are adequately represented in governance discussions. AI deployment affects employees in ways that governance bodies may not naturally consider: fear of job displacement, frustration with unreliable AI tools, pressure to use AI without adequate training, and concerns about accountability when AI-assisted work products contain errors. Employee representation in governance discussions ensures these concerns are heard and addressed.

Evaluate AI impact across the lifecycle. Evaluate the potential impacts of AI at every stage, from purchase and implementation to operation and decommissioning. Impact evaluation that occurs only before deployment misses the impacts that emerge during operation (performance degradation, fairness drift, security vulnerabilities discovered after deployment) and the impacts that arise at decommissioning (data disposal, model artifact management, transition of workflows back to manual processes).

Implementation tip: Report on AI governance practices to stakeholders using a standardized format that enables comparison across reporting periods. The format should include the number of AI systems in the inventory (new, continuing, and retired), the risk classification of each system, compliance status against applicable regulations, incident count and categories, governance review completion rates, and significant governance decisions made during the period. This format enables trend analysis: is the AI portfolio growing faster than governance capacity? Are incident rates increasing or decreasing? Are governance reviews being completed on schedule? Trends tell the governance story more effectively than snapshot data.

## Policy 3: Acceptable Use of AI

The acceptable use policy defines what employees may and may not do with AI tools. It's the policy that every employee interacts with directly, and its clarity determines whether AI governance translates into daily behavior.

The general principle is straightforward: employees must not use any AI in ways that contradict responsible AI principles or cause harm. The specific prohibitions define what "contradict" and "harm" mean in practice.

Ten categories of prohibited use define the boundaries.

Legal violations: Using AI to violate laws, regulations, or company policies. This includes using AI to generate content that infringes copyright, using AI to process data in violation of privacy regulations, and using AI in ways that violate industry-specific regulations.

Autonomous decision-making: Using AI to make critical decisions without human oversight. Decisions that affect individuals' access to services, employment, credit, insurance, healthcare, or legal rights must include meaningful human review of AI-generated recommendations before action is taken.

Black box systems: Deploying or relying on AI models that are opaque or difficult to understand without adequate explainability controls. If the AI system can't explain why it produced a specific output, it should not be used for decisions that require explanation to affected individuals, regulators, or auditors.

Harmful content: Using AI to generate content that exploits minors, promotes hate, incites violence, or causes psychological harm. This prohibition extends to using AI to generate realistic depictions of real individuals without consent.

Deceptive practices: Using AI for manipulation, impersonation, or creating content designed to deceive. This includes generating deepfakes, creating fake testimonials or reviews, impersonating real individuals in communications, and producing content designed to mislead recipients about its origin.

Privacy and security violations: Using AI in ways that compromise privacy, security, or intellectual property. This includes inputting confidential information into unapproved AI tools, using AI to circumvent security controls, and processing personal data through AI without appropriate legal basis.

Bias perpetuation: Using AI that perpetuates or amplifies biases, discrimination, or inequality against defined protected categories. The policy should specify which protected categories apply based on applicable law and organizational values.

Autonomous weapons: Using AI to develop or deploy autonomous weapons or systems designed to cause physical harm without human oversight.

Surveillance: Using AI for excessive surveillance or invasion of privacy beyond what is legally authorized and organizationally necessary.

Misinformation: Using AI to generate or spread false or misleading information, whether intentionally or through negligent failure to verify AI-generated content.

Implementation tip: The acceptable use policy should include specific examples for each prohibited category, not just abstract descriptions. "Don't use AI to violate privacy" is abstract. "Don't paste client email addresses, account numbers, or case details into ChatGPT, Claude, or any AI tool not on the approved tools list (Appendix B)" is specific. "Don't use AI for deceptive practices" is abstract. "Don't use AI to generate email responses that appear to come from a specific colleague, create meeting summaries for meetings that didn't occur, or produce client reports that present AI-generated analysis as human analysis without disclosure" is specific. Employees follow specific guidance. They interpret abstract guidance according to their own judgment, which varies widely across the organization.

## Policy 4: Content Provenance

Content provenance policy addresses the tracking and verification of the origin and changes made to AI-generated or AI-modified content. As AI-generated content becomes increasingly indistinguishable from human-created content, provenance tracking becomes essential for maintaining trust, preventing deception, and meeting emerging regulatory requirements.

Six provisions define a complete content provenance policy.

Recognize the need for content provenance tools. The organization must acknowledge that AI-generated text, images, audio, and video require verification mechanisms that ensure authenticity and protect against deepfakes and misinformation. Without provenance tracking, the organization cannot verify whether content presented as original was generated by AI, whether content attributed to a specific person was actually created by them, or whether content has been modified from its original form.

Adopt cryptographic provenance solutions. Use solutions that securely track the content creation process with cryptographic protection of records. Cryptographic provenance creates tamper-evident records of who created content, when it was created, what tools were used, and what modifications were made. The Coalition for Content Provenance and Authenticity (C2PA) has developed open standards for content provenance that multiple major technology companies have adopted.

Use digital watermarking techniques. Embed invisible information in AI-generated content for identification purposes. Digital watermarking tools include Google DeepMind's SynthID (which embeds imperceptible watermarks in AI-generated images, audio, and text), Meta's Stable Signature (which watermarks images generated by specific models), and other emerging tools. Watermarks enable downstream verification that specific content was generated by AI.

Acknowledge watermark limitations. Current watermarking technology has limitations. Watermarks can often only be decoded by the companies that encoded them. Different AI providers use different watermarking approaches that aren't interoperable. Watermarks can sometimes be removed or degraded through content manipulation. The policy should acknowledge these limitations and not rely solely on watermarking for content authenticity verification.

Advocate for cross-industry collaboration. Support efforts to create open, interoperable standards for content provenance. The C2PA standard, supported by Adobe, Microsoft, Google, Intel, and others, is the most promising current effort. Adopting open standards rather than proprietary solutions ensures that provenance information is verifiable across platforms and providers.

Work with content publishers. Ensure that content distribution channels support the embedding and display of digital watermarks and provenance details. Content provenance is only valuable if the provenance information travels with the content through distribution channels and can be verified by recipients. Publishing platforms, email systems, document management tools, and web distribution channels should all support provenance metadata.

Implementation tip: Start content provenance implementation with the highest-risk content categories: external communications to clients, regulatory submissions, published reports, and marketing materials. These categories carry the greatest risk if AI-generated content is presented without disclosure or if content authenticity is questioned. Build provenance tracking into the workflow for these categories first, then expand to internal documents and lower-risk content as the infrastructure matures. Provenance tracking for every piece of content the organization produces may be the long-term goal. Provenance tracking for high-risk content is the immediate priority.

## Policy 5: Bring Your Own AI/Algorithm (BYOAI)

The BYOAI policy addresses AI models brought to the workplace by employees, including the data used, model outputs, and intellectual property implications. As AI tools become accessible to individuals without organizational procurement, employees increasingly use personal AI subscriptions, open-source models, and self-built algorithms for work tasks. This creates risks that no other policy adequately addresses.

Seven provisions define a complete BYOAI policy.

Model ownership, usage rights, and liability. Specify who owns AI solutions built by employees during work hours or using organizational data. Clarify whether the organization claims ownership of models trained on company data, whether employees retain rights to models they developed independently, and who bears liability when employee-built models produce incorrect or harmful outputs. These questions need clear answers in the policy rather than case-by-case adjudication after disputes arise.

Intended users. Identify who the BYOAI policy applies to: employees who develop AI models for work use, employees who use personal AI subscriptions for work tasks, IT staff who must evaluate and monitor employee AI tools, and managers who must enforce policy compliance within their teams.

Approved tools list. Create and maintain a list of approved AI tools, platforms, and services that comply with data protection policies. The list should specify which tools may be used for which purposes (Tool X is approved for general text assistance but not for processing personal data) and should be updated as new tools are evaluated and existing tools change their data handling practices.

Acceptable use cases for employee AI. Define when and how employees can apply their own AI models or personal AI tool subscriptions for work-related tasks. Specify which tasks are appropriate for employee-provided AI (personal productivity, research assistance, brainstorming) and which are not (client deliverables, regulatory submissions, financial calculations, processing of confidential data).

Review and approval process. Implement a review process for any AI tools brought by employees, with a designated committee responsible for evaluating proposed tools against security, privacy, accuracy, and compliance criteria. The review should assess the tool's data handling practices, its security certifications, its terms of service (particularly data retention and training provisions), and its suitability for the proposed use case.

Employee agreement. Require employees to sign a BYOAI agreement confirming they understand the risks, ownership terms, and data usage policies. The agreement should explicitly acknowledge that the employee is responsible for any data they input into personal AI tools, that the organization is not liable for outputs from unapproved tools, and that violation of the BYOAI policy may result in disciplinary action.

Access controls for data protection. Design access controls that limit the exposure of sensitive data to non-compliant AI tools. Use encryption and monitoring technologies to prevent unauthorized data transfer to personal AI tools. Network-level controls can block access to unapproved AI services from the corporate network. Data loss prevention tools can detect and prevent sensitive data from being pasted into AI tool interfaces. Endpoint monitoring can identify which AI tools employees are using and whether those tools are on the approved list.

Implementation tip: [Shadow AI](https://hernanhuwyler.wordpress.com/2026/03/30/shadow-ai-risk-management-for-caios/), where employees use unapproved AI tools without organizational knowledge, is the risk that BYOAI policies are designed to address but frequently fail to prevent. Detection is as important as prohibition. Build monitoring capabilities that identify AI tool usage across the organization: network traffic analysis for connections to known AI service endpoints, browser extension inventories that identify AI-powered plugins, and periodic surveys that ask employees (anonymously if needed to encourage honesty) which AI tools they use for work. The gap between what the approved tools list contains and what employees actually use reveals the shadow AI exposure the organization needs to address. Addressing it through better approved alternatives (providing tools that meet employee needs within policy boundaries) is more effective than addressing it solely through prohibition (banning tools without providing alternatives).

## Policy 6: AI Safety by Design

The AI safety-by-design policy requires embedding safety features in the development process of AI systems from the start, minimizing risks from misuse or failure. This policy applies primarily to AI systems the organization develops internally but also establishes the safety requirements that procured AI systems must satisfy.

Six provisions define a complete safety-by-design policy.

Pre-development risk assessment. Conduct a risk assessment to identify potential safety concerns before starting AI system development. The assessment should evaluate potential harms if the system produces incorrect outputs, potential for misuse if the system is applied to unintended purposes, data quality and representation risks that could lead to biased or unreliable behavior, security vulnerabilities that could be exploited by adversaries, and the consequences of system failure (what happens when the AI is unavailable and fallback processes must activate).

Formal verification where applicable. Implement formal proofs to mathematically verify that AI systems behave within predefined limits where the system's criticality warrants formal methods. For high-risk systems making decisions that affect safety, liberty, or significant financial outcomes, formal verification provides stronger assurance than empirical testing alone. Formal methods can prove that the system satisfies specific properties (outputs are always within a defined range, the system never takes a specific prohibited action) rather than just demonstrating that the property held during testing.

Safety guardrails. Incorporate AI safety guardrails including bias mitigation (testing for and correcting discriminatory outcomes), harmful content prevention (filters that prevent the generation of dangerous, illegal, or harmful content), and limiting unintended behaviors (constraints that prevent the system from taking actions outside its defined scope). Guardrails should be implemented as external enforcement mechanisms independent of the model, not as instructions embedded in the model's prompt that can be overridden.

Provenance tracking for data and code. Integrate provenance-tracking methods to verify the origins of data and code within AI systems, ensuring transparency and integrity. Provenance tracking creates an auditable chain of custody that documents where every dataset came from, who processed it, what transformations were applied, and when it was used for training. Similarly, code provenance tracks the origin of algorithms, libraries, and pre-trained models to verify they come from trusted sources and haven't been tampered with.

Dataset and algorithm documentation. Document the sources of all datasets and algorithms used, ensuring they meet ethical standards. Documentation should cover data provenance (source, collection method, consent basis), data characteristics (size, demographic composition, temporal coverage, known limitations), algorithm selection rationale (why this approach was chosen, what alternatives were considered), and known limitations (conditions under which performance degrades, populations that are underrepresented, scenarios that weren't tested).

Continuous safety updates. Update safety measures based on new vulnerabilities or technological advancements to maintain long-term trust and system reliability. Safety is not a deployment-time characteristic. It's an ongoing operational requirement. New attack techniques, new vulnerability disclosures, new regulatory requirements, and new understanding of AI system behavior all create the need for safety updates after deployment. Schedule safety reviews quarterly for high-risk systems and annually for lower-risk systems.

Implementation tip: The safety-by-design policy should specify that pre-development risk assessment results determine the development methodology, not the other way around. If the risk assessment identifies high potential for harm, the development methodology should include formal verification, extensive adversarial testing, independent safety review, and conservative deployment (phased rollout with continuous monitoring). If the risk assessment identifies low potential for harm, a lighter-weight development methodology is appropriate. Organizations that apply the same development methodology to every AI system, regardless of risk level, either over-invest in safety for low-risk systems or under-invest in safety for high-risk systems. The risk assessment should drive methodology selection, ensuring that development effort is proportional to potential consequences.

## How the Six Policies Work Together

The six policies form an integrated governance framework where each policy addresses a specific domain of AI risk.

The AI governance policy establishes the overall framework, defines scope, and sets strategic direction. It's the policy that other policies reference and align to.

The maintaining accountability framework ensures that the governing body takes responsibility for AI outcomes and that governance mechanisms are adequate for AI's specific characteristics.

The acceptable use policy translates governance principles into daily behavior expectations for every employee.

The content provenance policy addresses the specific risk of AI-generated content being presented without attribution or verification.

The BYOAI policy addresses the specific risk of employees using unapproved AI tools that create security, privacy, and quality exposures.

The safety-by-design policy ensures that AI systems developed by the organization are built with safety embedded from the start rather than applied as an afterthought.

Together, these policies cover the full risk landscape: from strategic governance through operational use, from content authenticity through data protection, from organizational development through individual employee behavior.

Implementation tip: Cross-reference the six policies so that each policy references the others where relevant. The acceptable use policy should reference the BYOAI policy for provisions about employee-provided AI tools. The BYOAI policy should reference the governance policy for the approved tools list. The safety-by-design policy should reference the governance policy for risk classification criteria. Cross-referencing prevents contradictions between policies and ensures that employees can navigate from one policy to the related provisions in others. Policies that exist as independent documents without cross-references create gaps where an employee following one policy inadvertently violates another because they didn't know the other policy existed.

## Cross-Cutting Implementation Tips for AI Policy Development

These principles apply across all six policies.

Implementation tip: Build your AI policies with three characteristics that determine whether they're followed or filed. Specificity means the policy provides clear guidance for specific situations rather than general principles that require interpretation. Enforceability means the policy includes consequences for violations and mechanisms for detecting violations. Currency means the policy is updated when circumstances change rather than becoming progressively outdated. A policy that is specific, enforceable, and current governs behavior. A policy that is vague, consequence-free, and outdated governs nothing.

Implementation tip: Test your policies by running scenario exercises with employees who haven't been involved in policy development. Present them with realistic AI-related scenarios and ask them to determine what the policy allows. If different employees reach different conclusions from the same policy, the policy isn't specific enough. If employees can't find the relevant provision within two minutes, the policy isn't organized well enough. If employees don't know the policy exists, the communication and training program isn't adequate. Scenario testing reveals policy gaps that review by the policy's authors, who understand the intent behind every provision, will never surface.

Implementation tip: Require employees to acknowledge policies and agree to compliance, but don't treat acknowledgment as a substitute for training. Clicking "I agree" on a policy document without reading or understanding it provides legal documentation but not behavioral change. Pair every policy acknowledgment with training that covers the policy's key provisions, illustrates them with relevant examples, and includes a brief assessment that verifies comprehension. Annual policy refresher training maintains awareness as policies evolve and as employees encounter new AI tools and use cases.

## Key References and Authoritative Frameworks

Your AI policy framework should align with these established standards:

- ISO 38507:2022, Governance of IT, Governance Implications of the Use of Artificial Intelligence

- ISO/IEC 42001:2023, AI Management System

- NIST AI Risk Management Framework (AI RMF 1.0)

- EU AI Act (risk classification, transparency, and documentation requirements)

- OECD AI Principles (transparency, accountability, fairness)

- UNESCO Recommendation on the Ethics of AI

- C2PA (Coalition for Content Provenance and Authenticity) standards

- GDPR Articles 13-15, 22 (transparency and automated decision-making)

- ISO/IEC 23894:2023, AI Risk Management

- CFPB Circular 2022-03 (algorithmic decision-making requirements)

- IEEE Ethically Aligned Design

- White House Blueprint for an AI Bill of Rights

If you govern AI through a single broad policy that combines governance, acceptable use, content provenance, BYOAI, and safety-by-design into one document, you will produce a document that's too long for employees to read, too broad for auditors to verify compliance against, and too general to provide actionable guidance for any specific situation. The board won't find the accountability provisions because they're buried among employee use restrictions. Employees won't find the acceptable use guidance because it's surrounded by governance provisions they don't need. Developers won't find the safety-by-design requirements because they're mixed with content provenance standards they don't work with.

When you build six focused policies, each addressing a specific domain of AI risk with specific provisions for its specific audience, cross-referenced to ensure consistency and organized for the people who need to follow them, you create a governance framework that can actually be implemented. The board reviews the accountability framework. Employees follow the acceptable use policy. Developers build systems according to the safety-by-design policy. And the organization demonstrates to regulators that every dimension of AI governance has specific, documented, enforceable policies backed by training, monitoring, and consequences.

An AI policy nobody reads governs nothing. Six AI policies that the right people read and follow govern everything.

How many of these six policies does your organization currently have in place? Start drafting the missing ones this quarter.

* * *

## About the Author

The frameworks, tools, taxonomies, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
