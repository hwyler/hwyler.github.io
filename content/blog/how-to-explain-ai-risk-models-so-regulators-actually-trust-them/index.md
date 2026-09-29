---
title: "How to Explain AI Risk Models So Regulators Actually Trust Them"
date: 2026-03-12
tags: 
  - "ai-governance"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "business"
  - "explainability"
  - "hernan-huwyler"
  - "interpretability"
  - "iso-42001"
  - "iso-23894"
  - "shap-and-lime"
  - "technology"
  - "xai"
---

## How to Explain AI Risk Models to Regulators, Auditors, and Decision Makers

Most compliance teams ask for explainability too late.

They approve or pilot a high-performing AI risk model, then realize they cannot explain to auditors, regulators, or internal reviewers how the model reached a decision, which factors mattered most, where the limitations sit, or why the model should be trusted in a regulated setting. At that point, the technical work may already be strong. The governance position is weak.

This is a serious problem for AI-driven risk models used in areas such as regulatory reserves, fraud monitoring, customer risk assessment, underwriting, compliance surveillance, and operational risk. In these cases, explainability is not a nice extra. It is part of the control environment. This post shows how to explain AI risk models in a practical way, including the tradeoff between model complexity and explainability, when to prefer simpler techniques, how to use SHAP and related methods, and what documentation regulators actually need.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/cybersecurity-professional-analyzing-global-data.png?w=1024)

## The Explainability Tradeoff in Risk Modeling

Every AI risk model sits somewhere on a spectrum between perfectly explainable and completely opaque. Understanding where your model sits, and where it needs to sit, determines your compliance strategy.

On one end, interpretable models like logistic regression and decision trees produce predictions through processes that humans can follow step by step. A logistic regression that predicts loan default uses a formula where each risk factor has a visible weight. A decision tree makes a series of yes/no splits that can be drawn on a whiteboard. Anyone can trace why a specific prediction was made.

On the other end, complex models like deep neural networks and gradient boosting machines produce predictions through processes that exceed human comprehension. A gradient boosting machine with 500 trees, each with 8 levels of depth, makes predictions by aggregating thousands of decision paths. The prediction is accurate. The process that produced it is opaque.

The tradeoff is real. More complex models using multiple risk factors improve the accuracy of predictions. But explaining those complex models to regulators poses greater challenges. The question isn't which end of the spectrum is "right." It's which position on the spectrum is appropriate for your specific use case, given its regulatory requirements, decision criticality, and available explainability tools.

Regulators need to understand three things about any risk model: how the model works (its structure and logic), how predictions are made (what drives specific outputs), and how results are used to inform decisions (how model outputs connect to business actions). A model that can't satisfy all three requirements faces regulatory rejection regardless of its accuracy.

Implementation tip: Before selecting a model architecture, determine the explainability requirements for your specific regulatory context. Different regulators have different expectations. Banking regulators (OCC, Fed, ECB) have detailed model risk management guidance (SR 11-7, SS1/23) that requires comprehensive model documentation and challenge. Insurance regulators may accept different explainability standards. Consumer-facing models subject to ECOA or GDPR face specific right-to-explanation obligations. Map your explainability requirements first, then select the most accurate model architecture that satisfies those requirements. Selecting the model first and trying to explain it afterward frequently produces a model that's too complex for the available explainability tools to handle adequately.

## The Explainability Spectrum: From Transparent to Opaque

AI model types fall along the explainability spectrum in a roughly predictable order. Understanding where each type sits helps you match model selection to explainability requirements.

Models that are easier to explain include logistic regression (each feature has a coefficient showing direction and magnitude of influence), decision trees (visual split-based logic that can be traced for any prediction), naive Bayes (probability-based classification with transparent conditional probabilities), K-nearest neighbors (predictions based on similarity to known examples), rule-based systems (explicit if-then rules that can be read as business logic), explainable boosting machines (a constrained form of gradient boosting designed for interpretability), RuleFit (combines rule-based logic with linear models), and random forests (aggregated decision trees where feature importance can be computed).

Models that are harder to explain include support vector machines with non-linear kernels (predictions depend on mathematical transformations of the feature space), gradient boosting machines (sequential ensembles with complex interaction effects), deep neural networks (layers of interconnected neurons with millions of parameters), deep learning architectures (convolutional, recurrent, and transformer networks), and reinforcement learning (agents that learn through interaction with environments).

The placement isn't absolute. A random forest with 10 trees and 3-level depth is reasonably explainable. A random forest with 1,000 trees and 20-level depth is effectively a black box despite using the same algorithm. Model configuration choices within each type affect explainability as much as the choice of algorithm itself.

