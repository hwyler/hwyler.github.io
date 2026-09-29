---
title: "Problem Definition for AI Projects and Use Cases"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-roi"
  - "ai-use-case"
  - "ai-use-case-identification"
  - "ai-use-case-roi"
  - "artificial-intelligence"
  - "hernan-huwyler"
  - "ieee-2801"
  - "iso-25010"
  - "iso-5338"
  - "nist-ai-risk-management"
  - "technology"
---

## How to Choose the Right Use Case Before You Waste Time and Budget

Most AI projects go wrong before anyone builds a model.

They go wrong in the problem statement. The team says they want “an AI solution” when what they really have is a workflow delay, a reporting bottleneck, a quality issue, or a staffing constraint. Then they spend months testing tools against a vague ambition, only to discover they never defined the business problem tightly enough to judge whether the solution worked. That is expensive. It is also avoidable.

A strong AI project starts with problem definition. Not vendor demos. Not model selection. Not prompt experiments. This post shows you how to define the problem properly, screen for feasibility, structure a use case analysis, and avoid the common failure points that lead teams into broad, fuzzy, low-value AI work.

A RAND Corporation study found that approximately 80% of AI projects fail. The most common reason wasn't technical. The projects failed because the problem they were solving was poorly defined, misaligned with business needs, or better solved without AI.

This pattern plays out predictably. A team gets excited about a new AI capability. They build a solution. They deploy it. Then they discover that the business process they automated wasn't the bottleneck, or that users don't trust the output, or that a simpler tool would have worked better at a fraction of the cost. The technology worked. The problem definition didn't.

Defining the problem is the most important and most frequently rushed step in any AI project. It determines everything downstream: the data you need, the technology you select, the success metrics you track, and whether anyone actually uses what you build. This post covers the complete problem definition process, from initial business assessment through feasibility evaluation and use case documentation, with the practical controls that prevent the most common failure modes.

## Why Problem Definition Fails: The Technology is the First Trap

Most AI problem definitions fail because they start with the technology instead of the problem. "We need to use generative AI" is not a problem statement. "We spend 1,200 hours per year manually responding to client due diligence questionnaires, with a 12% error rate and a 9-day average turnaround" is a problem statement.

The difference matters because technology-first framing skips the analysis that determines whether AI is the right solution. When a team starts with "we need to use AI," every problem looks like an AI problem. When a team starts with "we need to reduce due diligence response time from 9 days to 2 days," they can objectively evaluate whether AI, workflow automation, template standardization, or some combination delivers the best result.

This trap intensifies during hype cycles. Generative AI's rapid adoption has created organizational pressure to "do something with AI" that often overrides disciplined problem analysis. Leadership wants AI initiatives on the roadmap. Teams respond by fitting AI to whatever problems are available rather than identifying problems where AI genuinely adds value.

The antidote is a structured problem definition process with specific gates that force teams to justify why AI is the right approach before any development begins.

Implementation tip: Before any AI project receives funding or staffing, require the proposing team to answer one question in writing: "What happens if we solve this problem without AI?" If the answer describes a viable, cost-effective alternative, that alternative should be the default approach. AI should be selected only when it offers a measurable advantage over non-AI solutions. This single gate eliminates a significant percentage of projects that would otherwise consume resources and fail. Many organizations skip this question because it feels like an obstacle to progress. In practice, it protects teams from investing months of effort into AI solutions for problems that a well-designed spreadsheet macro or workflow automation tool could handle in weeks.

## Step 1: Assess Business Needs Before Starting AI Projects

Problem definition begins with a thorough assessment of business needs and challenges, conducted before any AI project work starts. This assessment requires input from management, employees, and potentially customers. Each group brings a different perspective on where problems actually exist.

Management identifies strategic priorities, resource constraints, and organizational goals that AI projects should serve. Employees identify operational pain points, workflow bottlenecks, and repetitive tasks that consume excessive manual effort. Customers identify service quality gaps, response time issues, and unmet needs that affect their experience.

