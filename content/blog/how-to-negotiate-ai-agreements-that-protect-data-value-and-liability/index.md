---
title: "How to Negotiate AI Agreements That Protect Data, Value, and Liability"
date: 2026-03-15
tags: 
  - "ai"
  - "ai-contract-clauses"
  - "ai-contracts"
  - "ai-governance"
  - "ai-projects"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "ip-clauses"
  - "iso-42001"
  - "iso-23894"
  - "technology"
  - "third-party-models"
---

AI vendor contracts are still written as if AI were just another SaaS product.

That is the core problem.

AI vendor contracts raise issues that traditional software terms were never designed to handle properly. Who owns the output. Whether your data is used to train someone else’s model. What happens when the model hallucinates or discriminates. How performance should be measured when output can vary from one run to the next. How to exit when the vendor holds the embeddings, custom configurations, or fine-tuned behavior your workflow now depends on. These are not minor details. They are the structure of the risk.

And right now, standard vendor terms still favor the vendor heavily. Many claim broad data usage rights. Many avoid meaningful regulatory warranties. Many cap liability so low that the customer carries most of the AI-specific risk. That is why lawyers, procurement teams, privacy officers, and business owners need a stronger AI contracting playbook.

This post turns the material you provided into a practical article on AI vendor contracts, with clause logic, negotiation guidance, and control recommendations grounded in the realities of current AI deals.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/futuristic-glass-rods-1.png?w=1024)

## Understanding the Core Framework for AI Vendor Contracts

A strong AI vendor contract should do four things well. Protect your data, define accountable performance, allocate liability realistically, and preserve your exit options.

The framework I use has four layers. Data and output rights, risk and liability allocation, operational performance controls, and lifecycle protections. If one is weak, the deal usually becomes much riskier than it looks during procurement.

### 1\. Data and output rights

This layer answers what the vendor can do with your data and what rights you have over outputs and derived artifacts.

This is one of the most important areas because AI vendors often try to reserve broad rights in standard terms. If those rights are not narrowed, your confidential or regulated information may end up supporting broader vendor product development.

Implementation tip: Treat “data use” and “model improvement” clauses as high-priority negotiation items, not as boilerplate language.

### 2\. Risk and liability allocation

This layer covers hallucinations, bias, discrimination, IP infringement, privacy failures, and general AI underperformance. It defines who bears the cost when the AI behaves badly.

In many standard contracts, the customer carries too much of this risk. That makes little sense where the vendor controls the model, training choices, and core design.

Implementation tip: Ask one blunt question in every AI deal. Who creates the risk and who pays when it materializes? If the answers do not align, redraft.

### 3\. Operational performance controls

This layer includes AI-specific service levels, drift management, quality thresholds, fairness metrics, update controls, and practical remedies for underperformance.

Traditional uptime-only SLAs are not enough for AI. The real service question is not only whether the system is available. It is whether the outputs are usable and remain within acceptable limits.

Implementation tip: Define measurable AI-specific performance obligations before procurement signs, not after implementation problems appear.

### 4\. Lifecycle protections

This layer covers termination, transition, portability, data deletion, and support during exit or change.

AI lock-in is often more dangerous than ordinary software lock-in because the vendor may be holding not only data, but also embeddings, fine-tuned behavior, retrieval structures, or model-specific workflows that are hard to recreate elsewhere.

Implementation tip: Termination rights are not end-of-contract details. They are leverage from the first draft.

## Why AI Vendor Contracts Are Different From Traditional Software Agreements

Traditional software contracts assume deterministic behavior, stable service definitions, and relatively straightforward data processing relationships.

AI breaks those assumptions.

The output is probabilistic. The model may change without much notice. Performance may drift. Data rights become more ambiguous because vendors want to use usage data, prompts, and customer interactions to improve their systems. Liability gets harder because the vendor often wants to disclaim output quality while still marketing the tool as production-ready.

This creates a legal mismatch. The contract template was built for conventional software. The actual product behaves like a continuously evolving decision engine.

That mismatch is why so many current AI contracts leave customers exposed.

Implementation tip: Review AI agreements with a fresh structure. Do not start from the assumption that the standard SaaS paper is “mostly fine.”

## Stage 1: Lock Down Data Use, Training Rights, and Output Ownership

This is usually the first major negotiation front.

The responsible parties are legal, privacy, procurement, security, product owners, and the business sponsor. Data governance and compliance should also review if regulated or client-sensitive information is involved.

The critical artifacts are the master agreement, data processing terms, product documentation, security schedules, and any AI-specific addendum.

What to implement: Narrow the vendor’s rights to use customer data. If the tool processes client matter data, regulated records, internal knowledge, or proprietary content, the vendor should not have open-ended rights to use that information for model training, product development, profiling, or unrelated analytics unless you explicitly permit it.

This is also the stage to define output ownership. The contract should state clearly whether the customer owns the outputs, whether the vendor claims any rights in outputs, and what happens to derived artifacts such as embeddings, vector representations, or fine-tuned model behavior tied to your data.

The right answer depends on the use case, but ambiguity is dangerous. If the vendor can keep broad rights over derived artifacts, your exit options weaken significantly.

Implementation tip: Separate raw data, prompts, outputs, logs, embeddings, and fine-tuned derivatives in the contract. These are often treated loosely in standard terms, and that creates avoidable exposure.

## Stage 2: Fix the Liability Mismatch Before It Fixes You

This is the most commercially sensitive part of many AI deals, and one of the most important.

The responsible parties are legal, procurement, finance, product owners, risk, and executive sponsors where the use case is significant. Insurance advisors may also need to review the structure.

The critical artifacts are the liability clause, indemnity clauses, limitation language, carve-outs, insurance requirements, and product claims made in sales materials.

What to implement: Push back on blanket disclaimers that place all output risk on the customer while the vendor keeps control over model design and training. The vendor should not be able to market the system as suitable for a specific workflow, disclaim meaningful output responsibility completely, and still rely on a tiny liability cap when the system fails in a predictable AI-specific way.

This matters for hallucinations, discriminatory outputs, privacy leakage, and IP infringement. Hallucination is not a hypothetical edge case. It is a known product behavior. If the vendor cannot guarantee factual accuracy, that should shape the use case restrictions and performance terms. But it should not automatically eliminate all liability.

Bias and discrimination are even more serious in regulated use cases. If the AI affects hiring, credit, insurance, healthcare, or legal outcomes, the contract should require bias testing, disclosure of known limits, and vendor participation in liability if claims arise from model design.

IP risk also matters. If the vendor trained on problematic data or cannot warrant its training rights, output-related infringement exposure becomes a real issue. Some market leaders already offer output-level IP indemnification. Use that as leverage.

Implementation tip: Preserve the general liability cap if needed for ordinary service issues, but carve out stronger protection for data breaches, discrimination, confidentiality breaches, and IP indemnification. One cap should not govern every kind of AI failure.

## Stage 3: Build AI-Specific Performance Standards and SLAs

Most AI contracts still use the wrong service metrics.

The responsible parties are legal, procurement, product owners, operations, analytics, AI governance, and vendor management. The business team must help define what “acceptable” means in practical use.

The critical artifacts are the SLA schedule, benchmark definition, acceptance criteria, model update procedure, and monitoring rights.

What to implement: Move beyond uptime and support response alone. Define performance in measurable AI terms. Depending on the use case, this may include hallucination rate, factual accuracy, acceptance and rejection rates, fairness indicators, false positives, false negatives, latency, drift thresholds, or quality review pass rates.

For legal research tools, for example, hallucination rate may be a critical control metric. For hiring or credit tools, fairness and disparate impact metrics may need to be included. For operational copilots, task success and safe completion may matter more.

Also define what happens when performance falls below threshold. This should include service credits, mandatory remediation, retraining where appropriate, and termination rights if the underperformance persists.

A useful structure is escalation by severity. Minor underperformance earns credits. Persistent or serious underperformance triggers remediation. Severe underperformance or repeated failure gives the customer the right to exit.

Implementation tip: Put the metric calculation method in the contract. A performance threshold without a defined benchmark, test set, or calculation method will create disputes later.

## Stage 4: Address Bias, Drift, and Monitoring as Contractual Obligations

This is where AI vendor contracts start looking meaningfully different from standard software deals.

The responsible parties are legal, AI governance, compliance, product owners, and vendor management. Technical teams should help validate whether the proposed commitments are realistic and measurable.

The critical artifacts are the fairness testing clause, drift monitoring clause, notification requirements, and periodic review schedule.

What to implement: Require the vendor to monitor for model drift and report material degradation. Define what counts as drift for the use case. This might be a decline in core accuracy, an increase in hallucination rate, or a fairness gap that exceeds tolerance. Then define notification windows and remediation obligations.

For sensitive decision tools, require fairness testing on a recurring basis and disclosure of methodology and results. If statistically significant disparate impact appears, the contract should allow immediate suspension of the affected use and require corrective action.

These clauses matter because AI systems change over time. A good contract does not assume launch-day behavior remains stable forever.

Implementation tip: Tie update rights and drift obligations together. The vendor should not be free to change the model materially without corresponding review, notice, and accountability.

## Stage 5: Negotiate Exit, Portability, and Transition Assistance Before You Need Them

This is one of the most under-negotiated and high-impact sections in AI contracts.

The responsible parties are legal, procurement, vendor management, product owners, architecture, and security. The business sponsor should understand the practical effect of lock-in.

The critical artifacts are the termination clause, data portability obligations, deletion obligations, transition support terms, and exit assistance details.

