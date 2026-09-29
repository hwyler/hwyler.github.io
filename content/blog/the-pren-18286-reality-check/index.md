---
title: "The prEN 18286 Reality Check: Ditch Generic AI Governance"
date: 2026-06-17
tags: 
  - "ai"
  - "ai-governance"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "business"
  - "chatgpt"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "pren18286"
  - "pren18288"
  - "technology"
---

AI quality management systems look complete on paper and collapse the moment a notified body, regulator, or internal auditor asks a simple question. Show me the evidence that your controls are actually operating, traceable to this specific AI system, connected to a named accountable owner, and capable of detecting a serious incident before a civil society organization reports it to a market surveillance authority.

That gap is about to matter more.

prEN 18286 sets out the requirements for a quality management system for providers of AI systems under the EU AI Act. It is being developed by CEN/CLC JTC 21 and is currently under CEN enquiry, meaning it is not yet a harmonized standard and does not yet create a presumption of conformity. What it does create is the most detailed picture available of what regulators and notified bodies will expect when Article 17 conformity assessment begins in earnest. Organizations that wait for final publication before beginning implementation will not have time to build what the standard actually requires.

This discussion covers what the standard says, clause by clause and in its own words, and where implementation will break down.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/06/chatgpt-image-sep-11-2026-10_43_07-pm.png?w=1024)

* * *

## What the Standard Is and What It Is Not

The standard specifies requirements and provides guidance for the definition, implementation, maintenance, and improvement of a quality management system for organizations that provide AI systems. Its purpose is to support the organization in meeting applicable regulatory requirements.

> _`Quality, the set of control characteristics of an AI system that fulfils the EU AI Act regulatory requirements, ensuring the protection of health, safety, and fundamental rights throughout the lifecycle. Customer satisfaction is irrelevant here. Regulatory compliance is the only measure that counts.`_

Quality, in this context, means something specific and unfamiliar to most AI governance teams. The standard defines quality as a set of characteristics of an object that fulfils regulatory requirements. It adds explicitly that quality includes the protection required by applicable regulatory requirements aimed at ensuring and maintaining the protection of health, safety, and fundamental rights. It notes that in the context of this document, quality pertains to regulatory compliance to the EU AI Act, and that it differs from the concept of quality in ISO 9001, which includes expectations of customers.

This is not a customer satisfaction framework. It is not a capability maturity model. It is not a general AI governance standard. It is a regulatory compliance instrument built on product safety logic, specifically the New Legislative Framework that governs how products are placed on the EU market.

The standard is intended for use by providers irrespective of size, nature, or location, but its requirements are specifically tailored to support providers operating inside the European Union and those located outside the Union who are active in the European market or intend to enter it. A quality management system implemented under this standard can be directly associated with one or more AI systems that are intended to be put into service or placed on the market. It does not require the provider to maintain a separate quality management system if an existing sectoral QMS can incorporate its requirements. The standard uses ISO 13485 as its architectural reference, not ISO 9001 or ISO/IEC 42001, because ISO 13485 is itself oriented toward demonstrating compliance with regulatory requirements rather than customer satisfaction. This is a deliberate choice with significant implementation implications for organizations that currently anchor their AI governance to ISO/IEC 42001 or ISO 9001.

The European Commission's Joint Research Centre has formally assessed ISO/IEC 42001 as not aligned in objectives and approach with the AI Act. The JRC finding is that ISO/IEC 42001 is inadequate for harmonization under the AI Act. prEN 18286 was developed specifically to fill that gap. Organizations relying on ISO/IEC 42001 certification as their primary EU AI Act compliance instrument should treat that reliance as a documented risk, not a compliance position.  
  
The EU Comission assessment does not mean you should discard ISO/IEC 42001. While prEN 18286 dictates the exact compliance path for high-risk systems under Article 17, these strict QMS obligations only apply to a fraction of enterprise deployments. Most of your current inventory, including customer-facing chatbots and internal AI productivity agents, falls outside the high-risk scope, requiring only basic transparency disclosures under the AI Act.

Organizations recognize that regulatory compliance is not the same as managing internal business risk. ISO/IEC 42001 remains the most effective tool to structure enterprise-wide quality and operational risk management for these non-high-risk applications. It sets a horizontal baseline for industry best practices, protecting the company from financial, operational, and reputational failures that Brussels regulations completely ignore.

The correct strategy is to deploy ISO/IEC 42001 as your universal, horizontal governance layer across the entire organization. You then layer the specific prEN 18286 and JTC 21 requirements as a vertical extension solely for the systems that trigger high-risk compliance mandates. This converged process ensures efficiency because the JTC 21 standards explicitly reference and build upon the ISO/IEC 42001 framework anyway. You achieve a single, cohesive governance engine instead of managing fragmented, redundant compliance silos.

* * *

## The Definitions That Will Determine Whether Your Audit Succeeds or Fails