Implementation tip: Decision trees and regression methods are intrinsically explainable and can be preferred for models impacting consumers or regulated decisions. When a risk model directly determines outcomes for individuals, such as credit decisions, insurance pricing, or benefit eligibility, intrinsic explainability provides the strongest regulatory position. You can explain a logistic regression coefficient to a judge. Explaining a SHAP value derived from a gradient boosting machine to a judge requires significantly more context and creates more opportunities for challenge. For regulated models where individual-level explanation is required, start with interpretable models. Move to complex models only when interpretable models demonstrably fail to meet accuracy requirements and you have a robust explainability framework that satisfies your specific regulatory obligations.

## How Explainable AI Works in Practice

The XAI workflow connects training data and model outputs to explanations that different audiences can understand. The process flows from data through models to predictions, then through explainability methods to explanations that serve three distinct audiences: users who interact with the model, compliance officers who govern it, and regulators who oversee it.

Training data feeds the AI-based risk model. Feedback data from production outcomes flows back to improve the model over time. The model produces predictions. Explainable AI methods analyze those predictions and generate explanations. The explanations are tailored to the audience: technical detail for model developers, business context for compliance officers, and regulatory documentation for auditors and regulators.

Two categories of explainability methods serve different purposes.

Global methods explain the model's logic across the entire dataset. They answer the question: "In general, how does this model make decisions?" Global feature importance shows which risk factors have the most influence overall. Global behavior descriptions reveal the model's general decision patterns. These methods help compliance officers and regulators understand the model's overall approach.

Local methods explain the model's output for a specific observation or prediction. They answer the question: "Why did the model produce this specific result for this specific case?" Local explanations show which features drove a particular prediction and how changing those features would change the prediction. These methods are essential when individuals have the right to understand decisions that affect them.

Both categories are necessary. Global methods build confidence in the model's general approach. Local methods provide the specific explanations that regulatory challenge and individual rights require.

Implementation tip: Apply model-agnostic explainability methods to prevent reliance on a single explanation approach. Model-agnostic methods, such as SHAP and LIME, work with any model type, which means you can change your underlying model without changing your explainability framework. Model-specific methods (like directly reading decision tree splits) are valuable for intrinsically interpretable models but become unavailable if you later switch to a more complex architecture. Building your compliance documentation around model-agnostic methods provides flexibility for future model improvements while maintaining consistent explainability output.

## SHAP: The Most Versatile Explainability Framework

SHAP (Shapley Additive Explanations) is the most widely used framework for explaining the output of machine learning models. It assigns each input feature a Shapley value representing the feature's contribution to the model's prediction for a specific instance. Understanding SHAP's five components provides the foundation for most regulatory explainability requirements.

SHAP values represent the contribution of each feature to a specific prediction. A positive SHAP value indicates that the feature pushes the prediction toward the positive class or increases the predicted value. A negative SHAP value indicates the opposite. The magnitude represents the strength of the feature's influence. For a loan default prediction, a SHAP analysis might show that high debt-to-income ratio contributed +0.15 toward default prediction while long employment history contributed -0.08 against default prediction. These values explain not just which features mattered but how much each one mattered and in which direction.

SHAP feature importance shows the overall importance of each feature across all predictions. It's calculated by averaging the absolute SHAP values for each feature across all instances in the dataset. Features with higher importance scores have greater impact on the model's predictions overall. This global view helps identify which risk factors the model relies on most and can guide both feature selection and regulatory discussion about whether the model uses appropriate inputs.

SHAP interaction values measure how features work together to influence predictions. They quantify how the presence or absence of one feature affects the SHAP values of another feature. Interaction values uncover complex relationships and dependencies between features that aren't apparent from individual feature contributions. If high income combined with high debt produces a different risk prediction than either factor alone would suggest, interaction values reveal this pattern.

SHAP summary plots combine feature importance with the distribution of SHAP values across all predictions. They display the top features based on importance and show how different feature values contribute to predictions using colored dots. The plot allows reviewers to see at a glance which features matter most and how their values relate to model outputs.

SHAP dependence plots show the relationship between a specific feature and the model's predictions while accounting for interaction effects with other features. They reveal how predictions change as a feature value varies and can uncover non-linear relationships. These plots help reviewers understand whether the model's learned relationships make business sense, which is a critical validation step for regulatory acceptance.