What to implement: Require the vendor to return or delete not just raw customer data, but also embeddings, vector representations, caches, indexes, and other derivatives created from customer data. If custom models, fine-tuning, or specialized configurations were created for your use, the contract must state who owns them and what happens on exit.

The customer should also get transition assistance. This includes open-format exports, technical migration support, and continued access at existing rates during the transition window where needed.

This matters much more in AI than in many standard SaaS products because the lock-in often includes behavior and infrastructure the customer cannot easily reproduce elsewhere.

Implementation tip: Ask the vendor early whether model weights, embeddings, indexes, and fine-tuned artifacts can be exported in standard formats. If not, assume lock-in and negotiate accordingly.

## Stage 6: Use Negotiation Tactics That Match Today’s AI Vendor Market

This market is still favorable to informed buyers in many segments.

The responsible parties are legal, procurement, business sponsors, finance, and where relevant technical evaluators. Smaller buyers may need a sharper focus because they have less raw leverage but still have useful arguments.

The critical artifacts are competitor terms, public vendor commitments, approval chain notes, and your ranked list of non-negotiables.

What to implement: Understand the vendor’s incentives. Many want strategic logos, regulated industry customers, longer terms, and reference relationships. That creates leverage. Use competitive intelligence aggressively. If one vendor offers zero training on customer data, output IP indemnification, or residency controls, cite it directly.

Expect the standard objections. The vendor cannot identify all training data. The vendor cannot promise minimum accuracy. Deletion is technically impossible. Liability caps are non-negotiable. Security certifications solve everything. None of these should end the conversation automatically.

Trade intelligently. If the vendor resists changing the liability structure, ask for stronger audit rights, drift reporting, update notice, fairness testing, or termination flexibility. If they refuse broad contract changes, start with the DPA and build precedent there.

Pilots are also useful. A short, limited pilot can create real performance evidence and improve leverage for the full agreement if structured correctly.

Implementation tip: Go into negotiation with a ranked list of true non-negotiables. Most organizations lose leverage because they treat every clause as equally important.

## Stage 7: Flow Down Regulatory Compliance Obligations Properly

AI compliance is not optional, and vendor cooperation is increasingly necessary.

The responsible parties are legal, privacy, compliance, product owners, and the relevant business unit. Sector specialists matter here because healthcare, employment, finance, education, and consumer settings all bring different obligations.

The critical artifacts are the compliance schedule, use-case classification, high-risk system analysis, sector-specific addenda, and audit cooperation clauses.

What to implement: Require the vendor to support your compliance obligations actively, not merely disclaim responsibility and point back to you. The vendor controls the model, the infrastructure, and often the testing logic. That means they need to provide documentation, bias testing support, audit assistance, and evidence of conformity where required.

This is especially important under expanding AI regulation. If the use case may fall under a high-risk category, the contract should require the vendor to help with documentation, evaluation, register requirements where applicable, and deployer obligations.

Sector-specific compliance must also flow down clearly. HIPAA and BAAs for healthcare. Employment and bias audit requirements for hiring tools. GLBA, ECOA, FCRA, and sector rules for financial use. FERPA for education. These are not side notes. They should shape the contract.

Implementation tip: Add a clause that requires the vendor to provide compliance assistance materials sufficient for your deployer obligations. Otherwise you may buy a tool you cannot lawfully use at scale.

## Stage 8: Use Insurance and Risk Transfer Intelligently

This is often ignored until the deal is almost done.

The responsible parties are legal, procurement, finance, risk, and insurance advisors. Executive review may be necessary for larger or higher-risk commitments.

The critical artifacts are the vendor insurance certificates, your own coverage review, liability cap structure, and indemnity terms.

What to implement: Check whether your own insurance actually covers AI-related failures. Many professional liability and cyber policies still do not handle AI-specific incidents clearly. If there is a gap, you need to know before the contract is signed.

Then require the vendor to maintain appropriate professional liability and cyber coverage, with no AI-specific exclusion that would gut the protection. Use the insurance amount as a negotiation anchor for AI-specific liability caps. If the vendor carries $5 million in E&O coverage, it is difficult to justify a $60,000 contractual cap for all indemnifiable claims.

This creates a more realistic alignment between contractual risk transfer and actual available coverage.

Implementation tip: Search your own policy wording for “artificial intelligence,” “machine learning,” “algorithmic,” and “automated decision” before assuming you are covered.

# AI Contract Clause Negotiation Checklist

## A Practitioner's Guide to Redlining Artificial Intelligence Vendor Agreements

* * *

# Part One: AI Governance Terms

This domain covers the foundational contractual provisions that control how the vendor handles Company data within AI systems, who owns what the AI produces, how model quality is maintained, and what visibility the Company retains over the vendor's AI operations. These clauses either do not exist in traditional software agreements or take on fundamentally different significance in the AI context. Each should be reviewed and negotiated before execution.

* * *

## 1\. Training Data Restriction

This clause governs whether the vendor may use Company data to train, retrain, fine-tune, adapt, test, or otherwise improve AI models or related services. In AI contracting, this is often the highest-priority issue because use of inputs, prompts, outputs, metadata, and derivatives for model improvement can create confidentiality, attorney-client privilege, trade secret, privacy, and regulatory exposure.

Vendors frequently describe these rights using softer terms such as "product improvement," "service enhancement," "aggregated data," or "de-identified data," even where the data may still be re-identifiable or commercially sensitive. The negotiator should review all definitions of Customer Data, Usage Data, Aggregated Data, and De-identified Data and ensure that no customer-originated content may be used for training or product improvement without express written consent. A practical drafting objective is to prohibit any use of Company data and outputs except to provide the contracted service, while allowing only truly anonymized, non-reversible service analytics.

**Comparative Wording:**

- **Vendor Draft:** Customer acknowledges and agrees that Vendor may use Customer Data, including inputs, outputs, and usage data, in aggregated or de-identified form, to improve, develop, and enhance the Service and Vendor's other products, features, and machine learning models. Vendor may also use Customer Data to generate anonymous and aggregate statistics regarding use of the Service.

- **Company Redline:** Vendor shall not use any Customer Data, including inputs, outputs, prompts, usage content, or derivatives, for model training, retraining, fine-tuning, testing, or product improvement without Customer's prior written consent. Vendor may use only aggregated, anonymized usage statistics solely for internal service analytics, provided such statistics cannot be reverse engineered or otherwise used to identify Customer, any individual, or Customer Confidential Information.

**Negotiation Impact:** The revised language converts a broad implied license into a narrow, purpose-limited processing right. It removes the vendor's ability to exploit Company data for model development and blocks indirect reuse through outputs or derivatives. It also tightens the standard for permitted analytics by requiring true anonymization and non-reidentification, reducing confidentiality, privilege, privacy, and competitive risks. For negotiation, insist that any exception be opt-in, documented, and revocable.

* * *

## 2\. Subprocessor Controls

This clause addresses the vendor's use of third parties that host, process, store, index, or otherwise handle Company data in the AI delivery chain. AI products commonly rely on layered providers, such as a foundation model provider, cloud platform, vector database, embedding service, or monitoring provider, so Company data may pass through multiple entities.

The contract should require the vendor to identify all subprocessors and describe their functions, impose on each subprocessor the same data-use and security restrictions that bind the vendor, prohibit training on Company data at every tier, provide advance notice of changes, allow Company to object to new subprocessors, and require the vendor to stop using any subprocessor that violates those obligations. The negotiator should ask for a current subprocessor list, verify whether the vendor has flow-down restrictions in place, and avoid relying on assumptions about upstream contracts.

**Comparative Wording:**

- **Vendor Draft:** Vendor may engage affiliates and third-party service providers to support delivery of the Service. Vendor will remain responsible for the acts and omissions of its subprocessors in accordance with this Agreement. A current list of subprocessors will be provided upon request, and Vendor may update its subprocessors from time to time in its discretion.

- **Company Redline:** Vendor shall provide Customer with a complete and current list of all subprocessors that access, process, store, transmit, host, or derive value from Customer Data, together with a description of each subprocessor's role. Vendor shall ensure that each subprocessor is bound by written obligations at least as protective as this Agreement, including prohibitions on training, retraining, fine-tuning, or otherwise using Customer Data or output for product improvement. Vendor shall provide at least 30 days' prior written notice before appointing any new subprocessor, and Customer may object on reasonable data protection, confidentiality, security, or legal compliance grounds. If a subprocessor violates the required restrictions or Customer raises a reasonable objection that cannot be resolved, Vendor shall promptly cease use of that subprocessor with respect to Customer Data.

**Negotiation Impact:** The original language gives the vendor broad discretion and limited transparency, leaving Company exposed to unknown downstream data practices. The revised language creates visibility, mandatory contractual flow-downs, objection rights, and a remediation obligation if a subprocessor is noncompliant. This shifts operational and legal responsibility back to the vendor, where it belongs, and reduces hidden training, security, and regulatory risks. In negotiation, request named subprocessors in an exhibit and tie any noncompliant change to termination rights if needed.

* * *

## 3\. Output Ownership

This clause allocates ownership and use rights in AI-generated outputs and clarifies the boundary between vendor technology and Company work product. Because legal treatment of AI-generated content remains unsettled, the contract should resolve ownership by agreement rather than relying on evolving copyright doctrine.

The core issues are whether Company owns outputs generated from its data and prompts, whether the vendor retains any license to reuse those outputs, and whether the vendor may treat outputs as derivative improvements to its service. The negotiator should ensure that all outputs created for Company belong exclusively to Company to the fullest extent permitted by law, that the vendor has no residual rights to reuse or commercialize them, and that ownership of the vendor's preexisting models and platform remains separate.

