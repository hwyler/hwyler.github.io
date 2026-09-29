---
title: "Practical AI Assessments"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-data-assessment"
  - "ai-feasibility-assessment"
  - "ai-impact-assessment"
  - "ai-poc"
  - "ai-project-development-plan"
  - "ai-proof-of-concept"
  - "ai-risk-assessment"
  - "ai-use-case-assessment"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "technology"
---

## The 9-Stage AI Assessment Framework That Answers Three Questions Every Project Must Face

Every AI project, regardless of industry, budget, or technology, must answer three questions at the right time. Can we build this? Are we ready to deploy it? Did it actually succeed?

Most organizations answer the first question with enthusiasm, rush past the second, and never systematically address the third. The result is predictable. Projects that were technically feasible but operationally unready get pushed into production. Systems that are deployed never get measured against the business case that justified them. And organizations accumulate AI systems they can't confidently say are delivering value.

A structured AI assessment framework creates defined evaluation gates across the full project lifecycle. Nine assessments, grouped into three phases, ensure that every critical question gets asked at the point where the answer can still influence decisions. Skip an assessment and you're making downstream commitments based on untested assumptions. Complete each one rigorously and you build a chain of evidence that supports every decision from concept through sustained operation.

This post walks through all nine assessments, explains what each one evaluates, and provides the practical guidance that determines whether these assessments produce real decisions or decorative documentation.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/computer-cooling-system.png?w=1024)

## Phase 1: Can We Build This?

The first three assessments determine whether an AI project should proceed into development. They evaluate the problem, the technical viability, and the data foundation. Getting clear answers at this stage is the cheapest form of risk management available. Stopping a non-viable project during Phase 1 costs days of analysis time. Stopping it during development costs months of engineering effort.

These three assessments are interdependent. A strong use case with poor data readiness shouldn't proceed. Strong data readiness without a clear use case produces a solution looking for a problem. Strong feasibility without either produces a technology demonstration with no business value.

All three assessments should be completed within the same evaluation window, typically two to four weeks, and reviewed together in a single go/no-go decision meeting.

Implementation tip: Assign ownership of each Phase 1 assessment to a different team member or function. The use case assessment should be owned by a business stakeholder who understands the problem. The feasibility analysis should be owned by a technical lead who can evaluate architecture, skills, and infrastructure honestly. The data readiness assessment should be owned by a data engineer who can verify data quality empirically, not theoretically. When one person or team owns all three, assessments tend to confirm the conclusion the owner has already reached. When different people with different perspectives own different assessments, the combined evaluation produces a more honest picture of project viability.

## Assessment 1: Use Case Assessment

The use case assessment identifies the specific business problem the AI system will solve and quantifies the value of solving it. This is where most AI projects either build a strong foundation or begin accumulating the vague objectives that eventually undermine them.

Three activities define a thorough use case assessment.

Describe how users interact with AI to achieve a specific goal. This goes beyond describing what the AI system does. It describes the human workflow that the AI system fits into: who triggers the AI, what input they provide, what output they receive, what they do with that output, and how the AI-assisted workflow differs from the current process. A use case that describes only the AI component without describing the human workflow will produce a system that works in isolation and fails in practice.

Map current processes to quantify inefficiencies, expected value, and improvement areas. Before you can measure improvement, you need a documented baseline of how the process works today. Map each step in the current process, measure the time each step takes, identify where errors occur most frequently, and calculate the cost of the current approach. This map becomes the reference point against which all future performance measurements are compared.

Define measurable success metrics and align AI goals with user needs. Every use case should specify what success looks like in numbers: processing time targets, accuracy thresholds, cost reduction goals, and user satisfaction benchmarks. These metrics should reflect what users actually need, not what the technology can most easily deliver. A system that achieves 98% accuracy on a metric users don't care about while achieving 70% accuracy on the metric they depend on has failed its use case regardless of the headline number.

What to document: The use case assessment should produce a single document containing: the problem statement, the current process map with baseline measurements, the proposed AI-assisted process, identified user roles and their interactions with the system, success metrics with numerical targets, and a preliminary estimate of business value.

Implementation tip: The process mapping step reveals hidden complexity that interviews and requirements documents miss. Documented processes and actual processes frequently diverge. Employees develop workarounds, skip steps that seem unnecessary, and add informal quality checks that aren't in any procedure manual. Map the actual process by observing it, not by reading the documentation. The discrepancies between documented and actual processes often identify the real bottlenecks and the real opportunities for AI assistance, which may differ substantially from what the initial problem statement assumed.