The standard introduces defined terms that carry specific regulatory weight. Using familiar terms with different meanings is one of [the most common sources of audit failure.](https://hernanhuwyler.wordpress.com/2026/03/13/ai-performance-auditing/) The definitions below are drawn directly from the standard's own text, with annotations on where the gap between common usage and regulatory meaning is largest.

**AI system.** The standard defines this as a machine-based system that is designed to operate with varying levels of autonomy and that can exhibit adaptiveness after deployment, and that, for explicit or implicit objectives, infers, from the input it receives, how to generate outputs such as predictions, content, recommendations, or decisions that can influence physical or virtual environments. The standard adds that the verb can represents a possibility and that not all AI systems that fit this definition have the ability to adapt after deployment. The definition is drawn directly from Article 3(1) of the AI Act and is broader than most technical definitions used within engineering teams. Rule-based systems with post-deployment adaptiveness are within scope.

**Provider.** A natural or legal person, public authority, agency, or other body that develops an AI system or a general-purpose AI model, or that has an AI system developed and places it on the market or puts it into service under its own name or trademark, whether for payment or free of charge. The standard notes that a distributor, importer, deployer, or other third party can be considered a provider in certain circumstances. White-labeling, rebranding, and substantial modification all carry the risk of converting a downstream organization into a provider with full Article 17 obligations.

**Deployer.** A natural or legal person, public authority, agency, or other body using an AI system under its authority, except where the AI system is used in the course of a personal non-professional activity. Deployers have distinct obligations under the AI Act, and the QMS must be designed to support deployer compliance through the instructions for use, not assume that deployer obligations are handled separately.

**Intended purpose.** The use for which an AI system is intended by the organization, including the specific context and conditions of use, as specified in the information supplied by the organization in the instructions for use, promotional or sales materials and statements, as well as in the technical documentation. Marketing claims define regulatory obligations. What you say the system does, and where you say it works, becomes the baseline against which conformity is assessed.

**Reasonably foreseeable misuse.** Use of an AI system in a way that is not in accordance with its intended purpose, but which can result from reasonably foreseeable human behavior or interaction with other systems, including other AI systems. You cannot limit your QMS controls to intended use cases. Foreseeable misuse scenarios must be analyzed and addressed in the risk management system and reflected in the AI system requirements.

**Substantial modification.** A change to an AI system after its placing on the market or putting into service which is not foreseen or planned in the initial conformity assessment carried out by the provider and as a result of which the compliance of the AI system with applicable regulatory requirements is affected, or which results in a modification to the intended purpose for which the AI system has been assessed. This definition determines when a model update, retraining event, or deployment context change requires a new conformity assessment. Most organizations do not have documented criteria for making this determination. The absence of those criteria is itself a QMS nonconformity.

**Serious incident.** An incident or malfunctioning of an AI system that directly or indirectly leads to the death of a person or serious harm to a person's health, a serious and irreversible disruption of the management or operation of critical infrastructure, the infringement of obligations under applicable regulatory requirements intended to protect fundamental rights, or serious harm to property or the environment. The definition explicitly includes infringement of fundamental rights obligations. An AI system that produces discriminatory outcomes in a hiring process or benefit assessment can trigger a serious incident classification even if no physical harm occurs. Most incident management systems are not configured to detect fundamental rights harms as potential serious incidents.

**Harm.** Injury or damage to health or interference with the fundamental rights of a person or group of persons, or damage to property or the environment. The standard adds that harm can be material or immaterial, including physical, psychological, societal, or economic harm. The scope of harm is broad enough to encompass outcomes that most risk registers do not capture.

**Fundamental rights.** Basic rights and freedoms held by every human being irrespective of birth, religion, belief, age, race, ethnicity, sex, gender, or any other status. For the purposes of this document, fundamental rights and their applicability are those protected by EU law, including the protection of the rights outlined in EU law, including the Charter of Fundamental Rights of the EU and the European Convention on Human Rights. Fundamental rights harms are within the scope of the QMS risk management system, not a separate ethics process.

**Risk.** The combination of the probability of an occurrence of harm and the severity of that event. The standard notes that the probability of occurrence includes the exposure to a hazardous situation and the possibility to avoid or limit the harm, and that risk includes harm to health, safety, and interference of fundamental rights directly or indirectly impacted by hazardous situations created where an AI system is involved. This definition is drawn from prEN 18228 and is aligned with the AI Act's harm-based framework. It is not compatible with ISO 31000, under which risks can have positive outcomes. Compliance and regulatory risks are pure risks, only producing a loss. Organizations that have built their AI risk frameworks on ISO 31000 logic will need to rebuild their risk acceptability criteria under the harm-based framework this standard requires.

**Traceability.** The ability to trace the history of the AI system, including information on how AI systems have been specified, developed, verified, validated, operated, monitored, and retired. Traceability is a first-class requirement across the standard, not a documentation style preference. Every control, every test result, and every design decision must be traceable from the AI system requirement it addresses through to the evidence artifact that confirms it was implemented and effective.

**Verification.** Confirmation, through the provision of objective evidence, that specified requirements have been fulfilled. The standard notes that verification can rely on testing activities and results, and that verification activities pertaining to the identification, analysis, evaluation, and control of risks arising from fundamental rights hazards can include consultation with potentially affected stakeholders or their proxies, real-world conditions testing to evaluate the effectiveness of risk controls, review by a cross-functional team of independent experts, and consultation with national, European, or international bodies that supervise or enforce obligations under Union law protecting fundamental rights. Verification is not self-attestation. It is not a sign-off by the team that built the system. It requires objective evidence produced through defined activities.

**Validation.** Verification where the specified requirements are adequate for an intended purpose. The standard notes that the concept of validation as a procedure is not directly related to validation datasets used in machine learning. Validation in the QMS sense asks whether the right system was built, not whether the system was built correctly. Both are required.

**Quality objective.** A measurable goal established to ensure that regulatory requirements are consistently met throughout the lifecycle. Quality objectives must be verifiable, take into account applicable requirements including regulatory requirements, be monitored and regularly reviewed and updated, and be reviewed and updated to maintain regulatory compliance throughout the AI system lifecycle. A quality objective that cannot be measured against a specific regulatory requirement, or that is set once and not reviewed, does not meet the standard.

**AI system requirements.** Functional and non-functional requirements derived from regulatory requirements. This is the linkage mechanism between regulatory obligations and the technical design of the AI system. If the AI system requirements specification does not contain explicit requirements derived from regulatory obligations, including accuracy, robustness, cybersecurity, transparency, human oversight, data governance, and record keeping, the design and development process has no regulatory anchor.

Build a terminology mapping document before you begin implementation. Map each defined term to your organization's existing language and identify where the definitions diverge. Distribute that mapping to legal, compliance, engineering, data, and product teams. If your teams use the same word to mean different things, your QMS will produce contradictory documentation that no auditor can reconcile.

* * *

## Establishing and Scoping the Quality Management System

The provider shall establish, maintain, and continually improve the quality management system in accordance with the requirements of this document and in order to protect health, safety, and fundamental rights. The provider shall establish, document, implement, and maintain any process, procedure, and activity necessary to maintain the quality management system and its effectiveness in meeting applicable regulatory requirements throughout the applicable stages of the lifecycle.

The first operational requirement is identifying regulatory requirements. The provider shall determine and systematically review the regulatory requirements that the AI systems must comply with at any point of their lifecycle. This includes at least the essential requirements. The regulatory requirements identified shall be integrated into the strategy for regulatory compliance.

The standard identifies the essential requirements as those for the risk management system, data and data governance, technical documentation, record keeping, transparency and provision of information to deployers, human oversight, and accuracy, robustness, and cybersecurity. These are found in Chapter III, Section 2 of the AI Act.

The second operational requirement is determining scope. The provider shall determine the scope of the quality management system by determining the set of AI systems covered under the QMS and defining the boundaries, taking into account the regulatory requirements and the intended purpose of the AI systems. Scope is not an administrative label. It determines which systems require technical documentation, which require conformity assessment, and which post-market monitoring obligations apply. A scope statement that describes a category of systems without naming specific systems cannot support the system-level conformity assessment the standard requires.

The third operational requirement is a strategy for regulatory compliance. The provider shall determine a strategy that includes compliance with the regulatory requirements for the QMS itself, compliance with the essential requirements, compliance with the regulatory requirements for post-market monitoring, compliance with the regulatory requirements relating to serious incidents, and the strategy for data management. The strategy shall be available as documented information.

When demonstrating compliance with the essential requirements, the provider shall select from harmonized standards cited in the Official Journal, common specifications adopted in an implementing act, other standards, or other technical specifications or solutions. Where the provider uses approaches other than harmonized standards or common specifications, or where harmonized standards do not fully cover the essential requirements, the provider must document the essential requirements not fully covered, document and justify the measures used, and provide objective evidence that each essential requirement is met.

Most organizations complete scope definition and regulatory compliance strategy as documentation exercises that produce defensible-looking outputs with no operational connection to actual QMS processes. The scope statement sits in a QMS manual. The regulatory compliance strategy sits in a compliance register. Neither is linked to the specific AI system requirements, test plans, or post-market monitoring procedures that constitute actual compliance activity. Build the scope statement as a named inventory of specific AI systems. Build the regulatory compliance strategy as a live register that is updated when regulatory requirements change, when harmonized standards are published or revised, and when the AI system portfolio changes. Link both documents to the control matrix described in the planning section below.

AI Governance Map

| Lifecycle Stage | ISO 42001 | prEN 18286 | EU AI Act |
| --- | --- | --- | --- |
| **Plan and design** | Cl. 4, 6; A.3, A.4 | Cl. 6, 8 Design | Art. 9 AI Risk management |
| **Data engineering** | A.7 Data for AI | Cl. 8; prEN 18284 | Art. 10 Data governance |
| **Development** | A.6 AI Lifecycle | Cl. 8 (Development controls) | Art. 15 Accuracy |
| **Verification** | A.6.2.4 Verification and validation | Cl. 8 Verification and validation | Art. 9.7 Testing |
| **Deployment** | A.6.2.5 Deployment | Cl. 8 Release | Art. 16 Provider obligations |
| **Monitoring** | Cl. 9; A.6.2.6 | Cl. 9 Operations and control, post-market surveillance | Art. 72 Post-market |

| Lifecycle Stage | ISO/IEC 42001 | prEN 18286 | EU AI Act | Mapped standards |
| --- | --- | --- | --- | --- |
| **Data collection and acquisition** | A.7.3, A.7.5 Data acquisition and provenance | Clause 8 (Data management): data origin, collection processes, provenance | Art. 10(2)(a): design choices, data collection processes, origin, original purpose (for personal data) | prEN 18284 (data quality and governance) |
| **Preparation and labelling** | A.7.6 Data preparation | Clause 8: preparation operations (annotation, labelling, cleaning, enrichment) | Art. 10(2)(c): annotation, labelling, cleaning, updating, enrichment, aggregation | prEN 18284 (quality criteria) |
| **Quality and representativeness** | A.7.4 Data quality for AI systems | Clause 8: quality criteria, statistical properties, suitability for intended purpose | Art. 10(3): relevant, representative, free of errors, complete, appropriate statistical properties | prEN 18284 (quality and governance) |
| **Bias detection and mitigation** | A.2.2 Responsible AI policy, A.5 AI impact assessment, A.7.4 Data quality | Clause 8: bias assessment, examination for bias | Art. 10(2)(f–g): examine possible biases, detect, prevent, mitigate biases affecting health, safety, fundamental rights | prEN 18283 (bias concepts, measures, mitigation) |
| **Privacy and personal data** | A.7.3, A.7.5 Data acquisition, provenance, A.5 AI impact assessment | Clause 8: privacy controls, GDPR alignment | Art. 10(2)(a): purpose of collection; Art. 10(5): GDPR safeguards for special categories of data for bias detection/correction | GDPR alignment required |
| **Training, validation and test splits** | A.7.6 Data preparation | Clause 8: development controls, dataset management | Art. 10(1): quality criteria shall apply to training, validation, and testing datasets | prEN 18284 (quality for train/val/test sets) |
| **Monitoring and drift detection** | A.6.2.6 AI system operation | Clause 9: performance evaluation, post-market surveillance | Art. 72: post-market monitoring plan for high-risk AI systems | Monitoring aligned with Art. 72 |

* * *

## What the Documentation System Actually Requires

The documentation requirements in this standard are more demanding than most organizations expect, and the consequences of failing them are more severe than most compliance teams anticipate. The standard distinguishes between documentation of the QMS itself and operational documentation, and imposes specific controls on both.

Documentation of the QMS shall contain detailed information about the measures put in place by the provider to ensure that AI systems meet their applicable regulatory requirements. It shall be common to all AI systems under the QMS rather than specific to a particular AI system. It shall be written for an audience of auditors and kept at the disposal of notified bodies and competent authorities. It shall be presented in a clear, accessible, and version-controlled manner ensuring easy retrieval of relevant information, presented in one of the official languages of the European Union.

It must include the scope of the QMS, documented statements of a quality policy and quality objectives, processes and evidence, reference to documented procedures for the QMS, a description of how the provider ensures the effective planning, operation, maintenance, and control of QMS processes, a description of the interaction between those processes, and written evidence maintained to demonstrate conformance to the standard.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/06/qmaqhdswyx3u9rpq9axyp3ennndbf2ul9cu58ffe9v8f2a.png?w=640)