**Comparative Wording:**

- **Vendor Draft:** As between the parties, Customer retains ownership of Customer Data as submitted to the Service. Vendor retains all rights, title, and interest in and to the Service, including all improvements, modifications, derivative works, and any models, algorithms, or other technology developed or enhanced through operation of the Service, whether or not informed by Customer Data.

- **Company Redline:** Customer owns all right, title, and interest in and to all output generated by or through the Service using Customer Data, prompts, instructions, or other Customer-provided materials, to the fullest extent permitted by applicable law. Vendor retains no right, title, license, or interest in such output and shall not use, disclose, commercialize, or exploit such output for any purpose, including model training or product improvement, without Customer's prior written consent. Vendor retains ownership of the underlying Service, software, models, algorithms, and other vendor technology, excluding Customer Data and output.

**Negotiation Impact:** The original clause preserves customer ownership only in submitted data while allowing the vendor to capture value from outputs and improvements informed by Company use. The revised clause closes that gap by expressly assigning output ownership to Company and denying the vendor any reuse rights absent written consent. This protects work product, competitive advantage, and client deliverables while still preserving the vendor's ownership of its core platform. In negotiation, also align this clause with confidentiality, IP indemnity, and training restrictions.

* * *

## 4\. Model Performance Maintenance

This clause addresses model drift, performance degradation, version changes, and maintenance standards for AI systems. Unlike traditional software defects, AI quality can decline gradually and silently as models evolve or as inputs change over time.

A contract should therefore define measurable performance standards, monitoring obligations, remediation timelines, testing requirements, and notice obligations for model changes. The negotiator should require objective thresholds in an exhibit, periodic reporting, no-cost corrective action when performance falls below agreed levels, and advance notice plus regression testing before material model updates are deployed. This transforms vague maintenance promises into enforceable service commitments.

**Comparative Wording:**

- **Vendor Draft:** Vendor shall use commercially reasonable efforts to maintain, update, and improve the Service. Vendor may, in its sole discretion, modify, retrain, or replace the model or models underlying the Service at any time without notice. Such modifications shall not constitute a material change to the Service.

- **Company Redline:** Vendor shall continuously monitor model performance against the accuracy, precision, recall, error rate, and other service levels set forth in Exhibit A. Vendor shall maintain performance at or above the agreed thresholds. If performance falls below any threshold for two consecutive measurement periods, Vendor shall, at no additional charge, investigate the cause, implement corrective measures, and retrain, recalibrate, or replace the applicable model within 30 days. Vendor shall provide at least 30 days' prior written notice of any material change to model versions, training methodology, or deployment architecture, and shall complete regression testing and document the results before production release.

**Negotiation Impact:** The original language gives the vendor unilateral control over model changes and no enforceable performance commitment. The revised language introduces measurable obligations, mandatory monitoring, cost-free remediation, and advance notice of material changes. This reduces the risk that Company will rely on a silently degraded or materially altered system and provides a concrete basis for escalation, credits, or breach claims. In negotiation, press for objective metrics relevant to the use case and attach them as a schedule.

* * *

## 5\. AI Transparency and Audit

This clause governs the Company's ability to understand, assess, and verify how the AI system operates, how it was trained, how it is tested, and how it performs over time. In AI contracting, standard SaaS reporting is insufficient because usage dashboards do not reveal model provenance, limitations, bias controls, or governance practices.

The contract should provide audit rights on reasonable notice and require disclosure of model cards or equivalent documentation covering architecture, training data provenance, benchmark results, bias testing methods, monitoring outcomes, and material changes. The negotiator should balance transparency needs against legitimate vendor confidentiality concerns by allowing review under confidentiality restrictions rather than accepting complete opacity.

**Comparative Wording:**

- **Vendor Draft:** Vendor shall provide Customer with access to standard reporting dashboards reflecting Service usage metrics, including volume of queries processed and system availability. Additional reporting, documentation regarding model architecture, training methodology, or internal testing is proprietary and not included in the Service.

- **Company Redline:** Customer may audit Vendor's AI systems and related governance controls upon reasonable prior notice of not less than 15 business days, no more than twice annually unless required by law, security incident, or material breach. Vendor shall provide current model cards and supporting documentation describing model architecture, training data provenance, evaluation methods, accuracy benchmarks, known limitations, bias testing methodology, incident logs, and ongoing monitoring results. Vendor shall update such documentation at least quarterly and shall make knowledgeable personnel available to explain the documentation and respond to reasonable follow-up questions, subject to appropriate confidentiality protections.

**Negotiation Impact:** The original clause limits visibility to operational metrics and excludes the information needed to assess AI risk. The revised language grants structured audit rights and ongoing documentation obligations, enabling Company to evaluate compliance, performance, bias, and change management. This materially improves oversight and supports legal, regulatory, and internal governance requirements. In negotiation, be prepared to offer confidentiality protections and reasonable frequency limits, but do not waive access to substantive AI governance records.

* * *

# Part Two: AI Risk Allocation

This domain addresses the contractual mechanisms that determine who bears the financial, legal, and operational consequences when AI systems fail, produce harmful outputs, or create third-party liability. Traditional SaaS risk allocation frameworks are inadequate for AI because the failure modes are qualitatively different: hallucinated outputs, discriminatory decisions, confidentiality breaches through model training, and intellectual property infringement embedded in generated content. Each clause in this section should be reviewed early in the negotiation process and cross-referenced with the governance terms in Part One.

* * *

## 6\. Bias and Fairness Compliance

This clause allocates responsibility for testing, monitoring, and remediating discriminatory or unfair outcomes produced by the AI system, especially where outputs influence decisions affecting individuals. In regulated or high-impact use cases such as employment, credit, housing, benefits, and legal services, bias is not merely a quality issue; it is a direct litigation, enforcement, and reputational risk.

Vendors often attempt to disclaim all responsibility by stating that the customer alone determines suitability and legal compliance. The contract should instead require vendor-led bias testing and fairness audits, access to audit results, measurable non-discrimination standards where appropriate, and indemnification for claims caused by the service. The negotiator should emphasize that the vendor selected the model architecture and training data and is therefore best positioned to evaluate and control algorithmic bias.

**Comparative Wording:**

- **Vendor Draft:** Customer is solely responsible for determining the suitability of the Service for Customer's intended use case and for ensuring that Customer's use of the Service, including any decisions based on Service outputs, complies with all applicable laws, including non-discrimination, equal opportunity, and fair lending statutes. Vendor makes no representations regarding the suitability of outputs for use in legally regulated decision-making processes.

- **Company Redline:** Vendor shall conduct bias testing and fairness audits at least annually, and more frequently as required by applicable law or material system changes, using methodologies appropriate to the Service and the Customer use case. Such testing shall evaluate disparate impact and other relevant fairness metrics across protected characteristics recognized under applicable federal, state, and local law. Vendor shall provide summary audit reports and remediation plans to Customer upon request. For use cases involving employment, credit, housing, benefits, or legal services decisions, Vendor represents that the Service has been evaluated for discriminatory impact and shall indemnify, defend, and hold harmless Customer against third-party claims, governmental investigations, and losses arising from discriminatory or unlawfully biased outputs of the Service, except to the extent caused by Customer's unauthorized modifications or use contrary to Vendor's written instructions.

**Negotiation Impact:** The original clause shifts virtually all legal and operational risk to Company, even though the vendor controls model design and training inputs. The revised language rebalances responsibility by requiring vendor testing, disclosure, and indemnity for bias-related claims tied to the service. This significantly reduces Company's exposure in sensitive decision-making contexts and creates an incentive for the vendor to maintain defensible fairness controls. In negotiation, resist "customer is solely responsible" language and tie bias obligations to specific use cases if the vendor seeks narrower commitments.

* * *

## 7\. AI Liability Cap Carve-Outs

This clause addresses whether the general limitation of liability adequately covers AI-specific risks. Standard SaaS caps are often structured around fees paid and may be acceptable for uptime issues, but they are usually inadequate for harms arising from data breaches, intellectual property infringement, confidentiality violations, unlawful training on customer data, discriminatory outputs, or regulatory investigations.

The negotiator should review the liability section early and ensure that AI-specific high-severity risks are carved out from low caps or placed under a higher super-cap. A practical approach is to preserve the general cap for ordinary claims while excluding or elevating liability for confidentiality breaches, data misuse, security incidents, IP claims, and bias or discrimination claims.

**Comparative Wording:**

- **Vendor Draft:** In no event shall either party's aggregate liability arising out of or related to this Agreement exceed the fees paid or payable by Customer under this Agreement during the 12 months preceding the event giving rise to the claim. This limitation applies regardless of the form of action and notwithstanding any failure of essential purpose.

- **Company Redline:** Except for liability arising from Vendor's breach of confidentiality, misuse of Customer Data, violation of the training data restrictions, data security incident, infringement or misappropriation of intellectual property rights, gross negligence, willful misconduct, or claims relating to discriminatory or unlawful bias in the Service, each party's aggregate liability under this Agreement shall not exceed the fees paid or payable by Customer in the 12 months preceding the claim. Vendor's liability for the excluded matters shall be uncapped or, if uncapped liability is not accepted, subject to a separate cap of not less than three to five times the fees paid or payable under this Agreement during the same period.

**Negotiation Impact:** The original clause applies a low uniform cap to all claims, leaving Company underprotected against severe AI-related harms. The revised language preserves the commercial cap for ordinary contract claims but removes or raises the cap for high-risk categories that can create outsized losses. This reallocates financial responsibility toward the party best able to prevent those harms. In negotiation, if the vendor resists uncapped exposure, seek at minimum a meaningful super-cap and make sure indemnity obligations are not silently limited by the general cap.