The use case assessment identifies the specific business problem AI can solve. This is where the project gets anchored in an actual business need.

The responsible parties are the business owner, process owner, product lead, and AI governance or transformation lead. Legal, privacy, security, and compliance should be consulted where the use case touches regulated data or sensitive decisions.

The critical artifacts are the use case statement, user interaction description, current process map, pain point summary, value hypothesis, and success metrics. These should be clear enough that a reviewer can understand the business problem without needing a demo.

What to implement: Describe how users will interact with the AI system to achieve a specific goal. Map the current process to quantify inefficiencies, delays, rework, or quality problems. Identify the expected value and improvement areas. Define measurable success metrics and align the AI goal with user needs, not just management enthusiasm.

This assessment should answer a basic question. Is this a real business problem with a plausible AI role, or just a technology idea looking for a use case?

Implementation tip: Require one “current state” metric and one “target state” metric in the use case review. If there is no measurable gap, the value case is too weak.

## Assessment 2: Feasibility Analysis

The feasibility analysis assesses whether the proposed AI solution can be built, deployed, and maintained within the organization's technical, financial, and regulatory constraints. A viable use case that isn't feasible should be shelved until constraints change, not forced into development.

Four evaluation areas define feasibility.

Evaluate tech stack, data, and skill availability. Does your current infrastructure support the proposed AI system's compute, storage, and networking requirements? Does the team possess demonstrated experience with the required model architectures, development frameworks, and deployment patterns? Are gaps addressable within the project timeline through hiring, training, or partnerships? Honest answers to these questions prevent the common pattern of approving projects that require capabilities the organization doesn't have and can't acquire fast enough.

Estimate business ROI and strategic fit. Calculate projected return on investment using conservative assumptions. Include all costs: development, infrastructure, data preparation, training, deployment, and ongoing maintenance and monitoring. Compare projected value against projected cost over a 3-year horizon. Separately assess strategic fit: Does this project align with organizational AI strategy? Does it build capabilities that support future AI initiatives? Strategic value can justify projects with marginal ROI, but that tradeoff should be made explicitly, not by default.

Check regulatory and market readiness. Identify every regulation that applies to the proposed AI system in every geography where it will operate. Evaluate whether the system can meet compliance requirements. Assess whether the market context, including customer expectations, competitive dynamics, and industry norms, supports the proposed AI application. A technically feasible system that violates regulatory requirements isn't feasible regardless of its other merits.

Gauge time and budget constraints. Compare the estimated development timeline against business deadlines. If the business need expires before the AI system can be deployed, the project isn't feasible in its current form. Consider whether a reduced-scope version could deliver partial value within the available timeline.

Implementation tip: The most common feasibility analysis failure is evaluating each dimension independently and missing interactions between them. A project might be technically feasible (right skills, right infrastructure), financially feasible (positive ROI), and regulatorily feasible (compliant design) but still infeasible because the combination of regulatory compliance requirements and technical architecture decisions drives the cost above the ROI threshold. Evaluate feasibility dimensions in combination, not in isolation. Build a single feasibility summary that shows how constraints in one dimension affect assessments in others. This integrated view catches projects that pass each individual test but fail the combined evaluation.

## Assessment 3: Data Readiness

The data readiness assessment determines whether the data required for the AI system exists, is accessible, is of sufficient quality, and can be used within governance and privacy requirements. Data readiness issues are the most common cause of AI project delays and failures, and the most frequently underassessed.

Four evaluation areas define data readiness.

Confirm data volume and quality. Does enough data exist to train the proposed model effectively? Is the data accurate, complete, and representative of the scenarios the AI system will encounter in production? Quality assessment should include specific measurements: missing value rates, error rates verified against ground truth samples, consistency of formats across records, and demographic or segment representation compared to target population distributions.

Check accessibility and format fit. Can the required data be accessed by the development team within security and governance requirements? Is the data in formats that the proposed model architecture can consume, or does significant transformation work stand between raw data and usable training sets? Data that exists but isn't accessible, or that's accessible but requires months of reformatting, changes the project timeline and cost significantly.

Assess labeling effort required. If the proposed approach uses supervised learning, does labeled data exist? If not, how much labeling effort is required, who will do it, and how long will it take? Data labeling is one of the most underestimated costs in AI project planning. A model that requires 50,000 labeled examples, at an average labeling rate of 200 examples per day per labeler, needs approximately 250 person-days of labeling effort before model training can begin.