Implementation tip: Use SHAP summary plots as the primary communication tool when presenting model explanations to regulators and auditors. The summary plot answers the three questions regulators care about most in a single visualization: Which features does the model use? How important is each feature? How does each feature's value relate to predictions? When presenting to regulators, annotate the summary plot with domain context: "The model's most influential feature is debt-to-income ratio, which aligns with established credit risk principles. Higher values (shown in red) consistently push predictions toward higher default probability (rightward on the plot), which matches expected economic behavior." This combination of statistical evidence and domain validation builds regulatory confidence more effectively than either one alone.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/chaotic-chalkboard.png?w=771)

## Beyond SHAP: Additional Explainability Methods

SHAP provides the most comprehensive single framework, but several additional methods address specific explainability needs that SHAP alone doesn't fully cover.

Partial dependence plots show the functional relationship between an input feature and the prediction by varying the values of a single feature while holding all other features constant. They reveal the average effect of a feature on predictions. If a partial dependence plot for "age" shows a U-shaped curve, it means the model predicts higher risk for both very young and very old applicants, with lowest risk in the middle age range. This visualization makes the model's learned relationship directly comparable to established risk theory.

Individual conditional expectations track the prediction for individual cases as a single feature varies, rather than averaging across all cases as partial dependence plots do. They can detect interactions that partial dependence plots miss, because individual cases may follow different patterns that cancel out in the average.

Accumulated local effects extend partial dependence plots by handling feature correlations. When features are correlated (income and education level, for example), partial dependence plots can produce misleading results because they consider combinations of feature values that don't occur in reality. Accumulated local effects address this by restricting the analysis to feature value changes that are consistent with observed data patterns.

LIME (Local Interpretable Model-Agnostic Explanations) explains individual predictions by building a simple, interpretable model (usually a linear model) that approximates the complex model's behavior in the neighborhood of a specific prediction. The local model's coefficients serve as explanations for that prediction. LIME is particularly useful when you need a simple, linear explanation for a single case.

Counterfactual analysis describes the smallest change to the feature values that would change the prediction to a different output. "This loan application was predicted to default. If the debt-to-income ratio decreased from 0.45 to 0.38 while all other features remained the same, the prediction would change to non-default." Counterfactual explanations are intuitive for non-technical audiences because they describe actionable changes rather than statistical contributions.

Saliency maps use color to indicate which regions of the input space contribute most to the prediction. They're primarily used for image-based models (such as visual quality inspection or medical imaging) but the concept extends to any input type where spatial or structural relationships matter.

Local rule-based explanations generate decision rules that explain specific predictions in if-then format. "IF debt-to-income > 0.42 AND employment-length < 2 years THEN predicted default." These rules are highly interpretable and can be directly compared to existing business rules and regulatory criteria.

Implementation tip: Use different explainability methods for different audiences. For model developers: SHAP values, dependence plots, and interaction analysis provide the technical depth needed for model improvement. For compliance officers: summary plots, feature importance rankings, and partial dependence plots provide the model-level understanding needed for governance decisions. For regulators and auditors: counterfactual analysis, local rule-based explanations, and documented case examples provide the individual-level transparency needed for regulatory challenge. For affected individuals (when right-to-explanation applies): plain-language counterfactual explanations provide the most accessible format. Building a single "explanation" document for all audiences typically serves none of them well. Create audience-specific explanation outputs from the same underlying analysis.

## Testing and Validating Explanations

Explainability isn't just about generating explanations. It's about verifying that those explanations are accurate, stable, and useful.

Stability and sensitivity analysis stress-tests the model by assessing its performance and behavior on data ranges not captured by the training data. If a small change in input values produces a dramatically different explanation, the explanation is unstable and unreliable. Stable explanations should change proportionally to input changes, meaning a small input change produces a small explanation change.

Adversarial testing identifies vulnerabilities in machine learning algorithms that can be exploited by adversarial attacks and provides defense mechanisms. From an explainability perspective, adversarial testing reveals whether the model can be manipulated to produce misleading explanations, cases where the model appears to make decisions for reasonable reasons but is actually being influenced by hidden or inappropriate factors.

Attribution analysis compares the outcomes of two different scenarios of the machine learning model to understand the drivers behind differences in model performance. This technique is particularly valuable when model performance varies across subgroups: attribution analysis reveals whether the performance difference is driven by data representation, feature relevance, or model architecture.

Constraints on inputs maintain domain-specific rules and improve the explainability of complex models. By constraining the model to respect known business rules (for example, requiring that higher income always reduces default probability, holding all else equal), you ensure that explanations align with domain knowledge rather than reflecting spurious patterns in the training data.