* * *

## 8\. Unilateral Change Control

This clause governs the vendor's ability to modify the AI service, model behavior, terms of service, and data handling practices without Company approval or notice. In enterprise AI use, silent changes can affect accuracy, legal compliance, bias characteristics, security posture, and data rights.

The contract should prohibit material unilateral changes without advance notice and should give Company remedies if a change adversely affects compliance, performance, or agreed use restrictions. The negotiator should search for terms such as "modify," "update," "change," and "sole discretion," and remove provisions that allow the vendor to alter core obligations or model behavior without accountability.

**Comparative Wording:**

- **Vendor Draft:** Vendor may modify the Service, underlying models, features, technical specifications, and applicable policies from time to time in its sole discretion. Continued use of the Service following posting of an updated version constitutes acceptance of the modified terms.

- **Company Redline:** Vendor shall not materially modify the Service, underlying models, data handling practices, security controls, or applicable policies in a manner that adversely affects Customer's rights, compliance posture, or reasonably expected use of the Service without at least 30 days' prior written notice. No change to Vendor's online terms or policies shall amend this Agreement unless expressly agreed in writing by both parties. If a material change negatively affects the Service or Customer's legal or operational requirements, Customer may reject the change and terminate the affected Service without penalty.

**Negotiation Impact:** The original language allows the vendor to change the deal and the technology unilaterally, effectively shifting ongoing operational and legal risk to Company. The revised language imposes notice, freezes contractual terms absent mutual agreement, and gives Company an exit if harmful changes are introduced. This reduces uncertainty and protects against degradation of negotiated protections over time. In negotiation, insist that online policies cannot override the signed agreement.

* * *

## 9\. Termination and Data Deletion

This clause governs what happens to Company data and AI-derived artifacts when the agreement ends. In AI systems, deletion obligations must go beyond source files and standard backups to include embeddings, vector representations, indexes, cached prompts, fine-tuned models, evaluation datasets, and derived artifacts that may still contain or reflect Company information.

The negotiator should require prompt return or export of data in a usable format, comprehensive deletion from production and nonproduction systems, deletion by subprocessors, and a certification process. This is especially important where the vendor has built customer-specific indexes or tuned models using Company materials.

**Comparative Wording:**

- **Vendor Draft:** Upon termination or expiration of the Agreement, Vendor may delete Customer Data in the ordinary course of business in accordance with its retention policies. Customer is responsible for exporting any data prior to termination. Backup copies may be retained until overwritten in the normal course.

- **Company Redline:** Within 30 days after termination or expiration of this Agreement, Vendor shall return to Customer, in a commercially usable format, all Customer Data and all output then in Vendor's possession or control, and shall permanently delete or render inaccessible all remaining copies of Customer Data from its systems and the systems of all subprocessors, except to the extent retention is required by law. For the avoidance of doubt, Customer Data includes prompts, outputs, embeddings, vector representations, indexes, cached content, evaluation datasets containing Customer Data, and any customer-specific fine-tuned models or derivatives. Vendor shall certify deletion in writing upon Customer's request and shall not retain or use any such materials for training, testing, or product improvement after termination.

**Negotiation Impact:** The original clause gives the vendor broad retention flexibility and places the burden on Company to recover its data, while ignoring AI-specific derived artifacts. The revised language creates affirmative return and deletion duties, extends them to subprocessors, and expressly covers embeddings, vectors, and fine-tuned assets that might otherwise be overlooked. This reduces residual confidentiality, privacy, and competitive risks after the relationship ends. In negotiation, align the deletion timeline with business needs and require a written certification for auditability.

* * *

## 10\. Liability Cap and Consequential Damages

This clause determines the financial exposure each party bears when things go wrong. In AI contracts, the core issue is not whether a general liability cap exists, but whether the cap applies to AI-specific risks that can create losses far exceeding annual fees. Traditional software failures tend to involve downtime, data loss, or support issues. AI failures can include hallucinated citations, materially wrong contract analysis, discriminatory outputs, confidentiality breaches caused by model training, and data protection violations.

The negotiator should preserve a reasonable cap for ordinary service claims while carving out or increasing the cap for indemnity obligations, data protection breaches, gross negligence, willful misconduct, and harms caused by hallucinations or unlawful bias where the Company used the service as documented. If the vendor refuses uncapped liability, a super-cap tied to a multiple of fees or insurance limits is a practical fallback.

**Comparative Wording:**

- **Vendor Draft:** In no event shall vendor's aggregate liability arising out of or related to this agreement exceed the total fees actually paid by customer to vendor during the twelve month period immediately preceding the event giving rise to the claim. In no event shall either party be liable to the other for any indirect, incidental, consequential, special, exemplary, or punitive damages, including without limitation damages for lost profits, lost data, business interruption, or loss of goodwill, regardless of the cause of action or the theory of liability, even if such party has been advised of the possibility of such damages.

- **Company Redline:** Vendor's aggregate liability for ordinary performance-related claims shall not exceed the fees paid or payable by Customer during the twelve (12) months preceding the event giving rise to the claim. However, the foregoing cap and any exclusion of consequential or similar damages shall not apply to: (a) Vendor's indemnification obligations; (b) Vendor's breach of confidentiality or data protection obligations; (c) Vendor's misuse of Customer Data, including any prohibited training or product improvement use; (d) Vendor's gross negligence, willful misconduct, or fraud; and (e) claims arising from hallucinated, discriminatory, or otherwise unlawful outputs of the Service, to the extent Customer used the Service in accordance with the Agreement and applicable documentation. For such excluded claims, Vendor's liability shall be uncapped or, if uncapped liability is not accepted, subject to a separate cap equal to the greater of three (3) times the general cap or Vendor's applicable insurance coverage limits.

**Negotiation Impact:** The original language applies a low, one-size-fits-all cap to all claims and broadly disclaims consequential damages, which is inadequate for AI-specific harms. The revised language keeps a commercial cap for routine issues but removes or elevates the cap for the most serious risks under Vendor's control. This materially improves the Company's recovery position for data misuse, security failures, indemnity claims, and harmful outputs. In negotiation, if uncapped liability is rejected, seek a super-cap of two to three times the ordinary cap and ensure that indemnity and data misuse claims are expressly outside both the cap and the consequential-damages exclusion.

* * *

## 11\. Indemnification Scope

This clause allocates defense and payment responsibility for third-party claims arising from the service. In AI deals, standard indemnities are often too narrow because they cover only infringement by the platform itself and exclude claims based on outputs, discrimination, or risks the vendor says it did not know about. That approach is misaligned with AI risk because the vendor controls the training data, filtering, architecture, and deployment choices.

The negotiator should remove knowledge qualifiers, extend indemnity to covered outputs generated through authorized use, include discrimination or unlawful bias claims where relevant, and narrow exclusions so ordinary enterprise usage remains protected. A sensible fallback is to limit output indemnity to outputs generated in accordance with vendor documentation and not materially modified by the Company.

**Comparative Wording:**

- **Vendor Draft:** Vendor shall defend, indemnify, and hold harmless Customer against third-party claims alleging that the Service, as provided by Vendor and used in accordance with the Agreement and applicable documentation, infringes any third-party intellectual property right, to the best of Vendor's knowledge. This indemnity shall not apply to claims arising from: (a) Customer's combination of the Service with third-party products or services; (b) any modification of the Service not made by Vendor; (c) Customer Data or Customer's inputs; or (d) use of the Service other than as documented.

- **Company Redline:** Vendor shall defend, indemnify, and hold harmless Customer and its affiliates, officers, directors, employees, and clients from and against any third-party claims, damages, liabilities, costs, and reasonable attorneys' fees arising from or relating to: (a) allegations that the Service infringes, misappropriates, or otherwise violates any intellectual property right; (b) allegations that outputs generated by the Service infringe any third-party copyright, trademark, or trade secret right, provided Customer used the Service in accordance with the Agreement and applicable documentation and did not materially modify the allegedly infringing portion of the output; and (c) allegations that the Service produces discriminatory or otherwise unlawful results in violation of applicable law. Any knowledge qualifier, including "to the best of Vendor's knowledge," is deleted. The foregoing indemnity shall not apply solely to the extent a claim results from Customer's unauthorized modification of the Service itself or Customer's use of the Service in material breach of Vendor's written documentation.

**Negotiation Impact:** The original clause weakens protection through a knowledge qualifier and limits coverage to the platform, not the outputs or discriminatory effects that create real AI risk. The revised language expands indemnity to output-level IP claims and unlawful bias claims, while keeping reasonable conditions tied to documented use. This shifts risk to the vendor, which is best positioned to assess training data and model behavior. In negotiation, if the vendor resists broad output indemnity, propose a fallback limited to outputs generated under documented workflows and ask for technical safeguards, such as content filters or provenance controls, as part of the compromise.

* * *

## 12\. Data Use Restriction

This clause governs the scope of the vendor's license to access and use Company data. It often appears administrative but is one of the most consequential provisions in an AI agreement because a broad license to use data for "improvement" or "technology development" can allow the vendor to reuse confidential or privileged information to train models or enhance products used by others.

The negotiator should reduce the license to a limited processing right strictly necessary to provide the service during the term, prohibit use of inputs, outputs, feedback, and derivatives for training or product improvement, and eliminate any survival of rights after termination except where legally required. Definitions should be checked carefully to ensure that Customer Data includes prompts, outputs, and feedback.

**Comparative Wording:**