Ensure data governance, provenance, and privacy compliance. Document the origin of each data source. Verify that the data can legally be used for the proposed purpose. Confirm that privacy requirements, including consent, anonymization, retention limits, and data subject rights, can be met. Identify whether a data protection impact assessment is required and, if so, complete it before development begins.

Implementation tip: Data readiness assessments that rely solely on metadata and documentation consistently overestimate readiness. The data catalog says the dataset contains 500,000 records. The actual dataset contains 500,000 rows, of which 80,000 are duplicates, 35,000 have critical fields missing, and 12,000 contain values outside valid ranges. After deduplication and quality filtering, the usable dataset is 373,000 records, which may or may not be sufficient. Always run a quantitative data profile as part of the readiness assessment: record counts after deduplication, null rates per field, value distribution analysis, and sample-based accuracy verification against source systems. The gap between documented data quality and measured data quality is almost always larger than expected.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/watermark-free-gemini_generated_image_fn28r6fn28r6fn28-1.png?w=1024)

## Phase 2: Are We Ready to Deploy?

The next three assessments determine whether the AI system is ready for real-world operation. They progress from controlled validation (proof of concept) through limited real-world testing (pilot program) to full deployment preparation (production readiness).

Phase 2 assessments are inherently iterative. A proof of concept that reveals technical limitations feeds back into design changes. A pilot that surfaces user experience issues feeds back into interface refinement. A production readiness assessment that identifies security gaps feeds back into hardening work. This feedback is the point. Phase 2 exists to find problems while they're still cheap to fix.

The transition between Phase 1 and Phase 2 should be a formal gate. Only projects that pass all three Phase 1 assessments should enter Phase 2. Projects that pass Phase 1 with conditions (such as "proceed if data labeling is completed by date X") should have those conditions tracked and verified.

## Assessment 4: Proof of Concept

The proof of concept tests core AI functionality with a minimal viable prototype using actual company data. It validates that the proposed approach works in practice, not just in theory.

Two evaluation priorities define the proof of concept.

Validate algorithm performance against defined metrics and baseline requirements. Using the success metrics defined in the use case assessment and the baseline measurements captured during process mapping, test whether the AI system meets, approaches, or falls short of targets. This validation must use actual company data, not public datasets or synthetic examples. Performance on generic data tells you whether the algorithm works in general. Performance on your data tells you whether it works for your problem.

Identify technical limitations and data quality issues before major investment. The proof of concept is designed to surface problems early. Does the model struggle with certain input categories? Does data quality degrade for specific subsets? Are inference times acceptable under realistic conditions? Are there edge cases that produce clearly wrong outputs? Document every limitation discovered. Each one represents a decision: fix it before proceeding, accept it as a known limitation, or determine that it disqualifies the approach entirely.

The proof of concept should be time-boxed. Two to four weeks is typical. The goal is to gather enough evidence to make a confident proceed/pivot/stop decision, not to build a polished system. Feature completeness is not the objective. Evidence-based confidence in the approach is the objective.

Implementation tip: Define proof of concept success criteria before building the prototype, and make those criteria the basis for the proceed decision. Without predefined criteria, proof of concept evaluations become subjective. The data science team sees promising results and wants to continue. The business stakeholder sees limitations and has concerns. Without agreed-upon criteria, the discussion becomes a negotiation rather than an evidence-based evaluation. Specify: "The proof of concept succeeds if the model achieves at least 80% of the target accuracy metric on a representative sample of production data, with inference times below 2x the production latency requirement." Clear criteria produce clear decisions.

## Assessment 5: Pilot Program

The pilot program deploys the AI solution with a limited user group to gather real-world performance data. It bridges the gap between controlled testing and full production by exposing the system to actual users, actual workflows, and actual operational conditions.

Four evaluation areas define the pilot.

Gather user feedback and pain points. The pilot is the first time real users interact with the system in their actual work context. Their feedback reveals usability issues, trust barriers, workflow friction, and output quality concerns that no amount of internal testing can replicate. Collect feedback through structured channels: in-application feedback mechanisms, weekly survey check-ins, and direct observation sessions where a team member watches users interact with the system.

Assess operational integration ease. Does the AI system fit into existing workflows without creating disruption? Do users need to switch between multiple applications? Does the system's output arrive at the right point in the process and in a format users can act on? Integration friction that seems minor in a demo becomes a major adoption barrier in daily use.

