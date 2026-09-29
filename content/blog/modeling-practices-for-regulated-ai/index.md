---
title: "Modeling Practices for Regulated AI"
date: 2026-03-14
tags: 
  - "ai-model-validation"
  - "ai-projects"
  - "ai-risk-management"
  - "artificial-intelligence"
  - "business"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "lime"
  - "model-risk-management"
  - "shap"
  - "technology"
---

## The Validation Framework That Satisfies Both Data Scientists and Regulators

CFPB Circular 2022-03 made the regulatory position unambiguous: creditors using complex algorithms for credit decisions must provide specific reasons for adverse actions taken against applicants. They cannot excuse noncompliance by claiming their algorithms are too opaque to understand. Creditors must ensure the accuracy of any post-hoc explanations, as such approximations may not be viable with less interpretable models.

That circular changed the calculus for every financial institution deploying machine learning. A model that's accurate but unexplainable isn't just a governance concern. It's a compliance violation. And explaining a model isn't just about applying SHAP values after the fact. Post-hoc explainability tools are approximations. They may not accurately explain what the model is actually doing.

Sound modeling practices in regulated environments require rigor across four domains: statistical validation that proves the model works on data it hasn't seen, explainability approaches that provide genuine transparency rather than approximate reassurance, parameter optimization that ensures stability rather than just performance, and outcome analysis that identifies where the model fails before those failures cause harm.

This post covers all four domains with the technical depth that model developers need and the practical clarity that validators, auditors, and compliance officers require.

## Why Sound Modeling Practices Matter More in Regulated Industries

Banking models operate under regulatory expectations that general-purpose AI models don't face. The Basel frameworks, SR 11-7 guidance from the Federal Reserve, CRD IV in Europe, and sector-specific regulations like ECOA establish requirements for model transparency, validation rigor, and ongoing performance monitoring that exceed what most AI governance frameworks address.

Three characteristics make regulated model development different from general AI development.

First, the models make consequential decisions about individuals. Credit scoring, loan approval, fraud detection, and risk assessment directly affect people's access to financial services. Errors aren't just performance degradation. They're potential violations of fair lending laws, consumer protection regulations, and anti-discrimination statutes.

Second, regulators require explainability that goes beyond technical metrics. A model developer who reports "SHAP values indicate that income is the most important feature" has provided a statistical summary. A regulator who asks "Why was this specific applicant denied credit, and can you prove that the explanation accurately represents the model's actual reasoning?" is asking a fundamentally different question. The gap between these two questions defines the explainability challenge.

Third, models must demonstrate stability across economic conditions, population segments, and time periods. A credit risk model validated during economic expansion may fail during recession. A fraud detection model calibrated for one market may produce excessive false positives in another. Regulators expect models to perform reliably across the conditions they'll actually encounter, not just the conditions present in the training data.

These characteristics demand modeling practices that are more rigorous, more documented, and more independently validated than what standard ML development produces.

Implementation tip: Before starting model development for any regulated application, obtain and read the specific regulatory guidance applicable to your jurisdiction and use case. For US banking: SR 11-7 (Model Risk Management), OCC Bulletin 2011-12, and CFPB Circular 2022-03. For European banking: CRD IV and EBA guidelines on ML for IRB models. For insurance: applicable state-level model governance requirements. Each jurisdiction has specific expectations that affect model architecture choices, validation methodology, and documentation requirements. Developing a model and then checking regulatory requirements afterward frequently reveals that the chosen approach doesn't satisfy regulatory expectations, requiring costly redesign. Reading the guidance first shapes every subsequent decision.

## Sound Statistical and Machine Learning Practices

Sound modeling practices begin with validation methodology that proves the model works on data it hasn't seen, under conditions it hasn't encountered, and across populations it will actually serve.

Robust out-of-sample testing separates training data from evaluation data so that performance metrics reflect genuine predictive capability rather than memorization. The test set must be completely held out during all development phases: feature selection, hyperparameter tuning, model selection, and threshold calibration. Any contamination of the test set, where test data influences development decisions, invalidates the performance estimate.

For banking models, out-of-sample testing should include temporal holdout testing where the model is trained on earlier periods and tested on later periods. This mimics how the model will actually be used: predicting future outcomes based on historical patterns. Random train-test splits that mix time periods can produce optimistically biased performance estimates because the model effectively "sees the future" during training.