- **Vendor Draft:** Customer hereby grants Vendor a non-exclusive, worldwide, royalty-free, sublicensable license to access, use, copy, transmit, store, and process Customer Data (including inputs, outputs, feedback, and usage data) as necessary to (a) provide and maintain the Service, (b) improve, develop, and enhance Vendor's products, services, and technology, including machine learning models, (c) generate aggregated and anonymized benchmarks, and (d) comply with applicable law. This license survives termination or expiration of this Agreement with respect to data processed prior to termination.

- **Company Redline:** Vendor shall process Customer Data solely as necessary to provide, secure, support, and maintain the Service for Customer during the term of this Agreement and in accordance with Customer's documented instructions. Vendor shall not use Customer Data, including inputs, outputs, feedback, prompts, usage content, or derivatives, to train, retrain, fine-tune, improve, benchmark, or develop any product, service, model, or technology for Vendor or any third party. No license or other right in Customer Data is granted except the limited, non-exclusive, non-transferable right strictly necessary to perform the Service during the term. Any right to use Customer Data shall terminate immediately upon expiration or termination of this Agreement, except to the extent retention is required by applicable law.

**Negotiation Impact:** The original language grants the vendor a broad, sublicensable, worldwide license that extends well beyond service delivery and survives termination, creating serious confidentiality, privilege, and competitive concerns. The revised language replaces that broad license with a narrow, purpose-limited processing right and prohibits training, benchmarking, and product development uses. This materially reduces the risk of downstream reuse and makes the agreement easier to align with privacy notices, client commitments, and internal governance controls. In negotiation, focus on deleting survival language and any right to use feedback or outputs unless separately approved.

* * *

## 13\. Modification Notice Rights

This clause controls the vendor's ability to change the service, the model, data practices, or commercial terms over time. In AI agreements, unilateral modification is especially problematic because changes can affect output quality, bias, explainability, and legal compliance without obvious warning.

The negotiator should require advance written notice of material changes, define material modification broadly to include model version changes, training data changes, data processing changes, and shifts in accuracy characteristics, and secure a no-penalty termination right if the Company does not accept the change. If advance notice is not feasible, a shorter post-change notice coupled with an evaluation and termination window can be an acceptable fallback.

**Comparative Wording:**

- **Vendor Draft:** Vendor reserves the right to modify, update, or discontinue any features, functionality, or components of the Service at any time. Vendor will use reasonable efforts to notify Customer of material changes through the Service interface or by email to Customer's designated administrator. Continued use of the Service following notice of any modification constitutes Customer's acceptance of the modified Service.

- **Company Redline:** Vendor shall provide Customer with at least thirty (30) days' prior written notice before any material modification to the Service. A "material modification" includes any change to the underlying model, model version, training methodology, data processing practices, privacy practices, security controls, output accuracy characteristics, or any feature or functionality on which Customer materially relies. No material modification shall become binding on Customer through continued use alone. If Customer reasonably determines that a material modification adversely affects compliance, performance, security, or intended use, Customer may terminate the affected Service without penalty by written notice given within thirty (30) days after receipt of notice. If prior notice is not reasonably possible, Vendor shall notify Customer within forty-eight (48) hours after the change and Customer shall retain the same evaluation and termination rights.

**Negotiation Impact:** The original clause allows broad unilateral changes and deems continued use to be acceptance, which undermines negotiated protections and operational stability. The revised language creates a clear notice obligation, defines what changes matter, and gives the Company a practical exit right if the service changes in a harmful way. This reduces the risk of silent deterioration in model behavior or data handling. In negotiation, if the vendor argues that some changes are too dynamic for prior notice, accept prompt post-change notice only for urgent updates and preserve the termination right.

* * *

## 14\. AI Confidentiality and Use Ban

This clause adapts standard confidentiality language to AI-specific misuse risks. In a conventional NDA, the main concern is disclosure of confidential information to outsiders. In an AI context, the greater risk may be internal absorption of confidential information into training datasets, fine-tuned models, embeddings, patterns, or derivatives that later influence outputs delivered to other users.

The negotiator should expressly define prohibited "disclosure" and "use" to include training, fine-tuning, model improvement, and incorporation of confidential information into any shared model or dataset. The clause should also include a meaningful survival period, and where especially sensitive information is involved, the negotiator may seek longer survival or perpetual protection for trade secrets.

**Comparative Wording:**

- **Vendor Draft:** Each party agrees to maintain the confidentiality of the other party's Confidential Information using at least the same degree of care it uses to protect its own confidential information (but no less than reasonable care), and not to disclose it to any third party without prior written consent. Confidential Information does not include information that: (a) becomes publicly available through no fault of the receiving party; (b) was known to the receiving party prior to disclosure; (c) is independently developed without reference to the disclosing party's Confidential Information; or (d) is required to be disclosed by law.

- **Company Redline:** Each party shall protect the other party's Confidential Information using at least the same degree of care it uses to protect its own confidential information of a similar nature, and in no event less than reasonable care, and shall not use or disclose such Confidential Information except as expressly permitted by this Agreement. For the avoidance of doubt, prohibited use and disclosure include any use of Confidential Information to train, retrain, fine-tune, test, or improve any machine learning or artificial intelligence model, and any incorporation of Confidential Information, including patterns, structures, embeddings, derivatives, or other representations of such information, into any model, dataset, index, or product accessible by any third party. Vendor's confidentiality obligations shall survive for five (5) years after termination or expiration of this Agreement, and with respect to trade secrets, for so long as such information remains a trade secret under applicable law.

**Negotiation Impact:** The original clause addresses only traditional disclosure risk and leaves room for the vendor to argue that internal model training is not a disclosure. The revised language closes that gap by expressly prohibiting AI-related uses and derivative incorporation, which is critical to preserving confidentiality and avoiding privilege waiver arguments. It also strengthens post-termination protection through survival language. In negotiation, keep the standard confidentiality exceptions but ensure they cannot be used to justify model training or residual learning from Company information.

* * *

## 15\. Force Majeure Limits

This clause defines which extraordinary events excuse nonperformance and when the Company may exit if disruption continues. AI vendors may try to draft force majeure broadly enough to cover avoidable problems such as model degradation, upstream provider changes, subprocessor failures, or foreseeable regulatory requirements. Those events are often core operational risks that the vendor should manage, not external catastrophes.

The negotiator should narrow force majeure to genuinely external events beyond reasonable control, exclude AI-specific operational failures and third-party dependency problems, and obtain a termination right with refund if the event persists. This prevents the vendor from using force majeure as a shield for ordinary service risk.

**Comparative Wording:**

- **Vendor Draft:** Neither party shall be liable for any failure or delay in performance caused by circumstances beyond its reasonable control, including but not limited to acts of God, natural disasters, pandemic or epidemic, government actions or orders, war or terrorism, labor disputes, power or internet outages, cyberattacks, failure or disruption of third-party services or infrastructure, or any other event beyond the party's reasonable control (each, a "Force Majeure Event").

- **Company Redline:** Neither party shall be liable for delay or failure to perform to the extent caused by an event beyond that party's reasonable control that could not have been prevented through commercially reasonable diligence, including natural disasters, war, terrorism, government orders, or widespread internet or utility outages. The following shall not constitute a Force Majeure Event for Vendor: model performance degradation, hallucinations, training data deficiencies, ordinary cybersecurity incidents that Vendor was obligated to prevent, changes or failures of upstream AI providers, cloud providers, or other subprocessors, staffing shortages, increased costs, or compliance obligations that were reasonably foreseeable as of the Effective Date. If a Force Majeure Event materially affects the Service for more than thirty (30) consecutive days, Customer may terminate the affected Service without penalty and Vendor shall promptly refund any prepaid fees for the unused portion of the terminated term.

**Negotiation Impact:** The original clause is broad enough to excuse many risks inherent in the vendor's AI delivery model, including third-party failures and cyber incidents. The revised language limits relief to truly external events and expressly excludes risks that the vendor should contract for, monitor, or mitigate as part of normal operations. It also gives the Company a clear exit and refund right if disruption is prolonged. In negotiation, emphasize that reliance on upstream model providers and subprocessors is a business choice by the vendor and should not be shifted to the customer through force majeure language.

* * *

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/business-handshake-silhouette.png?w=1024)

# Part Three: Sector-Specific Safeguards

This domain addresses contractual protections tailored to specific regulatory frameworks, practice areas, and data categories that require heightened treatment beyond the general governance and risk allocation terms in Parts One and Two. These clauses recognize that AI vendor agreements serving legal, healthcare, financial, immigration, real estate, and other regulated environments must account for distinct privilege, confidentiality, compliance, and liability concerns that general-purpose AI contract terms do not adequately cover.

* * *

## 16\. Enterprise Tier Assurance

This clause confirms that the contracted service is the enterprise offering and not a consumer-tier product subject to broader data use rights. In AI contracting, marketing statements about enterprise privacy are not enough; the agreement must expressly state that the purchased version excludes consumer-style training rights and applies enterprise-grade controls. This is especially important for legal users because use of a consumer version for confidential matters can create privilege and confidentiality concerns regardless of sales representations.

The negotiator should require a contractual representation identifying the exact service tier and version, confirming that customer data is not used for model training except as expressly authorized, and stating that conflicting online consumer terms do not apply.

**Comparative Wording:**

- **Vendor Draft:** Vendor may provide the Service under its generally applicable terms, policies, and service descriptions, as updated from time to time. Certain features may be made available under consumer, business, or enterprise offerings subject to the then-current documentation.