Refine the implementation approach based on pilot findings. The pilot exists to generate the evidence needed to improve the system before full deployment. Plan for at least one refinement cycle between pilot completion and production rollout. Address the most common user complaints, fix the most impactful technical issues, and adjust the workflow integration based on observed usage patterns.

Estimate preliminary ROI and impact. Using pilot data, project the business impact of full deployment. If 20 pilot users processed 500 cases with 82% automation rate and 3.2x speed improvement, extrapolate what full deployment across 200 users would deliver. Compare this projection against the ROI estimate from the feasibility analysis. If the pilot suggests significantly lower returns than projected, reassess before committing to full deployment.

Implementation tip: Select pilot users deliberately, not randomly. Include enthusiastic early adopters (who will push the system's capabilities and provide detailed feedback), skeptical experienced users (who will identify where the AI falls short of expert human judgment), and typical average users (who represent how the majority will interact with the system). A pilot group composed entirely of enthusiasts will produce optimistic results that don't generalize. A pilot group composed entirely of skeptics will produce pessimistic results that discourage investment. A balanced group produces realistic data that supports honest deployment decisions.

## Assessment 6: Production Readiness

The production readiness assessment validates that the AI system meets all technical, operational, and governance requirements for full deployment. This assessment should confirm that every requirement identified during feasibility analysis has been met or explicitly accepted as a known limitation with documented mitigation.

Four evaluation areas define production readiness.

Validate algorithm performance against defined metrics and baseline requirements at production scale. Proof of concept and pilot performance may not extrapolate to production volumes. Test the system at projected production load with realistic data volumes and concurrent user counts. Verify that performance metrics hold under stress conditions, not just average conditions.

Confirm that monitoring, alerting, and incident response mechanisms are operational. Before the system goes live, verify that production monitoring dashboards are functioning, automated alerts are configured for key performance thresholds, the incident response team knows their roles and procedures, and escalation paths are documented and tested.

Verify compliance and governance readiness. Confirm that all regulatory requirements identified during feasibility analysis have been addressed. Verify that required documentation, including model cards, impact assessments, and data processing records, is complete and current. Confirm that access controls, audit logging, and data handling procedures meet security and privacy standards.

Confirm operational support readiness. Verify that the support team knows how to triage AI-specific issues. Confirm that retraining procedures are documented and the team knows when and how to execute them. Verify that the rollback procedure, the process for reverting to the previous system if the AI deployment fails, has been tested and works.

Implementation tip: Run the production readiness assessment as a formal checklist review with sign-off from every responsible function: engineering, operations, security, compliance, and the business owner. Each function signs off on the criteria within their domain. The system enters production only when all functions have signed. This process prevents the common pattern where one function, usually engineering, declares the system "ready" based on technical criteria while operational, security, or compliance readiness gaps remain unaddressed. The sign-off requirement forces every function to evaluate readiness through their own lens and take accountability for their determination.

## Phase 3: Did We Succeed?

The final three assessments evaluate whether the AI system delivers the value it promised. These assessments occur before launch (final validation), shortly after launch (performance review), and on an ongoing basis (value tracking).

Phase 3 is where most AI assessment frameworks end too early or never begin. Organizations invest heavily in determining whether they can build a system and whether they're ready to deploy it, then stop measuring once it's live. This creates a gap where systems operate without evidence of value, consuming resources indefinitely because nobody has the data to justify either continued investment or shutdown.

The transition from Phase 2 to Phase 3 should be seamless. Production readiness completion should automatically trigger the pre-launch validation timeline. Post-launch review should be scheduled before launch occurs. Value tracking cadence should be defined in the project plan, not established retroactively.

## Assessment 7: Pre-Launch Validation

Pre-launch validation ensures the AI system is technically robust, secure, and optimized before going live in production. This assessment occurs after production readiness approval and before the system is made available to all users.

Four validation activities define this assessment.

Stress-test for scalability and speed. Push the system beyond projected peak loads to identify breaking points. If normal production load is 1,000 predictions per hour, test at 3,000 and 5,000 predictions per hour. Determine where performance degrades, where errors begin, and where the system fails entirely. This information enables capacity planning and defines operational boundaries.

Validate security and privacy controls. Conduct security testing specific to the AI system: test API endpoints for input validation and authentication, verify that model artifacts and training data are protected against unauthorized access, test for AI-specific vulnerabilities including prompt injection and data leakage, and confirm that privacy controls including data anonymization, consent verification, and retention enforcement function correctly.

Run performance and load tests. Beyond stress testing, conduct sustained performance testing that simulates realistic production usage patterns over extended periods, typically 24 to 72 hours. This testing reveals issues that short-duration tests miss: memory leaks that accumulate over hours, gradual performance degradation under sustained load, and resource contention with other systems sharing infrastructure.

Fix all bugs identified during validation before production launch. Every defect discovered during pre-launch validation must be classified, prioritized, and resolved or explicitly accepted before the system goes live. Critical and major bugs must be fixed. Minor bugs may be accepted with documented justification and a scheduled fix date. Do not launch with known critical defects.

Implementation tip: Pre-launch validation should include a "chaos test" that simulates the failure of key dependencies. What happens when the database connection drops? What happens when the model serving endpoint becomes unavailable? What happens when input data arrives in an unexpected format? Systems that handle dependency failures gracefully, by queuing requests, falling back to default behaviors, or alerting operators, are production-ready. Systems that crash or produce silently wrong outputs when a dependency fails are not. These failure scenarios are inevitable in production. Testing for them before launch ensures the system responds safely when they occur rather than creating incidents.

## Assessment 8: Post-Launch Review

The post-launch review measures actual business outcomes against initial projections and success criteria. This assessment should occur at defined intervals after launch: 30 days, 90 days, and 6 months are typical checkpoints.

Three evaluation areas define the post-launch review.

Assess user adoption and satisfaction. Measure what percentage of target users are actively using the system, how frequently they use it, and how satisfied they are with its outputs. Compare adoption rates against the targets set during use case definition. If adoption is below target, investigate whether the gap is caused by usability issues, trust concerns, training gaps, or workflow friction. Low adoption negates all other performance metrics because a system nobody uses delivers no value regardless of its technical capabilities.

Monitor system performance, data drift, and model accuracy over time. Production performance should be measured against the same metrics used during proof of concept, pilot, and pre-launch validation. Track these metrics continuously, not just at review checkpoints. Watch for data drift, where the statistical properties of production data diverge from training data, causing model accuracy to degrade gradually. Establish automated alerts for accuracy drops, latency increases, and anomalous output distributions.

Identify operational lessons learned to refine future AI strategies. Every deployment teaches lessons that improve subsequent projects. Document what worked well, what didn't work as expected, what risks materialized that weren't anticipated, and what controls proved effective or ineffective. These lessons should be captured formally and shared with teams planning future AI initiatives.

Implementation tip: Schedule the 30-day post-launch review before the system launches, with a specific date, attendee list, and agenda template already established. Post-launch reviews that aren't pre-scheduled get postponed indefinitely because the team moves on to the next project. The 30-day review is the most critical because it catches early problems while they're still small and while the deployment team still has the context to diagnose them. By the 90-day review, team members may have rotated to other assignments and institutional memory about deployment decisions starts fading. The 30-day review window is the highest-leverage moment for identifying and correcting post-deployment issues.

## Assessment 9: Value Tracking

Value tracking evaluates whether the AI system delivers the promised business value over time. This is an ongoing assessment, not a one-time review. It answers the question that ultimately determines the system's fate: is this worth what we're paying for it?

Three evaluation areas define value tracking.

Calculate true ROI and cost benefits. Compare actual costs (infrastructure, maintenance, support, model retraining, monitoring) against actual benefits (time saved, errors prevented, revenue generated, cost avoided). Use the same methodology that was used to project ROI during the feasibility analysis, applied to actual data rather than estimates. This comparison reveals whether the business case has held up, exceeded expectations, or fallen short.

Identify optimization opportunities. Production operation reveals inefficiencies and improvement opportunities that weren't visible during development. Perhaps the model could be retrained on recent data to improve accuracy. Perhaps certain features could be simplified to reduce compute costs. Perhaps the system could be extended to adjacent use cases that share the same data and infrastructure. Value tracking should identify these opportunities and prioritize them based on expected incremental value.

Assess long-term business impact. Beyond direct ROI, evaluate the system's broader effects on the organization. Has it changed how teams make decisions? Has it created new capabilities that enable other initiatives? Has it affected employee satisfaction or customer perception? These broader impacts are harder to quantify but often represent more durable value than direct cost savings.

Implementation tip: Value tracking should include a "continuation decision" at regular intervals, typically annually. At each interval, explicitly decide whether the system should continue operating, be enhanced, be maintained without further investment, or be retired. This decision requires comparing the ongoing cost of operation against the ongoing value delivered. Without a formal continuation decision, AI systems persist indefinitely by institutional inertia, consuming infrastructure costs, maintenance effort, and monitoring attention long after their value has diminished. The continuation decision forces the organization to treat every AI system as an investment that must justify its ongoing costs, not as a permanent fixture that operates until something breaks.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/retro-ai-televisions.png?w=713)