Three categories of problems are strong candidates for AI solutions.

First, repetitive tasks consuming excessive manual effort. These are processes where humans perform the same cognitive work hundreds or thousands of times with minimal variation. Document classification, data extraction from forms, standard report generation, and routine customer inquiry responses all fall into this category.

Second, blockers in workflow initiation. These are bottlenecks where work stalls because it depends on a step that's slow, scarce, or inconsistent. If a compliance review takes 5 days because one specialist must manually review every submission, that bottleneck may be addressable with AI-assisted triage.

Third, skill bottlenecks requiring specialized capabilities. These are situations where the organization needs capabilities like data analysis, trend visualization, or code generation that require expertise that's scarce or expensive. AI can augment existing team members by handling the technical execution while humans provide judgment and context.

What to put in place: Build a structured intake process. Create a centralized repository for validated AI use case proposals. Every proposal should include the business problem, the current process, the expected improvement, and a preliminary assessment of whether AI is the right tool. Review proposals against your AI strategy and responsible AI principles before approving development.

Implementation tip: Start your AI program by educating teams on foundational AI applications before soliciting use case proposals. Teams that don't understand what AI can and cannot do will either propose nothing (because they don't see opportunities) or propose everything (because they overestimate capabilities). Run workshops covering practical applications like research automation, document analysis, and code generation assistance. After education, use case proposals are more realistic and more actionable. Organizations that skip this step and go straight to "submit your AI ideas" typically receive proposals that are either too vague to evaluate or too ambitious to execute. Foundational education calibrates expectations, and calibrated expectations produce better problem definitions.

## Step 2: Write Problem Statements That Are Specific Enough to Act On

Vague problem statements produce vague solutions. "Improve customer experience with AI" gives a development team no actionable direction. "Reduce average customer inquiry response time from 48 hours to 4 hours for the 15 most common question categories, which represent 73% of total inquiry volume" gives them everything they need to start.

Five rules produce actionable problem statements.

Avoid broad or vague formulations. Every problem statement should identify the specific process, the specific pain point, the specific people affected, and the specific outcome desired.

Clarify assumptions about the problem. Teams frequently carry assumptions that don't align with reality. "Our manual process is too slow" might be true, but the root cause might be a staffing shortage, not a process design issue. Validate assumptions with data before committing to a solution.

Break down the problem into manageable steps or processes. Large problems are composed of smaller tasks. Identify which specific tasks within the larger process are the best candidates for AI assistance. Not every step in a workflow needs AI. Some steps need better tooling. Some need process redesign. Some need additional staff.

Investigate how similar problems were handled before AI. Look at manual processes, prior AI attempts, and published methods as potential starting points. This research prevents teams from reinventing solutions that already exist and reveals approaches that have already been tried and failed, along with why they failed.

Focus on solving the problem, not on using the latest technology. Let the problem dictate the tools. The question is never "How can we use generative AI?" The question is always "What's the best way to solve this problem?" Sometimes the answer is generative AI. Sometimes it's a rules-based system, a database query, or a process change that requires no technology at all.

Implementation tip: The most reliable way to test a problem statement's quality is to hand it to someone outside the project team and ask them to describe what a successful solution would look like. If their description matches what the project team envisions, the problem statement is clear. If their description diverges significantly, the statement is ambiguous. This takes ten minutes and reveals gaps that days of internal discussion can miss. Ambiguity in problem statements is invisible to the people who wrote them because they share unspoken context. An outsider doesn't have that context, so ambiguity becomes immediately apparent.

## Step 3: Choose the Right Tool for the Problem

The temptation to use generative AI for everything is strong and should be actively resisted. Generative AI excels at specific task categories: natural language understanding and generation, content creation, summarization, and conversational interaction. It performs poorly at other tasks: precise numerical computation, deterministic logic, real-time data processing, and tasks requiring 100% accuracy.