- **Company Redline:** Vendor represents and warrants that the Service provided under this Agreement is the enterprise version identified in Order Form Exhibit A, and not any consumer or public-use offering. No consumer terms, clickwrap terms, privacy notices, or online policies applicable to consumer offerings shall apply to Customer or Customer Data unless expressly incorporated into this Agreement by written amendment signed by both parties. Vendor further represents that, except as expressly permitted in this Agreement, Customer Data will not be used for model training, retraining, fine-tuning, or product improvement.

**Negotiation Impact:** The original language leaves open the possibility that consumer-tier terms or shifting online policies will govern, creating ambiguity around training and privacy protections. The revised language locks in the enterprise tier and excludes conflicting consumer terms, reducing the risk that broader data-use rights will apply by implication. In negotiation, ask the vendor to name the exact product edition and to confirm that any free, trial, beta, or embedded features are also covered by the same enterprise restrictions.

* * *

## 17\. Training Data Explanation

This clause addresses the practical and legal consequences of using Company data to train AI systems. Training is not mere temporary processing; it changes model parameters so that patterns from Company data may influence future outputs across users, and the process is not realistically reversible. This creates confidentiality loss, competitive exposure, and regulatory risk, particularly where personal data is repurposed beyond the original collection purpose.

The negotiator should prohibit not only direct training but also fine-tuning, tuning, adaptation, reinforcement, evaluation on customer content, and use of derivatives such as embeddings or aggregated patterns. The clause should also ensure downstream providers are subject to the same restrictions.

**Comparative Wording:**

- **Vendor Draft:** Vendor may use Customer Data and related usage information to improve model quality, safety, and performance, including through model training, fine-tuning, evaluation, and related machine learning development activities, subject to Vendor's privacy policy.

- **Company Redline:** Vendor shall not use Customer Data, including prompts, inputs, outputs, documents, metadata, feedback, embeddings, vector representations, aggregated patterns, or derivatives, for any model training, retraining, fine-tuning, reinforcement learning, evaluation, testing, benchmarking, or product improvement purpose. Vendor shall process Customer Data solely to provide the Service to Customer in accordance with this Agreement. Vendor shall ensure that the same prohibition applies to all subprocessors, foundation model providers, hosting providers, vector database providers, and any other third parties that access or process Customer Data.

**Negotiation Impact:** The original language gives the vendor broad rights to absorb Company data into model development under the label of quality, safety, or performance improvement. The revised language expressly blocks both direct and indirect training uses and extends the restriction through the full processing chain. This materially reduces confidentiality, privilege, competitive, and privacy risks. In negotiation, do not allow exceptions for "safety" or "feedback" without tight purpose limits, minimal retention, and notice obligations.

* * *

## 18\. Downstream Training Ban

This clause focuses on the third-party processing chain behind many AI services. Even if the primary vendor agrees not to train on Company data, the same risk remains if a foundation model provider, cloud host, vector database, or other subprocessor can retain and use that data. The contract should therefore identify all entities touching the data, bind them to equivalent no-training restrictions, and make the primary vendor responsible for enforcement.

The negotiator should request a complete list of subprocessors and their functions and require confirmation that none may use Company data for training or model improvement.

**Comparative Wording:**

- **Vendor Draft:** Vendor may use third-party service providers, including cloud hosting, data storage, model providers, and analytics vendors, to support operation of the Service. Vendor will remain responsible for such providers in accordance with this Agreement.

- **Company Redline:** Vendor shall provide Customer with a complete list of all subprocessors, foundation model providers, cloud providers, vector database providers, and other third parties that access, process, store, host, or transmit Customer Data, together with a description of each party's role. Vendor shall contractually require each such party to comply with restrictions at least as protective as those set forth in this Agreement, including a prohibition on using Customer Data or any derivatives for model training, retraining, fine-tuning, evaluation, or product improvement. Vendor shall be fully liable for any act or omission of such third parties that would constitute a breach of this Agreement if committed by Vendor.

**Negotiation Impact:** The original language acknowledges third-party involvement but does not address the principal AI risk: downstream training and reuse. The revised language adds transparency, mandatory flow-down restrictions, and full vendor accountability. This closes a critical gap in AI data governance because much of the real risk sits with upstream model and infrastructure providers. In negotiation, ask for named providers in an exhibit and a representation that none have retained rights to train on Company data.

* * *

## 19\. AI Data Processing Agreement Core Terms

This clause updates the Data Processing Agreement for AI-specific processing risks. Standard DPAs often address instructions, security, and transfers but do not deal with model learning, embeddings, vector stores, or AI-specific deletion issues.

At minimum, the DPA should require processing solely on documented instructions, prohibit use of personal data for model training or improvement, disclose subprocessors with objection rights, require timely deletion including derived representations, and obligate cooperation with data subject requests. The negotiator should integrate these terms into the DPA or ensure the main agreement prevails over inconsistent DPA boilerplate.

**Comparative Wording:**

- **Vendor Draft:** Processor shall process Personal Data on behalf of Controller in accordance with the Agreement and the applicable Data Processing Addendum. Processor may engage subprocessors listed in its online subprocessor list and may update that list from time to time upon notice. Processor shall delete Personal Data in accordance with its standard retention schedule, unless otherwise required by law.

- **Company Redline:** Processor shall process Personal Data solely on Controller's documented instructions and only as necessary to provide the Services. Processor shall not use Personal Data or any derivatives thereof, including embeddings, vector representations, cached representations, aggregated patterns, or metadata linked to Personal Data, to train, retrain, fine-tune, benchmark, evaluate, or improve any machine learning model, algorithm, product, or service. Processor shall provide at least fifteen (15) days' prior written notice of any new subprocessor and Controller may object on reasonable privacy, security, or compliance grounds. Within thirty (30) days after termination or expiration of the Services, Processor shall delete or return all Personal Data, including embeddings, vector representations, cached content, and data stored in vector databases, unless retention is required by law. Processor shall reasonably cooperate with Controller in responding to data subject access, deletion, correction, portability, and objection requests.

**Negotiation Impact:** The original language reflects a conventional DPA that leaves AI-specific risks unaddressed and gives the processor broad operational discretion. The revised language adds instruction-only processing, a direct no-training rule, objection rights for new subprocessors, expanded deletion scope, and data-subject-rights support. This better aligns the DPA with modern AI processing realities and privacy law expectations. In negotiation, make sure the DPA and main agreement are consistent and that online DPA updates cannot reduce negotiated protections.

* * *

## 20\. Privilege Preservation

This clause is intended for legal users and addresses whether use of the enterprise AI service is structured to preserve attorney-client privilege and work product protections. Ethical guidance requires lawyers to understand how AI tools process data and to make specific disclosures to clients where necessary.

The contract should therefore include representations that the enterprise service is designed not to waive privilege through vendor use, that the vendor will enter into confidentiality and data processing commitments meeting the user's professional obligations, and that the vendor maintains appropriate security certifications. The negotiator should avoid relying on general marketing claims and instead require express contractual commitments.

**Comparative Wording:**

- **Vendor Draft:** Vendor will implement commercially reasonable administrative, technical, and organizational measures designed to protect Customer Data. Vendor does not provide legal advice regarding attorney-client privilege, work product protection, or Customer's professional responsibility obligations.

- **Company Redline:** Vendor represents that, when Customer uses the enterprise version of the Service in accordance with this Agreement, Vendor's processing and contractual restrictions are designed so that Vendor does not claim rights in Customer Data or output that would knowingly require disclosure to third parties or intentionally defeat Customer's assertion of attorney-client privilege or work product protection. Vendor shall execute confidentiality and data processing terms with protections at least as stringent as those reasonably required for Customer to comply with applicable ethical and professional responsibility obligations. Vendor further represents that it maintains current SOC 2 Type II certification, or an equivalent independently audited security standard, covering security and confidentiality controls relevant to the Service.

**Negotiation Impact:** The original language gives security comfort but disclaims any responsibility for privilege-sensitive processing, leaving legal users exposed. The revised language does not guarantee a court outcome, which vendors will resist, but it does secure operational and contractual commitments supporting privilege preservation and professional compliance. This is a more realistic and enforceable approach than asking the vendor to guarantee privilege as a matter of law. In negotiation, if the vendor resists the phrase "does not waive privilege," use "is designed and contractually restricted so as not to knowingly impair" and require strong confidentiality and no-training terms.

* * *

## 21\. Narrow AI Exceptions

This clause limits the vendor's use of broad carve-outs such as safety, abuse prevention, or feedback processing to circumvent no-training commitments. These exceptions are often presented as operational necessities, but if drafted broadly they can reintroduce training rights through the back door.

The negotiator should allow only narrowly tailored processing necessary for security and abuse detection, prohibit secondary use for model improvement, require minimization and short retention, and require notice where customer data is accessed under an exception except where legally prohibited. The goal is to preserve operational resilience without undermining core confidentiality protections.

**Comparative Wording:**

- **Vendor Draft:** Notwithstanding anything to the contrary, Vendor may use Customer Data as reasonably necessary to maintain safety, detect abuse, investigate misuse, improve content moderation systems, and process feedback to enhance the Service and related technologies.

- **Company Redline:** Notwithstanding the foregoing restrictions, Vendor may access and process limited Customer Data solely to the extent strictly necessary to detect, prevent, or remediate security incidents, fraud, abuse, or unlawful use of the Service, or to respond to binding legal process. Such processing shall be subject to data minimization, role-based access controls, and retention only for the period strictly necessary for the applicable purpose. Vendor shall not use any data accessed under this exception to train, retrain, fine-tune, evaluate, benchmark, or otherwise improve any model, product, or service. Vendor shall provide Customer prompt written notice of any such access or use, unless prohibited by law.

