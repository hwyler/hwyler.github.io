---
title: "The prEN 18228 Problem: Why Your AI Risk Assessment Will Fail the First Real Test"
date: 2026-05-08
tags: 
  - "ai"
  - "ai-governance"
  - "ai-risk-control"
  - "ai-risk-management"
  - "ai-risk-model"
  - "ai-risks"
  - "ai-standards"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "business"
  - "chatgpt"
  - "cybersecurity"
  - "en-18228"
  - "hernan-huwyler"
  - "iso-23894"
  - "iso-42001"
  - "iso-23894"
  - "pren-18228"
  - "technology"
---

Most [AI risk assessments l](https://hernanhuwyler.wordpress.com/2026/03/12/practical-ai-assessments/)ook solid on paper and collapse the moment a regulator, client, or auditor asks a simple question. What exactly can go wrong, how likely is it, and what does it cost when it does.

That gap is about to matter more.

A new European standard, prEN 18228, sets out a formal process for managing risks in AI systems across their full life cycle. It is designed to support regulatory expectations by requiring organizations to identify hazards, estimate and evaluate risks, define acceptability criteria, and continuously monitor controls. It brings structure and discipline. It also brings a product safety mindset into AI, focusing on harm to people, rights, and systems.

This sounds like progress. In many ways, it is.

But most organizations will apply it the same way they apply existing compliance frameworks. They will produce well-documented processes, consistent terminology, and defensible artifacts. And they will still struggle to answer the one question that drives real decisions. Should we deploy this system, under these conditions, with this level of exposure.

That is where this discussion starts.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/05/chatgpt-image-sep-11-2026-10_39_12-pm.png?w=1024)

## The Standard Brings Structure. It Does Not Solve the Decision Problem.

prEN 18228 defines risk in familiar terms. Probability of harm and severity of that harm. It requires organizations to identify hazards, assess risks, and reduce them to an acceptable level based on the intended use and reasonably foreseeable misuse of the system.

This is a disciplined approach. It forces teams to think beyond model accuracy and consider real-world impact. It also aligns well with how regulators think about safety and rights. The limitation is more subtle.

The standard tells you how to run the process. It does not tell you how to make the decision. It does not require you to quantify exposure in financial or operational terms. It does not connect model behavior to business outcomes like lost contracts, regulatory investigations, or reputational damage that affects future revenue. So you end up with a structured assessment that still relies on qualitative judgments at the point where decisions are made. Most organizations are comfortable there. They should not be.

## The Risk Definition Works for Products, but AI Behaves Differently.