Model validation on unseen data extends beyond standard test sets. Independent validation uses data that the development team never accessed during any phase of development. This data is held by a separate validation team and used only for final performance assessment. The independence of this validation is critical because development teams, even with the best intentions, make subtle decisions during development that optimize for their specific data characteristics.

Evaluating model performance under various economic scenarios tests whether the model remains reliable when conditions change. Backtesting compares model predictions against actual historical outcomes across different economic regimes. Stress testing evaluates model behavior under extreme but plausible scenarios such as financial crises, market shocks, rapid interest rate changes, or sudden unemployment increases. A credit risk model that performs well during stable economic conditions but produces wildly inaccurate predictions during downturns is not sound.

Internal benchmarks and peer comparisons validate the appropriateness of the model and ensure it adheres to industry standards. Compare your model's performance against simpler baseline models (logistic regression, industry-standard scorecards) to verify that the additional complexity of a more sophisticated approach is justified by meaningful performance improvement. Compare against published industry benchmarks for similar use cases to verify that your model's performance is within the expected range.

Implementation tip: The most common validation failure in regulated modeling is insufficient temporal separation between training and testing data. A model trained on data from January through September and tested on October through December of the same year may appear to generalize well because the economic conditions and customer behavior patterns are similar within the same year. True temporal validation requires testing across different economic cycles: train on pre-recession data, test on recession data, or train on low-interest-rate periods, test on rising-rate periods. If your historical data doesn't span different economic conditions, document this limitation explicitly in your model documentation and describe the scenarios under which the model's performance is unvalidated. Regulators prefer honest documentation of limitations over overconfident claims of robustness.

## Explainability: Post-Hoc Methods and Their Limitations

Model explainability is crucial in high-stakes decision-making environments where financial decisions directly affect customers and regulatory compliance. The choice of explainability approach depends on the model's architecture and the regulatory context.

Inherently interpretable models provide direct insight into how predictions are made. Decision trees and logistic regression models reveal their decision logic transparently. A logistic regression coefficient of 0.35 on "debt-to-income ratio" means that, holding all else equal, each unit increase in debt-to-income increases the log-odds of the predicted outcome by 0.35. This explanation is exact, not approximate. It describes what the model actually does, not what an external tool estimates it does.

Complex models require post-hoc explainability tools. Four primary tools serve this purpose, each with specific strengths and limitations.

Partial Dependence Plots (PDP) show the functional relationship between an input feature and the prediction, averaged across all other features. They reveal the average effect of a feature on the model's output as that feature's value changes. Limitation: PDPs assume feature independence. When features are correlated (income and education level, for example), PDPs can display relationships that include impossible feature combinations, producing misleading explanations.

Accumulated Local Effects (ALE) extend partial dependence plots by handling feature correlations. ALE plots restrict the analysis to feature value changes that are consistent with observed data patterns, avoiding the impossible combinations that PDPs can produce. ALE plots are generally preferred over PDPs for correlated features.

SHAP (Shapley Additive Explanations) assigns each feature a value representing its contribution to a specific prediction. SHAP provides both local explanations (why this prediction was made for this applicant) and global explanations (which features matter most across all predictions). Limitation: SHAP values are computationally expensive for large models and are still approximations of the model's true behavior.

LIME (Local Interpretable Model-Agnostic Explanations) builds a simple, interpretable model that approximates the complex model's behavior in the neighborhood of a specific prediction. The simple model's coefficients serve as the explanation. Limitation: LIME explanations depend on the neighborhood definition and can produce different explanations for the same prediction depending on how the neighborhood is constructed.

The critical caveat for all post-hoc methods: these tools are approximations. They may not accurately explain what the model is actually doing. Complex machine learning models can exhibit behavior in specific regions of the feature space that post-hoc tools don't capture because the tools simplify the model's behavior to make it understandable. In regulated environments where explanation accuracy is a compliance requirement, this approximation gap creates risk.

Implementation tip: When CFPB Circular 2022-03 states that creditors must ensure the accuracy of post-hoc explanations, it creates a specific compliance obligation that many organizations haven't fully addressed. How do you verify that a SHAP explanation accurately represents the model's actual reasoning? One approach: compare post-hoc explanations against the explanations from an inherently interpretable model trained on the same data. If the SHAP explanation for a complex model says "income was the most important factor" but a logistic regression trained on the same data shows "credit history was the most important factor," the discrepancy should be investigated. Consistent explanations across model types increase confidence in explanation accuracy. Inconsistent explanations indicate that the post-hoc tool may be misrepresenting the complex model's actual behavior.