Consider hybrid solutions that combine generative AI with other tools. A due diligence questionnaire automation system might use generative AI to draft responses, a retrieval system to find relevant source documents, and a rules-based engine to flag questions requiring human review. This combination is often more effective than any single technology alone.

Evaluate the capabilities of different technologies and choose the ones that best solve the specific problem. A classification task with clear categories and abundant labeled data might be better served by a traditional machine learning model than by a large language model. A data extraction task with structured input formats might be better served by template-based parsing than by AI of any kind.

Keep customer demands in perspective. Customers and internal stakeholders may request "AI-powered" solutions because the technology sounds impressive. The priority is delivering a solution that works and meets their needs, regardless of what technology drives it. A non-AI solution that works reliably at lower cost is superior to an AI solution that works inconsistently at higher cost.

Stay open to non-AI tools for certain aspects of the problem. Many successful "AI projects" are actually hybrid systems where AI handles 30-40% of the work and conventional software handles the rest. The AI component gets the attention, but the conventional components often deliver more of the value.

Focus on the end product's capabilities and performance. The success of an AI project is measured by whether it solves the stated problem within the stated constraints, not by how sophisticated its underlying technology is.

Implementation tip: When evaluating whether to use generative AI, traditional machine learning, or conventional software for a specific task, apply a simple decision filter. Does the task require generating novel content or understanding unstructured language? Consider generative AI. Does the task require classifying, predicting, or scoring based on patterns in structured data? Consider traditional ML. Does the task require applying deterministic rules to structured inputs? Consider conventional software. Many projects that start as "generative AI projects" end up as hybrid systems because the problem contains tasks from all three categories. Starting with this filter during problem definition prevents the common pattern of forcing generative AI into tasks where it performs worse than simpler alternatives.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/modern-disconnection.png?w=1024)

## Step 4: Feasibility Assessment Before Development Begins

Every problem definition must include a feasibility assessment that evaluates whether the proposed AI solution can actually be built, deployed, and maintained within organizational constraints. Feasibility covers two dimensions: requirements and assessments.

Requirements establish the governance gates. The proposed use case must comply with responsible AI principles, the organization's AI strategy, and applicable privacy, continuity, and cybersecurity regulations. This is a pass/fail evaluation. If the use case conflicts with any of these requirements, it should be redesigned or rejected before development resources are committed.

Assessments evaluate four practical feasibility questions.

First, is the projected return on investment positive? Estimate both the costs (development, data preparation, infrastructure, ongoing maintenance, monitoring) and the benefits (time savings, error reduction, revenue impact, compliance improvement). If the ROI case is negative or marginal, the problem may be real but the AI solution may not be justified.

Second, can the complexity and scalability be supported by existing and future infrastructure, data, models, explanatory requirements, and skills? An AI solution that requires capabilities the organization doesn't have and can't reasonably acquire isn't feasible regardless of how well the problem is defined.

Third, can quality, compliance, and security controls be met? If the use case requires processing sensitive personal data, can data protection requirements be satisfied? If the use case makes decisions affecting individuals, can explainability requirements be met? If the use case requires integration with regulated systems, can compliance controls be maintained?

Fourth, can the change be managed? This includes addressing both fear of job displacement among employees whose tasks may be automated and fear of missing out among leaders who want AI initiatives regardless of fit. Change management is a feasibility dimension that technical teams frequently overlook.

Implementation tip: The feasibility dimension most often underestimated is skills availability. Organizations frequently approve AI projects assuming they can hire or train the necessary talent during the development timeline. Industry data consistently shows that AI talent acquisition takes longer and costs more than initial estimates. Assess your current team's capabilities honestly before approving a project. If the project requires skills your team doesn't have, include talent acquisition or training timelines in the project schedule and treat them as dependencies, not assumptions. A project that's technically feasible but talent-infeasible will stall at the same rate as one that's technically impossible.

## Documenting the Use Case: What a Complete Analysis Form Looks Like

A well-defined problem needs structured documentation. A use case analysis form captures every element required for informed decision-making. The following sections should be completed for every AI project proposal.

