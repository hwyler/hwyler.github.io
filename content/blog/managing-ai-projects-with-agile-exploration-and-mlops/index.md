---
title: "Managing AI Projects With Agile, Exploration, and MLOps"
date: 2026-03-15
tags: 
  - "ai"
  - "ai-governance"
  - "ai-project-agile"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "iso-23894"
  - "mlops"
  - "technology"
---

## The AI Project Management Playbook

Most [AI projects](https://hernanhuwyler.wordpress.com/2026/03/15/practical-fixes-for-why-data-science-projects-fail/) fail to deliver real value, and the reason is almost never bad algorithms or insufficient data. The reason is that most teams manage AI projects like traditional software projects, and that approach ignores the fundamental differences that make AI projects uniquely challenging.

Software development is deterministic. A developer writes code, the code executes as written, and the output is predictable. AI development is experimental. A team trains a model, the model learns patterns from data, and whether it works well enough depends on [data quality](https://hernanhuwyler.wordpress.com/2026/03/15/data-and-tool-infrastructure-for-ai-projects/), feature interactions, model architecture, and production conditions that cannot be fully known during planning. Managing an experimental process with a deterministic management framework produces the friction that kills AI projects before they deliver.

Five characteristics make AI projects different from traditional software projects. Each one requires specific adaptations to standard project management practice, and each one creates predictable failure modes when ignored.

### Data Outweighs Code in Determining Outcomes

In software development, the code is the product. In AI development, the data is at least half the product, and often more. Preparing, cleaning, labeling, and validating data consumes between fifty and eighty percent of total project effort in most AI initiatives, depending on the maturity of the data infrastructure and the complexity of the use case.

A project plan that allocates twenty percent of the timeline to data preparation and eighty percent to model development will fail, because the ratio is inverted. The team will spend the first weeks discovering that the data has quality issues that block training. The mid-project weeks will be spent building and rebuilding data pipelines as new data sources are integrated. By the time the model development phase arrives, the timeline is exhausted, the model is rushed, and the data quality issues that were never resolved surface as production failures six months after release.

The deeper problem is conceptual. Software teams think in terms of features, user stories, and code reviews. AI teams must think in terms of datasets, labels, feature distributions, and training distributions versus production distributions. A feature in a software project has a clear definition and a stable interface. A feature in an AI project is a column in a dataset whose meaning, quality, and distribution can shift without warning. The same word means different things to a software engineer and a data scientist, and the project plan that does not make the distinction explicit will produce the wrong estimates, the wrong milestones, and the wrong success criteria.

[Data](https://hernanhuwyler.wordpress.com/2026/03/15/data-and-tool-infrastructure-for-ai-projects/) is not a one-time input to AI development. Data is a living system that requires ongoing stewardship. Production data drifts, new data sources emerge, labeling standards evolve, and regulatory requirements change what data can be used and how. The project plan that treats data preparation as a phase rather than a continuous practice will produce a model that ages badly.

The practical implication is that data preparation, data validation, data versioning, and data lineage documentation must receive budget, timeline, and staffing proportional to their actual cost and risk, not proportional to what software teams are comfortable budgeting.

### Uncertainty Is Structural, Not Incidental

In software development, uncertainty can be reduced through better requirements gathering. A skilled business analyst can clarify functional requirements, edge cases can be enumerated, and integration points can be specified. Uncertainty in software projects is incidental, meaning it can be reduced through better planning, better communication, and better requirements discipline.

In AI development, uncertainty persists regardless of how thorough the planning is. The central questions of an AI project can only be answered through experimentation, not through planning. Will the model achieve the accuracy target required for production use. Will the chosen features actually be predictive when tested against holdout data. Will the training data be representative of production conditions, or will production data look different in ways that destroy model performance. Will the model behave fairly across demographic groups, or will it produce disparate outcomes that create regulatory and reputational exposure.

These questions cannot be answered in a planning meeting. They can only be answered by training models, evaluating them against holdout data, testing them on edge cases, and measuring their behavior across subgroups. This is the irreducible uncertainty of AI development, and it is structural to the work, not a sign of poor planning.

A project plan that treats this uncertainty as a planning failure will produce teams that hide experimental results, avoid reporting bad news early, and rush to commit to timelines that the work cannot support. A project plan that treats this uncertainty as a structural feature of the work will produce teams that report experimental findings honestly, time-box exploration deliberately, and build decision points into the timeline that allow the project to pivot or stop based on evidence.

The practical tool for managing structural uncertainty is the time-boxed experiment with a go or no-go decision point. Instead of committing to a delivery date, the team commits to an experiment with a defined duration, a defined hypothesis, and a defined decision criteria. At the end of the experiment, the team has evidence to decide whether to proceed, pivot, or stop. This is a manageable commitment because the duration is bounded and the decision criteria are defined in advance. A fixed delivery date in an environment of irreducible uncertainty is a commitment the team may not be able to keep regardless of effort, and broken commitments erode trust faster than honest uncertainty.

> Time-boxed experiments with explicit go or no-go decision points are the only honest way to commit to delivery in an environment where model performance depends on factors beyond the team's control. Fixed delivery dates in experimental work are commitments to disappointment.

### Ethics and Governance Are Central, Not Peripheral

AI systems that make decisions about individuals can produce biased outcomes, violate privacy, or create harms that traditional software does not generate. A traditional software system that approves or rejects loan applications follows the rules written in the code. An AI system that approves or rejects loan applications learns patterns from historical data, and those patterns can encode historical bias, can produce disparate outcomes across demographic groups, and can be difficult to explain to the applicant, the regulator, or the court.

Fairness testing, bias auditing, explainability assessment, and regulatory compliance are not optional add-ons to AI development. They are core development activities that require time, expertise, and [governance integration](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/). A model that performs well on overall accuracy metrics but produces disparate outcomes across protected groups is a model that creates legal exposure, regulatory exposure, and reputational exposure, regardless of how impressive its technical performance is.

The [governance burden](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/) is not limited to the regulated industries. Any organization deploying AI systems that affect customers, employees, or the public is increasingly subject to regulatory expectations about fairness, transparency, and accountability. The European Union AI Act, the United States Executive Order on Safe, Secure, and Trustworthy AI, sector-specific guidance from financial regulators, and emerging international standards all signal that governance is moving from voluntary to mandatory.

The practical implication is that ethics and governance reviews must be integrated into the development workflow rather than treated as separate approval gates at the end of the project. A brief governance check in every sprint review, covering bias assessment status, compliance requirement review, residual risk update, and reproducibility evidence, converts governance from a periodic audit into a continuous control. This integration also creates the evidence trail that regulatory frameworks require, which means the project is producing audit-ready documentation as a byproduct of normal work rather than as a separate effort at the end.

> Governance treated as a final approval gate produces a model that ships with governance debt. Governance integrated into the development cadence produces a model that ships with governance evidence. The first model creates audit findings. The second model passes audits.

### The Team Is Inherently Interdisciplinary

AI projects require continuous collaboration between data scientists, machine learning engineers, software engineers, domain experts, compliance officers, and user experience designers. Each discipline speaks a different professional language, uses different tools, and optimizes for different objectives. A data scientist optimizes for model performance. A software engineer optimizes for system reliability. A compliance officer optimizes for regulatory defensibility. A domain expert optimizes for business relevance. A user experience designer optimizes for user trust and usability.

These objectives are not always aligned, and the tensions between them must be managed deliberately. A model that performs well on accuracy metrics but is too complex to deploy in production is a failure. A model that is easy to deploy but produces biased outcomes is a failure. A model that is fair and accurate but cannot be explained to the regulator is a failure. A model that passes all technical and governance reviews but does not solve the actual business problem is a failure.

Managing this interdisciplinary collaboration requires deliberate coordination that homogeneous software teams do not need. The project manager must be able to translate between disciplines, must understand enough of each discipline to identify when trade-offs are being made unconsciously, and must be able to facilitate the conversations that surface and resolve those trade-offs.

The most common failure mode I observe is the project manager who comes from a software background and treats the data science work as a special case of software development. The data science work is not a special case of software development. It is a different discipline with different rhythms, different uncertainty profiles, and different [success criteria](https://hernanhuwyler.wordpress.com/2026/03/15/field-guide-to-the-8-factors-that-determine-success-or-failure-of-ai-projects/). A project manager who does not understand this will impose software rhythms and software success criteria on work that does not fit them, and the team will either comply and fail or resist and be labeled as difficult.

The practical solution is rotating the Scrum Master position across team members, as described in the organizational fit section, and ensuring that the project manager has enough technical context to understand the work being managed. The project manager does not need to be able to train a model, but needs to be able to understand why a model training cycle takes longer than estimated, why a feature engineering approach did not work, and why a fairness metric is blocking release.

### Explainability Requirements Add Development Overhead

Complex models may require specialized algorithms to guarantee that results are explainable, unbiased, reproducible, and respectful of privacy. Documentation is more extensive than in software projects because it must capture not just what was built but how results were produced, with sufficient detail for auditors, regulators, and end users to understand and evaluate the model's behavior.

The documentation requirements for AI systems typically include model cards that describe the intended use, training data, performance metrics, and known limitations of the model. They include data sheets that describe the characteristics of the training data, including collection methods, labeling processes, and known biases. They include experiment logs that record the hyperparameters, training environment, and results of each experiment. They include lineage records that trace the data, code, and configuration used to produce the deployed model. They include fairness assessments that document the model's performance across demographic groups. They include explainability analyses that document how the model arrives at its decisions for representative cases.

This documentation is not optional. It is the evidence trail that allows auditors and regulators to evaluate the model, allows internal risk functions to assess model risk, allows incident response teams to investigate production failures, and allows future teams to understand and maintain the model after the original developers have moved on.

The practical implication is that documentation must be treated as a continuous activity integrated into daily work rather than a phase completed at the end of the project. Documentation written retrospectively after the project is complete is consistently less accurate and less detailed than documentation created as the work progresses. The difference is not effort. The difference is memory. A developer who documents a decision while making it captures the reasoning, the alternatives considered, and the trade-offs accepted. A developer who documents the same decision six months later captures the conclusion but loses the reasoning.

> Documentation produced as a byproduct of work is audit-ready. Documentation produced as a project deliverable is audit-prepared. The first survives contact with a regulator. The second survives contact with a skeptical auditor.

* * *

### Implementation Guidance: The Differences Briefing

At the start of every AI project, hold a differences briefing with the full team and key stakeholders. Walk through these five characteristics explicitly. Explain how each one affects timeline expectations, milestone definitions, and success criteria.

Stakeholders who understand that AI development is experimental rather than deterministic set more realistic expectations and respond more constructively when iterations are needed. Stakeholders who expect AI projects to follow software project patterns will interpret normal AI development iteration as project mismanagement, will pressure the team to commit to timelines the work cannot support, and will lose trust when those commitments are inevitably missed.

The briefing takes one hour. The expectation alignment it creates prevents months of friction. It is the single highest-return activity in the project initiation phase, and it is the one most often skipped because leadership wants to see the project start rather than spend an hour understanding why it is different from every other project they have run.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/abad3989-c049-422b-bd0a-4ae281b952ac.png?w=768)

## Understanding the Core Framework for Managing AI Projects

AI projects need a management model that handles both engineering discipline and scientific uncertainty at the same time. The framework I rely on has four layers: delivery rhythm, exploration capacity, production discipline, and organizational fit. When one of these layers is weak, the project usually slows down, fragments, or lands in production with avoidable weaknesses that surface during the first regulatory review or production incident.

The four layers are not independent practices. They form a balancing system. Too much exploration without discipline produces prototypes that never reach production. Too much discipline without exploration produces safe, compliant systems that solve the wrong problem. The art of AI project management is keeping all four in tension without letting any one collapse.

* * *

### Delivery Rhythm

Delivery rhythm is the operating cadence for turning AI ideas into tested, reviewable increments of value. In practice, that means short planning cycles, frequent stakeholder reviews, and clear decision points so the team keeps learning without losing momentum.

A good delivery rhythm prevents AI work from drifting into one of two failure modes. The first failure mode is endless research, where the team keeps refining the model and never commits to a release. The second failure mode is chaotic feature building, where the team ships quickly but loses track of what actually works.

AI work behaves differently from conventional software tasks. A sprint backlog can look clean on Monday and become invalid by Thursday because the data quality problem was larger than expected, the model failed to generalize, or the feature engineering approach produced a dead end. Standard two-week sprints with fixed velocity commitments create friction in this environment because they assume a level of predictability that experimental work does not offer.

The right approach is to use Agile principles for coordination and feedback without treating them as rigid promises that AI work will behave predictably every two weeks. Extend sprint duration to three or four weeks for projects with heavy modeling work. Reduce the number of committed tasks per sprint by thirty to forty percent compared to software norms. Use confidence-weighted estimation where each task carries both an effort estimate and a confidence level. High-confidence tasks like data pipeline construction and application programming interface development can be estimated conventionally. Low-confidence tasks like model architecture experiments and feature engineering exploration should be time-boxed rather than effort-estimated, with explicit go or no-go decision points at the end of each box.

A common failure pattern I see in regulated functions is treating the sprint review as a demo instead of a governance checkpoint. The right practice is to include a brief governance check in every sprint review covering bias assessment status, compliance requirement review, residual risk update, and reproducibility evidence. This converts the delivery rhythm into a continuous control surface rather than a periodic reporting event.

> Sprint cadence that assumes AI work behaves like software work is the single most common source of control deficiencies in regulated AI deployments. The cadence is the control, not the calendar.

* * *

### Exploration Capacity

Exploration capacity is the room you deliberately reserve for uncertain work such as data discovery, model experiments, prompt testing, feasibility studies, and architecture comparisons. AI projects need this capacity because the best solution is rarely obvious at the start, and some assumptions only fail once you actually look at the data.

A healthy framework protects this capacity instead of forcing every activity to look like routine software delivery. When organizations treat all time as feature delivery time, they kill the conditions under which useful AI innovation happens. Exploration gets squeezed because it does not carry the same stakeholder expectations as committed sprint work, and committed work always wins in a contest for time.

Two types of innovation matter in AI development. Iteration innovation improves existing approaches through progressive refinement and feedback, and Agile naturally supports this. Exploration innovation discovers entirely new approaches through experimentation, serendipity, and creative investigation, and Agile does not naturally support this. Both are necessary. A team that only iterates will eventually plateau. A team that only explores will never ship.

The practical system I recommend uses exploration time credits. After a team member completes a defined number of sprint tasks, they earn exploration time credit that they can save into an exploration account and spend when they choose. They share their exploration work with colleagues and receive recognition for useful applications. Allocating extra time credit when two or more people collaborate on exploration encourages knowledge sharing and cross-pollination of ideas. If exploration requires more than time, such as compute resources, new data, or data storage, time credits can be converted into tool credits that fund exploration infrastructure. This creates a self-regulating system where productive sprint work generates the currency for innovative exploration.

The system works because it makes exploration a reward for productivity rather than a competitor with it. The most common failure mode for exploration programs is that they feel like slack time to management and get cut during busy periods. When exploration is earned through sprint task completion, it has a visible connection to productive output that makes it more defensible during budget discussions. The system also creates a natural constraint: team members who do not complete their sprint commitments do not earn exploration time, which prevents exploration from becoming an excuse for avoiding committed work.

Start with a simple ratio, such as one exploration day earned per ten sprint tasks completed, and adjust based on results. Track what explorations produce over a six-month period. The connection between exploration and subsequent project improvements usually becomes visible enough to justify the investment.

| Exploration Practice | Failure Mode Without It |
| --- | --- |
| Protected exploration time | Innovation squeezed by delivery pressure |
| Exploration time credit system | Exploration seen as slack and cut under stress |
| Cross-team exploration collaboration | Knowledge silos across data, engineering, and product |
| Tool credits for compute and data | Exploration blocked by infrastructure gates |
| Leadership recognition of exploration outputs | Exploration perceived as low-status work |

* * *

### Production Discipline

Production discipline is the set of controls that make AI solutions dependable once they serve real users. It includes clear scope definition, testing, security checks, rollback planning, monitoring, human approval before release, and ongoing validation after release. The core idea is that AI should not move into production just because a prototype looks impressive in a stakeholder demo.

This is where many promising teams break. They can experiment well but cannot industrialize the result. The model performs well on holdout data, the demo wows the steering committee, and then the team discovers that nothing in the development process was designed for the realities of production. There is no model versioning, no reproducibility log, no drift monitoring, no rollback plan, no incident response runbook, and no clear ownership of the model after the data scientists rotate to the next project.

The framework that addresses production discipline is called Model Operations, or ModelOps for short. Model Operations is the set of practices that automate and govern the lifecycle of models in production, including deployment, monitoring, versioning, retraining, and decommissioning. Model Operations is not a project management framework on its own, but it is essential to any serious AI project that aims to survive contact with production systems and regulatory scrutiny.

The most important implementation guidance is to introduce Model Operations early enough that deployment, testing, and traceability shape development choices from the start. When Model Operations is added at the end of a project, the team typically discovers that the model artifacts are not reproducible, the data lineage is not documented, the training environment cannot be rebuilt, and the monitoring requirements are incompatible with the model architecture. These gaps create technical debt that compounds quickly and surfaces during the first audit.

Five production discipline controls consistently separate mature programs from immature ones. First, every model in production has a versioned, immutable record of the training data, hyperparameters, and code that produced it. Second, every model has defined performance thresholds and automated alerts when those thresholds are violated. Third, every model has a documented rollback procedure and a designated owner accountable for the model after release. Fourth, every model has a defined retraining cadence or a defined trigger for retraining based on drift detection. Fifth, every model has a documented decommission plan, because models age and the conditions under which they were trained eventually stop representing production reality.

> A model in production without drift monitoring, a defined owner, and a documented rollback procedure is a model waiting to fail. The failure will land on the operational risk register and the audit committee, not on the data science team that built it.

* * *

### Organizational Fit

Organizational fit asks whether the team structure, decision rights, skills, governance, and funding model match the kind of AI work being done. Successful AI delivery usually needs cross-functional teams, strong data and engineering support, and leadership that can [prioritize use cases and remove blockers.](https://hernanhuwyler.wordpress.com/2026/03/16/how-to-build-an-ai-roadmap-that-delivers-value-controls-risk-and-survives-change/) If the organization is not set up for it, even good models and good teams will struggle to scale.

The most common organizational failure I observe is the approval of more AI projects than the available talent can support. A data scientist or machine learning engineer is assigned to three or four concurrent projects because leadership approved a portfolio of use cases without checking whether the organization had the specialist capacity to deliver them. The result is daily task-switching between projects, which destroys the deep focus that experimental AI work requires. Context switching costs are higher for AI work than for software development because AI tasks require holding complex mental models of data distributions, feature interactions, and model behaviors in working memory. Each context switch flushes this mental model and requires rebuilding time.

Four approaches address this when multitasking cannot be avoided entirely. First, a portfolio-level Scrum that encompasses all projects in a single product backlog, enabling centralized prioritization across initiatives. Second, a pre-Scrum with a portfolio product backlog where product owners work with a portfolio owner to select priorities before sprint planning, ensuring that the highest-value work receives dedicated focus. Third, sequential sprint allocation where team members work on different projects in separate sprints rather than splitting attention within a single sprint, which preserves focus within each sprint while distributing expertise across projects over time. Fourth, a flow-based method such as Kanban that manages work-in-progress limits explicitly and accommodates the reality that some team members serve multiple projects without forcing artificial sprint commitments for each one.

The least damaging approach is sequential sprint allocation: dedicating each specialist to one project per sprint and rotating between projects across sprints. This preserves the deep focus that AI work requires while distributing expertise across the portfolio over time. The most damaging approach is daily task-switching between projects, where a data scientist works on Project A in the morning and Project B in the afternoon. If sequential allocation is not possible because multiple projects need the same specialist simultaneously, that is a signal that the organization has approved more projects than its staffing can support. The solution is project sequencing, not multitasking.

The second most common organizational failure is the Scrum Master knowledge gap. In Agile, the Scrum Master plays a servant leader role, removing impediments and facilitating ceremonies. This role is difficult to fill effectively if the Scrum Master is not sufficiently knowledgeable about AI development to guide the team through the project. A Scrum Master without data science experience may not understand technical terminology, may not know what a backtest is, and may not appreciate why a model training cycle cannot be estimated with the same confidence as a software development task.

The practical solution is rotating the Scrum Master position across team members. Different specialists take turns facilitating sprint ceremonies. This rotation distributes the facilitation burden, gives each team member perspective on project management challenges, ensures that the person facilitating has technical context for the work being discussed, and develops project management skills across the team rather than concentrating them in a single role. The rotation also creates a subtle governance benefit: every team member builds a working understanding of how the project is being managed, which improves the quality of risk reporting and the realism of estimates.

The third organizational consideration is framework selection. The major frameworks used in AI project management each have distinct strengths and weaknesses.

| Framework | Core Strength | Core Weakness | Best Fit |
| --- | --- | --- | --- |
| Cross-Industry Standard Process for Data Mining | Business-first structure, widely understood, strong on data assessment | Linear lifecycle, weak on governance, minimal production guidance | Early-stage analytics with clean data and low regulatory burden |
| Team Data Science Process | Structured roles, standardized artifacts, strong deployment guidance | Tooling assumptions tied to a specific cloud platform, rigid sprint structure, limited ethics integration | Mature teams already committed to a specific cloud ecosystem |
| Cognitive Project Management for AI | Built specifically for AI, governance-focused, vendor-neutral, regulatory-ready | Less widely adopted, smaller practitioner community | Regulated industries such as finance, healthcare, and government |
| Agile (Scrum and Kanban) | Flexibility, fast feedback, iterative development | Standard sprint commitments do not fit AI uncertainty, no native guidance on data or model validation | Iterative development phases after problem definition and data assessment are complete |
| Model Operations | Production-grade deployment, monitoring, versioning, automated retraining | Operational framework, not a project management framework | Production phase and ongoing lifecycle management |

The practical recommendation is to combine frameworks based on project phase and organizational context. Use Cross-Industry Standard Process for Data Mining or Cognitive Project Management for AI for early structure, covering problem definition, data assessment, and business alignment. Use Agile, adapted as described in the delivery rhythm section, for iterative development covering feature engineering, model training, validation, and refinement. Use Cognitive Project Management for AI again for governance, covering ethics review, compliance assessment, bias auditing, and stakeholder approval throughout the lifecycle. Use Model Operations for production, covering deployment automation, monitoring, versioning, drift detection, and model lifecycle management.

Do not adopt a method because it is fashionable. Choose the framework around the project's uncertainty, governance burden, and team maturity. Document the mapping between lifecycle phases and frameworks so that new team members understand why different practices apply at different stages. Review and adjust the framework combination after each major project, incorporating lessons learned about which practices worked and which created friction.

* * *

### How the Four Layers Work Together

The four layers form a balancing system. Delivery rhythm keeps work moving. Exploration capacity keeps learning alive. Production discipline keeps quality high. Organizational fit keeps the whole effort realistic. If one layer is missing, the project tends to drift toward a predictable failure mode.

A practical example: a team building a customer support assistant powered by a large language model might use a three-week sprint cadence, reserve two days per sprint for prompt engineering and retrieval strategy experiments, require security review and evaluation gate evidence before release, and run the project with product, data science, engineering, and operations jointly involved. That structure makes it easier to learn quickly and still ship something reliable.

The same example with weak organizational fit would look different. The data scientist is splitting time across three projects, the Scrum Master has no machine learning context, the prompt experiments are squeezed out by feature delivery pressure, and the security review happens after the model is already serving production traffic. The failure modes are structural, not technical.

The four layers are not a checklist to complete once. They are a control surface to maintain continuously. The moment any layer weakens, the other three lose effectiveness, and the project begins accumulating the technical and governance debt that shows up in the next audit or the next production incident.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/07/chatgpt-image-jul-6-2026-10_24_23-pm-edited.png)

## Adapting Agile for AI: What Changes and What Doesn't

Agile principles apply to AI projects. The twelve principles from the two thousand one Agile Manifesto, emphasizing iterative development, customer collaboration, and responding to change, are relevant and valuable for AI work. What does not work is applying Scrum or Kanban without modification, because the standard frameworks assume characteristics that AI projects do not have.

The core Agile loop remains the same. Prioritize, build, review, adapt. The difference is that in AI projects, the build phase produces experimental artifacts rather than deterministic features, the review phase must evaluate statistical metrics rather than pass or fail tests, and the adapt phase must respond to findings that may invalidate the original plan. The loop is the same. The work inside the loop is different.

Three specific adaptations make Agile work for AI. Each one addresses a predictable failure mode that appears when standard Agile frameworks are applied to experimental work.

* * *

### Sprints Must Accommodate AI Iteration Patterns

AI projects require more iterations than software projects, and the iterations behave differently. A model training cycle may span an entire sprint, especially for deep learning models on large datasets. Feature engineering experiments may produce dead ends that consume sprint capacity without producing deliverable output. Hyperparameter tuning may run for days or weeks without producing a result that improves on the baseline. These are not signs of project failure. They are the normal texture of experimental work.

The number of tasks during each sprint needs to be smaller to give sufficient time to complete and test them properly. Because of the added complexity in AI projects, including large data inputs and outputs, model parameters that require careful analysis, and version control for data as well as code, the flow of work may need to be slower than in traditional software sprints.

Two adjustments make the biggest difference. First, extend sprint duration from two weeks to three or four weeks for AI projects with heavy modeling work. A two-week sprint assumes that work can be completed, tested, and reviewed within the sprint boundary. A model training cycle that takes ten days cannot be completed, tested, and reviewed within a ten-day sprint. The team either pads the estimate (which creates waste) or commits to a timeline the work cannot support (which creates broken commitments). Extending the sprint duration to three or four weeks accommodates model training cycles and gives the team time to respond to findings before the sprint ends.

Second, build explicit experimentation tasks into the backlog that allow for learning without requiring a deliverable output. These tasks are called research spikes or experimentation stories, and they represent a deliberate investment in learning rather than a failure to deliver. A research spike has a defined hypothesis, a defined time box, and a defined decision criteria. At the end of the spike, the team has evidence to decide whether to proceed, pivot, or stop. This is a valid sprint outcome even though it does not produce a shippable feature.

The cultural shift required is significant. In traditional Agile, the sprint goal is a working increment of software. In adapted Agile for AI, the sprint goal can be a working increment of software, a validated hypothesis, a documented experimental finding, or a production-ready model component. The definition of "working increment" expands to include experimental artifacts that inform the next decision.

Accept that some sprint tasks will conclude with "this approach does not work", which is a valid and valuable outcome in AI development even though it does not produce a shippable feature. A team that documents a failed approach honestly has produced something valuable: the knowledge that this approach should not be tried again, the data that shows why it did not work, and the time saved by not pursuing it further. A team that hides failed experiments to preserve the appearance of progress has produced something dangerous: a false sense of momentum that will collapse when the evidence is eventually examined.

> The sprint goal is not to produce working software. The sprint goal is to produce evidence for the next decision. Sometimes the evidence is a working feature. Sometimes the evidence is a documented finding. Both are valid. Only the evidence that supports good decisions matters.

* * *

### The Definition of "Done" Must Reflect AI Complexity

In software development, done typically means the feature works as specified, tests pass, and code is reviewed. In AI development, done for a model training task must include a much longer list of completion criteria.

The model must meet performance thresholds on holdout data, not just on training data. The distinction matters because models that perform well on training data and poorly on holdout data have overfit, which means they have memorized the training examples rather than learned the underlying patterns. A model that performs well on training data and poorly on holdout data will fail in production, because production data will look more like holdout data than like training data.

Fairness metrics must have been evaluated. The model must be tested for disparate performance across demographic groups, and the results must be documented. A model that performs well on overall accuracy but poorly on a protected subgroup is not done, regardless of how impressive the overall accuracy is.

Explainability analysis must have been performed. The model's decisions must be interpretable to the degree required by the use case, the regulator, and the end user. A model that produces accurate predictions but cannot explain why it made a specific prediction is not done for any use case that affects individuals.

The experiment must be documented with sufficient detail for reproducibility. The model version, data version, hyperparameters, training environment, and evaluation methodology must all be recorded. A model that cannot be reproduced is a model that cannot be audited, cannot be maintained, and cannot be trusted.

The results must have been reviewed by a domain expert for business reasonableness. A model that passes all technical metrics but produces predictions that a domain expert considers unreasonable is a model that will fail when it encounters real-world complexity that the training data did not represent.

Create an AI-specific definition of done that includes these requirements as completion criteria for every model-related task. The definition of done is not documentation to write after the work is complete. It is a checklist to apply before the work is marked complete. The difference matters because work that is marked complete before meeting the definition of done creates technical debt that compounds over time, while work that is not marked complete until the definition is met creates a culture of quality that compounds over time.

The practical implementation is a definition of done document that is reviewed and updated at the start of every sprint. The document should list the completion criteria for each type of task: model training, feature engineering, data pipeline, deployment, monitoring setup, and documentation. Each criterion should be specific enough to be verified by inspection. "Model performance is acceptable" is not a verifiable criterion. "Model achieves at least ninety percent precision and eighty-five percent recall on the approved holdout dataset" is a verifiable criterion.

* * *

### Sprint Planning Must Account for the Dependency Between Experimentation and Execution

Standard sprint planning assumes that tasks can be estimated with reasonable accuracy. A software team can estimate a feature implementation with reasonable confidence because the work is deterministic. The developer knows the inputs, the outputs, the integration points, and the edge cases. The estimate may be wrong, but the uncertainty is bounded.

AI tasks frequently cannot be estimated with reasonable accuracy. Model training time depends on data volume, model complexity, and convergence behavior. Feature engineering effectiveness is unknown until experimented with. Hyperparameter tuning duration depends on the search space and the optimization landscape. Data quality issues may surface that invalidate weeks of planning. These uncertainties make accurate sprint estimation difficult, and pretending otherwise produces commitments that the work cannot support.

The adaptation that addresses this is confidence-weighted estimation. Each task is assigned both an effort estimate and a confidence level. High-confidence tasks like data pipeline construction, application programming interface development, and [infrastructure setup](https://hernanhuwyler.wordpress.com/2026/03/15/data-and-tool-infrastructure-for-ai-projects/) can be estimated conventionally. Low-confidence tasks like model architecture experiments, feature engineering exploration, and hyperparameter tuning should be time-boxed rather than effort-estimated.

A time-boxed commitment sounds like this: "We will spend two days exploring alternative feature engineering approaches. At the end of two days, we will evaluate results and decide next steps." This is a commitment the team can keep regardless of what the exploration reveals. A conventional estimate sounds like this: "Feature engineering will take five days." This is a commitment the team may not be able to keep because the effectiveness of the approach is unknown until tried.

The time-boxed commitment has another advantage. It builds decision points into the sprint rather than deferring decisions to the end. A team that time-boxes exploration and evaluates results at the end of each time box can pivot quickly when evidence suggests the current approach is not working. A team that commits to effort estimates cannot pivot as easily because the commitment is to a duration, not to a decision.

Sprint planning should also distinguish between tasks that produce deliverables and tasks that produce evidence. Deliverable tasks are the familiar software tasks that produce working code, tested features, and deployed systems. Evidence tasks are the AI-specific tasks that produce validated hypotheses, experimental findings, fairness assessments, and reproducibility documentation. Both types of tasks belong in the sprint, and both should be estimated using the appropriate method.

A useful AI sprint can look like this:

In sprint planning, the team picks one model or data problem, defines the hypothesis, and sets acceptance criteria. During the sprint, the team builds the experiment, runs evaluation, documents findings, and prepares integration needs early. At the end of the sprint, the team demos results, reviews metrics, and decides whether to improve, pivot, or move toward deployment.

The metrics reviewed at the end of the sprint should span three layers. Analytical metrics include accuracy, precision, recall, lift, or other model performance measures. Tactical metrics include velocity, cycle time, sprint predictability, and delivery of sprint goals. Strategic metrics include business outcomes such as reduced cost, faster decisions, or better customer conversion. A team that reviews only analytical metrics will optimize for model performance at the expense of business value. A team that reviews only business metrics will miss technical problems that will surface later. A team that reviews all three layers will make informed decisions about what to build next and why.

* * *

### Implementation Guidance: Choosing Between Scrum and Kanban

Consider moving from Scrum to Kanban for AI projects with high uncertainty. Kanban's continuous flow model, where work items move through stages at their own pace without being constrained to fixed sprint commitments, accommodates AI's variable task durations more naturally than Scrum's fixed sprint structure.

When a model training run takes three days or three weeks depending on convergence behavior, fitting that task into a two-week sprint creates either padding waste or commitment violations. Kanban's focus on managing work-in-progress limits and visualizing flow rather than committing to fixed delivery within fixed time periods reduces the friction that arises from forcing unpredictable AI work into predictable sprint structures.

Teams that struggle with sprint commitments for AI tasks often find immediate relief from switching to Kanban, which maintains Agile's iterative principles without Scrum's fixed-cadence constraints. The team still plans, reviews, and adapts. The team just does not commit to delivering a fixed set of tasks within a fixed time period. Work enters the flow, moves through stages, and ships when ready.

The trade-off is psychological. Scrum provides a rhythm that some teams find motivating. The sprint boundary creates a forcing function for completing work, reviewing progress, and planning the next increment. Kanban's continuous flow can feel less structured to teams that thrive on cadence. The right answer depends on the team's working style, the project's uncertainty profile, and the organization's reporting requirements.

A practical hybrid approach uses Kanban for the experimental work and Scrum for the engineering work. The data science work flows through a Kanban board because its duration is unpredictable. The software engineering work runs in sprints because its duration is more predictable. The two streams synchronize at regular intervals to ensure that experimental findings are translated into production code at a sustainable pace.

The right Agile adaptation is the one that reduces friction between the management framework and the nature of the work. When the framework fights the work, the work loses. When the framework supports the work, the work ships.

## Encouraging Exploration: The Innovation Practice Most AI Teams Skip

AI development benefits from two types of innovation. Iteration innovation, which Agile emphasizes, improves existing approaches through progressive refinement and feedback. Exploration innovation, which Agile doesn't naturally support, discovers entirely new approaches through experimentation, serendipity, and creative investigation.

Exploration can strengthen team competency, motivation, and rate of innovation. Team members should be able to dedicate time to explorations without feeling the pressure to show semiweekly progress. Exploration can be conducted with external partners such as academic researchers, other companies, or with internal partners from other divisions. Though ideally exploration should yield tangible results for the organization, the knowledge gained during exploration can be beneficial on its own.

The sprint time box should account for allocated exploratory time or even allow some team members to skip part of the sprint to dedicate time to exploration. Without this allocation, exploration competes with committed sprint work and invariably loses because committed work has stakeholder expectations and deadlines while exploration doesn't.

One practical system for encouraging exploration uses exploration time credits. After a team member completes a defined number of sprint tasks, they earn exploration time credit that they can save into an exploration account and spend when they choose. They share their exploration work with colleagues and receive recognition for useful applications.

Teams can also explore together. Allocating extra time credit when two or more people collaborate on exploration encourages knowledge sharing and cross-pollination of ideas. If two members collaborate on an exploration project and each uses five credits, they can each receive an additional credit to reward the collaboration.

If exploration requires more than time, such as compute resources, new data, or data storage, time credits can be converted into tool credits that fund exploration infrastructure. This creates a self-regulating system where productive sprint work generates the currency for innovative exploration.

The exploration time credit system works because it makes exploration a reward for productivity rather than a competitor with it. The most common failure mode for exploration programs is that they feel like slack time to management and get cut during busy periods. When exploration is earned through sprint task completion, it has a visible connection to productive output that makes it more defensible during budget discussions. The system also creates a natural constraint: team members who don't complete their sprint commitments don't earn exploration time, which prevents exploration from becoming an excuse for avoiding committed work. Start with a simple ratio (one exploration day earned per ten sprint tasks completed) and adjust based on results. Track what explorations produce over a six-month period. The connection between exploration and subsequent project improvements usually becomes visible enough to justify the investment.

## Managing the Scrum Master Challenge and Skill Scarcity

Two practical challenges affect how agile roles function in AI projects, and both are widespread enough that most organizations building AI systems will encounter them. The first is the knowledge gap between what a traditional process facilitator understands and what AI development actually requires. The second is the chronic scarcity of specialized AI talent and the organizational habit of spreading that talent across too many projects at once. Neither challenge has a perfect solution, but both have practical responses that significantly reduce the damage they cause.

These are not theoretical concerns. They are the operational realities that determine whether an AI team's agile practice creates value or creates friction. A team with excellent data scientists and a poorly adapted facilitation role will waste hours in planning sessions that do not reflect the actual work. A team whose best specialists are split across four projects simultaneously will produce mediocre results on all four while appearing busy on each one. Getting these two challenges right does not guarantee project success, but getting them wrong reliably produces project dysfunction.

* * *

### The Scrum Master Knowledge Gap

In agile practice, the process facilitator serves as a servant leader. They remove obstacles, facilitate planning and review sessions, protect the team from external disruptions, and help the group maintain a productive working rhythm. This role does not require the facilitator to do the technical work themselves, but it does require them to understand the work well enough to recognize when the process is serving the team and when it is fighting them.

For software development teams, this understanding is relatively easy to acquire. The work follows patterns that a non-engineer can learn to recognize: building features, fixing defects, writing tests, refactoring code, deploying releases. The vocabulary is stable and well documented. The estimation practices are mature. A facilitator who invests a few months in learning the team's domain can become effective at guiding planning, spotting blockers, and facilitating productive retrospectives.

AI development presents a fundamentally different challenge. The work involves concepts and practices that have no direct equivalents in software development, and a facilitator without data science experience may struggle to understand what the team is actually doing, why tasks take as long as they do, or why a sprint plan that looked reasonable at the start of the week no longer makes sense by midweek.

Consider the practical implications. A facilitator who does not understand what a backtest is cannot evaluate whether the team's validation approach is adequate. A facilitator who does not appreciate the difference between training accuracy and generalization performance cannot distinguish between a model that is genuinely performing well and one that has memorized its training data. A facilitator who does not understand why feature engineering is experimental cannot facilitate a useful conversation about why a task that was estimated at two days consumed an entire week without producing a deliverable artifact. A facilitator who has never worked with probabilistic systems may instinctively apply the certainty expectations of software development, treating every missed estimate as a planning failure rather than recognizing it as the normal outcome of experimental work.

This knowledge gap distorts every ceremony in the agile process. Sprint planning sessions produce commitments that do not reflect the actual uncertainty of the work because the facilitator does not recognize which tasks are predictable and which are experimental. Daily coordination meetings become status reporting exercises rather than problem-solving conversations because the facilitator cannot ask the probing questions that would surface emerging issues. Sprint reviews focus on whether tasks were completed rather than on what was learned, because the facilitator does not have the context to evaluate the significance of experimental results. Retrospectives miss the most important process improvements because the facilitator cannot distinguish between friction caused by the team's practices and friction caused by the inherent nature of AI work.

The conventional response is to hire or train a facilitator who has data science knowledge. This is ideal when it is achievable, but in practice it is rarely available. People with deep data science expertise and strong process facilitation skills are exceptionally rare, and those who have both are usually more valuable and more interested in doing technical work than in facilitating it. Training a traditional facilitator in data science takes significant time and investment, and even after training, they may lack the experiential knowledge that comes from having actually built and evaluated models.

A more practical and often more effective response is to rotate the facilitation role among team members on a sprint-by-sprint basis. Each sprint, a different member of the team takes responsibility for facilitating planning, daily coordination, review, and retrospective sessions. The rotation ensures that the person guiding the conversation always has technical context for the work being discussed. A data scientist facilitating a sprint where the primary work involves feature engineering understands the uncertainty involved and can set realistic expectations. A machine learning engineer facilitating a sprint focused on deployment pipeline construction understands the technical dependencies and can spot potential blockers that a non-technical facilitator would miss.

Rotation produces several additional benefits beyond solving the knowledge gap. It distributes the facilitation burden across the team rather than concentrating it in a single person, which prevents the burnout that often affects dedicated facilitators on high-intensity AI projects. It gives every team member direct experience with the coordination and communication challenges of project management, which builds empathy for the management perspective and produces a team that is more self-aware about its own process. It develops project management skills across the team rather than leaving them concentrated in one role, which makes the team more resilient to personnel changes. And it prevents the dynamic where the team views the facilitator as an outsider who imposes process requirements without understanding the work, because every team member has experienced the facilitation role and understands why certain process disciplines exist.

Rotation is not without costs. Not every team member will be equally comfortable or skilled at facilitation. Some may struggle with time management during meetings or with guiding difficult conversations about missed targets or interpersonal friction. The quality of facilitation will vary from sprint to sprint as different people bring different strengths to the role. These are real costs, but they are generally smaller than the cost of having a permanent facilitator who does not understand the work well enough to guide it effectively.

To make rotation work well, establish a lightweight facilitation guide that documents the purpose, agenda, and expected outcomes of each ceremony. This gives each rotating facilitator a clear structure to follow, reducing the variability in facilitation quality. Include specific prompts that are relevant to AI work: "Which tasks this sprint have uncertain outcomes?" during planning, "Did any experiment produce unexpected results?" during daily coordination, and "What did we learn that changes our approach going forward?" during retrospectives. These prompts keep the conversation focused on the aspects of the work that matter most for AI development, regardless of who is facilitating.

For organizations that prefer to maintain a dedicated facilitator rather than rotating the role, the minimum viable adaptation is to pair the facilitator with a technical liaison from the team. The liaison attends planning and review sessions alongside the facilitator and provides real-time translation between the team's technical work and the facilitator's process perspective. This pairing does not fully resolve the knowledge gap, but it prevents the worst manifestations: planning sessions where the facilitator commits the team to work they cannot estimate, and review sessions where the facilitator evaluates outcomes using software development criteria that do not apply to AI work.

* * *

### Skill Scarcity and the Multitasking Trap

The second challenge is more pervasive and more damaging. In most organizations building AI systems, the number of experienced data scientists, machine learning engineers, and specialized AI practitioners is smaller than the number of projects that need their expertise. This gap between demand and supply is not a temporary hiring problem that will resolve itself as the talent market matures. The skills required for effective AI development, including statistical reasoning, experimental design, domain modeling, and the judgment to know when a model is ready for production, take years to develop and are genuinely scarce. Organizations that wait for the talent shortage to resolve itself will wait a very long time.

The default organizational response to this scarcity is to spread specialized talent across multiple projects. A senior data scientist who is the only person in the organization with experience in a particular type of modeling gets assigned to three or four projects that each need that expertise. The reasoning is understandable: if the specialist works on one project at a time, the other three are blocked. Spreading them across all four projects means every project gets at least some attention.

This reasoning is intuitive and wrong. Multitasking does not distribute expertise. It dilutes it. And for AI work specifically, the dilution is far more severe than for conventional software development.

The reason is cognitive. AI work requires holding complex mental models in working memory. When a data scientist is deep in a feature engineering investigation, they are maintaining a detailed understanding of the data distributions, the relationships between variables, the known quality issues, the domain constraints, the model's current behavior, and the hypotheses they are testing. This mental model takes significant time to build, often an hour or more of focused reorientation when returning to a project after time away. Every context switch between projects flushes this mental model and forces the specialist to rebuild it from scratch.

In software development, context-switching is also costly, but the rebuilding time is shorter because software work involves more stable structures. A software engineer returning to a codebase after a few days away can review recent commits, read the relevant code, and reorient themselves relatively quickly because the code is a complete, inspectable record of the system's state. A data scientist returning to a modeling project after time on another assignment has to reconstruct not just the state of the code and data, but the conceptual understanding of why particular choices were made, what alternatives were considered and rejected, and what the current experimental results imply about next steps. This conceptual reconstruction takes longer and is more error-prone, because much of the relevant context exists in the scientist's memory rather than in any artifact.

Research on cognitive switching costs supports what practitioners observe: every context switch imposes a fixed overhead that does not shrink with practice or skill. A specialist working on two projects does not produce the output of one person working full-time on each project. They produce something closer to sixty to seventy percent of full-time output per project, because the switching overhead consumes the rest. A specialist working on four projects may produce less total value than if they had been assigned to two projects sequentially, because the switching overhead on four projects can consume more than half of their productive capacity.

The organizational cost is even worse than the individual productivity loss suggests. When specialists are spread thin, every project moves slowly. Slow projects accumulate coordination overhead, stakeholder management effort, and carrying costs that would not exist if the project had been completed quickly with dedicated resources. A project that takes six months with a part-time specialist may produce less total value than the same project completed in three months with a dedicated specialist and then followed by the next project for another three months. The sequential approach delivers the same two outcomes in the same total elapsed time but with higher quality on each one, because the specialist could focus deeply on each problem without the cognitive overhead of switching.

Four practical approaches address multitasking when it cannot be avoided entirely, ordered from most effective to least effective.

The strongest approach is sequential sprint allocation. Each specialist is dedicated to one project per sprint or per planning cycle, and they rotate between projects across cycles. During any given sprint, the specialist focuses entirely on one project, building and maintaining the deep mental model that produces their best work. At the sprint boundary, they complete their current work, document their progress and open questions thoroughly, and shift to the next project. This approach preserves the deep focus that AI work requires while distributing expertise across the portfolio over time. The documentation requirement at each transition is critical, because it captures the mental model that would otherwise be lost during the switch, making the re-entry faster and less error-prone when the specialist returns.

The second approach is portfolio-level coordination using a single prioritized backlog that spans all active projects. Instead of each project maintaining its own backlog and competing for specialist time, all AI work across the organization flows into one prioritized list. A portfolio-level coordinator works with individual project owners to select the highest-value work for each planning cycle, and specialists are assigned to that work based on priority rather than project allegiance. This approach prevents the common situation where a low-priority project consumes specialist time that would produce more value if applied to a higher-priority initiative. It requires a governance structure that can make cross-project prioritization decisions and project owners who are willing to accept that their project may not receive specialist attention during every cycle.

The third approach is a pre-planning alignment session where project owners meet with a portfolio coordinator before sprint planning to agree on how specialist time will be allocated across projects for the coming cycle. This is a lighter-weight version of the portfolio backlog approach that does not require a full reorganization of project management structures. It ensures that allocation decisions are made consciously and based on relative priority rather than defaulting to the most vocal project owner or the most recent escalation.

The fourth approach, appropriate when the other three are not organizationally feasible, is to shift from a fixed-cadence sprint model to a continuous flow model for the projects that share specialists. Continuous flow manages work-in-progress limits explicitly, which makes it visible when a specialist is overloaded and forces the organization to make explicit choices about which work to advance and which to pause. In a sprint-based model, a specialist assigned to four projects may nominally commit to work on all four during each sprint, creating an illusion of progress on each one while actually producing fragmented, low-quality contributions to all of them. In a continuous flow model, work-in-progress limits make this overcommitment visible and unsustainable, forcing a conversation about realistic allocation that the sprint model allows the organization to avoid.

* * *

### Recognizing When the Problem Is Not Multitasking but Overcommitment

If sequential allocation is not possible because multiple projects genuinely need the same specialist at the same time, the problem is not a scheduling challenge. It is a portfolio management failure. The organization has approved more projects than its staffing can support, and no scheduling technique can fix that. Adding more projects to an already overloaded specialist does not increase total output. It decreases it, because the switching overhead grows with each additional project while the productive capacity remains fixed.

The honest response in this situation is project sequencing: deciding which projects proceed now with dedicated specialist attention and which projects wait until capacity is available. This decision is uncomfortable because it requires telling some project sponsors that their initiative is not the current priority. But it is far less costly than the alternative, which is allowing all projects to proceed simultaneously at reduced speed and quality, consuming the specialist's capacity on switching overhead rather than on productive work, and eventually delivering mediocre results on all of them.

A useful diagnostic question for any organization struggling with AI talent allocation: how many projects currently have a claim on your most specialized AI practitioner's time? If the answer is more than two, ask a harder question. What is the total value those projects would deliver if completed sequentially with dedicated focus, compared to the total value they are likely to deliver running in parallel with fragmented attention? In most cases, the sequential approach delivers more total value in the same elapsed time, with each individual project producing a better result because it received the deep attention the work demands.

The role of leadership in this challenge is not to find cleverer ways to split specialist time across more projects. It is to make clear, defensible priority decisions about which projects receive specialist attention and in what order, and to communicate those decisions transparently to stakeholders. This is a governance function, not a scheduling function, and it requires the same kind of rigorous prioritization discipline that organizations apply to capital allocation decisions. AI specialist time is at least as scarce and at least as valuable as capital. It deserves the same quality of allocation decision-making.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/futuristic-interior-space.png?w=1024)

## Choosing the Right Framework: A Practical Decision Guide

No single project management framework covers all AI project needs. The most successful teams use hybrid approaches that combine strengths from multiple frameworks based on project characteristics, regulatory context, and team maturity. This section provides a practical guide to the five frameworks that appear most often in AI project management, along with a decision logic for combining them.

The five frameworks are not competitors. They address different phases of the AI lifecycle and different aspects of the work. A team that treats framework selection as a binary choice between options misses the opportunity to build a management system that is calibrated to the actual work.

### The Five Frameworks

The Cross-Industry Standard Process for Data Mining, known as CRISP-DM, provides a business-first, data-aware structure that has been widely used since the late nineteen nineties. It organizes work into six phases: business understanding, data understanding, data preparation, modeling, evaluation, and deployment. The framework is well documented, broadly understood across industries, and effective for structured analytics projects with relatively clean data.

Its weaknesses for modern AI work are significant. The framework is linear in its original formulation, which predates the iterative development practices that dominate contemporary AI development. It provides limited guidance on ethics, fairness, and governance, which are central concerns for AI systems that affect individuals. It offers minimal direction for production operations, monitoring, and lifecycle management after deployment. A team that relies on CRISP-DM alone will produce a model but will struggle to industrialize it.

The Team Data Science Process, known as TDSP, is Microsoft's structured approach to data science project management. It provides clear team roles, standardized artifacts, and strong deployment guidance. TDSP incorporates an agile-lite iteration model within a defined lifecycle, which makes it more compatible with modern development practices than CRISP-DM.

Its weaknesses are related to its origins. The framework assumes tooling and infrastructure tied to the Microsoft Azure ecosystem, which creates friction for organizations that use other cloud platforms or on-premises infrastructure. Its sprint structure is more rigid than what experimental AI work requires, and its integration of ethics and governance considerations is limited compared to frameworks built specifically for AI.

Cognitive Project Management for AI, known as CPMAI, is built specifically for AI projects. It is iterative, governance-focused, vendor-neutral, and deployment-ready. The framework emphasizes ethical AI practices and regulatory compliance throughout the lifecycle, which makes it particularly appropriate for regulated industries such as financial services, healthcare, and government. CPMAI was developed by the Cognitive Computing Consortium and is maintained as an industry-specific methodology.

Its weakness is adoption. CPMAI is less widely adopted than CRISP-DM or standard Agile, which means fewer practitioners have direct experience with it and fewer training resources are available. Organizations that adopt CPMAI may need to invest more in internal training and may struggle to find experienced practitioners in the hiring market.

Agile, in its Scrum and Kanban variants, provides the flexibility, [quick feedback loops,](https://hernanhuwyler.wordpress.com/2026/03/15/ai-deployment-governance-for-feedback-loops-and-mlops/) and iterative development that AI's experimental nature demands. Agile principles support the adaptive planning and continuous improvement that AI work requires, and the ceremonies and artifacts provide coordination structures that help interdisciplinary teams stay aligned.

Its weakness for AI is that standard implementations assume characteristics that AI projects do not have. Standard sprint commitments do not accommodate AI's unpredictable task durations. The standard definition of done does not capture the reproducibility, fairness, and explainability requirements of model development. Agile alone provides no guidance on data management, model validation, or production operations, which means a team that uses only Agile will produce working software but may not produce a working model lifecycle.

Model Operations, known as ModelOps, provides the production infrastructure for model deployment, monitoring, versioning, and automated retraining. It is the discipline that makes AI systems dependable once they serve real users. ModelOps includes the practices and tools for continuous integration and continuous deployment of models, drift detection, performance monitoring, and incident response.

Its weakness as a project management framework is that it is an operational discipline rather than a project management framework. It does not address project planning, stakeholder management, or team coordination. A team that uses ModelOps without a complementary project management framework will have strong production controls but weak delivery discipline.

### Comparing the Five Frameworks

| Framework | Core Strength | Core Weakness | Best Phase | Regulatory Readiness |
| --- | --- | --- | --- | --- |
| CRISP-DM | Business-first structure, widely understood, strong on data assessment | Linear lifecycle, limited governance, weak production guidance | Early structure and data assessment | Low |
| TDSP | Clear roles, standardized artifacts, strong deployment guidance | Cloud-specific tooling assumptions, rigid sprint structure, limited ethics | Full lifecycle in cloud-native teams | Medium |
| CPMAI | Built for AI, governance-focused, vendor-neutral, regulatory-ready | Lower adoption, fewer experienced practitioners | Full lifecycle in regulated industries | High |
| Agile (Scrum and Kanban) | Flexibility, fast feedback, iterative development | Standard sprint assumptions do not fit AI uncertainty, no native governance | Iterative development and refinement | Low without adaptation |
| ModelOps | Production-grade deployment, monitoring, versioning, automated retraining | Operational discipline, not a project management framework | Production and ongoing lifecycle | High for operational controls |

### The Practical Recommendation: Combine Frameworks by Phase

Combine frameworks based on your project phase and organizational context. The following allocation works well for most regulated AI projects.

Use CRISP-DM or CPMAI for early structure, covering problem definition, data assessment, and business alignment. CRISP-DM works well when the project is more analytics-oriented and the regulatory burden is lower. CPMAI works well when the project will be deployed in a regulated environment and governance must be embedded from the start.

Use Agile, adapted as described in the Agile adaptation section, for iterative development. This covers feature engineering, model training, validation, and refinement. The adaptation extends sprint duration, reduces committed task count, redefines done to include AI-specific criteria, and uses confidence-weighted estimation for experimental tasks.

Use CPMAI for governance throughout the lifecycle. This covers ethics review, compliance assessment, bias auditing, and stakeholder approval. Governance integrated into the development cadence produces audit-ready evidence as a byproduct of normal work rather than as a separate documentation effort at the end of the project.

Use ModelOps for production. This covers deployment automation, monitoring, versioning, drift detection, and model lifecycle management. ModelOps is what makes the model dependable after release, and it is the discipline that connects development work to ongoing operational reality.

### Mapping Frameworks to Your Project

Start by mapping your project lifecycle phases to the frameworks that best serve each phase. A typical mapping for a regulated AI project looks like this:

| Lifecycle Phase | Primary Framework | Supporting Framework |
| --- | --- | --- |
| Business understanding and problem definition | CPMAI or CRISP-DM | Agile for stakeholder ceremonies |
| Data assessment and preparation | CRISP-DM or CPMAI | Agile for data exploration sprints |
| Model development and training | Adapted Agile | CPMAI for governance checkpoints |
| Validation and fairness assessment | CPMAI | Adapted Agile for iteration |
| Deployment | ModelOps | CPMAI for approval gates |
| Monitoring and lifecycle management | ModelOps | Agile for incident response cadence |

Document this mapping so that new team members understand why different practices apply at different stages. The documentation should explain not just which framework is used in which phase, but why that framework was chosen and what trade-offs were accepted. A team that inherits a framework mapping without the reasoning behind it will not know how to adapt the mapping when conditions change.

### Customization Principles

Do not adopt any framework blindly. Customize it for your specific project, team, and organizational context. The teams that achieve the best results with AI project management use hybrid approaches where each framework contributes its strongest elements, and they adapt each framework to the constraints of their environment.

Three principles guide effective customization.

First, match the framework to the uncertainty profile. Projects with high uncertainty, where the feasibility of the approach is unknown at the start, benefit from more exploratory frameworks like CPMAI and from Agile variants that accommodate variable task durations. Projects with lower uncertainty, where the approach is well understood and the work is primarily execution, can use more structured frameworks like TDSP with less adaptation.

Second, match the framework to the governance burden. Projects in regulated environments require frameworks with strong governance integration. CPMAI is built for this context. Projects in less regulated environments can use lighter governance integration, though the trend across jurisdictions is toward stronger governance requirements for all AI systems that affect individuals.

Third, match the framework to the team maturity. Teams new to AI work benefit from more structured frameworks with clearer guidance, such as TDSP or CPMAI with explicit training. Teams experienced in AI work can operate effectively with lighter frameworks, adapting Agile and ModelOps to their context without the scaffolding that newer teams need.

Review and adjust the framework combination after each major project, incorporating lessons learned about which practices worked and which created friction. The framework mapping is not a one-time decision. It is a living document that should evolve as the organization builds experience and as the regulatory environment changes.

The right framework combination is the one that reduces friction between the management system and the nature of the work. When the framework fights the work, the team loses. When the framework supports the work, the team ships. The goal is not framework purity. The goal is framework fit.

## AI Project Management Tools: Practical Capabilities That Matter

Beyond frameworks, AI project management tools can significantly reduce administrative overhead and improve execution. The practical capabilities that matter most for AI projects are automated scheduling and resource allocation, predictive risk identification based on historical project data, workflow automation for repetitive planning and documentation tasks, and integrated knowledge management across project artifacts.

Eight tools address these needs with different strengths. ClickUp provides a unified platform for AI-driven productivity with workflow automation that converts workspace knowledge into execution. Wrike excels at AI-powered task creation and meeting summarization. Taskade enables building customizable project applications. Monday.com provides AI workflow templates. Jira offers AI-driven issue management that maps well to sprint-based AI development. Notion excels at AI-powered knowledge bases and documentation management, which is particularly valuable for AI projects with extensive documentation requirements. Asana integrates well with external AI applications. Motion provides automated task scheduling that can adapt to AI project dynamics.

The most valuable capability for AI project managers isn't content generation but predictive intelligence: predicting delays before they occur, automatically adjusting schedules when priorities change, and synthesizing information from multiple sources into actionable summaries.

Implementation tip: Select AI project management tools based on three criteria specific to AI projects. First, documentation depth: AI projects produce more documentation than software projects (model cards, experiment logs, data lineage records, validation reports, bias assessments). Choose a tool that handles documentation as a first-class workflow item, not an afterthought. Second, experiment tracking integration: the tool should connect with experiment tracking platforms (MLflow, Weights and Biases) so that model development progress is visible in the project management context without requiring manual status updates. Third, cross-functional visibility: AI projects involve multiple disciplines with different work patterns. The tool should provide a unified view across data engineering pipelines, model development experiments, and software engineering tasks without forcing all teams into the same workflow structure. No single tool optimizes for all three criteria. Most AI teams use a project management tool for overall coordination supplemented by specialized tools for experiment tracking and documentation.

## A Comprehensive AI Project Checklist

Ten questions form the essential project management audit for AI initiatives.

- Has the project team adopted Agile principles adapted for AI's experimental and iterative nature? Standard Agile provides the foundation, but AI-specific adaptations for sprint cadence, task estimation, and definition of done are necessary.

- Has the team selected between Scrum and Kanban based on the project's uncertainty profile? High-uncertainty AI projects with unpredictable task durations often benefit from Kanban's flow-based approach over Scrum's fixed-cadence sprints.

- Does the project methodology account for the additional iterations that AI development requires compared to software development? Model training cycles, feature engineering experiments, and hyperparameter tuning create iteration patterns that standard sprint planning doesn't accommodate.

- Does the methodology encourage and resource exploration in addition to planned development? Exploration time, whether through credit systems or dedicated sprint allocation, enables the innovation that produces breakthrough approaches.

- Is the Scrum Master role filled by someone with sufficient technical context to guide the team effectively, or is the role rotated to leverage distributed expertise?

- Has the team identified and planned for multitasking requirements created by skill scarcity, using approaches that minimize context-switching costs?

- Does the project plan account for AI-specific complexity including version control for data, model documentation requirements, explainability analysis, and reproducibility standards?

- Are governance and ethics reviews integrated into the development workflow rather than treated as separate approval gates?

- Does the project use an appropriate combination of frameworks (CRISP-DM or CPMAI for structure, Agile for iteration, MLOps for production) rather than relying on a single framework?

- Are project management tools selected and configured to support AI-specific needs including experiment tracking, extensive documentation, and cross-functional visibility?

Use this checklist during project planning and review it at each major milestone. The questions that receive "no" answers identify the highest-priority gaps in your project management approach. Address the top three gaps before the project advances to its next phase. A project that proceeds without adapted Agile practices, without exploration time, and without multitasking management will accumulate the friction that these practices are designed to prevent. The friction compounds over the project lifecycle, producing increasingly severe delays, quality compromises, and team frustration.

## Implementation Tips for AI Project Management

The principles covered in this playbook converge into a set of practical implementation tips that apply across framework selection, Agile adaptation, team management, and tool selection. Each tip addresses a failure mode that appears consistently when AI projects are managed with patterns borrowed directly from software development.

### Managing Expectations About AI Project Timelines

AI project timelines are inherently less predictable than software project timelines because they include experimental phases with uncertain outcomes. A model that achieves the target accuracy on Monday may fail to generalize on Wednesday. A feature set that looks promising during exploration may produce no signal during training. A dataset that seems representative during development may drift from production reality within months of release.

Communicate this unpredictability to stakeholders explicitly and manage it through time-boxed experiments with clear go or no-go decision points rather than fixed delivery commitments. A commitment that sounds like "we will spend three weeks evaluating whether this model architecture can achieve the accuracy target, and at the end of three weeks we will have evidence to decide whether to proceed, pivot, or stop" is a manageable commitment. The duration is bounded, the decision criteria are defined, and the outcome produces learning regardless of which direction the evidence points.

A commitment that sounds like "the model will be ready by March fifteenth" is a commitment the team may not be able to keep regardless of effort, because model performance depends on factors beyond the team's control. Broken commitments erode trust faster than honest uncertainty. A leader who is told "we cannot promise March fifteenth, but we can promise a decision point on March fifteenth" has more useful information than a leader who is given a date and then watches it slip.

### Documentation as a Continuous Practice

AI project documentation must capture not just what was built but how results were produced, which data was used, which hyperparameters were selected, and why design decisions were made. This documentation is more extensive than software project documentation and is essential for reproducibility, auditability, and regulatory compliance. A model that cannot be reproduced cannot be audited, cannot be maintained, and cannot be defended when an examiner asks how a specific prediction was generated.

Treat documentation as a continuous activity integrated into daily work rather than a phase completed at the end of the project. Documentation written retrospectively after the project is complete is consistently less accurate and less detailed than documentation created as the work progresses. The difference is not effort. The difference is memory. A practitioner who documents a decision while making it captures the reasoning, the alternatives considered, and the trade-offs accepted. A practitioner who documents the same decision months later captures the conclusion but loses the reasoning that would allow a future reader to evaluate whether the decision still makes sense.

The practical implementation is to make documentation a completion criterion in the definition of done. A model training task is not done until the experiment log is written. A feature engineering decision is not done until the rationale is documented. A deployment is not done until the model card, the data sheet, and the lineage record are complete. This integrates documentation into the work rather than treating it as overhead to be performed when time allows.

### Building the Right Governance Rhythm

AI project governance should be integrated into the Agile cadence rather than operating as a separate process that runs in parallel. Include a brief governance check in every sprint review, covering bias assessment status, compliance requirement review, residual risk update, and reproducibility evidence. This integration ensures that governance receives consistent attention rather than being concentrated in occasional review meetings that are too infrequent to catch problems early and too intensive to be sustainable.

The alternative is governance as a separate process with its own meetings, its own documentation, and its own reviewers. This alternative fails for predictable reasons. The governance meetings are scheduled monthly or quarterly, which means problems that emerge during the sprint are not surfaced for weeks. The governance documentation duplicates the project documentation, which means the team maintains two parallel records that drift out of sync. The governance reviewers are disconnected from the work, which means their feedback is generic rather than specific to the actual decisions the team is making.

The integrated approach produces a different outcome. The governance check is a five-minute addition to the sprint review that the team already holds. The governance evidence is a byproduct of the work the team is already doing. The governance feedback is informed by the actual decisions the team has made in the past sprint. The result is governance that is continuous, specific, and sustainable.

### The Portfolio View

AI project management at the organizational level requires a portfolio view that balances resource allocation across active projects, sequences new projects based on available capacity, tracks the aggregate risk exposure from all AI systems in production, and measures cumulative value delivery across the AI program.

Individual project management ensures each project is well-run. Portfolio management ensures the organization's AI investment is well-allocated. Both are necessary, and the absence of either creates predictable problems.

Organizations that manage individual projects well but lack portfolio management frequently discover that their best people are spread across too many projects, that similar data pipelines are being built independently by different teams, and that the cumulative risk from their AI portfolio exceeds what any individual project's risk assessment revealed. A single project that passes its risk review may still contribute to a portfolio risk profile that the organization cannot accept, because the aggregate exposure across projects, models, and use cases compounds in ways that no single project assessment captures.

The portfolio view also enables better resource allocation. When the organization has visibility into which projects are consuming specialist time, which projects are blocked by data dependencies, and which projects are ready to move from experimentation to production, it can sequence work to maximize throughput without overloading any individual or team. The portfolio view makes the trade-offs between projects visible, which is the prerequisite for making the trade-offs deliberately rather than accidentally.

### The Connection Between the Four Tips

These four tips reinforce each other. Time-boxed experiments with go or no-go decision points produce evidence that the [governance](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/) rhythm can review. Continuous documentation produces the evidence trail that the governance rhythm requires. The portfolio view reveals whether the organization's time-boxed experiments are concentrated on the highest-value projects or scattered across too many initiatives.

A program that applies all four tips builds a management environment where AI projects can succeed on their own terms rather than being forced into a software development mold they do not fit. A program that ignores any one of them accumulates friction that compounds over time, producing increasingly severe delays, quality compromises, and governance gaps.

The best AI project management framework is not the one that imposes the most structure. It is the one that accommodates uncertainty without abandoning discipline, encourages exploration without sacrificing delivery, and adapts to each project's unique characteristics rather than imposing a uniform process. The four tips above are the operational expression of that principle.

## Key References and Authoritative Frameworks

Your AI project management practices should align with these established standards and practical references:

- [Agile Manifesto (2001)](https://agilemanifesto.org/), foundational principles for iterative development

- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html), AI Management System (governance and lifecycle requirements)

- [ISO/IEC 5338](https://www.google.com/search?q=https://www.iso.org/standard/81234.html), AI System Life Cycle Processes (lifecycle phase management)

- [CRISP-DM (Cross-Industry Standard Process for Data Mining)](https://www.google.com/search?q=https://www.ibm.com/docs/en/spss-modeler/18.5.0%3Ftopic%3Ddm-crisp-help-overview)

- [CPMAI (Cognitive Project Management for AI)](https://www.google.com/search?q=https://www.cognilytica.com/cpmai/)

- [Microsoft TDSP (Team Data Science Process)](https://learn.microsoft.com/en-us/azure/architecture/data-science-process/overview)

- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) (governance integration)

- MLOps maturity model frameworks from [Google](https://www.google.com/search?q=https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-in-machine-learning), [Microsoft](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/mlops-maturity-model), and [AWS](https://www.google.com/search?q=https://docs.aws.amazon.com/wellarchitected/latest/machine-learning-lens/mlops-maturity-model.html)

- Schwaber and Sutherland, "[The Scrum Guide](https://scrumguides.org/)" (adapted for AI)

- Anderson, "[Kanban: Successful Evolutionary Change for Your Technology Business](https://www.google.com/search?q=https://www.amazon.com/Kanban-Successful-Evolutionary-Technology-Business/dp/0984530500)"

- [PMBOK Guide](https://www.pmi.org/pmbok-guide-standards) adapted for AI project lifecycle management

- [EU AI Act documentation](https://artificialintelligenceact.eu/) and compliance requirements for project planning"

If you manage AI projects using unmodified Scrum with two-week sprints, fixed task estimates, and software-style definitions of done, you will create a management framework that fights the work rather than supporting it. Sprint commitments will be missed because model training takes longer than estimated. Exploration will be squeezed out because every sprint demands deliverable output. Team members spread across multiple projects will context-switch daily rather than focusing deeply on one problem. And the experimental nature of AI development will be treated as planning failure rather than structural reality.

When you adapt your project management approach to accommodate AI's experimental nature, build in exploration time that enables breakthrough innovation, manage skill scarcity through portfolio-level resource allocation rather than individual project multitasking, combine frameworks so that each phase of the lifecycle is managed with the approach best suited to its characteristics, and select tools that support AI-specific documentation, experiment tracking, and cross-functional coordination, you create a management environment where AI projects can succeed on their own terms rather than being forced into a software development mold they don't fit.

The best AI project management framework is the one that accommodates uncertainty without abandoning structure, encourages exploration without sacrificing delivery, and adapts to each project's unique characteristics rather than imposing a uniform process.

Which aspect of your current AI project management is creating the most friction with AI's experimental nature? Fix that specific friction point before adopting an entirely new framework.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