**Negotiation Impact:** The original language uses broad operational concepts like safety and feedback to create an open-ended right to enhance the service using Company data. The revised language narrows exceptions to true security and legal necessity, adds minimization and retention controls, and preserves the prohibition on model improvement. This prevents the exception from swallowing the rule. In negotiation, accept only those exceptions the vendor can clearly operationalize and audit.

* * *

## 22\. Criminal Defense Controls

This clause adapts the agreement for criminal defense practice, where attorney work product and strategy materials are exceptionally sensitive and errors can directly affect liberty interests. AI outputs in this context should be used cautiously and independently verified.

The contract should expressly confirm that criminal defense prompts, strategy materials, witness assessments, and plea positions will not be used for training or improvement and should support a restricted use case focused on research pre-screening rather than unverified substantive advice. The negotiator should also seek language acknowledging work product sensitivity and strong confidentiality controls.

**Comparative Wording:**

- **Vendor Draft:** Customer is responsible for determining whether the Service is appropriate for any legal matter and for independently reviewing all outputs before use. Vendor disclaims responsibility for Customer's legal judgments and case strategy.

- **Company Redline:** Vendor acknowledges that Customer may use the Service in connection with criminal defense matters involving highly sensitive attorney work product, case strategy, witness evaluations, plea discussions, and sentencing analysis. Vendor shall not use any criminal defense-related Customer Data, prompts, outputs, or derivatives for model training, retraining, fine-tuning, benchmarking, or product improvement. Vendor further agrees that its processing of such data under the enterprise version is subject to strict confidentiality obligations intended to preserve work product protections. Customer shall independently verify all outputs before external use, and the Service is authorized only as a research pre-screening and internal drafting aid unless otherwise expressly agreed in writing.

**Negotiation Impact:** The original language places all suitability and strategy risk on the customer without recognizing the elevated sensitivity of criminal defense content. The revised language preserves the need for independent verification while adding explicit no-training and confidentiality protections tailored to criminal practice. This reduces work product and strategic exposure. In negotiation, position the use restriction as a shared risk-control measure rather than a concession by the customer.

* * *

## 23\. Family Law Safeguards

This clause addresses family law matters, which often involve spousal communications, child-related information, settlement positions, and detailed financial disclosures. Exposure of this data can create severe privacy and privilege consequences.

The contract should prohibit any use of family law matter details for training or improvement, and because breach harms can be particularly acute, the customer should seek immediate termination rights and indemnification where exposure causes privilege-waiver or confidentiality claims. The negotiator should also ensure that incident response obligations are strong and prompt.

**Comparative Wording:**

- **Vendor Draft:** Vendor shall maintain industry-standard safeguards to protect Customer Data and shall notify Customer of Security Incidents in accordance with Vendor's security policy. Customer remains responsible for determining whether the Service is appropriate for sensitive matters.

- **Company Redline:** Vendor acknowledges that Customer may process highly sensitive family law information through the Service, including settlement positions, spousal communications, child-related information, and financial disclosures. Vendor shall not use any such Customer Data, prompts, outputs, or derivatives for model training, retraining, fine-tuning, evaluation, or product improvement. In the event of any unauthorized access, disclosure, or use affecting such data, Customer may immediately suspend or terminate the affected Service without penalty, and Vendor shall indemnify Customer for third-party claims to the extent arising from Vendor's breach of its confidentiality, security, or data-use obligations.

**Negotiation Impact:** The original language relies on general safeguards and leaves the customer to assess sensitivity risk. The revised language adds subject-matter-specific no-training protection, an immediate termination right after exposure, and indemnity tied to vendor breach. This better reflects the stakes in family law matters. In negotiation, focus on strong incident response timing and a clear right to exit if trust in the service is compromised.

* * *

## 24\. Data Residency

This clause addresses immigration-related data, which can include national origin, travel history, family relationships, and status information that may expose clients to enforcement or cross-border privacy concerns.

The contract should prohibit training on immigration-related prompts and case details and should address data residency and transfer capabilities, particularly where data subjects or family members may be in the European Union or other restricted jurisdictions. The negotiator should verify hosting locations, transfer mechanisms, and subprocessor geography.

**Comparative Wording:**

- **Vendor Draft:** Vendor may process Customer Data in any jurisdiction in which Vendor or its subprocessors maintain operations, subject to applicable law and Vendor's transfer mechanisms.

- **Company Redline:** Vendor acknowledges that Customer may process highly sensitive immigration-related information through the Service, including national origin, visa or immigration status, family structure, travel history, and related legal strategy. Vendor shall not use any immigration-related Customer Data, prompts, outputs, or derivatives for model training, retraining, fine-tuning, evaluation, or product improvement. Vendor shall provide Customer with available data residency options, identify the jurisdictions in which such data will be processed, and implement lawful transfer mechanisms for any cross-border transfer of Personal Data. Upon Customer's request, Vendor shall disclose the locations of all relevant subprocessors handling immigration-related Customer Data.

**Negotiation Impact:** The original language gives the vendor broad freedom to process data globally, which may be unacceptable for sensitive immigration matters. The revised language adds a strict no-training rule and increases transparency and control over data location and transfers. This reduces enforcement, privacy, and regulatory risk. In negotiation, ask for region-specific hosting commitments if the vendor offers them and ensure transfer terms are reflected in both the main agreement and the DPA.

* * *

## 25\. HIPAA Business Associate Agreement Requirement

This clause applies where the AI service may process protected health information. General privacy and security language is not sufficient for HIPAA-regulated use; a separate Business Associate Agreement is required.

The contract should state that the service may not receive PHI until the BAA is executed, prohibit use of PHI for model training, require HIPAA-appropriate safeguards including encryption, and include breach notification timing consistent with the parties' compliance needs. The negotiator should avoid relying on generic security schedules as a substitute for a compliant BAA.

**Comparative Wording:**

- **Vendor Draft:** Vendor will maintain appropriate safeguards designed to protect Customer Data and will comply with applicable data protection laws as set forth in the Agreement.

- **Company Redline:** If Vendor will create, receive, maintain, transmit, or otherwise process Protected Health Information on behalf of Customer, the parties shall execute a HIPAA-compliant Business Associate Agreement before any such processing occurs. Vendor shall not use Protected Health Information for model training, retraining, fine-tuning, benchmarking, evaluation, or product improvement. Vendor shall implement administrative, physical, and technical safeguards, including encryption in transit and at rest, sufficient to satisfy applicable HIPAA requirements. Vendor shall notify Customer of any breach of unsecured Protected Health Information without unreasonable delay and, in any event, sufficiently promptly to enable Customer to comply with its legal notification obligations, and no later than sixty (60) days after discovery.

**Negotiation Impact:** The original language is too general to satisfy HIPAA-driven contracting needs. The revised language makes the BAA a condition precedent to PHI processing, adds an explicit no-training restriction for PHI, and incorporates breach-timing and safeguard requirements suited to healthcare data. This closes a major compliance gap. In negotiation, confirm whether the vendor is willing to sign its standard BAA only or can accept customer paper, and align the breach timeline with operational reality.

* * *

## 26\. Real Estate Audit Trail

This clause addresses output traceability for real estate and property-related work, where hallucinated documents, incorrect zoning citations, or misidentified authorities can affect title, escrow, and transactional compliance. Because these use cases depend heavily on source reliability, the contract should require audit trails showing what sources informed each output and when they were accessed.

The negotiator should also tie this to model performance commitments and retention of logs sufficient for dispute resolution and internal review.

**Comparative Wording:**

- **Vendor Draft:** Vendor may provide usage dashboards and general output history as part of the Service. Vendor does not warrant that all outputs will include source attribution or complete provenance data.

- **Company Redline:** For outputs used in connection with real estate, land use, title, escrow, zoning, or property-related matters, Vendor shall maintain and make available to Customer, upon request, audit trails sufficient to identify the underlying data sources, source citations, retrieval timestamps, and material system actions associated with the generation of each output, subject to reasonable confidentiality protections for Vendor's proprietary systems. Vendor shall retain such audit information for at least twelve (12) months or such longer period as required by applicable law or Customer's written retention schedule communicated in advance.

**Negotiation Impact:** The original language treats provenance as optional, which is risky in property-related matters where source accuracy is critical. The revised language creates a practical audit trail obligation that supports verification, error investigation, and defensible use. This improves accountability without requiring the vendor to disclose source code. In negotiation, if full provenance is not available for every output, at least require it for retrieval-augmented outputs and high-risk use cases.

* * *

## 27\. Client Disclosure Support

This clause supports the customer's obligation to make informed disclosures to its own clients regarding AI tool use. Ethical guidance increasingly requires specificity about which tools are used, which versions are deployed, what categories of client data are processed, and whether training occurs.

The contract should require the vendor to provide accurate documentation about the service version, data practices, and known material risks so the customer can make truthful client disclosures and obtain informed consent where needed. The negotiator should also seek prompt notice of changes that would alter prior disclosures.

**Comparative Wording:**

- **Vendor Draft:** Vendor may update its documentation, privacy disclosures, and service descriptions from time to time. Customer is responsible for its own compliance with professional responsibility rules and client communication obligations.

- **Company Redline:** Vendor shall provide Customer with accurate and current documentation reasonably sufficient for Customer to describe to its clients the specific Service and version in use, the categories of data processed, whether Customer Data is used for training or product improvement, the locations and categories of subprocessors involved in processing, and the material confidentiality, privacy, and security controls applicable to the Service. Vendor shall promptly notify Customer of any material change to such information so that Customer may update client disclosures and obtain any additional consents required by law or professional responsibility obligations.