Use case title and objective. Write a clear, specific title and a one-paragraph objective that states what the AI system will do, what manual effort it will reduce, and what quality improvements it will deliver. Example: "Automating due diligence questionnaire reporting with AI. Objective: To automate the generation of due diligence questionnaire reports using an AI agent, reducing manual effort and ensuring consistency and accuracy."

Business need. Describe the problem in operational terms. Quantify the pain where possible. Example: "We frequently receive due diligence questionnaires from clients, requiring detailed responses on security controls, policies, and procedures. The current manual process is time-consuming, prone to error, and inconsistent across different formats."

Expected user roles. Identify every role that will interact with the AI system and their specific responsibilities. For a due diligence automation system: Security analysts review and finalize AI-generated reports. Compliance officers ensure responses align with regulatory requirements. IT managers oversee integration with existing systems. Each role should be named specifically, not described generically.

Expected reach. Quantify the internal and external populations affected. Example: "Internal teams: 7 employees in security, compliance, and IT departments. External stakeholders: 240 clients receiving due diligence confirmations per year." These numbers establish the scale of impact and inform risk assessment.

Expected needed data. List every data source the AI system will require, with specifics about volume and content. Example: "IT control matrix: 154 security controls and corresponding narratives. Internal policies: 12 security policy documents. Procedures: 23 SOPs with steps and processes followed by the organization." This inventory determines data preparation effort and identifies potential gaps before development begins.

Implementation tip: The "expected needed data" section is where use case proposals most frequently underestimate effort. Teams list the data sources they know about and skip the preparation work required to make that data usable by an AI system. A list of "12 security policy documents" doesn't reveal that 4 of those documents are outdated PDF scans that require OCR processing, 3 contain conflicting information that needs reconciliation, and 2 haven't been reviewed in over a year and may not reflect current practices. For every data source listed, add a data readiness assessment: Is the data current? Is it in a format the AI system can process? Is it complete? Is it consistent with other sources? Does it require any transformation? This assessment typically adds 2-4 weeks to the project timeline. Discovering these issues during development adds 2-4 months.

## Documenting Process Changes and Anticipated Challenges

The use case analysis form must capture how the process will change and what challenges are anticipated. These sections prevent the common pattern of documenting the happy path while ignoring the difficult parts.

As-is process. Document the current process step by step, with enough detail that someone unfamiliar with it could understand the workflow. Example: "(1) Clients send due diligence questionnaires in various formats. (2) Security analysts manually review and respond to each questionnaire based on current practices. (3) Responses are reviewed and approved by a compliance officer before submission."

To-be process. Document the proposed AI-assisted process with the same level of detail. Clearly indicate where AI handles tasks and where humans remain in the loop. Example: "(1) Clients send due diligence questionnaires in various formats. (2) The AI agent automatically reviews and responds to each questionnaire based on the control matrix, internal policies, and SOPs. (3) The AI agent's responses are reviewed and validated by the security leader."

Expected changes. Describe the anticipated improvements in specific terms: "Significant reduction in time required to generate due diligence reports. Increased consistency and accuracy in responses. Improved efficiency, allowing employees to focus on higher-value tasks."

Expected challenges. Document known difficulties honestly. For a due diligence automation system, realistic challenges include: ensuring the AI agent accurately interprets and extracts relevant data from internal documents, fine-tuning the AI to understand different formats and client-specific requirements, and integrating the AI agent smoothly with existing systems and workflows.

AI limitations. Document what the AI system will not do well. This section is critical for setting realistic expectations. Example limitations: "The AI may struggle with highly nuanced or complex questions requiring deep contextual understanding. Potential for errors if the AI misinterprets data or lacks sufficient context. Dependence on the quality and completeness of input data." Teams that skip this section create an expectation gap between what stakeholders believe the AI will do and what it actually can do. That gap becomes a project risk.