## Inherently Interpretable Machine Learning: Beyond the Post-Hoc Approximation

Complex machine learning models can be made inherently interpretable when their architectures are properly constrained. This approach provides exact explanations without the approximation risk of post-hoc methods.

Two locally interpretable model architectures provide exact region-specific explanations.

Deep ReLU Networks use the Rectified Linear Unit activation function, which outputs the input directly if positive and returns zero otherwise. A ReLU network is locally interpretable because it acts as a piecewise linear function. The network divides the input space into regions, each defined by a specific activation pattern, where it behaves as a local linear model. For any input, the network's predictions are governed by a corresponding local linear model, providing exact local interpretability. There is no need for post-hoc explanation methods like LIME or SHAP, which approximate local behaviors.

This architecture preserves the power of deep learning (capturing complex non-linear relationships through hierarchical feature learning) while providing the interpretability of linear models within each region of the input space. The tradeoff is that the model's global behavior across all regions may still be complex, but any individual prediction can be explained exactly.

Boosted Linear Trees, as implemented in frameworks like LightGBM, use decision trees where each terminal node contains a linear model instead of a constant value. The tree partitions the data, and within each terminal node, a linear model is fitted to the data points that fall into that node. This combines the non-linear partitioning power of decision trees with the predictive strength and interpretability of linear models within each segment.

The model is locally interpretable because each input follows a path to a specific terminal node where a local linear model is applied. The linear models from different terminal nodes can be aggregated, and the aggregation of linear models results in another linear model. This structure provides exact local explanations and makes it easier to understand the model's behavior without post-hoc explanation techniques.

For globally interpretable models, the functional ANOVA (fANOVA) structure constrains machine learning models by decomposing them into main effects and low-order interactions.

The function f(x) is expressed as a sum of additive components: the overall mean, the main effects of individual features, and pairwise interactions between features. Higher-order interactions can be included but typically only low-order interactions (pairwise) are considered for interpretability.

The construction process involves three steps. Decomposition breaks the model function into main effects and interaction terms, keeping complexity manageable. Regularization limits the complexity of interactions and emphasizes main effects. Machine learning models like gradient boosting or neural networks are trained to estimate these components, identifying the most important features and interactions while maintaining interpretability.

Because fANOVA models focus on main effects and low-order interactions, they offer a natural framework for global interpretability. The model's behavior across the entire input space is understandable. Each feature's contribution and interaction can be explicitly understood without complex post-hoc explanation techniques.

Implementation tip: For regulated banking applications, start with inherently interpretable architectures and move to post-hoc explained complex models only when the interpretable architecture demonstrably fails to meet performance requirements. The regulatory burden for inherently interpretable models is substantially lower. A boosted linear tree model where each prediction can be explained exactly through its terminal node's linear model requires no explanation accuracy verification. A gradient boosting model requiring SHAP explanations requires verification that the SHAP values accurately represent the model's behavior, which is an additional validation burden that adds cost, complexity, and regulatory risk. Document the performance comparison between interpretable and complex architectures. If the interpretable model achieves 91% accuracy and the complex model achieves 93%, the 2-point improvement must justify the substantial additional explainability burden. In many regulated contexts, it doesn't.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/1710924913361.png?w=1024)

## Parameter and Hyperparameter Optimization

Model parameters (the coefficients learned during training) and hyperparameters (the settings chosen before training) both require careful optimization and stability verification in regulated environments.

Model parameters must be estimated correctly using well-established techniques such as maximum likelihood estimation or gradient-based optimization. The parameter estimation process should be documented with sufficient detail for an independent validator to reproduce the results.

Hyperparameter tuning is crucial for avoiding both underfitting and overfitting. Techniques like grid search or random search, combined with cross-validation, find the optimal hyperparameter values that balance model complexity and performance. Regularization techniques (L1 or L2 penalties) prevent overfitting, especially when dealing with high-dimensional financial data.

Two stability assessments verify that parameter and hyperparameter choices produce reliable models.

Model replication involves building the model anew using different samples of data or subsets (through bootstrapping) to verify that it produces consistent results. This validates the model's performance across various datasets and ensures that predictions are not artifacts of specific training data. If a model trained on one bootstrap sample produces substantially different coefficients or predictions than a model trained on another bootstrap sample of the same size, the model is unstable and its predictions should not be trusted for consequential decisions.