Implementation tip: Conduct a stability analysis before presenting any explanation to a regulator. Generate explanations for a set of representative cases, then perturb the input values slightly (by 1-5%) and regenerate the explanations. If the feature importance rankings change dramatically with minor input changes, the explanations are unreliable and should not be used for regulatory communication. Unstable explanations undermine regulatory trust more than no explanations at all, because they suggest the model's behavior isn't well understood even by the team deploying it. Identify and resolve stability issues before regulatory review, not during it.

## Practical Tips for Regulatory Compliance

Ten practical recommendations address the most common explainability challenges in regulated risk modeling.

Reduce the input variables to the most important risk factors that influence the model's predictions. Fewer features produce simpler explanations without necessarily sacrificing significant accuracy. Many risk models include dozens of features that contribute marginally to prediction quality but substantially to explanation complexity.

Use graphs to represent the model's structure and decision-making process. Visual representations are more accessible than numerical tables for most regulatory audiences. Decision tree visualizations, SHAP summary plots, and partial dependence plots convey model behavior more effectively than parameter listings.

Provide simple probability estimates that can be interpreted by humans. Instead of raw model outputs, present calibrated probabilities: "This vendor has a 23% probability of payment default within 12 months." Calibrated probabilities are intuitive and actionable.

Explain which features the model uses and why they are important. Don't just list features. Explain their relevance: "The model uses supplier financial ratios because historical data shows they are the strongest predictors of payment default, consistent with established credit analysis principles."

Clearly communicate limitations, assumptions, and potential biases. Every model has conditions where it performs less reliably. Document these honestly: "The model was trained on data from 2019-2024 and may not perform as well during economic conditions significantly different from this period."

Use real-world case studies to demonstrate how the model works. Walk regulators through specific predictions with full explanations. Concrete examples build understanding and trust more effectively than abstract descriptions.

Get user feedback to refine interpretability over time. The people who use model outputs daily can identify where explanations are confusing, insufficient, or misleading. Incorporate their feedback into explanation design.

Regularly monitor accuracy and update explanations when new data and algorithms are added. Explanations based on an earlier model version become misleading when the model is retrained. Update explanation documentation with every model version change.

Use tools that allow legal auditors to validate the model's compliance and monitor its real-world impact. Auditors need the ability to independently verify explanations, not just read pre-prepared documentation.

Prioritize intelligibility and transparency over other factors. A model that's 3% more accurate but can't be explained to regulators creates more risk than value. A model that's slightly less accurate but fully explainable provides a defensible regulatory position.

Implementation tip: Define "black box checks" that explain complex models to business users, technical reviewers, and compliance officers separately. Each audience needs different depth. Business users need to understand what the model does and whether its outputs make sense in their domain context. Technical reviewers need to understand the model architecture, training methodology, and validation results. Compliance officers need to understand the regulatory implications of model decisions, the fairness properties of the model, and the audit trail connecting inputs to outputs. Create a black box check procedure that produces all three levels of explanation from the same underlying analysis. Run these checks before any model goes into production and after every significant model update.

## Documentation Requirements for Regulatory Compliance

Document the entire process of how the AI model determines decision-making and risk reserves. This documentation helps auditors and regulators understand the model's workings and constitutes the primary artifact for regulatory review.

Four documentation areas must be covered comprehensively.

Data sources: Document every data source the model uses, including the source system, the time period covered, the variables extracted, any filtering or sampling applied, and the data quality assessment for each source. Explain why each data source was selected and how it relates to the risk being modeled.

Preprocessing steps: Document every transformation applied to the data before model training: missing value treatment, outlier handling, feature encoding, normalization, feature engineering, and data splitting methodology. Preprocessing decisions can significantly affect model behavior and must be transparent for regulatory review.

Model architecture: Document the model type selected, the rationale for selection (including comparison with alternative approaches), the model's configuration parameters, the training methodology, and the validation approach. Include the explainability methods applied and the explanation outputs they produce.

Decision-making logic: Document how model outputs translate into business decisions. If the model produces a probability score, document the thresholds that determine different actions. If the model informs reserve calculations, document the formula connecting model output to reserve amount. This documentation must be specific enough that an auditor can independently verify that a given input produces the expected output and the expected business action.

Implementation tip: Structure your model documentation as a layered document with three levels. Level one (executive summary, 2-3 pages): describes what the model does, its performance, and its key risk factors in business language. Level two (technical overview, 10-15 pages): describes the model architecture, training approach, validation results, and explainability analysis in enough detail for a technically literate reviewer. Level three (detailed appendices, variable length): contains the full technical documentation including code references, data dictionaries, complete validation results, and all explainability outputs. This layered structure allows each reviewer to engage at their appropriate depth. Regulators typically start with level one, drill into level two for areas of concern, and reference level three for specific technical questions. A flat document that mixes executive summaries with code-level detail serves nobody well.