Operational documentation covers documents that support the application of QMS processes, including traceability documents and documents written for communication purposes.

Control of documented information is specified in detail. Documented information required by the QMS shall be controlled to ensure it is suitable for use where and when it is needed, it is adequately protected from loss of confidentiality, improper use, or loss of integrity, and that storage and preservation including preservation of legibility, control of changes including version control, retention and disposition, and traceability including documents from external and internal sources are all addressed.

The provider shall retain documented information for a period as specified by applicable regulatory requirements. The retention period shall ensure that documents related to AI systems that have been developed and tested are available for at least the lifetime of each AI system as defined by the provider, but not less than the retention period of any resulting written evidence, or as specified by applicable regulatory requirements.

A documented procedure shall define the controls needed to review and approve documents for adequacy prior to issue, review and update as necessary and reapprove documents taking into account written evidence, ensure that the current revision status of and changes to documents are identified, and ensure that the storage, protection, and traceability outcomes are achieved.

Changes to documents shall be reviewed and approved either by the original approving function or another designated function that has access to pertinent background information on which to base its decisions.

The single most common documentation failure is the gap between what the QMS says should happen and what the written evidence shows actually happened. A QMS that requires management review but cannot produce a management review record with documented inputs, conclusions, and outputs has a QMS documentation system failure, not just a governance gap. Implement document control as a formal system with version numbering, approval workflows, retention schedules, and audit trails. Every procedure must name the person or role responsible for approval. Every record must be linked to the procedure that required it. Every document must have a retention period specified. If your documentation system cannot answer the question of what version of a procedure was in force on the date a specific decision was made, it does not meet the standard.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/06/qmxrtw45wvb4cdpawmt45cw2rypfd1ankxfn5u5jsadwju.png?w=640)

* * *

## Management Responsibility: What Top Management Must Actually Do

The standard places extensive and non-delegable obligations on top management. These are not obligations that can be fulfilled by the compliance function, the risk team, or the legal department acting on behalf of leadership. They are personal obligations of the people who direct and control the organization at the highest level.

Top management shall ensure that the quality policy and quality objectives are established, that the resources needed for the QMS are available, that other relevant roles can carry out their roles effectively within their areas of responsibility, that QMS requirements are integrated into the provider's processes, that the QMS achieves its intended results, and that the importance of effective quality management is communicated to relevant personnel.

The quality policy must be established by top management and shall provide a framework for setting quality objectives, include a commitment to meet applicable requirements, implement the regulatory strategy, include a commitment to continual improvement of the QMS, be included in the documentation of the QMS, and be communicated to the provider's relevant personnel.

The assignment of roles, responsibilities, and authorities requires top management to assign supervision and responsibility for the QMS to personnel with relevant expertise and experience, including by assigning top management level responsibilities wherever applicable. Top management shall specifically assign responsibility and authority for ensuring that the QMS conforms to the requirements of the standard, and for reporting on the performance of the QMS to top management.

The assignment of roles shall ensure that roles are applicable given the context of the provider, roles are traceable to the quality policy and quality objectives, responsibilities and decision-making authority are defined for all AI systems in scope, for the regulatory requirements identified, responsibilities are assigned to monitor and address them, and responsibilities are identified for the handling of all processes required by the standard including across the lifecycle and which roles are consulted or informed.