## Implementation of AI Assessments

These principles apply across all nine assessments and all three phases.

Implementation tip on assessment documentation standards: Use a consistent template across all nine assessments. Each assessment document should include: assessment name, date, assessor, the system being assessed, the criteria evaluated, the findings for each criterion, the overall determination (pass/conditional pass/fail), any conditions or actions required, and the date of the next scheduled assessment. Consistent formatting enables comparison across assessments and across projects. When your tenth AI project uses the same assessment templates as your first, organizational learning compounds because patterns become visible across projects. Teams spot recurring failure modes, common data readiness issues, and consistent integration challenges that project-specific documentation would never reveal.

Implementation tip on assessment independence: The person or team conducting an assessment should not be the same person or team whose work is being assessed. Data scientists should not assess their own model's production readiness. Project managers should not assess their own project's feasibility. Business owners should not assess their own use case's viability without external challenge. This principle creates tension that many organizations find uncomfortable. But self-assessment consistently produces optimistic evaluations because the assessor has a personal interest in the outcome. Independent assessment, whether from a dedicated governance function, a peer team, or an external party, produces more honest evaluations and catches issues that self-assessment misses.

Implementation tip on connecting assessments across phases: Each assessment should explicitly reference findings from previous assessments. The pilot program assessment should reference proof of concept findings and document whether identified limitations were addressed. The post-launch review should reference production readiness findings and verify that accepted risks are being monitored. The value tracking assessment should reference the ROI projections from the feasibility analysis and document variance. This cross-referencing creates a continuous evidence chain that supports governance, demonstrates due diligence, and prevents the common pattern where each assessment exists as an isolated document disconnected from the assessments before and after it.