## Cross-Cutting Implementation Tips for AI Risk Model Explainability

These principles apply across all model types, explainability methods, and regulatory contexts.

Implementation tip on choosing between intrinsic and post-hoc explainability: Intrinsic explainability (using inherently interpretable models) is always preferable to post-hoc explainability (explaining opaque models after the fact) when both approaches can meet accuracy requirements. Post-hoc explanations are approximations. They describe what the complex model appears to be doing, not what it's actually doing. The approximation may be inaccurate, especially in regions of the feature space where the explainability method has limited data. If your intrinsically interpretable model meets regulatory accuracy thresholds, use it. The regulatory burden is dramatically lower.

Implementation tip on explaining feature interactions: Individual feature explanations are necessary but insufficient for complex models where features interact. A model that treats income and debt independently may produce different predictions than one that considers the debt-to-income ratio. SHAP interaction values reveal these relationships, but they're harder to communicate than individual feature effects. When presenting interaction effects to regulators, use concrete examples: "For applicants with income above $150,000, the model is relatively insensitive to employment length. For applicants with income below $60,000, shorter employment length significantly increases predicted default risk." Concrete conditional statements are more accessible than interaction statistics.

Implementation tip on maintaining explanation quality during model updates: Every model retraining has the potential to change which features matter, how they interact, and what explanations the model produces. Build an automated explanation comparison into your model update pipeline: generate SHAP summary plots for both the current and updated models and compare them. If feature importance rankings change substantially, investigate whether the change reflects genuine pattern shifts in the data or artifacts of the retraining process. Document explanation changes alongside performance changes in your model version records. A model update that improves accuracy by 1% but dramatically changes the explanation raises more regulatory risk than one that maintains both accuracy and explanation stability.

Implementation tip on the regulatory audience: Because risk models are used for critical and highly regulated decisions, external regulators must trust their predictive outputs. Trust is built through demonstrated competence in three areas: the model produces accurate predictions (validation evidence), the model's predictions can be explained (explainability evidence), and the model is governed responsibly (documentation and process evidence). Most regulatory challenges focus on the second area, explainability, because it's where regulators have the least independent ability to verify. They can check your accuracy numbers. They can review your governance documentation. But they can only evaluate your model's decision logic through the explanations you provide. Invest in explanation quality proportionate to this reality.

## Key References and Authoritative Frameworks

Your AI risk model explainability practice should align with these established standards:

- ISO/IEC 42001:2023, AI Management System (transparency and documentation requirements)

- EU AI Act, Articles 13-14 on transparency and human oversight for high-risk AI systems

- GDPR Articles 13-15 and 22 (right to explanation for automated decision-making)

- NIST AI Risk Management Framework, particularly transparency and explainability guidance

- Basel Committee SR 11-7, Model Risk Management (model documentation and validation)

- UK PRA SS1/23, Model Risk Management (explainability requirements for financial models)

- OECD AI Principles on transparency and explainability

- ISO/IEC 42005, AI Impact Assessment (explanation requirements for impact documentation)

- Lundberg and Lee, "A Unified Approach to Interpreting Model Predictions" (foundational SHAP paper)

- Ribeiro et al., "Why Should I Trust You? Explaining the Predictions of Any Classifier" (foundational LIME paper)

- Molnar, "Interpretable Machine Learning" (comprehensive practical reference)

- EBA Guidelines on ML for IRB models (European banking explainability standards)

If you deploy risk models that produce accurate predictions but can't explain how those predictions are generated, you create a regulatory liability that grows with every decision the model informs. Regulators who can't understand a model's logic can't approve it. Auditors who can't trace a model's decision path can't validate it. Affected individuals who can't understand why a model rejected their application can't exercise their legal rights. And when the model produces an incorrect output that causes harm, the inability to explain why it happened prevents both remediation and accountability.

When you build explainability into your risk models from design through deployment, selecting model complexity appropriate to your regulatory context, applying SHAP and complementary methods to generate both global and local explanations, documenting the complete decision pipeline, and tailoring explanation outputs to each audience, you create models that are both accurate and trustworthy. Regulators can approve them because they understand them. Auditors can validate them because they can trace their logic. Affected individuals can challenge them because they can understand the basis for decisions. And when errors occur, the explanation framework provides the diagnostic capability needed to identify root causes and prevent recurrence.

A risk model that can't explain itself is a liability wearing the mask of an asset.

Can your most critical risk model explain its predictions to a regulator in terms a non-technical reviewer would understand? If not, start building that explanation capability this month.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