Implementation tip: Require every use case analysis form to include both the "expected challenges" and "AI limitations" sections before approval. These sections are the ones teams most want to skip because they feel like arguments against the project. In practice, they're the opposite. A proposal that honestly documents challenges and limitations demonstrates that the team understands what they're building. A proposal that claims no challenges and no limitations demonstrates that the team hasn't thought carefully enough. Review committees should be more skeptical of proposals with empty limitation sections than proposals with detailed ones. The projects that fail most expensively are the ones where nobody documented what could go wrong.

## Defining Success Metrics That Prevent Ambiguity

Every use case analysis must include success metrics with specific numerical targets. Without defined success criteria, a project can never conclusively succeed or fail. It exists in a permanent state of "we're still working on it."

Four categories of success metrics cover the essential dimensions.

Time saved measures the operational efficiency gain. Example: "85% reduction in hours spent generating due diligence reports." This metric requires a documented baseline. If you don't measure how long the current process takes before deploying AI, you can't measure improvement after.

Accuracy rate measures quality of AI outputs. Example: "95% of AI-generated responses pass human review without significant modification." Define "significant modification" precisely. A typo correction is not significant. Rewriting a substantive response is. Without this definition, the metric becomes subjective and unreliable.

Customer or stakeholder satisfaction measures the impact on the people receiving AI-assisted outputs. Example: "80% positive feedback from clients on quality and timeliness of responses." This metric requires a feedback collection mechanism designed before deployment, not added as an afterthought.

Adoption rate measures whether target users actually use the system. Example: "99% of due diligence questionnaires processed through the AI system within 6 months of deployment." This metric is the ultimate test of whether the problem definition was correct. If users don't adopt the system, either the problem wasn't as painful as believed, the solution doesn't address it adequately, or change management was insufficient.

Implementation tip: Set success metric targets before development begins and resist the pressure to adjust them downward during the project. Target adjustment is sometimes legitimate, when new information reveals that initial targets were based on incorrect assumptions. But more often, targets get adjusted because the project is underperforming and the team wants to redefine success rather than address the gap. Protect against this by requiring any target adjustment to be approved by the original project sponsor with a documented justification for the change. If the original target was "85% reduction in processing time" and the team wants to adjust it to "50% reduction," the sponsor should understand why and explicitly accept the reduced ambition. This governance prevents the common pattern where projects gradually redefine success until any outcome qualifies.

## Piloting Before Scaling: The Sequence That Works

Problem definition should include a deployment strategy. The most reliable approach follows a specific sequence: educate, pilot, validate, scale.

Pilot solutions addressing repetitive tasks first to demonstrate quick wins. Quick wins build organizational confidence in AI, generate concrete data for ROI calculations, and reveal integration challenges at low risk. A pilot that automates 5% of due diligence responses teaches you more about data quality requirements, user trust dynamics, and accuracy thresholds than months of theoretical analysis.

Scale validated AI workflows while maintaining audit trails for compliance accountability. Scaling should begin only after the pilot has met its success metrics and the team has documented lessons learned. The audit trail requirement ensures that as the system handles more volume and higher-stakes decisions, every AI-generated output can be traced back to its inputs, the model version that produced it, and the human who reviewed it.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/futuristic-data-display-1.png?w=724)

Implementation tip: Define "pilot success" criteria before the pilot starts, and make those criteria the gate for scaling. The most common pilot failure mode is indefinite extension. The pilot runs for its planned duration, produces mixed results, and instead of making a go/no-go decision, the team extends the pilot "to gather more data." Pilots that get extended once tend to get extended repeatedly, consuming resources without producing a scaling decision. Set clear criteria: "The pilot will run for 8 weeks with 50 due diligence questionnaires. If accuracy exceeds 90% and processing time reduction exceeds 70%, we proceed to scaled deployment. If either metric falls short, we conduct a root cause analysis and make a continue/modify/stop decision within 2 weeks." That specificity forces decisions instead of indefinite experimentation.

## Cross-Cutting Tips for AI Problem Definition

These principles apply across every stage of the problem definition process.