**Negotiation Impact:** The original language leaves the customer solely responsible for disclosures while allowing the vendor to change service details over time. The revised language does not shift ethical duties to the vendor, but it does require the vendor to provide the information needed for accurate disclosures and updates. This reduces the risk that the customer will unknowingly make incomplete or outdated representations to clients. In negotiation, tie this clause to modification notice rights so that disclosure-relevant changes cannot occur silently.

* * *

## 28\. AI Deletion Certification

This clause expands deletion obligations to AI-specific data artifacts and requires certification that personal data has not been retained in training assets. Traditional deletion clauses often cover raw files but not embeddings, cached representations, vector database entries, or evaluation datasets. For AI systems, those derived forms can still carry sensitive or personal information.

The contract should require deletion within a defined period, cover all such artifacts, and provide written certification, including confirmation that personal data does not persist in model weights or training datasets to the extent the vendor has prohibited such use. The negotiator should align this clause with the DPA and termination provisions.

**Comparative Wording:**

- **Vendor Draft:** Upon termination, Vendor will delete or return Customer Data in accordance with its standard retention policies, except for archived copies retained in the ordinary course of business.

- **Company Redline:** Upon termination or expiration of the Services, Vendor shall, within thirty (30) days, delete or return all Personal Data and other Customer Data in its possession or control, including all embeddings, vector representations, cached representations, retrieval indexes, evaluation datasets containing Customer Data, and data stored in vector databases, except to the extent retention is required by law. Vendor shall provide written certification upon Customer's request that such data has been deleted or returned and, to the extent Vendor has complied with the no-training obligations in this Agreement, that Customer Data and Personal Data do not persist in any Vendor training datasets or model weights.

**Negotiation Impact:** The original language relies on standard retention practices and omits AI-derived artifacts, leaving residual data risk. The revised language broadens the deletion scope, imposes a firm timeline, and adds certification to support auditability and legal compliance. This is especially important where the customer must demonstrate deletion to clients or regulators. In negotiation, confirm whether backup deletion follows a longer cycle and require those backups to remain inaccessible and excluded from active use.

* * *

## 29\. Hallucination Liability Link

This clause connects liability exposure to documented model performance rather than allowing the vendor to disclaim responsibility for inaccurate outputs entirely. AI systems have known baseline hallucination risk, and if the vendor markets the service for legal, analytical, or regulated uses, the contract should address the consequences when documented performance standards are not met.

The negotiator should tie remedies and liability-cap carve-outs to failure to meet agreed accuracy or quality thresholds, especially where the customer used the service as instructed. This creates a more rational allocation of risk than a blanket disclaimer.

**Comparative Wording:**

- **Vendor Draft:** The Service may generate incomplete, inaccurate, or non-unique outputs. Customer is solely responsible for reviewing and validating all outputs before use, and Vendor shall have no liability arising from Customer's reliance on any output.

- **Company Redline:** Vendor acknowledges that the Service may generate inaccurate or hallucinated outputs and that Customer will independently review outputs before external reliance. Notwithstanding the foregoing, Vendor shall remain responsible for failure of the Service to meet the performance standards, accuracy thresholds, and documented capabilities expressly set forth in this Agreement or in Exhibit A. Claims arising from materially inaccurate, fabricated, or hallucinated outputs shall not be subject to Vendor's general disclaimer of output reliability to the extent Customer used the Service in accordance with the Agreement and applicable documentation, and such claims shall be subject to the liability allocation and any applicable super-cap or carve-outs set forth in this Agreement.

**Negotiation Impact:** The original language places all output risk on the customer and effectively nullifies any performance promises. The revised language preserves the need for human review but prevents the vendor from using that principle as a complete shield when its service falls below agreed standards. This better aligns risk with the vendor's representations and the product's intended use. In negotiation, use the vendor's own benchmark claims and documentation to define measurable standards.

* * *

## 30\. Bias Risk Allocation

This clause addresses discrimination and disparate-impact exposure arising from AI outputs in hiring, credit, insurance, housing, benefits, legal services, and similar contexts. Because the vendor selects the model design and training approach, it should bear meaningful responsibility for testing and defending the system.

The contract should require bias testing, disclosure of results, and indemnity for claims arising from discriminatory model design or outputs, especially where the customer followed the vendor's instructions. The negotiator should resist language making the customer solely responsible for suitability and legal compliance.

**Comparative Wording:**

- **Vendor Draft:** Customer is solely responsible for determining whether the Service is suitable for any use case involving decisions about individuals and for ensuring compliance with all anti-discrimination and equal opportunity laws. Vendor disclaims any liability arising from Customer's use of the Service in such contexts.

- **Company Redline:** Vendor shall conduct periodic bias testing and fairness assessments using methodologies appropriate to the intended use cases of the Service and applicable law. Upon Customer's request, Vendor shall provide summaries of such testing, identified risks, and remediation measures. To the extent Customer uses the Service in accordance with this Agreement, the applicable documentation, and any stated use limitations, Vendor shall defend, indemnify, and hold harmless Customer from third-party claims, governmental investigations, and losses arising from discriminatory or unlawfully biased outputs or model design attributable to the Service.

**Negotiation Impact:** The original clause attempts to shift all discrimination risk to the customer, even though the vendor controls core technical design choices. The revised language rebalances that risk by imposing testing and indemnity obligations on the vendor while preserving conditions tied to authorized use. This is particularly important in high-impact decision contexts. In negotiation, if the vendor resists full indemnity, seek at least a super-cap, annual audit rights, and use-case-specific fairness representations.

* * *

## 31\. Output IP Protection

This clause addresses the risk that AI outputs may infringe third-party intellectual property rights if the underlying model was trained on unauthorized material or if the output reproduces protected expression. Several major vendors now offer enterprise output indemnity, which makes this a realistic negotiating ask rather than a theoretical one.

The contract should provide indemnity for output-level copyright and related IP claims where the customer used the service in accordance with documentation and did not materially alter the allegedly infringing content. The negotiator should use competitor benchmarks as leverage and ask the vendor to explain any refusal.

**Comparative Wording:**

- **Vendor Draft:** Vendor shall indemnify Customer from third-party claims that the Service infringes any intellectual property right, but Vendor shall have no liability for any claims based on outputs generated by the Service or Customer's use of such outputs.

- **Company Redline:** Vendor shall defend, indemnify, and hold harmless Customer from and against any third-party claim alleging that the Service, or output generated by the Service, infringes or misappropriates any copyright, trademark, trade secret, or other intellectual property right, provided that Customer used the Service in accordance with this Agreement and applicable documentation and did not materially modify the allegedly infringing portion of the output. Vendor shall not exclude output-level claims from its indemnity solely because the allegedly infringing material appears in generated output rather than in the Service code or interface.

**Negotiation Impact:** The original clause covers only the platform and leaves the customer exposed to one of the most visible AI litigation risks. The revised language extends indemnity to generated outputs under commercially reasonable conditions, aligning the contract with market movement among leading enterprise AI vendors. This materially improves risk allocation for customer-facing or published uses of output. In negotiation, cite competitor practice and ask for at least copyright-only indemnity if the vendor will not agree to broader IP coverage.

## Negotiation Tips for AI Vendor Contracts

These principles apply across the full agreement.

### Tip 1: Start with the actual AI risk, not the template

A standard software paper will hide too much.

Implementation tip: Build a simple AI contract issue list before the first vendor redline. Use that list to drive the review instead of reacting clause by clause.

### Tip 2: Turn every material risk into one of three things

Every meaningful AI risk should become either a contract clause, an operational control, or a deal-breaker.

Implementation tip: If a risk is serious and appears nowhere in the agreement or implementation plan, assume it has been left with you.

### Tip 3: Use market examples aggressively

The AI contract market is moving. Use that movement.

Implementation tip: Bring named competitor commitments into the negotiation. They shift the conversation from “custom ask” to “market norm.”

### Tip 4: Preserve the right to walk

This is still the strongest negotiation position.

Implementation tip: If the vendor will not restrict training on your data, share liability meaningfully, or provide a realistic exit path, be prepared to walk away.

## References for AI Vendor Contracting

If you want these negotiations to stand up under legal, operational, and governance scrutiny, anchor them in strong market and regulatory references.

Here are the references I would use.

- ISO/IEC 42001, AI management systems

- ISO/IEC 23894, AI risk management

- NIST AI Risk Management Framework 1.0

- Sector-specific privacy, discrimination, consumer protection, and financial regulations

- Public commitments and contract benchmarks from major AI providers

- Emerging AI legislation such as the EU AI Act and state-level high-risk AI rules

- Data portability and switching rights under relevant digital regulation

- Internal procurement, third-party risk, privacy, and security review frameworks

If your organization already has strong SaaS contracting, DPA review, and vendor risk management, use those channels. The important step is adding the AI-specific protections that standard software procurement still misses.

## Why AI Vendor Contracts Fail When Treated Like Ordinary Procurement

When teams treat AI contracting as ordinary procurement, they focus on price, uptime, support, and confidentiality, then assume the rest will behave like any other software product. That is how they miss the most consequential AI risks. Broad training rights. Weak output protections. Minimal liability. Unclear drift obligations. Lock-in through embeddings and custom behavior. Thin regulatory support.

When teams treat AI vendor contracts as risk allocation instruments for a probabilistic, evolving, data-dependent system, the quality of the deal changes. The contract becomes usable. The risks become visible. The vendor has to share responsibility more realistically. The customer has more control over data, output, and exit.

A strong AI vendor contract works because it allocates AI risk where it actually belongs, not where the standard template tries to leave it.

* * *

## About the Author

The frameworks, tools, checklists, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you’re building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