Implementation tip on assessment cadence after Phase 3: Once all nine assessments are complete for a given AI system, the assessment cycle doesn't end. Post-launch reviews should recur quarterly for the first year and semi-annually thereafter. Value tracking should recur annually at minimum. Any significant system change, such as model retraining, scope expansion, infrastructure migration, or regulatory change, should trigger reassessment of production readiness. Define this ongoing cadence in your AI governance framework so that it applies automatically to every deployed system rather than depending on individual project teams to remember.

## Authoritative Frameworks

Your AI assessment framework should align with these established standards:

- ISO/IEC 42001:2023, AI Management System (planning, evaluation, and improvement requirements)

- ISO/IEC 5338, AI System Life Cycle Processes (stage-gate processes across AI development)

- ISO/IEC 42005, AI Impact Assessment (assessment methodology and documentation)

- ISO/IEC 23894:2023, AI Risk Management (risk assessment across lifecycle stages)

- NIST AI Risk Management Framework, Map, Measure, and Manage functions

- EU AI Act, Articles 9-15 for high-risk AI system assessment requirements

- ISO/IEC 25010, Systems and Software Quality Requirements (quality criteria for system evaluation)

- IEEE 2801-2022, Recommended Practice for Quality Management of Datasets (data readiness criteria)

- ISO/IEC 27001:2022, Information Security Management (security assessment requirements)

- PMBOK Guide stage-gate methodology adapted for AI project governance

If you conduct AI assessments as paperwork exercises, filling in templates to satisfy governance requirements without allowing findings to influence decisions, you will approve projects that should have been stopped, deploy systems that aren't ready, and operate AI that may or may not be delivering value. Each unchecked assumption compounds risk. Each skipped assessment creates a blind spot. The assessments will exist in your document management system. The problems they should have caught will exist in your production environment.

When you treat each assessment as a genuine decision point, where findings lead to actions, where criteria determine outcomes, and where the answer "no, not yet" is valued as much as "yes, proceed," you create a governance framework that protects both the organization and the people affected by its AI systems. The nine assessments answer three simple questions. Can we build this? Are we ready? Did it work? Organizations that answer these questions honestly, with evidence rather than optimism, build AI systems that earn the trust they require and deliver the value they promise.

An AI system that passes every assessment on evidence earns confidence. An AI system that skips assessments borrows confidence it may never repay.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and globally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