Stability testing assesses whether predictions remain consistent over time and across different segments of the population. Two specific tests are essential.

Random seed variation evaluates how changes in data partitioning affect model performance. By training and testing the model with different random seeds for the train-test split, banks can evaluate sensitivity to specific data configurations. If the model yields similar performance metrics across different seeds, it suggests stability. Significant performance variation across seeds indicates instability that requires investigation.

Stochastic optimization initialization tests whether models using stochastic optimization methods (like stochastic gradient descent) converge to similar solutions consistently. Running the model with different random seeds for parameter initialization reveals whether the optimization landscape contains multiple local optima that produce different models. Significant variations in model performance due to different initializations indicate instability and the need for further investigation.

Implementation tip: Define quantitative thresholds for acceptable stability before running stability tests. "The model should be stable" is not a testable criterion. "Model accuracy should vary by no more than 2 percentage points across 20 different random seeds for train-test splitting, and feature importance rankings should maintain the same top 5 features across 90% of bootstrap samples" is testable. Without predefined thresholds, stability assessment becomes subjective: some team members will consider 4-point variation acceptable while others won't. Predefined thresholds create an objective standard that the model either passes or fails. For regulated models, document these thresholds in the model development plan before running the tests, so that validators can verify the thresholds were defined prospectively rather than adjusted to match results.

## Outcome Analysis: Identifying Where the Model Fails

Outcome analysis assesses how well the model's predictions align with actual outcomes in real-world application. It determines whether the model remains reliable and accurate under various conditions. In banking, this analysis is essential because models drive high-stakes decisions in credit scoring, fraud detection, and risk management.

Outcome analysis focuses on four components: identifying model weaknesses, assessing output reliability, evaluating robustness against input noise, and testing resilience to distribution drift.

Identification of model weakness begins with systematic evaluation of the model's performance under a wide range of conditions to uncover areas where it produces unreliable results.

Performance decomposition breaks down the model's performance across different segments: geographic regions, loan categories, income levels, credit score ranges, and demographic groups. A credit scoring model may perform well overall but exhibit higher error rates for specific subgroups, indicating either a data representation issue or a model architecture limitation. Decomposition reveals these hidden weaknesses that aggregate metrics conceal.

Segmentation by key variables analyzes predictions across subgroups based on key features like loan type, loan-to-value ratio, and credit score. A credit risk model might perform well for middle-income borrowers but poorly for high-income or low-income groups. Identifying these segments enables targeted model improvement.

Clustering for latent patterns uses techniques like k-means or hierarchical clustering to group similar instances based on input features without predefined segments. This reveals latent patterns where performance varies significantly. A cluster of borrowers with thin credit history and low credit scores might exhibit high error rates, indicating a model weakness in handling high-risk borrowers that segment-based analysis wouldn't detect.

Error analysis examines the types of errors the model makes. False positives and false negatives have different business consequences and often concentrate in different population segments. A loan approval model that falsely predicts low-risk customers as high-risk leads to missed lending opportunities. A model that falsely predicts high-risk customers as low-risk leads to increased defaults. Understanding which error type dominates in which segment guides remediation priorities.

Backtesting and stress testing detect weaknesses that emerge only under particular conditions. Regular backtesting compares predictions against actual historical outcomes across different economic periods. Stress testing evaluates behavior under extreme scenarios that may not appear in normal training data.