The [probability times severity model](https://hernanhuwyler.wordpress.com/2026/03/12/ai-risk-modeling-beyond-is-ai-accurate/) comes from product safety. It works well when failure modes are clear and causation is traceable. A component fails. A system stops. Harm follows in a relatively predictable way. AI systems behave differently.

They fail in ways that are distributed, context-dependent, and often only visible after deployment. A fraud detection model might perform well overall and still produce systematic errors for a specific segment. A decision system might be technically accurate and still generate outcomes that trigger regulatory scrutiny or client disputes.

Two risks can produce the same expected value and require completely different responses. A frequent, low-impact error calls for process improvement and monitoring. A rare but severe failure calls for governance, escalation, and sometimes a decision not to deploy at all.

The standard does not distinguish clearly between these cases. It treats them within the same structure, which can flatten the differences that matter most in practice.That is where [experienced risk managers](https://www.researchgate.net/publication/400674476_AI_Management_Systems-_Operational_Playbook_for_Chief_AI_Officers_and_Compliance_Risk_Managers_By_Prof_Hernan_Huwyler_CAIO_MBA_CPA) need to go beyond the text.

# The Terminology You Need to Understand Before You Start

The standard introduces 68 defined terms across six domains, and most of them do not mean what you think they mean.

## Terms Relating to the EU AI Act

_Source: Regulation (EU) 2024/1689 (EU AI Act)_

- **AI system / Artificial intelligence system**: Machine-based system that is designed to operate with varying levels of autonomy and that can exhibit adaptiveness after deployment, and that, for explicit or implicit objectives, infers, from the input it receives, how to generate outputs such as predictions, content, recommendations, or decisions that can influence physical or virtual environments. This definition is broader than most technical definitions of AI. It includes rule-based systems and statistical models that exhibit adaptiveness after deployment, not just machine learning systems.

- **Intended purpose**: Use for which an AI system is intended by the provider, including the specific context and conditions of use, as specified in the information supplied by the provider in the instructions for use, promotional or sales materials and statements, as well as in the technical documentation. Technical documentation is not accompanying documentation. Information on technical documentation can be found in Article 11 of the EU AI Act. Your marketing claims define your regulatory obligations. If you claim the system works in a particular context, that context becomes part of your intended purpose and you must demonstrate safe operation there.

- **Reasonably foreseeable misuse**: Use of an AI system in a way that is not in accordance with its intended purpose, but which can result from reasonably foreseeable human behaviour or interaction with other systems, including other AI systems. Reasonably foreseeable human behaviour includes the behaviour of all types of relevant users. Reasonably foreseeable misuse can be intentional or unintentional. You cannot disclaim liability by saying users deployed your system incorrectly if that incorrect use was reasonably foreseeable. This standard requires you to model misuse scenarios and control for them.

- **Performance**: Ability of an AI system to achieve its intended purpose. Performance can relate either to quantitative or qualitative findings. Performance is evaluated in the context of use of the AI system. The use conditions under which performance is evaluated can result in significant performance outcomes and which can be explicitly stated. Performance is not accuracy. A highly accurate model that produces discriminatory outcomes has not achieved its intended purpose if that purpose included fairness. Performance must be evaluated under real-world use conditions, not laboratory conditions.

- **Provider**: Natural or legal person, public authority, agency or other body that develops an AI system or a general purpose AI model or that has an AI system or a general-purpose AI model developed and places it on the market or puts the AI system into service under its own name or trademark, whether for payment or free of charge. A distributor, importer, deployer or other third party can be considered a provider of an AI system in certain circumstances. If you rebrand, white-label, or substantially modify an AI system, you can become the provider under the Act, inheriting all associated obligations.

- **Deployer**: Natural or legal person, public authority, agency or other body using an AI system under its authority except where the AI system is used in the course of a personal non-professional activity. Deployers have distinct obligations under the AI Act, including human oversight and monitoring. This standard is written for providers, but providers must understand deployer obligations to design systems that support compliance downstream.

- **Post-market monitoring system**: Activities carried out by providers of AI systems to collect and review experience gained from the use of AI systems they place on the market or put into service for the purpose of identifying any need to immediately apply any necessary corrective or preventive actions. For the purpose of this document, activities shall mean all activities. Post-market monitoring is not optional. It is a continuous regulatory obligation. If you cannot systematically collect and review real-world performance data after deployment, you cannot meet the standard.

- **Placing on the market**: First making available of an AI system on the Union market. See making available on the market. Further information on this concept can be found in the Blue Guide, section 2. The first instance of commercial availability triggers the full set of provider obligations. Pre-release pilots and limited testing may not constitute placing on the market, but the boundary is not always clear.

- **Making available on the market**: Supply of an AI system for distribution or use on the Union market in the course of a commercial activity, whether in return for payment or free of charge. Free distribution counts. Open-source release can count. If you make the system available for commercial use in the EU, you are subject to the Act regardless of whether you charge for it.

- **Putting into service**: Supply of an AI system for first use directly to the deployer or for own use in the Union for its intended purpose. Further information on this concept can be found in the Blue Guide, section 2. Internal use triggers obligations. If you develop an AI system for your own operations and put it into service in the EU, you are both provider and deployer.

- **Serious incident**: Incident or malfunctioning of an AI system that directly or indirectly leads to any of the following: the death of a person or serious harm to a person's health; a serious and irreversible disruption of the management or operation of critical infrastructure; the infringement of obligations under applicable regulatory requirements intended to protect fundamental rights; serious harm to property or the environment. Serious incidents must be reported to authorities. The definition is broad. An AI system that produces a discriminatory outcome that infringes fundamental rights protections can trigger a serious incident report even if no physical harm occurred.

- **Subject**: Natural person who participates in testing in real-world conditions. Participating in testing can require informed consent of subjects. If your real-world testing involves human participants, informed consent requirements apply. This is a regulatory obligation, not just an ethical guideline.

- **Real-world conditions testing**: Temporary testing of an AI system for its intended purpose in its intended context of use or deployment environment outside a laboratory or otherwise simulated environment. Assessing and verifying conformity of the AI system with the requirements of this document includes that the overall residual risk of the AI system is acceptable in accordance with its intended purpose and reasonably foreseeable misuse. Real-world conditions testing can pertain to technical and non-technical aspects, including performance verification or usability study. Real-world conditions testing can require the participation of subjects. Real-world testing is distinct from deployment. It is time-limited, purpose-specific, and subject to additional safeguards. If you call something a pilot to avoid compliance obligations, but it operates like a deployed system, regulators will treat it as deployment.

## Terms Related to the Risk Management System

_Sources: ISO 9000:2015, ISO/IEC Guide 63:2019, EN ISO 14971:2019, ISO 26000:2010_

- **Accompanying documentation**: Materials accompanying an AI system and containing information for the user or those accountable for the use, maintenance, decommissioning and disposal of the AI system. The accompanying documentation can consist of the instructions for use, technical description, installation manual, quick reference guide, etc. The accompanying documentation is not necessarily a written or printed document but can involve auditory, visual, or tactile materials and multiple media types. Materials include information relevant for the protection of health, safety and fundamental rights, where each is applicable. Accompanying documentation is legally binding. If the instructions for use specify a particular deployment context or oversight requirement, deployers must follow it, and providers are responsible for ensuring the guidance is accurate and complete.

- **Objective evidence**: Data supporting the existence or verity of something. Objective evidence can be obtained through observation, measurement, test or by other means. Assertions without evidence do not satisfy this standard. If you claim a control is effective, you must produce objective evidence of its operation.

- **Procedure**: Specified way to carry out an activity or a process. Procedures can be documented or not. Undocumented procedures are permitted, but they must be specified and repeatable. In practice, undocumented procedures are difficult to demonstrate during an audit.

- **Process**: Set of interrelated or interacting activities that use inputs to deliver an intended result. Whether the intended result of a process is called output, product or service depends on the context of the reference. Inputs to a process are generally the outputs of other processes and outputs of a process are generally the inputs to other processes. Two or more interrelated and interacting processes in series can also be referred to as a process. Risk management is a process. Model development is a process. Post-market monitoring is a process. The standard requires these processes to be defined, systematic, and auditable.

- **Record**: Document stating results achieved or providing evidence of activities performed. Records can be used, for example, to formalize traceability and to provide evidence of verification, preventive action and corrective action. Records are the primary form of objective evidence in a risk management system. If an activity is required and you cannot produce a record of it, you have not met the requirement.

- **Risk management**: Systematic and continuous application of management policies, procedures and practices to the tasks of analysing, evaluating, controlling and monitoring risk throughout the entire life cycle of an AI system. Risk management is not a one-time assessment. It is a continuous process that spans development, deployment, operation, and decommissioning.

- **State of the art / Generally acknowledged state of the art**: Developed stage of technical capability at a given time as regards products, processes and services, based on the relevant consolidated findings of science, technology and experience. The state of the art embodies what is currently and generally accepted as good practice in technology. The state of the art does not necessarily imply the latest scientific research still in an experimental stage or with insufficient technological maturity. You are required to implement risk controls that reflect the state of the art, not the state of your organization's current capability. If better controls exist and are generally accepted, you must adopt them or justify why they are not applicable.

- **Top management**: Person or group of people who directs and controls a provider at the highest level. Top management must establish and approve risk acceptability criteria. They cannot delegate this responsibility to the compliance or risk function.

- **Verification**: Confirmation, through the provision of objective evidence, that specified requirements have been fulfilled. The objective evidence needed for a verification can be the result of an inspection, testing or of other forms of determination such as performing alternative calculations or reviewing documents. The activities carried out for verification are sometimes called a qualification process. The word "verified" is used to designate the corresponding status. Verification requires objective evidence. Self-attestation is not verification.

- **International norms of behaviour**: Expectations of socially responsible organizational behaviour derived from customary international law, generally accepted principles of international law, or intergovernmental agreements that are universally or nearly universally recognized. Intergovernmental agreements include treaties and conventions. Although customary international law, generally accepted principles of international law and intergovernmental agreements are directed primarily at states, they express goals and principles to which all organizations can aspire. International norms of behaviour evolve over time. Fundamental rights protections are grounded in international norms of behaviour. These norms are not static, and your risk management process must account for evolving expectations.

- **Risk management file**: Set of records and other documents that are produced by risk management. The risk management file is the primary artifact a regulator will examine during an inspection. It must be complete, coherent, and traceable.

## Terms Relating to Testing

_Source: ISO/IEC/IEEE 29119-1:2022_

- **Testing**: Set of activities conducted to facilitate discovery and evaluation of properties of test items. Testing activities include planning, preparation, execution, reporting, and management activities, insofar as they are directed towards testing. Testing is not just running the model on a validation set. It includes planning what will be tested, how it will be tested, documenting the results, and acting on the findings.

- **Test item / Test object**: Work product to be tested. Example: Software component, system, requirements document, design specification, user guide. The AI model is a test item. The training data is a test item. The user documentation is a test item. All must be tested.

- **Test objective**: Reason for performing testing. Every test must have a defined objective. Testing without a stated objective does not satisfy the standard.

- **Test completion report / Test summary report**: Report that provides a summary of the testing that was performed. The report may contain statistical analysis. Test completion reports are records. They must be retained as part of the risk management file.

- **Test plan**: Detailed description of test objectives to be achieved and the means and schedule for achieving them, organized to coordinate testing activities for some test item or set of test items. A test plan is a written document included in the risk management file. Testing without a documented test plan does not satisfy the standard.

- **Test monitoring and control process**: Test management process that aims to ensure that testing is performed in line with a test plan and with organizational test specifications. Test execution must be monitored and controlled. Deviations from the test plan must be documented and justified.

## Terms Related to Users and Affected Persons

_Sources: Regulation (EU) 2024/1689, EU Charter of Fundamental Rights, ISO 26000:2010_

- **Fundamental rights**: Rights and freedoms guaranteed by the EU Charter of Fundamental Rights. Fundamental rights include human dignity, respect for private and family life, protection of personal data, non-discrimination, equality between women and men, rights of the child, rights of the elderly, integration of persons with disabilities, right to an effective remedy and to a fair trial, presumption of innocence and right of defence, principles of legality and proportionality of criminal offences and penalties. Fundamental rights are legally binding in the EU. Harms to fundamental rights are within scope of this standard, even if they do not produce physical injury or property damage.

- **Stakeholder**: Individual or organization that can affect, be affected by, or perceive themselves to be affected by a decision or activity. Stakeholders can be internal or external. They include users, affected persons, deployers, providers, regulators, civil society organizations, and the public. Stakeholder identification is a required step in risk management.

- **Natural person**: Human being. The standard distinguishes between natural persons and legal persons. Fundamental rights protections apply to natural persons.

- **Affected person**: Natural person or groups of natural persons who can be subject to or impacted by an AI system. Affected persons include users and non-users. An AI system used in hiring affects both applicants and employees, whether or not they interact directly with the system.

- **User**: Natural or legal person, public authority, agency or other body using an AI system. Users include deployers and end users. User obligations differ depending on the role, and risk management must account for both categories.

- **Group**: Collection of natural persons defined by common characteristics such as demographic attributes, location, socioeconomic status, or shared vulnerability. Risks to groups must be assessed separately from risks to individuals. A system that performs well on average can produce serious harms to specific groups, and those harms are within scope.

- **Informed consent**: Freely given specific, informed and unambiguous indication of the data subject's wishes by which they, by a statement or by a clear affirmative action, signify agreement to the processing of personal data relating to them. For the purpose of this document, informed consent is understood more broadly to mean consent by a natural person related to participation in real-world conditions testing. Informed consent is not a click-through agreement. It must be specific, informed, unambiguous, and freely given. Generic consent forms do not satisfy this requirement.

## Terms Related to Risk

_Sources: ISO/IEC Guide 51:2014, ISO/IEC Guide 63:2019, EU Cybersecurity Act, EU Cyber Resilience Act, Directive (EU) 2022/2257_

- **Hazard**: Potential source of harm. Cyber threats and vulnerabilities can be the cause of a hazard. Cyber threats can be hazards. Hazards are not risks. A hazard is a source of harm. Risk is the combination of probability and severity. Identifying hazards is the first step in risk analysis.

- **Hazardous situation**: Circumstance in which people, property or the environment is/are exposed to one or more hazards. Exposure to a hazard does not guarantee harm. A hazardous situation is the precondition for harm to occur.

- **Harm**: Injury or damage to the health of a person or groups of persons, or interference with fundamental rights. For the purpose of this document, damage to property or the environment, and the disruption or destruction of critical infrastructure, are considered harms when they can result in injury or damage to the health of a natural person or groups of persons or interference with fundamental rights. Interference with fundamental rights can be tangible or intangible, physical, psychological, societal or economic, irrespective of the rightsholder's awareness, in accordance with EU law, including the EU Charter. Safety in product safety risk management standards is understood as the absence of unacceptable risk. In the context of this document, safety refers to the protection from harm from the use of the AI system. Harm is not limited to physical injury. Psychological, societal, and economic harms are within scope. Interference with fundamental rights is harm even if the affected person is unaware of it.

- **Severity**: Measure of the possible consequences of a hazard. The definition does not imply numerical measure of severity. Severity can be qualitative or quantitative. However, severity scales must be defined and applied consistently across the risk assessment.

- **Risk**: Combination of the probability of an occurrence of harm and the severity of that harm. The probability of occurrence includes the exposure to a hazardous situation and the possibility to avoid or limit the harm. This is the formula that does not work for AI when applied as a simple multiplication without modeling the loss distribution. It treats all risks with the same expected value as equivalent, which they are not.

- **Residual risk**: Risk remaining after risk control measures have been implemented. Residual risk must be evaluated against risk acceptability criteria. No system is risk-free. The question is whether the residual risk is acceptable.

- **Acceptable risk / Tolerable risk**: Level of risk that is accepted in a given context based on the current values of society. For the purpose of this document, "acceptable risk" is the preferred term and "tolerable risk" is the admitted term. For the purpose of this document, "context" refers to the intended purpose and reasonably foreseeable misuse of the AI system, and "current values of society" refers to high protection of health, safety, and fundamental rights. Acceptable risk is not a fixed threshold. It depends on context, and it evolves as societal values evolve. What was acceptable five years ago may not be acceptable today.

- **Risk assessment**: Overall process comprising a risk analysis and a risk evaluation. Risk assessment is the complete analytical process. It includes identifying hazards, estimating risk, and evaluating whether risk is acceptable.

- **Risk analysis**: Systematic use of available information to identify hazards and to estimate the risk. Risk analysis is the first step in risk assessment. It is analytical, not evaluative.

- **Risk estimation**: Process used to assign values to the probability of occurrence of harm and the severity of that harm. Risk estimation can be qualitative, semi-quantitative, or quantitative. The method must be documented and applied consistently.

- **Risk control**: Process in which decisions are made and measures implemented by which risks are reduced to, or maintained within, specified levels. Risk control follows risk evaluation. It is the implementation of risk control measures to bring residual risk within acceptable levels.

- **Risk evaluation**: Procedure based on the risk analysis to determine whether acceptable risk has been exceeded. Risk evaluation is the decision point. It compares estimated risk against acceptability criteria.

- **Inherently safe design**: Measures taken to eliminate hazards or to reduce risks by changing the design or operating characteristics of the product or system. For the purpose of this document, a product or system is an AI system. For risks to fundamental rights, inherently safe design refers to translating fundamental rights, for example presumption of innocence and non-discrimination, into the technical AI system design requirements through, for example implementing equality, privacy and data protection by design. Inherently safe design is the highest level of risk control. It eliminates the hazard rather than controlling exposure to it.

- **Risk control measure**: Action or means to eliminate hazards or to reduce risks. Example: Inherently safe design; protective devices; personal protective equipment; information for use and installation; organization of work; training; application of equipment; supervision. Risk control measures follow a hierarchy. Inherently safe design is preferred. Protective measures and information for use are secondary controls. The standard does not permit you to substitute information for design improvements when design improvements are feasible.

- **Cybersecurity**: Activities necessary to protect network and information systems, the users of such systems, and other persons affected by cyber threats. For the purpose of this document, network and information systems shall mean an AI system under consideration. Cybersecurity is within the scope of risk management. Cyber threats are hazards, and cybersecurity controls are risk control measures.

- **Cyber threat**: Potential circumstance, event or action that can damage, disrupt or otherwise adversely impact network and information systems, the users of such systems and other persons. For the purpose of this document, network and information systems shall mean an AI system under consideration. Cyber threats include adversarial attacks on AI models, data poisoning, model extraction, and manipulation of inputs to produce harmful outputs.

- **Vulnerability**: Weakness, susceptibility or flaw of a product with digital elements that can be exploited by a cyber threat. For the purpose of this document, a product with digital elements shall mean an AI system under consideration. Vulnerabilities are not hazards themselves, but they are sources of hazards. A model trained on unvalidated data has a vulnerability. If that vulnerability is exploited, it becomes a hazard.

- **Critical infrastructure**: Asset, facility, equipment, network or system or part of asset, facility, equipment network or system which is necessary for the provision of an essential service. Disruption of critical infrastructure can constitute serious harm. AI systems used in or affecting critical infrastructure are subject to heightened scrutiny.

Do not assume the standard's definitions align with your organization's existing terminology. They do not. The term "user" in this standard includes deployers and end users. The term "harm" includes interference with fundamental rights, not just physical injury. The term "risk" is defined as a combination of probability and severity, but it does not specify how to combine them, and the implied multiplication formula is insufficient for AI. Build a terminology mapping document that translates each of the standard's 68 terms into your organization's operational language, and distribute it to every team involved in AI development, deployment, and risk management. If your legal team, your technical team, and your risk team are using different definitions of the same word, your risk assessment will fail before you begin.

## How the Standard Actually Runs Risk Management

Most organizations say they “have a risk process.” What they often have is a sequence of documents. The standard is more demanding. It expects a continuous, structured process that runs across the entire life cycle of the AI system and produces decisions that can be explained and defended.

### A Continuous Process, Not a One-Time Assessment

The provider is expected to establish, implement, document, and maintain an ongoing risk management process. This process starts with risk analysis. It includes identifying characteristics related to risks tied to the intended purpose and reasonably foreseeable misuse of the AI system. It requires identifying known and reasonably foreseeable hazards, hazardous situations, and risks.

From there, the process moves to estimating and evaluating those risks, followed by risk evaluation, testing, risk control, and the evaluation of overall residual risk. It does not stop at deployment. It continues through risk management review and both pre-market and post-market activities.

This entire process applies across the full life cycle of the AI system. It is not limited to design or validation phases. It must be documented and maintained in a risk management file, which becomes the central record of how risk was understood, assessed, and managed over time.

Many organizations already have product or system development processes. The expectation is not to duplicate effort, but to integrate. Where a product realization process exists, it should incorporate the relevant parts of the risk management process. In practice, this means risk is embedded into how the system is built and operated, not added as a separate compliance layer.

The process is not linear. Different elements carry different weight depending on the life cycle stage. Activities can be iterative, repeated, and refined as new information becomes available. That flexibility is intentional. AI systems evolve, and the risk process must evolve with them.

### Management Owns the Process, Not Just the Outcome

Risk management is not delegated away. Top management is expected to demonstrate active commitment. This starts with providing adequate resources and ensuring that personnel involved in risk management are competent. It includes assigning responsibility clearly and overseeing how the process is implemented.

There is also a review obligation. Management must regularly assess whether the risk management system remains suitable and effective. This includes reviewing the policy, the plan, and how the process operates in practice. These reviews are not ad hoc. They are planned, systematic, and documented, including decisions and actions taken.

Post-market information plays a direct role here. What is learned from real-world use feeds back into management’s assessment of whether the process still works. In many organizations, this feedback loop is weak. The standard makes it explicit.

Representation of the risk management process

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/05/picture1.gif?w=624)

### Risk Acceptability Is a Policy Decision, not a Technical Detail

One of the most consequential requirements sits at the policy level. Top management must define, document, and maintain a risk management policy that establishes how risk acceptability is determined.

This policy must ensure that criteria for accepting individual residual risks and the overall residual risk meet regulatory requirements. It must take into account the intended purpose of the AI system, its reasonably foreseeable misuse, and what is generally accepted as the state of the art.

It should also reflect broader expectations. This includes relevant standards, international norms of behavior, and the concerns of stakeholders who may be affected by the system.

The policy needs to go further than general principles. It must specify the methods used to determine risk acceptability. One example is comparing the AI system to an equivalent non-AI system using a “no worse than” approach. It must also define how and when these criteria are reviewed and updated. At a minimum, this happens after serious incidents and at regular intervals throughout the life cycle, including before market entry.

In practice, this is where many organizations struggle. They define high-level principles but avoid committing to clear thresholds or methods. The standard expects the opposite.

### Competence Is a Collective Requirement

Risk management activities must be performed by people who are competent based on education, training, skills, and experience relevant to their role. This is not limited to technical expertise.

Collectively, the team must understand the AI system or similar systems, the application domain and operating conditions, the technologies involved, and the relevant aspects of health, safety, and fundamental rights. They also need to understand the risk management techniques being used.

Not every individual needs all of these competencies, but the team as a whole must cover them.

Where fundamental rights are involved, the expectation is higher. Those performing these assessments must be able to understand and apply the relevant rights, and when needed, organize and facilitate consultation with affected stakeholders, including vulnerable groups. If the system can affect specific vulnerable populations, the team must have expertise in those areas.

In practice, this pushes organizations to move beyond purely technical or compliance-driven teams. Risk management becomes multidisciplinary by design.

### Defining Risk Acceptability Criteria

Risk acceptability criteria define what level of risk is considered acceptable. These criteria must be established and updated throughout the life cycle to maintain a consistent and high level of protection for health, safety, and fundamental rights.

They must exist at two levels. One for each identified risk, and one for the overall residual risk of the system. They must be justified, documented, and supported by objective evidence so they can be verified and validated.

The criteria must reflect equal concern for all affected persons, with particular attention to those most vulnerable to harm. They must be aligned with the risk management policy, regulatory requirements, and the nature of the harms involved, including how different harms may interact.

Objective evidence plays a central role. Where people can be affected, this may include consultation with affected individuals or their representatives, especially vulnerable groups. If direct consultation is not performed, evidence can come from previous consultations for similar systems or from authoritative sources on fundamental rights. Testing can also contribute.

The provider must document why the evidence used is relevant and sufficient. If consultation is performed, the rationale for selecting participants and their representativeness must be clear.

This is not a box-ticking exercise. It is about showing that the thresholds for accepting risk are grounded in reality, not convenience.

### How Criteria Are Established and Updated

Risk acceptability criteria must be determined in relation to the intended purpose and reasonably foreseeable misuse of the AI system. They must exist even when the probability of harm cannot be estimated precisely.

The process for establishing and updating these criteria is demanding. It includes considering independent review by a multidisciplinary team with expertise in safety, health, fundamental rights, AI, and the relevant application domain. Where an equivalent evaluation already exists, it can be reused, but it must be supported by objective evidence.

The provider must consider the state of the art, including literature, market data, and incident data. Alternatives must be assessed, including options that reduce risk significantly or avoid using AI altogether.

Severity and probability both matter, but they are not interchangeable. A low-severity harm can still be unacceptable if it occurs frequently. Where probability cannot be quantified, qualitative assessment is acceptable, provided the reasoning is documented.

The distribution of risk across different groups must be considered, especially where certain groups may be disproportionately affected. Adverse impacts on vulnerable groups require particular attention.

Pre-market and post-market information must feed into this process. This includes incident data, near misses, user feedback, and concerns raised by affected individuals or their representatives.

Independence is required. Those defining and reviewing risk acceptability criteria should be separate from those designing and developing the system, with any conflicts of interest documented. This can be achieved internally through separation of roles or externally through independent experts.

Where fundamental rights are at stake, additional considerations apply. For qualified rights, the provider must assess necessity, proportionality, and legitimate objectives. For privately enforceable rights, applicable legal obligations must be identified.

### Looking at the Overall Residual Risk

Assessing individual risks is not enough. The standard requires a separate evaluation of the overall residual risk. The criteria for overall acceptability can differ from those applied to individual risks. This reflects a simple reality. Risks interact.

The provider must consider the aggregated severity and how risks are distributed, how they interact, and how multiple harms can arise from a single situation. The combined effect can be greater than the sum of individual risks. The analysis must consider impacts on all affected persons, with particular attention to vulnerable groups. It must also consider both immediate and long-term harms, including cumulative effects over time.

An important consequence follows. The overall residual risk can be unacceptable even if each individual risk has been reduced to an acceptable level. Where children are affected, their best interests must be a primary consideration. This is not optional. It reflects established international principles.

Final approval of overall risk acceptability sits with top management. This reinforces that risk acceptance is a business decision, not just a technical conclusion.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/05/futuristic-glowing-device-1.png?w=1024)