Implementation tip on stakeholder alignment: Present the problem definition document to every stakeholder group before development begins and get their explicit agreement that the problem statement, success metrics, and scope accurately reflect their needs. Misalignment between what the project team thinks the problem is and what stakeholders actually need is the single most common source of AI project failure. This alignment meeting should produce a signed-off document, not a verbal agreement. When priorities shift mid-project (and they will), the signed document provides a reference point for scope discussions. Without it, every stakeholder remembers the problem definition differently, and the project tries to solve multiple unstated problems simultaneously.

Implementation tip on documenting what you chose not to do: Your use case analysis should include a section on alternatives considered and reasons for rejection. "We considered using a template-based system but rejected it because client questionnaire formats vary too widely for template matching. We considered hiring additional analysts but rejected it because the volume is seasonal and full-time hiring isn't cost-effective." This documentation serves two purposes. It demonstrates that the team evaluated alternatives, which satisfies governance requirements. And it creates institutional memory that prevents future teams from revisiting the same options without benefiting from the analysis already performed.

Implementation tip on the relationship between problem definition and ongoing monitoring: Your success metrics from the problem definition phase should become your post-deployment monitoring metrics. If you defined success as "95% accuracy rate on AI-generated responses," that same metric should be tracked continuously after deployment. If you defined success as "85% reduction in processing time," that measurement should appear on your operational dashboard. Disconnection between how you defined success and how you monitor the deployed system creates a gap where degradation goes undetected. Design your monitoring framework during problem definition, not after deployment.

Implementation tip on revisiting problem definitions as projects mature: Problem definitions should be treated as living documents during the early stages of a project. The pilot phase will reveal aspects of the problem that weren't visible during initial analysis. User feedback will surface needs that weren't captured in stakeholder interviews. Data quality assessment will reveal constraints that affect solution design. Schedule a problem definition review at the end of the pilot phase. Update the use case analysis form to reflect what you've learned. Adjust success metrics if the pilot revealed that initial targets were based on incomplete understanding. This review doesn't weaken the problem definition process. It strengthens it by incorporating real-world evidence.

## References and Frameworks

Your AI problem definition process should align with these established standards and guidelines:

- ISO/IEC 42001:2023, AI Management System (planning and context requirements)

- ISO/IEC 42005, AI Impact Assessment (pre-deployment analysis requirements)

- NIST AI Risk Management Framework, particularly the Map function

- ISO/IEC 5338, AI System Life Cycle Processes (requirements analysis phase)

- OECD AI Principles, particularly the robustness and accountability provisions

- EU AI Act, Annex IV documentation requirements for high-risk AI system purpose and intended use

- IEEE 2801-2022, Recommended Practice for Quality Management of Datasets

- PMI guidance on project scope definition adapted for AI initiatives

- COBIT 2019 for alignment of AI projects with business governance objectives

- ISO/IEC 25010, Systems and Software Quality Requirements (for defining quality-based success metrics)

If you treat AI problem definition as a formality, filling in a use case form with vague objectives and optimistic metrics to get budget approval, you set the project up for the most expensive kind of failure: the kind where everything works technically but nothing works practically. The model performs well. Nobody uses it. Or everyone uses it for the wrong thing. Or it solves a problem that wasn't the real bottleneck. And the organization concludes that "AI doesn't work for us" when the real issue was that the problem was never properly defined.

When you treat problem definition as the most consequential decision in the AI project lifecycle, with structured assessment, honest feasibility evaluation, specific success metrics, and documented alternatives, you create the foundation for everything that follows. The right problem definition makes technology selection obvious, makes data requirements clear, makes success measurable, and makes the go/no-go decision at each phase defensible. Every hour invested in rigorous problem definition saves multiples of that time in avoided rework, scope creep, and failed deployments.

The best AI projects don't start with the best technology. They start with the clearest understanding of the problem they need to solve.

What business problem in your organization are you currently considering for AI? Run it through the feasibility framework in this post before writing a single line of code.