Implementation tip: The most actionable outcome analysis technique for regulated models is range analysis on identified weak segments. Once performance decomposition identifies an underperforming segment, analyze which specific feature value ranges drive the weakness. A model might perform well for credit scores between 600 and 750 but produce inaccurate predictions for scores below 500 or above 800, where risk factors behave differently. Document these specific ranges in the model card and the validation report. This documentation serves two purposes: it informs model users about conditions where predictions are less reliable, and it provides the development team with specific targets for model improvement (adding interaction terms for underperforming ranges, collecting additional training data for underrepresented segments, or creating segment-specific models for populations where a single model can't achieve adequate performance).

## Detecting Underfitting, Overfitting, and Benign Overfitting

Two failure modes require specific detection in outcome analysis.

Underfitting occurs when the model is too simple to capture underlying patterns, resulting in poor performance across segments. Signs include high error rates across multiple segments (the model consistently makes errors regardless of input characteristics), biased predictions where the model produces overly simplified outputs (always predicting low risk for an entire segment), and training error that's high relative to reasonable expectations for the problem complexity.

Remediation for underfitting includes adding interaction terms between variables to capture more complex relationships, introducing non-linear terms for features with non-linear effects on the outcome, using more sophisticated model architectures that can represent the complexity of the underlying relationship, and adding features that capture information the current model misses.

Overfitting occurs when the model becomes too complex and fits noise in the training data, leading to poor generalization. Signs include training errors that are dramatically lower than test errors (the model memorizes training data but can't generalize), overly complex patterns learned for small or rare segments (the model captures patterns specific to a few training examples that won't recur), and performance that varies significantly across different random seeds or bootstrap samples.

Remediation for overfitting includes regularization techniques (L1/L2 penalties, dropout, early stopping) to control model complexity, simplifying the model architecture to reduce the number of learnable parameters, increasing training data to provide more examples for the model to learn generalizable patterns from, and ensemble methods that average across multiple models to smooth out individual model overfit.

In some cases, creating separate models for different population segments improves overall performance when a single model can't achieve adequate accuracy across all segments. Separate credit risk models for high-net-worth individuals and low-income borrowers may outperform a single model covering both populations.

Implementation tip: When outcome analysis reveals that overfitting is concentrated in a specific population segment, investigate whether the training data for that segment is sufficient before applying regularization. Regularization reduces overfitting by constraining model complexity, but it also reduces the model's ability to capture genuine patterns. If a segment contains only 200 training examples while other segments contain 20,000, the apparent overfitting may be a data sufficiency problem rather than a complexity problem. Adding more training data for the underrepresented segment may resolve the overfitting without sacrificing the model's ability to capture genuine patterns. Regularization applied uniformly across segments can underfit the data-rich segments while failing to adequately address overfitting in the data-poor segments. Segment-level diagnosis before segment-level remediation produces better outcomes than uniform regularization.

## Reliability Assessment and Robustness Against Input Noise

Outcome analysis must assess whether model outputs are reliable and whether the model is robust against the input noise present in real-world data.

Reliability assessment evaluates whether the model's predicted probabilities accurately reflect actual outcome frequencies. A model that assigns a 30% default probability should be correct approximately 30% of the time among all cases it scores at 30%. Calibration analysis (comparing predicted probabilities against actual outcome rates across probability bins) measures reliability. Poorly calibrated models produce probability estimates that can't be used directly for risk quantification, reserve calculation, or regulatory capital computation.

Robustness against input noise evaluates whether the model's predictions remain stable when inputs contain the measurement error, data entry mistakes, and natural variation present in production data. Real-world input data is noisier than the clean datasets used for model training. A model that produces dramatically different predictions when a single input feature changes by a small amount is brittle and unreliable for consequential decisions.

Robustness testing involves introducing controlled noise into input features (small random perturbations within realistic ranges) and measuring how much predictions change. A robust model produces predictions that change proportionally to input changes. A brittle model produces predictions that change dramatically in response to minor input variations.

Testing for benign overfitting evaluates whether apparent overfit in certain metrics actually causes harm in production performance. In some high-dimensional settings, models can achieve near-zero training error (apparent overfitting) while still generalizing well to new data. This phenomenon, called benign overfitting, needs to be distinguished from harmful overfitting through production performance monitoring.

Distribution drift testing evaluates whether the model remains accurate when the data distribution shifts over time. Credit risk models validated during stable economic periods may underperform during recessions, rate changes, or market disruptions. Regular comparison of production data distributions against training data distributions detects drift before it degrades predictions.

Implementation tip: Build robustness testing into your standard validation procedure rather than treating it as an optional additional test. For each model submitted for validation, introduce Gaussian noise at 1%, 3%, and 5% of each feature's standard deviation and measure prediction stability. Define an acceptable stability threshold: "Predictions should not change by more than X% when any single input feature is perturbed by up to Y% of its standard deviation." This threshold should be calibrated to the use case. A credit scoring model used for automated decisioning needs tighter stability requirements than a risk monitoring model used for portfolio-level reporting. Document the robustness test results in the validation report alongside accuracy and fairness metrics. Regulators increasingly expect evidence of robustness testing, and providing it proactively demonstrates mature model risk management practices.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/glowing-monitors-scene.png?w=771)

## Implementation Tips for Sound Modeling Practices

These principles apply across validation, explainability, optimization, and outcome analysis.

Implementation tip on documentation standards for regulated models: Every modeling decision should be documented with three elements: what was decided, why it was decided, and what alternatives were considered. "We used a gradient boosting model" is insufficient. "We evaluated logistic regression, random forest, gradient boosting, and a ReLU deep neural network. Gradient boosting outperformed logistic regression by 4.2 percentage points on AUC-ROC on the temporal holdout test set, while the ReLU network achieved 0.8 points higher but required 3x the inference time, exceeding our latency constraint. We selected gradient boosting as the best balance of performance and operability, with fANOVA constraints applied to maintain global interpretability." This documentation level satisfies regulatory reviewers who need to understand not just what the model is, but why it is.

Implementation tip on independent validation: The validation team should be independent from the development team, with no reporting relationship that could compromise their objectivity. Independent validation means: the validators did not participate in model design or development, they have access to their own holdout data that the development team never saw, they perform their own performance calculations rather than reviewing the development team's calculations, and they have the authority to reject the model. In many organizations, "independent validation" means a different person on the same team reviews the work. This is peer review, not independent validation. True independence requires organizational separation between model development and model validation functions.

Implementation tip on the relationship between sound modeling practices and model cards: Every element of sound modeling practice should be reflected in the model card. The validation methodology, out-of-sample test results, explainability analysis, stability test results, and outcome analysis findings should all be documented in or referenced from the model card. The model card serves as the single point of access for anyone needing to understand how the model was built, validated, and how it performs. A model card that documents only the model architecture and aggregate performance metrics without covering validation methodology, explainability approach, stability assessment, and identified weaknesses falls short of regulatory expectations and governance best practices.

Implementation tip on using specialized tooling: Toolboxes like PiML provide suites of model diagnostic tools for outcome analysis, including performance decomposition, weakness identification, and robustness testing. Using established, peer-reviewed tooling rather than custom diagnostic scripts provides two advantages: the tools have been validated by the research community, reducing the risk of diagnostic errors, and regulators are more likely to accept results from recognized tooling than from proprietary scripts whose correctness they can't independently verify. Document which tools were used for each diagnostic and cite the methodological references supporting them.

## Key References and Authoritative Frameworks

Your sound modeling practices should align with these established standards and methodological references:

- Federal Reserve SR 11-7, Guidance on Model Risk Management

- OCC Bulletin 2011-12, Sound Practices for Model Risk Management

- CFPB Circular 2022-03, Adverse Action Notification Requirements for Credit Decisions Based on Complex Algorithms

- CRD IV and EBA Guidelines on ML for IRB Models (European banking)

- Basel Committee on Banking Supervision, Principles for the Sound Management of Operational Risk

- ISO/IEC 42001:2023, AI Management System

- Friedman (2001), Partial Dependence Plots

- Apley and Zhu (2020), Accumulated Local Effects

- Lundberg and Lee (2017), SHAP (Shapley Additive Explanations)

- Ribeiro et al. (2016), LIME (Local Interpretable Model-Agnostic Explanations)

- Yang et al. (2020), Constructive Approach to Explainable Neural Networks

- Sudjianto and Zhang (2021), Practical Guide to Inherently Interpretable Machine Learning

- Sudjianto et al. (2023), PiML Toolbox for Model Diagnostics

- Lou et al. (2013), GA2M: Intelligible Models with Pairwise Interactions

- Ke et al. (2017), LightGBM

If you validate models using only aggregate accuracy metrics on random train-test splits, explain them using post-hoc tools without verifying explanation accuracy, optimize hyperparameters without testing stability, and skip outcome analysis that decomposes performance across population segments, you will deploy models that appear sound during development and fail under regulatory scrutiny, economic stress, or population shifts. The validation report will show strong numbers. The model will have weaknesses that those numbers concealed. And when a regulator asks why a specific applicant was denied credit and whether the explanation provided is accurate, the absence of rigorous modeling practices will become immediately apparent.

When you validate with temporal holdout and stress testing, explain through inherently interpretable architectures or verified post-hoc methods, verify stability through replication and seed variation, and decompose performance across every relevant segment and value range, you build models that withstand regulatory review because they were built to withstand it. The model's strengths are documented with evidence. Its weaknesses are identified with specificity. Its explanations are verified for accuracy. And its stability is tested under conditions that approximate the variability it will encounter in production.

A model that's accurate on average but unreliable in the segments where decisions matter most isn't a sound model. It's a sound model waiting to be found unsound.

Has your most critical regulated model been validated with temporal holdout testing across different economic conditions? If not, that validation gap is your highest priority.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