Top management shall specifically assign responsibility and authority for ensuring that the risk management system addresses risks to fundamental rights, health, and safety, reviewing applicable regulatory requirements, ensuring that [threats and vulnerabilities of the AI system n](https://hernanhuwyler.wordpress.com/2026/03/15/ai-threat-and-vulnerability-assessment/)ecessary to address regulatory requirements are also addressed, and ensuring ongoing monitoring of the technological and regulatory state of the art relevant to the AI systems covered by the QMS.

The accountability and responsibility for overseeing the implementation of the risk management system and the approval of the risk control measures shall be assigned to a specific role.

The provider may outsource roles and responsibilities to external organizations and different types of workers. However, the responsibility for ensuring that all outsourced activities comply with the QMS and other applicable regulatory requirements remains with the provider.

The practical implementation problem here is that most board-level executives have not been personally briefed on what prEN 18286 requires of them. They have been told that the organization is implementing a QMS for AI Act compliance. They have not been told that they must personally establish the quality policy, personally approve risk acceptability criteria, and personally conduct or authorize management reviews with documented outputs. When an auditor asks to see evidence of top management commitment, a signed quality policy is not sufficient. The auditor will also ask to see management review records, resource allocation decisions, and evidence that top management has responded to post-market monitoring findings. If those records do not exist, the QMS has a governance failure at the highest level. Schedule a structured briefing for board-level leadership that explains their specific obligations under the standard, get written acknowledgment that they have accepted those obligations, and embed those obligations into board governance documentation.

* * *

## Planning the QMS: Risk, Objectives, and What Gets Left Out

Planning under this standard has two distinct components that are frequently confused with each other.

The first component is [actions to address risks](https://hernanhuwyler.wordpress.com/2026/03/28/how-to-actually-use-iso-iec-23894-for-ai-risk-management/) related to the functioning of the QMS itself. When planning for the QMS, the provider shall, based on the identified regulatory requirements, determine the risks that need to be addressed to give assurance that the QMS can achieve its intended results, prevent or reduce undesired effects of the application of the QMS, and achieve continual improvement of the QMS.

The provider shall plan actions to address these risks and plan how to integrate and implement those actions into QMS processes and evaluate their effectiveness.

When determining actions to address risks related to QMS functioning, the provider shall consider at least the regulatory compliance strategy, the AI technologies used, the need for other parties to provide information and assistance throughout the AI system lifecycle that is relevant for fulfilling regulatory requirements, and the availability of resources and expertise.

The standard is explicit that addressing risks when planning the QMS is different from, and is not to be confused with, the risk management process for the AI system. These are separate activities with separate outputs.

The second component is quality objectives. The provider shall establish quality objectives at relevant functions, levels, and processes that are consistent with the quality policy. Each AI system's quality objective shall, as applicable, be verifiable, take into account applicable requirements including regulatory requirements, be monitored, regularly reviewed, and updated, and be regularly reviewed and updated to maintain regulatory compliance throughout the AI system lifecycle.

When planning how to achieve quality objectives, the provider shall determine what will be done including the relevant processes and applicable quality criteria of those processes, the measures to be taken to implement the requirements of the standard, and who will be responsible including responsibilities and roles on relevant levels and functions.

The distinction between QMS-level risk planning and AI system-level risk management is one of the most frequently misunderstood requirements in the standard. QMS-level risk planning asks what could prevent the QMS from working as intended. AI system risk management asks what could harm people through the operation of the AI system. Both are required. Neither substitutes for the other. An organization that has a mature AI risk management process under prEN 18228 but has not conducted QMS-level risk planning has addressed only one of the two planning requirements. Build separate documented outputs for each. [The QMS-level risk register i](https://hernanhuwyler.wordpress.com/2026/03/30/shadow-ai-risk-management-for-caios/)dentifies threats to governance processes. The AI system risk management file addresses threats to health, safety, and fundamental rights.

* * *

## Support: Resources, Competence, and Communication

The provider shall determine and provide the resources needed for the establishment, implementation, maintenance, and continual improvement of the QMS. When determining necessary resources, the provider shall take into account at least human resources and their competences, organizational, discipline, application, and technology-specific knowledge, organizational infrastructure and work environment including for design, development, and testing, measures to ensure the security of supply, and time.

Competence requirements are extensive. The provider shall determine the necessary competences of personnel doing work under its control that affects quality objectives, ensure that personnel are competent on the basis of education, training, or experience, take actions to acquire necessary competences and evaluate effectiveness, and document the processes for establishing and validating competences, providing needed training, maintaining supervision, and ensuring awareness of personnel. Documented information shall be available as evidence of competence.

The provider shall ensure that relevant personnel are familiar with their duties related to quality management and the provider's QMS processes, and that it has or has access to the competences necessary to understand the regulatory requirements identified and the intended purpose. This includes competences necessary to understand regulatory requirements relating to health, safety, and fundamental rights.

The provider shall evaluate how the following factors influence competency requirements: each AI system's intended purpose and how it can be reasonably foreseeably misused, the nature of the AI technologies and data being processed, the relationship between the intended purpose, foreseeable misuse, and risks including significant effects on affected persons, and the effect of the usability and accessibility of each AI system for diverse users including persons with disabilities.

Communication requirements distinguish between general internal and external communications and communications for regulatory purposes. For general communications, the provider shall determine what will be communicated, when, with whom, how, and how communication with the provider can be established.

For regulatory communications, the provider shall handle communication with national competent authorities, other authorities, notified bodies, other operators, customers, and other interested parties including those identified through the risk management process. The provider shall define and maintain procedures to communicate with national competent authorities and other authorities.

In the event of nonconformities, the provider shall inform relevant interested parties including market surveillance authorities, notified bodies, importers, distributors, authorized representatives, and deployers of those nonconformities and of any actions taken to correct them, including bringing each AI system into conformity, withdrawing it, disabling it, or recalling it.

When a competent authority issues a reasoned request, the provider shall provide the necessary documentation and information to demonstrate compliance within an appropriate time frame. The provider shall ensure that it has processes in place to identify, collect, and transmit or make available the information and documentation necessary to demonstrate the conformity and continuous compliance of each AI system, including any information requested by a competent authority such as automatically generated logs within the control of the provider.

The competence requirement for fundamental rights is where most organizations will find the largest gap. Assessing fundamental rights risks requires expertise in the EU Charter of Fundamental Rights, in the legal obligations that flow from specific rights protections, and in the characteristics of vulnerable groups who may be disproportionately affected. This expertise is rarely present in engineering or compliance teams. It requires either specialized legal and human rights expertise within the team or documented access to independent expert resources including human rights organizations and civil society. The standard does not permit you to assert that fundamental rights were considered without evidence that someone with the relevant competence conducted that assessment.

* * *

## Product Realization: Lifecycle Controls From Inception Through Deployment

The product realization section covers the largest portion of the standard's operational requirements and is the section where the gap between documented governance and auditable evidence is most severe. It covers the lifecycle structure, design and development controls, verification and validation, data management, environmental sustainability, and product documentation.

The provider shall establish, implement, document, and maintain a risk management system throughout the lifecycle of each AI system, in accordance with regulatory requirements, aimed at achieving a high level of protection for health, safety, and fundamental rights. The standard states that prEN 18228 can be used for this in whole or in part. The risk management system under prEN 18228 is the primary mechanism for identifying hazards, estimating risks, implementing risk controls, and evaluating residual risk acceptability. The QMS provides the governance architecture within which the risk management system operates.

The provider shall determine the stages of the lifecycle, establish processes and procedures appropriate to ensure that AI system requirements are met across the lifecycle, and include techniques and systematic actions for design control and design verification, development, quality control and quality assurance, data management, examination, test and validation procedures, post-market monitoring, and support.

In establishing these processes, the provider shall determine the requirements for each AI system, establish criteria for the processes necessary to meet those requirements, determine the sequence and interaction of those processes, and determine the methods and criteria needed to ensure that both the operation and supervision of these processes are effective.

The planning factors the provider must consider explicitly include the requirements for each AI system, the nature, duration, and complexity of lifecycle activities, the required process stages including design and development reviews, the required verification and validation activities, the responsibilities and authorities involved in each lifecycle process, internal and external resource needs, the need to control interfaces between persons involved in the lifecycle process, the need for involvement of relevant interested parties including deployers and affected persons in relevant processes throughout the lifecycle, the requirements for subsequent provision of each AI system and services including ongoing maintenance, retraining, and updates, and the documented information needed to demonstrate that requirements applicable to the AI system throughout its lifecycle have been met.

Planning and process control documents shall be maintained and updated as the AI system lifecycle progresses for each AI system. The effectiveness of these measures shall be monitored and corrective actions taken if intended results are not achieved.

* * *

### From Inception to Design: Where Risk Control Begins

At the inception stage, the provider shall determine the intended purpose of the AI system. The provider should consider consultation with interested parties regarding fundamental rights at this stage. The standard's Annex A, discussed later, provides structured guidance on how that consultation should be conducted.

At the design and development stage, the provider shall determine AI system requirements for the intended purpose, including reasonably foreseeable misuse, of each AI system that translates the applicable regulatory requirements into definitions of explicit features in a form that can be used during design and development.

The AI system requirements shall include accuracy, robustness, cybersecurity, transparency, human oversight, data and data governance, and record keeping according to the intended purpose, applicable regulatory requirements, requirements related to applicable risk control measures resulting from the risk management system, information derived from previous similar designs where appropriate, and other requirements essential for design and development.

The AI system requirements shall be complete, unambiguous, able to be verified or validated, not in conflict with each other, and reviewed for continued appropriateness during the lifecycle.

The AI system requirements shall be reviewed for adequacy and approved before placing the AI system on the market or putting it into service. The review shall be conducted systematically and shall allow the provider to ensure that requirements are defined and documented, cover applicable regulatory requirements, and can be met. The results of the review and actions arising from it shall be documented.

AI system specifications shall meet the AI system requirements, provide information for processes, products, and services that are integrated into the AI system that are relevant to maintaining quality, and be verifiable. Written evidence of the specifications of each AI system shall be maintained in the technical documentation.

The provider shall ensure that reviews are conducted to ensure design and development objectives are met, verification and validation activities are conducted to ensure that the design and development specifications meet the AI system requirements, any necessary actions are taken to address problems determined during reviews or verification and validation activities, and documented information of these activities is retained.

Most organizations document intended purpose as a product brief and treat the AI system requirements specification as an engineering document separate from regulatory obligations. Under this standard, those are the same document. Every AI system requirement must be derived from a regulatory requirement, traceable to that requirement, and verifiable through a defined test or review activity. If you cannot trace a line from each AI system requirement back to an essential requirement, a risk control measure identified in the risk management file, or another regulatory obligation, the requirements specification is not regulatory-grade documentation. Rebuild the requirements specification as a traceability matrix with three columns at minimum: the regulatory obligation, the derived AI system requirement, and the verification activity that confirms the requirement was met.

* * *

### Verification and Validation as Regulated Activities

Testing and verification shall be performed to ensure that each AI system meets the AI system specifications. The provider shall define and document testing plans and test procedures that are appropriate to the specified intended purpose and for identified reasonably foreseeable misuse, include methods and numerical limits, ranges, or other suitable and verifiable measures for acceptance of test results, and are aligned with best practices and are reproducible, in particular by setting out the conditions for testing.

Written evidence of the results and conclusions of verification and necessary actions shall be maintained.

Design and development validation shall be performed in accordance with planned and documented arrangements to ensure that each AI system is capable of meeting the requirements for the specified intended purpose, carried out taking account of the AI system's instructions for use and technical documentation, carried out during and after development with the provider determining the frequency of validation and performing a risk evaluation based on results, completed prior to placing the AI system on the market or putting it into service including for modifications that are not substantial modifications, and include documented validation plans and test procedures with methods and numerical limits or other suitable measures for acceptance of test results.

Written evidence of the results and conclusion of validation and necessary actions shall be maintained.

The provider should consider consultation with interested parties regarding fundamental rights when conducting validation. When developing an AI system to manage or recruit workers, for example, it is essential to consult workers and workers' representatives in order to know which potential impacts to investigate.

Acceptance criteria must be specified before testing begins, not derived from results after testing is complete. This is not a procedural recommendation. It is a structural requirement that determines whether testing produces evidence of compliance or post-hoc rationalization. If your test plans do not contain documented acceptance criteria that were approved before the first test was run, your testing does not produce objective evidence of compliance. Implement a mandatory test plan approval step before any verification or validation activity begins, with documented evidence that acceptance criteria were established and approved before testing commenced.

* * *

### Data Management as a QMS Control, Not a Separate Function

The provider shall put in place a strategy to comply with applicable regulatory requirements relating to data management. The provider shall define, document, and implement data management processes related to the design and development of each AI system.

As appropriate and proportionate to the risk of the AI system, the provider shall establish and maintain systems and procedures for data management covering data acquisition, collection, analysis, labeling, storage, filtration, mining, aggregation, retention, and any other operation regarding the data that is performed before and for the purpose of placing on the market or putting into service each AI system. The provider shall also define and document processes about data requirements, data planning, data preparation, and data decommissioning.

The provider shall specify a mechanism for data no longer in use to be destroyed when each AI system is decommissioned. These mechanisms shall detail how data no longer in use is destroyed or archived to fulfill regulatory requirements. Data can be reused in certain situations, and destruction of data shall not conflict with the ability of the provider to comply with applicable regulatory requirements.

The data management section of the standard is where the gap between enterprise data governance and system-level QMS compliance is most visible. Most organizations have enterprise data governance frameworks that set policies for data quality, lineage, access, and retention across the organization. Those frameworks produce portfolio-level compliance with data governance principles. The standard requires something different: documented data management processes for each AI system individually, specifying how data was acquired, prepared, and used for that specific system, with evidence that those processes were followed. If your data governance function cannot produce a system-specific data management record that traces training data sources, quality assessment results, labeling procedures, and retention decisions for each AI system, the data management requirement has not been met at the system level.

* * *

### Technical Documentation and Instructions for Use

For each AI system, the provider shall establish and maintain technical documentation. The technical documentation shall contain comprehensive, detailed, technical, and specific information about each AI system and its elements to demonstrate compliance to auditors, notified bodies, and competent authorities.

When the specifications for or characteristics of an AI system are changed, the provider shall ensure that outdated technical documentation is amended and communicated to interested parties as applicable.

For each AI system, the provider shall establish and maintain instructions for use with information on how to use each AI system and its outputs. The instructions for use shall be written in a clear and accessible manner for the intended deployers of AI systems, noting that the intended audience can include persons who are not necessarily of technical background. They shall contain information, specifications, and procedures for deploying and using each AI system, including integration, installation, deployment, and servicing, to ensure it can operate in a manner fit for its intended purpose.

Where applicable, instructions for use shall include specific information prescribing organizational measures and procedures that are needed during deployment to ensure that affected persons are provided with opportunities to provide input to post-market monitoring. Such measures and procedures can be related to human oversight, logging, and other traceability measures. They shall also include requirements for maintenance activities, including frequency and scope, to ensure AI system quality is maintained.

Instructions for use are legally binding downstream documents. Whatever you say the system requires in terms of oversight, monitoring, or operational context, deployers must follow. If you write instructions that are aspirational, incomplete, or drafted without knowledge of actual deployer operational environments, you have created a gap between what the system requires and what deployers will do. That gap will appear in your post-market monitoring data as anomalies you did not anticipate and cannot explain.

* * *

## Operation and Control: Deployment, Supply Chain, Changes, and Monitoring

The operation and control section covers the ongoing management of AI systems after they are placed on the market or put into service. It addresses how systems are deployed, how suppliers are managed, how changes are controlled, and how post-market monitoring operates. These are the requirements where most organizations' implementation efforts will encounter the largest operational gaps.

* * *

### Deployment and Operational Monitoring

The provider shall put into place procedures to ensure that the version of each AI system can be clearly identified, enabling its traceability and linking as a product on the market or in service to its instructions for use and technical documentation. The standard notes that traceability is enabled by written evidence and documented information from the provider, such as a Software Bill of Materials, and that record keeping provides traceability of changes to the version of the AI system and relevant components after the system is put into service or placed on the market.

The AI system version shall be linked to technical versions of AI components, such as software or specific AI models, and other relevant information including datasets.

Support services shall be identified, specified, and provided considering entities expected to require support, support channels, expected types of problem and appropriate responses, diagnostic tools, and a mechanism to ensure that deployers can communicate received feedback regarding potential risks to health, safety, and fundamental rights to AI providers.

The Software Bill of Materials reference in this section reflects a growing international norm in software supply chain transparency. The EU Cyber Resilience Act and analogous US requirements under Executive Order 14028 have both accelerated adoption of SBOMs for software products. For AI systems, the SBOM concept extends to model components, training data sources, and third-party model layers. If you cannot produce a current, accurate SBOM for each AI system that links the deployed version to its specific model components and datasets, you cannot demonstrate version traceability as the standard requires.

* * *

### Supply Chain: The Regulated Obligation That Most Organizations Have Not Built

The supply chain requirements in this standard are more demanding than the supplier management practices found in most AI governance frameworks. They apply to all external products, components, data, and services, without exception for open-source, freely available, or commonly used components.

The provider shall define and document procedures to ensure that products, components, data, and services that are supplied externally conform to specified requirements, applicable regulatory requirements, and standards. The standard specifies that these can come from outside or inside the provider, meaning internal teams that supply components to the QMS-scoped AI system are also subject to supply chain controls.

The provider shall determine measures when products and components including software and hardware are supplied externally, when model training and test data for AI systems are supplied externally, and when services for certain lifecycle activities such as design and development, model training, data annotation, evaluations, and testing are supplied externally.

For evaluation and selection of external suppliers, the provider shall establish and document criteria based on the suppliers' ability to provide products, components, data, and services that meets the provider's requirements, history of reliability, adherence to agreed-upon specifications, and ability to [meet contractual obligations](https://hernanhuwyler.wordpress.com/2026/03/15/how-to-negotiate-ai-agreements-that-protect-data-value-and-liability/) including quality and applicable standards. Criteria shall also be based on the likely effect of the supplied products, components, data, and services on the quality of AI systems, and shall be proportionate to the [risk associated with AI systems](https://hernanhuwyler.wordpress.com/2026/05/08/the-pren-18228-problem-why-your-ai-risk-assessment-will-fail-the-first-real-test/) and their intended purpose as determined by the risk management system.

For ongoing monitoring and re-evaluation, the provider shall plan the monitoring and re-evaluation of suppliers, monitor performance based on ability to meet regulatory requirements and the requirements of the standard, use results of monitoring as input into the supplier re-evaluation process, and retain documented information of these activities and any necessary actions.

The provider should communicate to suppliers requirements and specifications covering the products, components, data, and services to be supplied, the acceptance procedures, the supplier's quality management system, competences including required qualifications, interactions with the provider, use of [security by design principles](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/), control and monitoring of supplier performance, the absence of known vulnerabilities and disclosure of future vulnerabilities, and verification or validation activities the provider intends to perform at the supplier's premises.

In determining the extent of control, the provider shall ensure and document that supplied products, components, data, and services remain within the control of its QMS, define and document both the controls it intends to apply to a supplier and those it intends to apply to the supplied products, components, data, and services, take into consideration the potential impact on the provider's ability to consistently meet user requirements and regulatory requirements, and the effectiveness of controls applied by the supplier, and determine the verification, product acceptance, or other activities necessary to ensure requirements are met.

The open-source model component problem is one that most organizations have not resolved and that the standard does not exempt. If you use a foundation model, a pretrained embedding, or a third-party dataset that is freely available, you are still required to evaluate that component against your supplier criteria, document the evaluation, assess the likely effect on AI system quality, and verify that it meets your specified requirements. The fact that a component costs nothing and is widely used does not eliminate the supplier governance obligation. Build your supplier evaluation process to explicitly address open-source and freely available components, with a documented rationale for how each component was assessed and what risk controls address any identified limitations.

* * *

### Change Management: Where Continuous Learning Systems Face Their Hardest Test

The provider shall implement a change management process to control planned changes and review the consequences of unintended changes to AI systems that can result in a substantial modification.

The provider shall review the consequences of both planned and unintended changes in accordance with the risk management system. The provider shall specify procedures to identify, document, and review modifications to each AI system whether intended or unintended. Those procedures shall include processes, methods, and mechanisms to ensure that the AI system is kept under recurrent review to ensure that risks to health, safety, and fundamental rights continue to be acceptable, and to enable the prompt identification of any changes to risks and the undertaking of any necessary action.

AI systems on the market or in service that are modified shall result in a reviewed and updated set of documentation required for the QMS. The technical documentation shall reflect all versions of the product, including pre-determined changes.

Once any changes are identified, the provider shall review them and if needed take action to address adverse impacts on quality, any risk not documented and accepted in accordance with the risk management system at the time of the previous conformity assessment, and gaps in monitoring and detection measures.

For AI systems using continuous learning, pre-determined changes can be considered planned maintenance activities. Providers can conduct verification and validation activities on pre-determined changes to ensure they do not affect the intended purpose, affect the QMS, or increase risks to health, safety, and fundamental rights. If the provider intends to rely on such pre-determined changes, they can document it in the technical documentation and instructions for use.

The technical documentation for pre-determined changes can include a description of the pre-determined changes including a specification of expected changes to performance, how various versions of the AI system can be identified to avoid situations where a regulator is faced with previous versions for which the technical documentation presented is not applicable, a step-by-step modification procedure including appropriate data, test methods, and numerical limits for acceptance of test results used to develop, verify, validate, and implement all proposed modifications and the update process and any communication or training requirements, and an impact assessment covering any impact on quality objectives, risks introduced by the pre-determined change, how those risks and impacts have been mitigated by verification and validation, and how implementation of one change affects implementation of another and the cumulative impact of all pre-determined changes.

The existence of the pre-determined change procedure can be included in the instructions for use and should include a description of the implemented modifications covering a summary of current AI system performance, a description of the relevant data used, associated inputs and outputs, and validation requirements and related evidence, a description of how the modifications were implemented, and a description of how users will be informed of implemented modifications.

For organizations deploying continuously learning AI systems, the pre-determined change requirements represent a fundamental design constraint that must be addressed before deployment, not after the first model update. A continuously learning system that has not been designed and documented with a pre-determined change procedure in place is not compliant at the point of deployment. The technical documentation must include the pre-determined change framework as part of the original conformity assessment package. Retroactively adding this documentation after deployment constitutes a change to the technical documentation that itself requires review and approval.

* * *

### Post-Market Monitoring: Active, Systematic, and Proactive

The post-market monitoring section is where most AI governance frameworks have their largest gap and where regulatory enforcement is most likely to produce findings. The standard's requirements are specific, operational, and demanding.

The provider shall establish and document a post-market monitoring system that applies from when each AI system is placed on the market or put into service until it is no longer in use, allows the provider to evaluate continuous compliance of each AI system in scope, is proportionate to the nature of the AI technologies and [the risks](https://hernanhuwyler.wordpress.com/2026/03/28/how-to-actually-use-iso-iec-23894-for-ai-risk-management/) including residual risk present after the risk management process has been applied, and provides processes to collect and review experience gained from use to identify needs for immediate and necessary corrective or preventive actions.

The provider shall identify the scope of the post-market monitoring system including each AI system in scope, the quality objectives connected to those systems, and the objectives of the monitoring system.

The monitoring approach shall be planned and documented and include consideration of potential negative impacts of the operation of each AI system, applicable regulatory requirements including data privacy and fundamental rights, the potential reliance on other organizations including distributors, importers, and deployers as well as t[hird parties supplying tools, services, components, or processes](https://hernanhuwyler.wordpress.com/2026/03/15/how-to-negotiate-ai-agreements-that-protect-data-value-and-liability/), the intended purpose including reasonably foreseeable misuse, technical constraints that need to be addressed to facilitate effective monitoring, the performance of the AI system, and where relevant, interaction with other AI systems.

The monitoring approach shall track the effectiveness of risk management prevention and mitigation measures through qualitative or quantitative indicators, and by drawing on feedback from both internal and external sources including affected persons. In order to be effective, the monitoring approach shall be active and systematic, address nonconformities promptly, and feed into the continual improvement process.

The provider shall determine policies and procedures for systematically gathering and storing information gained from use of each AI system, including information provided by deployers, end users, or other interested parties, monitoring the AI system or its logs, regulatory authorities, and feedback and complaint mechanisms and serious incidents. The provider shall implement AI system logging to capture relevant data about the AI system as appropriate.

The provider shall implement procedures to identify and act upon new and emerging risks when monitoring and information provided indicate that risks are not currently being managed and reduced to an acceptable level.

Where the provider is not able to monitor an AI system directly without deployer involvement, appropriate requirements for monitoring shall be included in the instructions for use. The provider shall consider including technical monitoring requirements of the AI systems in line with the post-market monitoring plan, recommended tools for monitoring if not integrated into the AI system, and recommendations on technical competency requirements to monitor the AI system.

Nonconformities identified by post-market monitoring shall follow a documented procedure that defines what constitutes a breach of quality objectives, including single events, a collection of events over a defined time period, time-based performance deviations and shifts, and tolerances or threshold ranges within which exceeding a threshold is considered acceptable.

The most dangerous gap in most post-market monitoring systems is the absence of defined thresholds and triggers for corrective action. Monitoring that collects data without defined thresholds is not monitoring. It is logging. You need to define, before deployment, what result from your monitoring would cause you to initiate a risk reassessment, what result would cause you to escalate to top management, what result would trigger a nonconformity process, and what result would cause you to consider withdrawal. Those thresholds must be documented in the monitoring plan, linked to the quality objectives they protect, and reviewed at each management review cycle. If your monitoring system cannot answer the question of whether the overall residual risk of this system is still acceptable today given what we have learned from post-market data, it is not operating as the standard requires.

* * *

### Serious Incident Reporting: Hard Deadlines That Cannot Be Tested Under Live Conditions for the First Time

The provider shall implement a process for investigating serious incidents to determine if there is a causal link between the AI system and the serious incident. The provider shall ensure that the serious incident is reported to the competent authorities after establishing a causal link or considering that there is a reasonably plausible link.

The statutory timelines are fixed. For serious incidents involving critical infrastructure, the report shall be submitted immediately or at the latest within two days. For serious incidents involving the death of a person, the report shall be submitted immediately or at the latest within ten days. For all other serious incidents, the report shall be submitted immediately or at the latest within fifteen days. A provisional version may be submitted followed by a complete version.

The provider shall document, implement, and maintain procedures for reporting serious incidents within these timelines, including procedures for deployers to report serious incidents to the provider and to suspend use of the AI system.

The procedures should include establishing key internal contacts responsible and the internal escalation process, promoting awareness of the risks of serious incidents and the relevant escalation process to relevant provider personnel, implementing and maintaining processes that will enable the provider to meet applicable regulatory timescales, ensuring that the provider can allocate adequate resources including competent personnel and necessary tools to support an investigation and respond to authority enquiries, maintaining detailed written evidence of all serious incidents and associated investigations including root cause analysis and actions taken, and procedures and obligations between provider and deployer to enable reporting from deployer to provider.

The standard notes that some serious incidents need to be reported by the deployer to the provider first before the provider can be aware of the situation and apply the relevant procedures.

A two-day reporting window for critical infrastructure incidents is shorter than the time most organizations need to convene an incident response team, establish a causal link, draft a report, and obtain approval to submit to a competent authority. The ten-day window for death-related incidents and the fifteen-day window for other serious incidents are both shorter than the time most legal review processes require for regulatory submissions. These timelines must be stress-tested before a real incident occurs. Run a tabletop exercise that simulates a serious incident notification at the worst possible time, with key personnel unavailable, and measure whether your organization can produce a provisional report within the statutory window. If it cannot, identify the specific bottlenecks and redesign the escalation process to eliminate them.

* * *

## Performance Evaluation: Management Review, Improvement, and Change Control

The QMS shall be effective when it and the AI systems within its scope align with the applicable requirements of the standard including protection of health, safety, and fundamental rights and quality objectives.

The effectiveness of the QMS as a whole shall be reviewed using clear and measurable criteria of a quantitative or qualitative nature. The provider shall establish and document procedures for review at planned intervals to ensure continuing suitability, adequacy, and effectiveness, and to identify the need for changes including the quality policy, the quality objectives, adherence to policies and procedures, monitoring the effectiveness of risk control measures, the interested parties particularly affected persons, and opportunities for improvement.

In addition to planned reviews, the provider shall ensure that a review of its QMS is conducted when an investigation of a serious incident finds the QMS or its measures to be inadequate.

The provider shall periodically review the applicable regulatory requirements for changes. The provider shall maintain review documentation including recommendations and written evidence.

The periodic review process should be proportionate to the risks potentially presented by each AI system, provided that the degree of rigor and the level of protection to health, safety, and fundamental rights is maintained and ensured.

Management review inputs should include interested party feedback, concerns and complaints and handling and investigation reports, reporting to regulatory authorities, internal and external audits, monitoring and measurement of QMS processes, monitoring and measurement of the performance of the AI system in operation, corrective action, follow-up actions from previous management reviews, changes that can affect the QMS, recommendations for improvement, applicable new or revised regulatory requirements, and monitoring of new or revised harmonized standards related to applicable regulatory requirements.

The output from reviews shall be recorded and include any improvement needed to maintain suitability, adequacy, and effectiveness of the QMS and its processes, any improvement of the AI system related to interested party requirements, any changes needed to ensure compliance with applicable new or revised regulatory requirements, and any changes to resource needs.

For improvement, the provider should continually improve the suitability, adequacy, and effectiveness of the QMS.

When changes to the QMS are needed, the provider shall specify and document the procedures required to manage those changes, carry out the changes in a planned and controlled manner, and systematically keep written evidence of implemented changes.

Whenever a new AI system becomes covered by the QMS or is substantially modified, the provider shall assess the need to review the QMS processes, and if review concludes that changes to processes are needed, those processes shall be revised accordingly.

Changes to QMS processes shall be evaluated for their impact on the QMS, evaluated for their impact on each AI system under the QMS, and controlled in accordance with the requirements of the standard.

The requirement to conduct a management review when an investigation of a serious incident finds the QMS or its measures to be [inadequate creates a feedback loop t](https://hernanhuwyler.wordpress.com/2026/03/15/ai-deployment-governance-for-feedback-loops-and-mlops/)hat most organizations have not designed for. A serious incident that exposes a QMS gap triggers not only an incident investigation and corrective action but a management review of the QMS itself. That review must be conducted, documented, and its outputs acted upon. Organizations that treat management review as an annual calendar event rather than a triggered activity will not meet this requirement. Design your management review process to include a standing trigger list that initiates an unplanned review when specific events occur, including serious incidents, significant near-misses, major regulatory changes, significant post-market monitoring findings, and audit findings that reveal systemic QMS failures.

* * *

## Consulting Affected Persons on Fundamental Rights: What Annex A Actually Requires

Annex A is informative but describes the expected approach to consultation with affected persons that verifiable consultation under the standard will need to reflect. The standard's consultation references in the normative clauses make this annex operationally significant.

In respect to fundamental rights, the provider should seek to understand the concerns of potentially affected persons by consulting them directly in a manner that takes into account differences and similarities between European citizens and other potential barriers to effective engagement. Where consultation is not possible, the provider should consider reasonable alternatives such as consulting credible, independent expert resources including human rights organizations and others from civil society.

The consultation process should comprise planning for material and human resources to ensure that affected persons or groups of persons or their representatives are properly consulted, identification and mapping of individuals and groups that can be negatively impacted with a focus on disadvantaged, under-represented groups or persons in situations of vulnerability, establishing clear objectives for the consultation such as identification of fundamental rights risks, defining risk acceptability criteria, mitigation of fundamental rights risks, investigation of serious incidents, and post-market monitoring, and determination of the consultation method and sharing of relevant and meaningful information about the AI system.

The consultation method should take into account considerations of age-appropriateness, accessibility needs, and the need for capacity building to ensure meaningful involvement, and provide opportunities to obtain meaningful feedback concerning concerns about the risks the AI system poses.

Consultations should begin at the inception stage, prior to the commencement of design and development and throughout the examination, testing, and validation process. Consultation can be of added value at every stage of the AI system lifecycle. Testing and validation should be conducted in consultation with affected persons and groups of persons and others whose health, safety, and fundamental rights are likely to be adversely affected.

The outcomes of these consultations can result in the provider modifying the intended purpose of the proposed system and the introduction of [additional safety by design measures](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/).

After potential impacts are identified, processes can be designed to observe the magnitude of impacts on affected persons, provided that those affected are properly informed of any material risks and have given express consent to observation and measurement activities.

The practical challenge with fundamental rights consultation is that most organizations do not know how to conduct it, who should participate, or how to document it in a form that satisfies a regulatory reviewer. A consultation that convenes an internal ethics board and records a summary of their discussion does not constitute consultation with affected persons. A consultation that distributes a survey to existing users does not constitute consultation with potentially affected non-users, including vulnerable groups who may be subject to the system's outputs without choosing to use it. Map your consultation design against the process steps the annex describes. Identify specifically which groups will be consulted, by what method, with what information provided in advance, and how the findings will be documented and fed back into design decisions and risk control measures. Document the rationale for any groups you do not directly consult and the alternative sources of information you use instead.

* * *

## What Comes Next

prEN 18286 is under CEN enquiry until December 2025. It is not yet a harmonized standard. The presumption of conformity it is designed to provide under Article 17 will arise only after formal publication and citation in the Official Journal, a process that may extend into 2027 or later depending on the outcome of the enquiry, resolution of comments, national body votes, and the broader legislative environment including the Digital Omnibus proposal that introduced potential delays to AI Act application dates.

Below is the consolidated list of **prEN standards** under the EU AI Act based on their role in compliance ecosystem and explicit cross-references in the draft standards.

- [PrEN 18228 Risk Management System](https://hernanhuwyler.wordpress.com/2026/05/08/the-pren-18228-problem-why-your-ai-risk-assessment-will-fail-the-first-real-test/): Defines a lifecycle risk management process for AI systems, covering risks to health, safety, and fundamental rights; implements Article 9 and is explicitly integrated into prEN 18286 clauses.

- [prEN 18286 Quality Management System](https://hernanhuwyler.wordpress.com/2026/06/17/the-pren-18286-reality-check/): Specifies QMS requirements and guidance for AI providers; operationalizes Article 17; lifecycle governance, documentation, traceability, post-market monitoring, incident reporting.

- prEN 18284 Dataset Quality and Governance: Covers quality and governance of datasets used to build/assess AI systems; implements Article 10; explicitly referenced in prEN 18286 subclause 8.5.

- prEN 18283 Managing Bias in AI Systems: Defines concepts, measures, and requirements for assessing and treating unwanted bias (data and model bias); supports Article 9 risk management and fairness obligations.

- prEN 18229-1 AI Trustworthiness Framework Part 1: Logging, Transparency and Human Oversight Establishes methods for logging, transparency, and human oversight; supports Articles 12, 13, and 14.

- prEN 18229-2 AI Trustworthiness Framework Part 2: Accuracy and Robustness Specifies accuracy and robustness testing methods; addresses Article 15; referenced in prEN 18286 clause 8.4.1 for accuracy testing.

- [prEN 18282 Cybersecurity Specifications:](https://aiassurance.institute/pren-18282-clauses.html) Describes organizational and technical measures to secure AI systems against cyber threats, including data poisoning and model attacks; supports Article 15.

Organizations in the medical device sector face additional complexity. The European Commission's December 2025 proposal to simplify the MDR and IVDR includes a potential shift that would bring AI-related obligations for medical AI systems fully under the MDR and IVDR rather than the AI Act, which would mean that harmonized standards under the AI Act would not automatically apply to medical devices. If that proposal advances through the European Council and Parliament, the applicability of prEN 18286 to medical AI systems would depend on whether its requirements are subsequently harmonized under the MDR and IVDR, potentially through implementing acts. That outcome remains uncertain and should be tracked through national standards body channels.

For organizations implementing ISO/IEC 42001, the position is clearer. The European Commission's JRC has formally assessed ISO/IEC 42001 as not aligned with the AI Act in objectives and approach and as inadequate for harmonization under the Act. Using ISO/IEC 42001 as the primary compliance instrument for Article 17 is a documented risk position, not a compliance position. Organizations should treat their ISO/IEC 42001 implementation as a foundation that can support prEN 18286 implementation where the structures overlap, particularly in the governance and planning clauses, while building the additional product-centric, system-level, and regulatory-specific controls that prEN 18286 requires and that ISO/IEC 42001 does not address.

What does not change regardless of harmonization timelines is the fundamental obligation. Article 17 requires providers of high-risk AI systems to implement a QMS. That obligation applies from the dates set out in the AI Act. Organizations that are waiting for harmonized standards before beginning implementation are not in a waiting period. They are in a non-compliance period, building the compliance gap that will need to be closed at an accelerated pace when enforcement begins.

The question every provider should be able to answer now is the same one a notified body will ask on the first day of a conformity assessment. Show me the risk management file for this specific AI system. Show me the technical documentation that demonstrates it meets the essential requirements. Show me the test plans, the acceptance criteria, and the test results. Show me the post-market monitoring system that is actively tracking whether the residual risk is still acceptable. Show me the management review record where top management approved the deployment decision.

If any of those documents cannot be produced, assembled, and made coherent within the time a notified body allows, the QMS is not ready. Under the EU AI Act, that is a placement on the market problem, not a planning problem.

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