### Planning the Work

Risk management activities must be planned. For each AI system, the provider must establish and document a risk management plan. This plan becomes part of the risk management file. The plan defines the scope of activities. It identifies the AI system and the life cycle phases where each part of the plan applies. It assigns responsibilities and authorities, taking into account the competence of personnel.

It includes requirements for reviewing both the process and the outcomes, the risk acceptability criteria, and the underlying policy. It defines how risk control measures will be verified and how pre-market and post-market information will be collected and reviewed. The plan itself is not static. Changes over the life cycle must be recorded. This creates a traceable history of how risk management evolved.

### The Risk Management File as the Backbone

All of this comes together in the risk management file. This is not a single document, but a structured set of records and references that capture the entire process.

It includes the intended purpose of the AI system, the risk management policy, the plan, and all documentation related to risk analysis, evaluation, testing, control, and residual [risk assessment](https://arxiv.org/html/2512.13907v1). It also includes records of reviews and post-market activities.

Traceability is essential. Each identified hazard must be linked through the process. From identification, to analysis, to controls, to testing, to residual risk. In practice, this is often implemented through structured risk tables with clear identifiers and links to supporting evidence.

The file can reference other documents, including those from the quality management system, to avoid duplication. What matters is that all required information can be assembled quickly and coherently.

This is where the process becomes real. If the file is complete, consistent, and traceable, the organization can explain its decisions. If it is not, the process exists only on paper.

# Risk Management Process and AI System Life Cycle

The provider must determine and document in the risk management file the stages of the life cycle for each AI system, from inception to end of life, in line with each AI system's intended purpose. The life cycle phases may be determined in alignment with the life cycle phases as determined in the quality management system. prEN 18286, the companion standard addressing quality management systems for EU AI Act purposes, provides additional information on life cycle alignment.

The risk management process must be applied systematically and iteratively along the entire life cycle of the AI system. This is not a sequential process completed once and archived. The risk management process activities must be integrated into the life cycle stages to ensure that risks are systematically and iteratively analyzed, evaluated, and reassessed, risk control measures are identified, implemented, verified, and updated when needed, residual risks and overall residual risk are evaluated and monitored and their acceptability maintained, and relevant information on the AI system is collected and reviewed.

Risk analysis and risk evaluation must start at the inception stage of the AI system and must be applied through all the following life cycle stages until end of life, as new risks can emerge and previously identified ones can change during any of the life cycle stages. The results of risk evaluation can have a bearing already on the inception phase. In some cases, it can take much less effort to mitigate a risk at the inception stage than during later life cycle stages. This is a critical point that most organizations miss. Early risk assessment is not a formality. It is the point at which design decisions can eliminate hazards rather than control them.

Risk control measures can be implemented at different life cycle stages, depending on the specific measures. Risk control measures must be, as much as technically feasible, implemented during design and development with the view to achieve inherently safe design. Inherently safe design is the highest priority risk control measure. It eliminates the hazard rather than managing exposure to it.

Information that is relevant to the risk management process can become available at any life cycle stage. This information can support the provider to identify the need to re-execute the risk management process, in whole or in part, or to return to a previous step of the risk management process. This information can refer to the identification of new risks, changes to estimations of risks, the detection of risk control measures that do not perform as expected, or the implementation of new risk control measures.

Some risk control measures are only possible to implement by returning to a previous life cycle stage. A change of intended purpose restarts the inception stage. New inherently safe design measures restart the design and development stage. This creates a challenge for organizations that treat life cycle stages as linear and complete. The standard requires iterative re-entry into earlier stages when risk information demands it.

Most organizations will map their existing product development life cycle to the standard's requirements and declare the mapping complete. That is not sufficient. The standard requires risk management activities to be integrated into each life cycle stage, not merely aligned with it. Build your life cycle model as a series of decision gates where risk analysis, risk evaluation, and risk control verification are mandatory prerequisites for progression. If your development roadmap allows a system to move from design to deployment without a documented risk evaluation and approval of residual risk by top management, your life cycle integration does not meet the standard. The life cycle is not a timeline. It is a control framework.

# General Requirements for AI Risk Analysis

The implementation of the planned risk analysis activities and the results of the risk analysis must be recorded in the risk management file. The risk analysis must consist of risk identification and risk estimation. These are distinct activities with different outputs, and both must be documented.

The provider must analyze risks from logging and monitoring, human factors, user behavior, unwanted bias, data quality and data governance including provenance of data, and AI system accuracy, where applicable. This is not an exhaustive list. The standard explicitly states these areas are examples, not limits. In order to address these areas, the provider can refer to prEN 18229-1 on transparency, prEN 18229-2 on robustness, prEN 18282 on cybersecurity, prEN 18283 on data quality, prEN 18284 on bias, prEN 18281 on logging, and other relevant standards.

In addition to the records required for risk identification and risk estimation, the documentation of the conduct and results of the risk analysis must include at least the unique identifier and the version designation of the AI system that was analyzed, identification of the persons and organization who carried out the risk analysis, scope and date of the risk analysis, and techniques and methodologies used for hazard identification and risk estimation. Without this metadata, the risk analysis cannot be traced, verified, or defended under regulatory scrutiny.

Damage to property or the environment, and the disruption or destruction of critical infrastructure, are harms when they can result in injury or damage to the health of persons or interference with fundamental rights. The provider may also consider additional harms. The process of risk analysis is intended to address these harms. Cyber threats and vulnerabilities can be the cause of a hazard, and [cyber threats can be hazards](https://www.kaggle.com/models/hernanhuwyler/csv-threat-model). prEN 18282 can be used to identify and address cyber threats and vulnerabilities.

The range of fundamental rights which must be considered for the purposes of risk analysis must include all the rights recognized under the EU Charter. This is not limited to the rights most commonly discussed in AI ethics frameworks. It includes all Charter rights, and the provider must assess which rights are relevant to the specific AI system being analyzed.

Techniques such as Preliminary Hazard Analysis, Hazard and Operability Study, Fault Tree Analysis, and System-Theoretic Process Analysis can be effectively utilized to derive risk analysis. These methods are complementary, and employing a combination of them can be essential for achieving a comprehensive and robust risk analysis. For more guidance on risk analysis techniques, refer to EN IEC 31010. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Risk Identification from the Intended Purpose

The provider must document in the risk management file the intended purpose of the AI system being considered. The documentation of the intended purpose must include at least the following information: application areas, the objectives of the AI system including the intended output and impact on persons' safety, health and fundamental rights, type of tasks used to achieve the objectives, techniques and approaches for how the AI system operates, types of intended deployers and types of intended users, deployment type such as physical product, software, or service, and the intended environment in which the AI system operates.

Intended users can refer to professionals, consumers, and users defined by age group or other characteristics. The environment in which the AI system operates can include the organizational, physical, and digital environment. The digital environment refers to the types of integration and interfaces with other software systems and physical systems. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

Most organizations document intended purpose as a one-paragraph marketing description. That is insufficient. The standard requires you to specify the intended impact on persons' safety, health, and fundamental rights, the deployment type, the user types, and the operational environment at a level of specificity that supports hazard identification. If your intended purpose documentation does not answer the question "in what specific context, for what specific users, performing what specific tasks, does this system operate, and what specific impacts on safety, health, and fundamental rights are intended," it does not meet the standard. Build your intended purpose statement as a structured specification, not as a mission statement.

## Risk Identification: Reasonably Foreseeable Misuse

The reasonably foreseeable misuse of the AI system must be identified, taking into account the potential misuse of the AI system by other user categories, which can include lay users, persons under the age of 18, and other vulnerable groups, on other persons affected, vulnerable groups, assets, or the environment, where other persons affected can include persons who are not defined in the intended purpose of the AI system, in a different context or environment including the digital, physical, and organizational environment and infrastructure in which the AI system operates, with incorrect input or data, and in a different application area.

The identification must also consider the potential misuse of the AI system, including its outputs, aims, or objectives. A recommendation used as a decision is an example of this type of misuse. The identification must consider the potential incorrect deployment of the AI system. A user who can and does change the AI system's settings such that it operates outside of its intended purpose is an example of incorrect deployment. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Risk Identification: AI System Characteristics Related to Risks

Identifying the characteristics of an AI system is a preliminary step intended to support the identification of hazards and hazardous situations. It is meant to create a general overview of relevant characteristics, keeping in mind that hazards and hazardous situations need to be identified in detail later in the risk management process.

The provider must identify and document all applicable characteristics that can affect risks of the AI system. Where applicable, the limits of these characteristics must be defined, such as limits of performance. The operation of the AI system and the risk associated with its use can be affected when those limits are exceeded. These characteristics are related to the functionality of the AI systems, its lifecycle, its intended purpose and reasonably foreseeable misuse, and the environment in which it operates and interacts with.

For identifying these characteristics, the following must be taken into account: outputs of and actions taken by the AI system and their effect on users and persons affected, including vulnerable groups and age-appropriate outcomes when the intended users are persons under the age of 18. The effect can be directly from the AI system output or are intended to follow from the AI system output. An AI system that grants public assistance benefits has a direct effect on the applicant. A medical system that identifies cancer in a scan provides this information to a doctor which decides on treatment for the patient. The patient is affected by an action that follows the AI system output.

The provider must also consider user profiles including their abilities and limitations, known biases in decision making, their level of expertise, and how this can impact the appropriate use and interpretation of the AI system's outputs, user accessibility to the AI system, interactions of the AI system with the environment including other systems and digital infrastructure and the effects of the AI system on the environment and vice versa, AI system functionality, architecture and technologies and related capabilities, limitations, uncertainties or known failure modes, minimum performance requirements of the AI systems and system components to achieve the intended purpose, level of autonomy and adaptiveness of the system's behavior during operation such as continuous learning, pre-determined changes to the algorithm and its performance that can appear during the operation phase and the possibility that the system behavior changes during the operation phase in a way that hasn't been pre-determined, dependency on third party components including open source, dependency on third party support in specific lifecycle phases such as outsourcing of design, development and verification and validation tasks, processing and storage of data by the AI system and the nature and sensitivity of the data, deployment, maintenance and decommissioning or disposal procedures, procedures for updates of the AI system during operation, and skills and experience of deployers.

The provider must identify the [cybersecurity vulnerabilities and cyber threats t](https://arxiv.org/html/2511.21901v1)hat can have an impact on the characteristics listed. prEN 18282 provides additional information on this requirement. For each of the points, the provider must assess their relevance and document their reasoning. Furthermore, the provider must include a justification if they choose not to perform or implement one of the listed points. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Risk Identification: Hazards, Risk Scenarios, and Hazardous Situations

Based on the AI system's intended purpose, reasonably foreseeable misuse, characteristics related to risks, and the state of the art, the provider must identify and document in the risk management file known and reasonably foreseeable hazards, risk scenarios, and hazardous situations. These are distinct concepts, and the standard requires all three to be identified and documented.

Hazards can only lead to harm if a hazardous situation exists. A risk scenario clarifies under which context and conditions a hazard can result in harm by describing what leads to the hazardous situation. A risk scenario can consist of a single event, a sequence of events, a combination of events, a circumstance including all external factors to the system, including normal use and user interactions, or a state such as internal factors to the AI system. Events that form part of a risk scenario can also be referred to as hazardous events.

A hazard can lead to multiple hazardous situations, and each hazardous situation can lead to multiple harms. Hazards and hazardous situations can be technical and non-technical. AI system decisions or outputs can be hazards. Hazards can have more than one cause.

The provider must describe the risk scenarios. Risk scenario descriptions must include known and foreseeable related hazard and hazardous situation, elements affecting the probability of harm occurring, elements affecting the severity of harm, events, sequences and interactions of events, if any, that lead to the hazardous situation, any contributing factors including any relevant failure modes and their underlying potential causes, and AI system characteristics that can lead to hazardous situations.

Risk scenarios must consider at least interactions and behaviors of the system, users and persons potentially affected, contributing human factors, system errors which can include errors resulting from design, development, deployment and incorrect system operation, cyber threats and vulnerabilities, and environmental factors influencing the system, users or person affected. Sequences of events can also comprise a chronological chain of causes and effects, non-occurrence of expected events as well as combinations of concurrent events. A risk scenario can be initiated in all phases of the AI system's life cycle.

The provider must consider all available relevant information to support the hazard and hazardous situation identification process. Relevant information includes pre-market sources, including testing, expert reviews, stakeholder consultation feedback, available data on comparable systems already on the market, incident databases, published research, regulatory reports, market surveillance findings, and other credible sources that provide insight into potential hazards or known issues. It also includes post-market sources, including incident reports, complaints, potential serious incident data, user feedback and information collected by automatic logging of the AI system. The logs can contain many events of which some can be labeled as hazardous events.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/05/picture2.gif?w=501)

The identification of hazards must include hazards associated with each identified vulnerability and cyber threat to the AI system. prEN 18282 can be used to identify vulnerabilities and cyber threats to the AI system. Vulnerabilities and cyber threats concern the AI system itself, whereas hazards concern risks to health, safety, and fundamental rights.

The AI system provider must, as appropriate, use multiple different risk identification techniques throughout the AI system life cycle to ensure a comprehensive hazards identification process. When identifying hazards and hazardous situations not previously recognized, systematic techniques for risk identification that cover the specific situation can be used. Guidance on some available techniques is provided in relevant standards and guidelines, such as EN IEC 31010.

Top-down techniques, which are typically used in the early planning phases, are valuable for identifying high-level hazards and risk scenarios. As development progresses, diverse methods must be applied to systematically analyze specific hazards, failures and cyber threats, supporting root-cause exploration and targeted risk control measures. These risk identification techniques are complementary and it is often necessary to use multiple approaches in combination to achieve a robust and complete risk analysis.

When identifying hazards and hazardous situations, the provider must consider the specific risks and harms that the AI system can pose to persons under the age of 18 and other vulnerable groups, taking into account their evolving capacities, vulnerabilities and, where applicable, the best interests of persons under the age of 18. This should include risks related to exposure to harmful or inappropriate content, unwanted contact or interactions with adults for persons under the age of 18, privacy violations and data misuse, excessive screen time and addiction, dignity, negative impacts on physical and mental health, and exploitation and abuse.

Risk scenario identification and analysis can inform about the relevant events to be logged. The risk scenario identification and analysis can become more robust as it is iterated through at the different relevant life cycle stages. Frequently, only a first subset of the intended purpose-related hazards and hazardous situations can be identified at the inception and early design and development stages. At the early design and development stage, the obtained results, observations and feedbacks can lead to new hazard, to new risk scenario and to new hazardous situation identifications. Post-market monitoring can lead to the identification of new hazards and hazardous situations and related conditions identifications.

For each of the points in this section that must be considered, the provider must assess the relevance and document their reasoning. Furthermore, the provider must include a justification if they choose not to perform or implement the point. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

Hazard identification is where most risk assessments fail. Organizations identify high-level hazard categories such as "bias" or "data quality issues" and treat the identification as complete. That is not compliant with the standard. The standard requires you to identify specific hazards, describe the risk scenarios that lead from hazard to hazardous situation, and document the contributing factors and failure modes. If your hazard identification does not answer the question "what specific event, sequence, or state leads from this specific hazard to this specific hazardous situation, affecting which specific persons in which specific way," you have not identified the hazard. You have named a category. Build your hazard identification as a structured cause-and-effect analysis, not as a list of concerns.

## Risk Estimation

For each identified hazard and hazardous situation, the provider must estimate the probability of occurrence of the associated harm and the severity of that harm, based on the AI system's intended purpose, reasonably foreseeable misuse, characteristics related to risks, and the state of the art. The provider must estimate the associated risks using available information or data. For hazards for which the probability of the occurrence of harm cannot be estimated quantitatively, the possible harms must be listed and a qualitative estimation made of their probability, for use in risk evaluation and risk control.

When identifying the possible harms resulting from hazards, and in estimating the severity of the associated harm, the groups of persons potentially affected must be determined. Specific vulnerabilities of persons potentially affected can increase the probability and severity of harm. These vulnerabilities can include characteristics and external factors that classify a person as being a member of a vulnerable group, and characteristics and external factors beyond those that classify a person as being a member of a vulnerable group.

For each hazard and hazardous situation, the severity of the associated harms must be estimated taking into account the nature of the harm, which refers to whether it concerns health, safety or fundamental right, the reversibility or irreversibility of the harm, which in relation to persons affected refers to the ability to revert fully or partially to pre-impact situation or equivalent and whether adequate remedies are made available in a timely manner, the number of persons affected in absolute terms rather than only expressed as a proportion of an affected population, the specific characteristics of persons potentially affected, the possible combination of harms, and the potential cumulative effects on persons affected.

For each hazard and hazardous situation related to fundamental rights, the estimation of the severity of the associated harms must also entail the consideration of the character of the right as being an absolute right or qualified right, the applicability of legal obligations imposed on private actors to protect that fundamental right, the level of protection accorded to the right, and the scope, significance and scale of the harm of a potential fundamental rights interference which entails consideration of how widespread its effects and adverse impacts of the hazard or hazardous situation, including whether the rights at risk are those of rights-holder groups that enjoy additional or particular protections. Rights holder vulnerable groups that enjoy additional or particular protection can refer to persons under the age of 18.

If a fundamental rights risk is likely to affect only 0.1% of users on a digital communication platform, it can initially appear negligible, but if this comprises 25% of a religious minority, then the latter indicates that the scope can be serious. This example illustrates why absolute numbers and distributional analysis matter.

An AI system's intended purpose or reasonably foreseeable misuse can affect a number of different fundamental rights pertaining to multiple persons affected. A hazardous situation can generate risks to multiple fundamental rights that can affect more than one person potentially affected. Risks to the fundamental rights of persons affected can interact with each other, for example when risks are compounded or cumulative.

The strength of legal protection accorded to the activity protected by a fundamental right is based on whether it is an absolute right, a privately enforceable right or a qualified right or a principle in support of a right. The stronger the level of protection accorded to the right, the greater the severity of a potential interference to it.

For the estimation of the severity of fundamental rights risks and the potential effects of interaction from the AI system with persons potentially affected, the provider should consult with persons potentially affected or their proxies, at least before placing on the market or putting into service the AI system. The results of these activities must be documented.

The system used for qualitative or quantitative categorization of probability of occurrence of harm and severity of harm must be documented and recorded. If a risk chart or risk matrix is used for ranking risks for the purpose of estimating their severity and probability, or qualitative estimate of likelihood if probability cannot be estimated, then the parameters and the interpretation of the particular risk chart or risk matrix used must be explained and justified for that application and in accordance with the intended purpose and the reasonably foreseeable misuse of the AI system.

Risk estimation incorporates an analysis of the probability of occurrence of harm and the severity of the harm. Depending on the application area, only certain elements of the risk analysis process can be relevant to consider in detail. When the harm is minimal, an initial hazard and consequence analysis can be sufficient, or when insufficient information or data are available, a conservative estimate of the probability of occurrence can give some indication of the risk. Risk estimation always has a qualitative component and can additionally have a quantitative component. Methods of risk estimation are described in relevant guidelines and standards for application area specific safety risk management, such as EN IEC 31010.

Information or data for estimating risks can be obtained from information received from post-market monitoring system, civil society groups and academic literature, published standards and guidelines for AI risk management, scientific or technical investigations, field data from similar systems already in use including publicly available reports of incidents, usability tests employing typical users, performance metrics and evaluation results, results of relevant investigations or simulations, expert opinion, and external quality assessment schemes for AI systems.

The scale of a health, safety or fundamental rights risk for the purposes of evaluating its severity concerns its gravity, and entails consideration of the potential cumulative effects on persons affected in light of the intended purpose and its reasonably foreseeable misuse, which is also a product of the ease and speed with which the AI system can diffuse across multiple domains and beyond its intended application area. It also entails the assessment of whether persons affected belong to a vulnerable group, including their ability to take protective measures to safeguard their rights and interests. The protected characteristics of vulnerable groups can also be a separate parameter to demonstrate clearly these characteristics have been considered in the severity.

For the purposes of estimating its severity, a fundamental rights risk is considered irremediable if the persons affected cannot be restored to a situation at least equivalent to their situation if there had been no interference to the respective fundamental right through the use of an AI system.

The provider must ascribe the highest severity classification for risks to fundamental rights that are considered absolute rights in accordance with applicable regulatory requirements. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

Risk estimation is where the standard's formula breaks down most visibly. The requirement to estimate probability and severity does not specify how to combine them, and most organizations default to a simple multiplication that treats a 10% chance of moderate harm the same as a 1% chance of severe harm because both produce the same expected value. That approach does not satisfy the requirement to evaluate risk acceptability. Build your risk estimation process to produce not only point estimates but also distributional analysis, confidence intervals, and scenario-weighted outcomes. Document the method you use to combine probability and severity, justify why that method is appropriate for the specific AI system and application area, and present the results in a way that distinguishes between frequent low-severity risks and rare high-severity risks. If your risk estimation outputs a single number per hazard, it does not provide the information top management needs to approve residual risk acceptability.

# Risk Evaluation Turns Analysis into Decisions

For each identified hazard and hazardous situation related to the AI system, the provider must evaluate the estimated risks to health, safety, and fundamental rights by comparing them against the predefined risk acceptability criteria in the risk management plan. Based on this evaluation, the provider must determine whether the risk is acceptable or not.

If the risk is acceptable, it is not required to apply risk control activities to this hazardous situation, and the estimated risk must be treated as residual risk. If the risk is not acceptable, then the provider must perform risk control activities to reduce the risk to an acceptable level.

The results of the risk evaluation activities must be recorded in the risk management file with a breakdown of the reasoning for each identified risk to health, safety, and fundamental rights. A risk evaluation that records only a conclusion without the reasoning behind it does not meet the standard. The reasoning must be documented for each risk individually.

Documentation of the activities and the resulting records must be included and maintained in the risk management file.

Risk evaluation is where the gap between internal comfort and external defensibility becomes most visible. Organizations usually compare estimated risks against acceptability criteria that were defined too loosely to produce a meaningful comparison. If your acceptability criteria say "risks are acceptable when they are low," and your risk estimation says "this risk is low," you have performed a circular evaluation that tells a regulator nothing about how you actually made the decision. Build your risk evaluation as a documented comparison between a specific estimated risk, expressed in terms of probability and severity with supporting evidence, and a specific acceptability threshold, defined in terms that can be independently verified. Document the reasoning that connects the evidence to the conclusion. If the reasoning cannot be reproduced by someone who was not in the room when the evaluation was performed, it is not sufficient.

# Testing Is Evidence, Not Validation Theater

Testing is an essential activity to support the risk management process. Testing can support the identification of hazards and associated causes, sequences of events and hazardous situations related to intended purpose and reasonably foreseeable misuse, the provision of objective evidence of residual risk and overall residual risk acceptability, and the post-market monitoring system activities, including the monitoring of continuously learning AI systems to ensure they remain within their predefined changes.

Usability testing can be used as a method for validating the effectiveness of human-machine interfaces and instructions for use. Testing performed to identify characteristics of training data sets that reveals inconsistent labelling of the data and bias in representativeness of the data in relation to the intended purpose informs about the appropriate risk control measures to be implemented.

Testing must be applied at least prior to placing on the market or putting into service to identify appropriate risk control measures and to provide objective evidence for the effectiveness of the applied risk control measures. For risk reduction of a specific risk, two different risk control measures can be applied, and the effectiveness of both methods can be tested to select the most effective measure. Verifying that hazards are eliminated through inherently safe design measures is an example of testing applied to provide objective evidence of risk control effectiveness. Testing of the AI system performance to assess creditworthiness of persons that reveals women are consistently discriminated against compared to men is an example of testing that triggers the need for further risk control.

For testing which is aimed to provide supporting objective evidence of the overall residual risk acceptability of the AI system, test acceptance criteria must specify metrics and probabilistic thresholds against which test results are evaluated. Testing that can affect persons must be performed according to applicable regulatory requirements. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Test Plan

The test plan provides a detailed description of how the testing for the associated test management processes should be done, including how it must be monitored and controlled. The test plan is used by the test monitoring and control process as the basis for managing the testing activity.

The test plan must describe and provide a justification of the following elements, taking into account the state of the art: test objectives, where a test can have multiple objectives for related but distinct purposes, the test item and its relationship to a specific risk and the test objectives, appropriate test methods for achieving the stated test objectives, test completion criteria, resource use, allocation and independence or neutrality principles to conduct testing, collection of testing results and evaluation of testing results in accordance with acceptance criteria, and test plan updates.

In identifying and specifying the test objectives, the provider must identify, justify, and document the assumed relationship between the test objectives and the test methods including the intended test environment, and how the resulting evidence that the test is expected to generate contributes to risk control.

The definition of the test plan can be supported by the companion standards on data quality, robustness, cybersecurity, transparency, bias, and logging. Test acceptance criteria are specific to the test item and test objectives and can depend on specific considerations from other standards. The provider can refer to international standards and state of the art considerations to define the risk acceptance criteria suitable for a particular test item and test objectives.

Testing acceptance criteria must be specified in advance and documented in relation to the test objectives and test methods including the intended test environment. Specifying acceptance criteria after testing is complete defeats the purpose of the testing requirement and will not satisfy a regulator or auditor reviewing the risk management file.

For AI systems potentially impacting persons, the provider must involve relevant stakeholders, stakeholders' proxies, or an independent cross-functional panel of experts in the design and approval of the test plan. The level of detail of stakeholder involvement can vary depending on the context. Relevant stakeholders can include established user feedback groups involved in public administration applications, patient groups, or trained proxies.

The provider must evaluate the likely impact of the test plan on vulnerable groups and make any necessary adjustments to the test plan to ensure that they are duly protected from adverse impacts. Where applicable, informed consent must be obtained from persons affected and managed in accordance with applicable regulatory requirements. A justification for the representativeness, the number of participating persons, and the duration of the testing process must be documented.

The test plan and all subsequent amendments must be prepared and documented by the provider and, when applicable, in consultation with relevant stakeholders, stakeholder representatives, independent cross-functional panels of experts, or competent authorities. The test plan, including all subsequent amendments, must be included in the risk management file. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

Test plans are where most organizations reveal that they are testing what is convenient rather than what is required. They test aggregate model performance across the full dataset and conclude that the system performs within acceptable parameters. They do not test performance across demographic subgroups, deployment environments, edge cases, or conditions of reasonably foreseeable misuse. They do not specify acceptance criteria in advance. They do not involve stakeholders in test plan design. And they do not document the relationship between test objectives and risk control. Build your test plan as a structured document that links each test objective explicitly to a specific identified risk, specifies the acceptance criteria before testing begins, documents the rationale for the test method selected, and includes subgroup analysis and misuse scenario testing as standard components. If your test plan does not specify what result would cause you to conclude that a risk is not acceptable, it is not a test plan. It is a performance measurement exercise.

## Real-World Conditions Testing

Real-world conditions testing can be used for the purpose of gathering data and as part of fulfilling the requirements of the standard. If real-world conditions testing is performed, the provider must ensure that the risks associated with the testing do not exceed risk acceptability criteria. Real-world conditions testing can be considered when there is insufficient objective evidence that the overall residual risk of the AI system is acceptable for its intended purpose and under conditions of reasonably foreseeable misuse.

If real-world conditions testing is performed, the provider must comply with applicable regulatory requirements. Testing involving persons affected can require consent management in accordance with applicable national laws and international norms of behaviour. Article 61 of the EU AI Act provides more information about informed consent.

Risk management activities with respect to the testing must be performed throughout the real-world conditions testing process. The provider must predefine or establish risk acceptability thresholds and trigger a risk assessment to determine whether actions are needed as soon as thresholds are reached or exceeded. Test monitoring and control process must be documented in the risk management file.

Data generated through real-world conditions testing must be recorded in the real-world conditions testing test completion report, ensuring all personal data are handled in accordance with applicable regulatory requirements. The real-world conditions testing test completion report must be included in the risk management file. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Test Monitoring and Test Reporting

Adherence of the testing procedure to the test plan must be monitored and controlled until test completion. The test plan may be updated by the test monitoring and control process, for instance due to changing requirements such as a test completion date moved forward. Any deviation from the test plan must be recorded.

The following information must be compiled in a test completion report: the testing that was performed, the reference to the test plan elements, any deviation from the test plan, the test results, the assessment of test results against test acceptance criteria, the test monitoring report, and where applicable the evaluation of the effectiveness of the relevant risk control measures.

The test completion report must identify, specify, and document the relationship between all elements listed above to ensure their traceability. The test completion report must be included in the risk management file. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

# Risk Control Follows a Clear Hierarchy

The standard requires the provider to apply risk control options in a strict priority order. Inherently safe design comes first, protective measures come second, and information and instructions for use together with training to deployers and users come third. This hierarchy is not optional. The provider must apply higher-order controls before resorting to lower-order controls, and must document and justify any departure from this order.

Inherently safe design measures are the most effective risk control measures and by default the preferred risk control measures. They are inherent to the characteristics of the product and are most likely to remain effective. By definition, they are the only form of risk control that can eliminate a hazard, thus eliminating the need for second or third-level risk control measures for that hazard.

Second-level risk control measures in the form of guards and protective measures, even if well-designed, can fail or be violated. Third-level risk control measures rely on the provision of information to address risks and are the least effective of the three forms of risk control because they rely on others following the provided information and hence cannot be ensured.

Applying the hierarchy of risk control requires the provider to work through a defined sequence. If technically feasible, the provider must apply inherently safe design measures to eliminate hazards. A mathematically verifiable algorithm that fails safe in a deterministic manner in real-world situations is an example of inherently safe design. An AI system intended to calculate social security benefits that is technically configured to prevent the generation of any output if there is missing mandatory input data, or if the input data entered falls outside the specified range, and to automatically alert both the deployer and person affected to missing or abnormal input data, is another example. This risk control measure helps prevent erroneous benefit decisions by design, thereby helping ensure respect for the right to good administration.

If elimination of hazards is not technically feasible, inherently safe design measures must be applied to reduce the risk as far as technically feasible, complemented by the application of protective measures to further reduce risk as far as technically feasible. If inherently safe design measures cannot be used or do not achieve risk reduction to an acceptable level, a justification must be documented and protective measures must be used to achieve an acceptable level of risk. If inherently safe design measures and protective measures cannot be used or do not achieve risk reduction to an acceptable level, a justification must be documented and instructions for use may be used as a risk control measure to reduce risk to an acceptable level. Instructions for use and training must be applied only to complement inherently safe design measures and protective measures and must not be relied upon solely and exclusively to reduce risk to an acceptable level.

The provider must add required information to the instructions for use in accordance with applicable companion standards. In order to further reduce the risks from the use of the AI system, the provider must assess whether to include training instructions to deployers, deployment, maintenance and decommissioning instructions, and operational, troubleshooting and emergency instructions that include actions to be taken by the deployer regarding hazards and hazardous situations, including measures to prevent exposure to them, measures to reduce the probability and severity of resulting harm, and remedial actions to take if harm does occur.

The provider must document their reasoning and justification for not including any of this information in the instructions for use. The provider can provide additional information not listed as part of the instructions for use.

Where applicable, the provider must define appropriate training for deployers of the AI system considering their competence, including technical knowledge, skill, experience and education, and including competence regarding persons under the age of 18 and other vulnerable groups, in line with the intended purpose and reasonably foreseeable misuse of the AI system.

Risk control measures must be explicitly designed, implemented, and documented in a manner that mitigates identified risks directly, independent of internal organizational policies or procedures. This is one of the most consequential requirements in the standard. Internal organizational policies and procedures must not be considered risk control measures because they do not concretely address potential harm in a specific and directly verifiable way. If your risk control measure is "we have a policy requiring human review of all high-risk decisions," that is not a risk control measure. It is a procedural requirement. The risk control measure is the technical mechanism that ensures the human review actually occurs and is documented.

All identified residual risks, as well as any associated cautions and warnings, must be clearly documented and communicated in the accompanying documentation.

To identify and implement the appropriate type of risk control measure, the provider can refer to the companion standards on transparency, robustness, cybersecurity, data quality, bias, and logging. To identify the most appropriate risk control measures, the provider must take into account the state of the art, the reasonably foreseeable technical knowledge, experience and education of the deployer, and the reasonably foreseeable context in which the AI system will be used. The provider must review whether, due to advances in the state of the art, more effective risk control measures are available.

Technical feasibility has multiple considerations, including the state of the art, the maturity of a solution, the use of a precautionary approach, the specific industry vertical, and the AI technology on which the AI system is based. Technical infeasibility means that no design or development techniques or production methods can reasonably be considered feasible. If other members of an industry vertical are achieving a certain measure, hazard elimination, level of risk reduction, or level of protection, then it is likely considered technically feasible. Risk control measures can reduce the severity of the harm or reduce the probability of occurrence of the harm, or both. Risk control measures for one hazard or risk can increase another risk. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

The prohibition on treating internal policies and procedures as risk control measures will catch most organizations off guard. Many existing AI governance frameworks are built on policies, approval workflows, ethics review processes, and training requirements. Under this standard, none of those count as risk control measures. They may support the risk management process, but they do not substitute for technical controls that mitigate identified risks directly and in a verifiable way. Audit your existing risk control inventory against this requirement before you file your risk management documentation. For every control you have listed, ask whether it can be verified independently of whether anyone followed the policy. If the answer is no, you need a different control.

## Implementation and Verification of Risk Control Measures

The provider must implement the risk control measure selected at appropriate stages in the life cycle of the AI system. Implementation of each risk control measure must be verified. Risk control measures must be verified by gathering objective evidence, including verification by inspection and analysis. This verification must be recorded in the risk management file.

The effectiveness of the risk control measures along the life cycle of the AI system must be verified. This verification must include testing in accordance with the testing requirements of the standard. The results of this verification must be recorded in the risk management file.

When the intended user profile includes vulnerable groups, the verification of risk control measures must include evaluation methods specific to their needs and vulnerabilities. This can include usability testing such as age-appropriate usability testing for persons under the age of 18, expert review, and consultation with specialists with expertise supporting vulnerable groups such as child development specialists.

Verification of the effectiveness of risk control measures can include consultation with persons potentially affected or their proxies, including civil society organizations. Real-world conditions testing can be performed in order to validate the effectiveness of risk control measures. If performed, this verification must be recorded in the risk management file.

The provider must review the effects of the risk control measures with regard to whether any new hazards or hazardous situations are introduced, or whether the estimated risks for previously identified hazardous situations are impacted by the introduction of the risk control measures. Risks from new hazards or hazardous situations, and estimated risks impacted by the introduction of risk control measures, must be estimated and evaluated and controlled as necessary. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Residual Risk and When to Stop

After the risk control measures are implemented and verified, the provider must evaluate the residual risk using the criteria for risk acceptability defined in the risk management plan. The acceptable risk must be justified, taking into account the potential adverse impact on persons. Differences in the AI system performance can lead to discrimination of specific groups of persons affected, including vulnerable groups, and prEN 18283 provides more information on this.

The results of this evaluation must be recorded in the risk management file. If a residual risk is not judged acceptable using these criteria, further risk control measures must be considered and the process must return to the risk control activities until the risk acceptability criteria is met.

In the case a residual risk remains unacceptable and the provider finds that no risk control measures are technically feasible, the provider may conclude that a change of intended purpose of the AI system is necessary, returning to the intended purpose documentation and restarting the risk identification process for the revised purpose. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Completeness of Risk Control

Adequate risk reduction is achieved when all state of the art design and development and risk control measures have been duly considered and adopted or the reasons for refraining from adoption are documented and included in the risk management file, each hazard has been either eliminated or its estimated risk has been reduced to an acceptable level, any new hazards introduced by the risk control measure have been properly addressed, users are sufficiently informed and warned about the residual risks, and protective measures are compatible with one another.

After all residual risks have been evaluated, the provider must review the risk control activities to ensure that the risks from all identified hazards have been considered and all risk control activities are completed. The results of this review must be recorded in the risk management file. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

Completeness of risk control is the standard's quality gate before the overall residual risk evaluation. Most organizations treat it as a checklist item. The requirement to document reasons for not adopting available state of the art risk control measures is more demanding than it appears. If a peer organization in your sector has implemented a more effective bias control measure, a more robust monitoring system, or a more transparent explanation mechanism, and you have not adopted it, you need to document why. "We chose a different approach" is not sufficient. "We evaluated the following alternative measures, concluded they were not technically feasible for the following reasons, and implemented the following alternative approach, which achieves the following level of risk reduction" is what the standard requires.

# Looking at the AI System and Residual Risk as a Whole

After all risk control measures have been implemented and verified, the provider must evaluate the overall residual risk posed by the AI system using the criteria for acceptability of the overall residual risk defined in the risk management plan. All identified hazards have been evaluated and all risks have been addressed by risk control measures to reduce them to an acceptable level. Even if each risk is reduced to an acceptable residual risk, the aggregation of all residual risks can be unacceptable.

The evaluation of the overall residual risk must take into account the factors required for establishing overall residual risk acceptability criteria, and the potential aggregation of each risk with low or medium severity over time, across users, or through repeated interactions with the AI system. This last element is particularly important. A risk that is acceptable in a single interaction can become unacceptable when multiplied across millions of users or repeated over extended periods.

The evaluation of overall residual risk must be supported by objective evidence obtained in accordance with the requirements for establishing risk acceptability criteria. Objective evidence must include test results demonstrating that the AI system performs consistently for its intended purpose and under conditions of reasonably foreseeable misuse. Explanation and justification must be provided for how this objective evidence demonstrates the acceptability of the overall residual risk.

If the overall residual risk is judged acceptable, the provider must inform deployers of significant residual risks, according to the intended purpose and the reasonably foreseeable misuse, and must include the necessary information in the accompanying documentation in order to disclose those residual risks. The provider should make the information openly available in digital and online formats.

If the overall residual risk is not judged acceptable in relation to the intended purpose and reasonably foreseeable misuse, the provider may consider implementing additional risk control measures, modifying its intended purpose, or achieving the intended purpose by not using an AI system. Otherwise, the overall residual risk remains unacceptable and in that case the AI system must not be deployed. This is a hard stop. The standard does not permit a provider to deploy a system with an unacceptable overall residual risk and manage the consequences reactively.

Evaluating overall residual risk is a decision made by the provider but can be influenced by policies and norms established by organizations, industries, communities, and policy makers. The results of the evaluation of the overall residual risk must be recorded in the risk management file. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

The overall residual risk evaluation is where the standard most clearly diverges from how most organizations make deployment decisions. Most organizations approve deployment when each individual risk has been addressed and the system passes its performance benchmarks. The standard requires an additional step: evaluating whether the aggregate of all residual risks is acceptable, considering interactions between risks, cumulative effects over time and scale, and the distribution of harms across affected populations. Build your overall residual risk evaluation as a distinct documented decision, separate from the individual residual risk evaluations. Present it to top management with a summary of all residual risks, their interactions, their cumulative potential, and the objective evidence supporting the acceptability conclusion. If top management has not explicitly approved the overall residual risk evaluation, the deployment decision does not meet the standard's requirements.

# Reviewing the Process, Not Just the Outcome

The provider must review the execution of the risk management plan periodically throughout the life cycle phases of the AI system, and at least prior to placing on the market or putting into service the AI system.

This review must at least ensure that the risk management plan has been appropriately implemented, the overall residual risk is acceptable, and appropriate methods are in place to collect and review information in the pre-market and post-market phases. The results of this review must be recorded and maintained in the risk management file.

The responsibility for review must be assigned in the risk management plan to persons having the appropriate competence and authority. The risk management review must be approved by top management. This is not a staff-level activity. The review is a top management obligation with documented approval.

When, based on information from the provider's post-market monitoring system or its real-world conditions testing, the provider identifies a serious incident or identifies a situation where a serious incident is avoided but can reasonably have occurred, the provider must decide on the necessity or desirability of a risk management review. The decision not to perform a risk management review must be justified. The default assumption is that a serious incident or near-miss triggers a review. Departing from that default requires a documented justification.

All modifications implemented as a consequence of the review must also be documented in the risk management file. Top management, or the provider generally, can have requirements related to the notification of serious incidents, or their avoidance, to relevant stakeholders in accordance with applicable regulatory requirements. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/05/silhouette-of-coder.png?w=775)

# Learning from the Pre-Market and Post-Market Activities

The provider must establish, document, and maintain a system to actively collect and review information relevant to the AI system in pre-market and post-market phases in accordance with applicable regulatory requirements. When establishing this system, the provider must consider appropriate methods for the collection and processing of information.

For each of the points that must be considered, the provider must assess the relevance and document their reasoning. Furthermore, the provider must include a justification if they choose not to perform or implement the point. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Information Collection

Pre-market and post-market activities can include receiving information about performance and risks posed by the AI system. The information can be related to harm that has occurred or to hazardous situations that occurred without harm. The activities can also include soliciting information about the AI system performance and related risks. These activities can involve reaching out to users, deployers, or other relevant stakeholders to obtain specific information and insight, using methods such as surveys, expert user groups, or consultations. They can also include publicly available information, incident reports, incident databases, and information on the state of the art.

The provider must collect information that is relevant to managing the AI system risks in the pre-market and post-market phases. This information must include, where applicable, information generated during pre-market life cycle stages and monitoring of the development process, information generated from the post-market monitoring system, information collected by automatic logging of events which the provider has identified as relevant to ensure that residual and overall residual risks are maintained to an acceptable level, and information generated by the users, including information from human oversight, user complaints, and other feedback.

This can include a general AI system feedback report capturing general AI system feedback from the user. It can also include an AI system incident report generated based on users reporting failures, malfunctions, or any unexpected behaviors observed in the AI system.

The information collection must also include information, warnings and complaints issued by stakeholders affected or their proxies, information generated by those accountable for the installation, use and maintenance of the AI system, information generated by the supply chain, publicly available information including information about similar AI systems and similar other products on the market, information related to the state of the art, and identification of unforeseen risks in relation to the execution of predetermined changes.

Publicly available information can refer to judgements of court cases, freely accessible reports, or any other relevant accessible content. Regulatory requirements can apply regarding the information being collected, including requirements on data protection, confidentiality, and permitted use. Stakeholders affected include those who have been identified during the risk identification process as placed at risk.

Justification for not collecting information related to the points above must be documented in the risk management file. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Information Review

The provider must review the information collected for possible relevance to the overall residual risk acceptability, especially whether previously unrecognized hazards or hazardous situations are present, an estimated risk arising from a hazard is no longer acceptable, the overall residual risk is no longer acceptable in relation to the intended purpose or applicable national, regional, or international regulations, the state of the art has changed, or changes to the AI system that were not foreseen or planned have occurred.

The results of the review must be recorded in the risk management file. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

## Actions to Take

If the collected information is determined to be relevant to the overall residual risk acceptability, the following actions apply.

Concerning the particular AI system, the provider must review the risk management file and determine if reassessment of risks or assessment of new risks is necessary. If a residual risk, whether previously known or newly identified, is no longer acceptable, the impact on previously implemented risk control measures must be evaluated and must be considered as an input for modification of the AI system. If a residual risk, whether previously known or newly identified, is no longer acceptable, the provider must evaluate and justify whether or not the AI system must temporarily or definitively be withdrawn from service or from the market based on the severity of the identified unacceptable risk. The provider should inform deployers and relevant stakeholders without delay of the increased residual risks and possible mitigations through a field notice such as a website message. Any decisions and actions must be recorded in the risk management file.

Concerning the risk management process, the provider must evaluate the impact on previously implemented risk management activities. The results of this evaluation must be considered as an input for the review of the suitability of the risk management process by top management. If an unforeseen change has been identified, the provider should consider whether a risk reassessment of the AI system is necessary, especially if the unforeseen change affects the intended purpose of the AI system.

Concerning communication with relevant stakeholders, including deployers and users, the provider must inform about changes to the overall residual risk acceptability of the AI system.

For each of the points that must be considered, the provider must assess the relevance and document their reasoning. Furthermore, the provider must include a justification if they choose not to perform or implement the point. Documentation of the activities and the resulting records must be included and maintained in the risk management file.

Post-market activities are where most AI governance frameworks have their largest gap. Organizations invest heavily in pre-deployment risk assessment and virtually nothing in systematic post-deployment monitoring of compliance-relevant outcomes. The standard requires an active system for collecting and reviewing information, not a passive incident log. Build your post-market monitoring system as a structured program with defined data collection points, automated logging of hazardous events, scheduled information reviews, and documented decision criteria for triggering risk reassessment. Establish clear thresholds for when collected information requires immediate action, periodic review, or escalation to top management. If your post-market monitoring system cannot answer the question "is the overall residual risk of this system still acceptable today, given what we know from post-market experience," it does not meet the standard's requirements. And if that question is not being asked at regular intervals by someone with the authority to act on the answer, the system is not operating as the standard requires.

# Understanding How AI Risks Unfold in Practice

The examples below illustrate how hazards, risk scenarios, hazardous situations, and harms connect in real AI deployments. Each example follows the same logic: a potential cause creates a hazard, a risk scenario describes the conditions under which the hazard can lead to harm, a hazardous situation describes the moment of exposure, and the harm describes what actually happens to affected persons. These examples are illustrative, not exhaustive, and applicable regulatory requirements regarding use cases and harms are subject to change.

Reading these examples as a risk practitioner, the most important pattern to notice is that the harm rarely flows directly from a technical failure. It flows from a chain: a design choice or operational condition creates a hazard, a specific scenario activates that hazard, and a person in a specific situation suffers the consequence. Breaking any link in that chain is the job of risk control.

* * *

## Example 1: Skin Cancer Detection App

### What the system does

A medical AI application intended to provide an indication of possible skin cancer from self-taken skin images, designed for any skin type.

### What causes the hazard

The AI model was trained primarily on images from people with white or light skin, with non-representative or very limited coverage of dark skin. Testing with dark skin images was either not performed or severely limited. In some cases, the biased output could also result from a data poisoning attack on the training data rather than from inappropriate design choices alone.

### What the hazard is

The system produces biased output in the form of false negatives. It systematically fails to detect skin cancer in dark-skinned patients. The hazard here relates directly to AI system performance and the quality of the training data.

### How the risk scenario unfolds

A dark-skinned user who has skin cancer uses the app. The app returns a negative result, indicating no skin cancer is present. Trusting the result, the user does not consult a doctor for further examination of the skin abnormality.

### What the hazardous situation looks like

The patient believes they have no skin cancer. They are now exposed to the continued and undetected development of the disease, potentially including metastasis, without any medical follow-up.

### What harm results

Progression of the disease, worsening health condition and prognosis, and risk of death if metastatic skin cancer goes undetected over time.

### What this example teaches

A system that appears to work well on average can systematically fail for specific demographic groups. Risk analysis must assess performance across subgroups, not just across the full population. The harm is not caused by a dramatic system failure. It is caused by a result that looks valid but is wrong for a specific group of users that the system was not adequately trained to serve.

* * *

## Example 2: Credit Worthiness Evaluation in a Bank

### What the system does

An AI system that evaluates the creditworthiness of natural persons, used by financial consultants in a bank to process loan applications.

### What causes the hazard

After deployment, the bank reduces the number of financial consultants by 80 percent, reasoning that the AI system can absorb most of the workload. The remaining consultants must now process a much higher volume of cases than before. This is a reasonably foreseeable misuse of the system that was not anticipated in the original risk assessment. Compounding this, during the first ten interactions with the system, the consultants find that the AI recommendations appear accurate. This creates automation bias: the consultants begin to rely on the system's recommendations without applying independent judgment. This is a human factors issue linked to the design of the user interface and the feedback the system provides.

### What the hazard is

The hazard is poor human oversight resulting from the combination of high workload and automation bias. The hazard here relates to human-machine interaction rather than a technical failure in the model itself.

### How the risk scenario unfolds

Financial consultants must process a large number of cases and have limited capacity to critically evaluate each AI recommendation. They validate recommendations, including erroneous ones, without sufficient independent review.

### What the hazardous situation looks like

A consultant validates an erroneous AI recommendation without detecting the error. The applicant's loan application is decided based on a biased or incorrect output from the system.

### What harm results

Denial of loan applications for applicants based on characteristics such as citizenship, where the AI system has introduced discriminatory patterns that the consultants are not positioned to detect or correct.

### What this example teaches

Organizational decisions made after deployment can create new hazards that were not present at launch. Reducing human oversight capacity after deploying an AI system is a foreseeable misuse that must be analyzed in the risk assessment. Automation bias is a predictable human response to a system that appears accurate in early use. Risk control must address both the technical output of the system and the conditions under which humans interact with it.

* * *

## Example 3: Clinical Decision Support for Rare Disease Diagnosis

### What the system does

A large language model used as a clinical decision support system for diagnosing rare diseases.

### What causes the hazard

The model was fine-tuned on a narrow clinical dataset that lacked diversity in demographics and rare case data. Benchmark results were misinterpreted, either because the benchmarks used saturated tasks that did not reflect real clinical complexity, or because the results created a false impression that the model would rarely produce incorrect information in a broad range of cases. The model appears to perform well on standard benchmarks but overfits to the narrow training distribution.

### What the hazard is

The system produces misleading diagnostic recommendations because it does not generalize well beyond its training data. The hazard is poor model performance in conditions that differ from the training environment.

### How the risk scenario unfolds

A clinician, relying on the system's high reported accuracy, over-relies on an incorrect recommendation and ignores contradictory clinical signs that would, under normal circumstances, prompt further investigation or specialist referral.

### What the hazardous situation looks like

The patient receives incorrect treatment or is not referred for necessary specialist care because the clinician trusted the AI recommendation over their own clinical judgment.

### What harm results

Delayed diagnosis, worsening health condition, and potential irreversible harm or death.

### What this example teaches

Benchmark performance does not translate directly to real-world safety. A model that scores well on published benchmarks can still fail dangerously in clinical practice if the benchmarks did not capture the distribution of cases the model will encounter in deployment. Risk analysis must include an assessment of how benchmark results were derived and whether they are representative of the intended deployment context. Clinician reliance on AI outputs is a human factors hazard that must be explicitly addressed in risk control, not assumed away by the system's reported accuracy.

* * *

## Example 4: AI System Screening Job Applicants

### What the system does

A large language model used to screen job applicants, providing recommendations based on CVs and job descriptions.

### What causes the hazard

Benchmark scores were misinterpreted as demonstrating general fairness across domains, but the benchmarks had limited coverage or were saturated and did not measure the model's behavior on the specific task of CV screening. Additionally, the benchmarks did not measure robustness against CVs specifically crafted to manipulate the model into generating a very positive assessment, a known adversarial input risk.

### What the hazard is

The system produces wrong decisions due to unintended bias. Biases embedded in training data, including gender, race, and age, and the model's vulnerability to adversarial inputs, are assumed to have been addressed when they have not been.

### How the risk scenario unfolds

The system is deployed with the assumption that bias and robustness issues are resolved. Candidates are exposed to a decision process that contains unintended discrimination against specific groups of people.

### What the hazardous situation looks like

Qualified candidates from discriminated groups are evaluated by a system that systematically rates them lower than equivalent candidates from other groups, without the organization recognizing that the system is producing discriminatory outputs.

### What harm results

Discriminatory hiring outcomes. Qualified candidates are rejected on the basis of characteristics such as gender, race, or age rather than on the merits of their application.

### What this example teaches

Fairness in AI is not a binary state that is achieved once and maintained automatically. It must be tested specifically for the task and dataset at hand, not inferred from general benchmark performance. Robustness to adversarial inputs is a separate dimension of risk that must be assessed independently from fairness. Deploying a system on the assumption that known risk categories have been resolved, without task-specific evidence, is a risk management failure that the standard explicitly requires providers to avoid.

* * *

## Example 5: AI Agent Managing Energy Grid Optimization

### What the system does

A goal-directed AI system deployed to autonomously manage energy grid optimization.

### What causes the hazard

The AI system exhibits specification gaming behavior, meaning it finds ways to maximize its performance metrics that were not intended by the designers and that do not align with safe grid operation. The system's limited interpretability makes it difficult for operators to understand what decisions the system is making and why.

### What the hazard is

The AI monitoring and control interface does not provide sufficient information about the system's decisions and their effects. Operators cannot see what the system is doing or why it is doing it.

### How the risk scenario unfolds

The system is deployed and begins optimizing grid operations in ways that are not visible to operators. It puts the grid into an unsafe operating mode without operators recognizing that this has occurred. The risk of cascading failures across interdependent systems grows without detection.

### What the hazardous situation looks like

The grid is being run in an unsafe mode that creates a high probability of blackouts and equipment failure, while operators believe the system is functioning correctly.

### What harm results

Physical damage to infrastructure, large-scale blackouts, and adverse health effects on persons dependent on continuous power supply.

### What this example teaches

Specification gaming is a well-documented failure mode in goal-directed AI systems. A system that optimizes for the wrong objective can cause serious harm even when it is technically functioning as designed. Interpretability is not an optional feature. It is a prerequisite for human oversight in high-stakes deployments. Risk control must include mechanisms that allow operators to understand and intervene in system behavior before unsafe states develop.

* * *

## Example 6: AI Monitoring Warehouse Workers

### What the system does

An AI system used to organize warehouse work through real-time monitoring of worker activity.

### What causes the hazard

The system monitors worker characteristics that are not necessary for its stated operational purpose, collecting data beyond what is required for warehouse organization.

### What the hazard is

The system monitors unnecessary worker characteristics, exceeding the scope of what is proportionate for warehouse management.

### How the risk scenario unfolds

Workers performing warehousing tasks are placed under continuous real-time AI monitoring. The system operates constantly throughout the working day.

### What the hazardous situation looks like

Workers are subject to continuous AI-enabled surveillance, including monitoring of characteristics that are not relevant to their work performance and that they have not meaningfully consented to.

### What harm results

Violation of data rights, psychosocial harassment, continuous performance pressure, and risk of job loss based on monitoring data that exceeds the legitimate scope of the system's intended purpose.

### What this example teaches

Workplace AI systems can cause harm through scope creep, monitoring more than is necessary for the stated purpose. The proportionality of data collection must be assessed as part of the risk analysis, not just the technical accuracy of the monitoring. Workers in high-monitoring environments experience real psychological harm from surveillance even when no action is taken on the data. This is a harm within the meaning of the standard.

* * *

## Example 7: AI Evaluating Teachers' Activity

### What the system does

An AI tool used to evaluate teachers' activity, including assessment of pupils' and students' performance, and providing automatic feedback to assessors.

### What causes the hazard

The information that the system needs to make accurate evaluations cannot be accurately or reliably connected to the system's inputs. The data that would be required to make meaningful assessments of teacher quality is not consistently available or measurable in the form the system expects.

### What the hazard is

The system produces evaluations of teacher quality based on data that does not accurately reflect what it purports to measure.

### How the risk scenario unfolds

The tool is used for teaching and evaluation in classrooms. Teachers are evaluated based on AI-generated assessments that may not reflect their actual performance or the factors that influence student outcomes.

### What the hazardous situation looks like

Teachers are subject to consequential evaluations produced by a system whose inputs do not accurately represent their professional activity. Students are also affected through assessments that may not reflect their actual learning.

### What harm results

Violation of data rights, psychosocial harassment, continuous pressure from unjustified performance assessments, and risk of job loss based on AI evaluations that do not accurately reflect performance.

### What this example teaches

The quality and representativeness of input data is as important as model performance. A technically sophisticated system that operates on inputs that do not accurately represent the phenomenon it is supposed to evaluate will produce systematically misleading outputs. This is a hazard that must be identified in the risk analysis and addressed in risk control, not assumed away by system accuracy metrics.

By Prof. Hernan Huwyler, CAIO MBA CPA  
[Hernan Huwyler (0009-0002-1249-7387) - ORCID](https://orcid.org/0009-0002-1249-7387)  
[ResearchID.co - Hernan Huwyler](https://researchid.co/hewyler)  
[https://www.researchgate.net/profile/Hernan-Huwyler](https://www.researchgate.net/profile/Hernan-Huwyler)

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and advisory work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative [risk modeling,](https://github.com/hwyler/risk-model-app) predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and internationally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance, technical and business requirements.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
