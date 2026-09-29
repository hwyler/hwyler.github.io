---
title: "Implementation Tips for Expert Calibration and AI-Augmented Risk Estimation"
date: 2026-03-12
tags: 
  - "ai"
  - "artificial-intelligence"
  - "expert-calibration"
  - "expert-estimate-calibration"
  - "hernan-huwyler"
  - "iso-31000"
  - "llm"
  - "quantative-risk-management"
  - "risk-management"
  - "technology"
---

# Why Expert Calibration Matters for GRC Professionals

Most risk assessments rely on expert judgment. When historical loss data is absent, limited, or conflicting, you ask knowledgeable people to estimate probabilities and impacts. The problem is that unstructured expert judgment is unreliable. Experts overestimate rare events, underestimate common ones, anchor to previous numbers, and conform to dominant opinions in group settings.

Expert calibration is a quantitative technique that measures and improves the accuracy of expert predictions over time. It treats expert judgment as data, subject to the same scientific principles of review, critical appraisal, and repeatability that you'd apply to any other data source in your risk assessment.

The difference between a calibrated risk assessment and an uncalibrated one is the difference between a defensible estimate and an educated guess. Regulators, auditors, and boards increasingly expect the former.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/purposeful-stride-in-minimalist-setting.png?w=1024)

* * *

## The Core Mechanism: How Expert Calibration Works

### The Basic Cycle

Expert calibration follows a straightforward cycle. Ask experts to estimate potential losses or probabilities of events occurring. Compare actual outcomes to their estimates. Use multiple data points over time to determine whether an expert tends to overestimate or underestimate. Feed this information back to improve future estimates.

**How to implement:**

Group estimated probabilities into bands (for example, events the expert rated as 10-20% likely, 20-30% likely, and so on). Compare these bands to actual occurrence rates. A well-calibrated expert who assigns 20% probability to events should see roughly 20% of those events actually occur.

Calculate each expert's overall accuracy by averaging multiple estimates. A perfectly calibrated expert's estimates should, on average, match what you'd expect from a uniform distribution across probability bands.

Very low probability events present a challenge. If an expert estimates a 2% probability, you need 50 or more observations to determine whether 2% is accurate. For rare events, combine calibration data across similar event categories to build a sufficient sample.

**Original implementation tip:** Start building calibration histories now, even if you don't plan to use them for six months. Every time your organization conducts a risk assessment, record each expert's estimate alongside the question, the date, and eventually the actual outcome. Most organizations can't calibrate their experts because they never retained the historical estimates. They have last year's risk register but not the individual predictions that went into it. Store individual expert estimates in a structured database with fields for expert name, question, estimated probability, estimated impact range, date of estimate, and actual outcome when known. After 12 months of accumulation, you'll have enough data points to calculate meaningful calibration scores for your most active experts. Without this history, calibration is impossible and you're permanently stuck with uncalibrated judgment.

* * *

## Two Approaches to Aggregating Expert Opinions

### Behavioral Aggregation: The Workshop Method

Behavioral aggregation brings experts together in face-to-face meetings to reach shared judgment through discussion and consensus. Experts exchange and debate their knowledge, potentially producing more informed and balanced decisions.

This method is familiar. Most risk workshops use some version of it.

**The problem:**

Behavioral aggregation is vulnerable to well-documented biases. Group thinking causes experts to conform to the majority view even when they disagree. The halo effect allows a dominant expert's opinion to unduly influence others. Anchoring causes experts to gravitate toward the first number mentioned. Polarization can prevent consensus even with skilled facilitation. And forced consensus, when imposed despite genuine disagreement, masks important differences in opinion and reduces the quality of the final judgment.

**Original implementation tip:** If you must use behavioral aggregation, implement three structural safeguards. First, collect individual written estimates before any group discussion begins. This prevents anchoring to the first number spoken aloud. Second, give equal time to every expert, actively drawing out quiet participants and managing dominant voices. Third, never force consensus. If experts genuinely disagree after discussion, document the disagreement and the range of estimates rather than artificially converging on a single number. A documented range of expert opinion is more honest and more useful than a false consensus that nobody actually believes. I've facilitated dozens of risk workshops where the "consensus" estimate was the number the most senior person in the room stated first. Everyone else adjusted toward it. The estimate reflected hierarchy, not expertise.

### Algorithm Calibration: The Mathematical Method

Algorithm calibration limits expert interaction to training and briefing sessions. Consensus is not achieved through discussion but through mathematical aggregation of individual expert opinions.

This approach makes the aggregation process explicit and auditable. The Classical Model, developed by Roger Cooke, uses a linear combination of judgments weighted by each expert's past performance in estimating risk impacts and probabilities. Better-calibrated experts receive higher weights. Poorly calibrated experts receive lower weights or zero weight.

**The tradeoff:**

Algorithm calibration can be less effective when experts strongly disagree and receive little feedback from their peers. The mathematical aggregation may miss contextual nuances that discussion would surface. But it eliminates group biases entirely, produces reproducible results, and creates an auditable record of exactly how the final estimate was derived.

**Original implementation tip:** Use algorithm calibration as your primary method and behavioral discussion as a supplementary input. Collect individual estimates first using the structured elicitation protocol described below. Aggregate them mathematically using calibration weights. Then, if the weighted estimates show extreme divergence among high-weight experts, convene a focused discussion limited to understanding why those experts disagree. The discussion informs whether the divergence reflects genuine uncertainty (which should be preserved in the final estimate as a wider distribution) or a misunderstanding of the scenario (which should be corrected). This sequence, individual estimation first, mathematical aggregation second, targeted discussion third, captures the benefits of both approaches while minimizing the biases of each.

* * *

## Mathematical Aggregation Methods

### Bayesian Updating

Use each expert's opinion to update your existing knowledge about the risk. Start with a prior estimate based on historical data or organizational experience. Then adjust that estimate based on each expert's input, weighted by how confident you are in both your prior and in each expert's judgment.

**How to implement:**

Define your prior distribution based on available data. For each expert opinion, update the distribution using Bayes' theorem. The result is a posterior distribution that incorporates both your historical knowledge and the experts' collective judgment. Experts whose opinions align with strong historical evidence reinforce the estimate. Experts whose opinions diverge from historical patterns shift the estimate only if their track record or the strength of their reasoning justifies it.

**Original implementation tip:** The Bayesian approach works best when you have a meaningful prior, meaning real historical data to start from. If your prior is purely a guess, the Bayesian update is just averaging guesses with extra mathematical notation. Before choosing this method, honestly assess whether your prior distribution is based on data or assumption. If it's based on data, Bayesian updating is powerful. If it's based on assumption, opinion pooling or the Cooke method may be more appropriate because they don't pretend you have knowledge you don't have.

### Opinion Pooling (Weighted Average)

Assign each expert a specific weight reflecting their relative expertise and trustworthiness. Combine their opinions as a weighted average. The result is a blended estimate that reflects how much you value each expert's input.

The Cooke method is a specific form of opinion pooling where weights are determined empirically by each expert's past accuracy, not by subjective assessment of their credentials.

**How to implement:**

In the Cooke method, give more weight to experts who have been more accurate in the past, measured through calibration questions with known answers. Experts who consistently predict historical outcomes correctly receive higher weights. Experts who consistently miss receive lower weights or zero weight.

Calculate weights by scoring each expert's responses to calibration questions against known correct answers. The simplest scoring method assigns 1 for correct and 0 for incorrect, totals the scores, and converts them to percentages. More sophisticated scoring uses proper scoring rules that evaluate the full probability distribution each expert provides, not just point estimates.

**Original implementation tip:** The weight assignment step is where most implementations fail. Organizations resist giving zero weight to experts with impressive titles or seniority. But the entire point of calibration is that credentials don't guarantee accuracy. An expert with 20 years of experience who consistently overestimates by 300% should receive less weight than a junior analyst who consistently hits within 20% of actual outcomes. If you can't bring yourself to weight experts by demonstrated accuracy rather than organizational rank, don't use the Cooke method. You'll corrupt it by overriding the calibration data with political judgments, and the result will be worse than simple averaging because it will carry a false veneer of scientific rigor.

* * *

## The Structured Elicitation Protocol

### Step-by-Step Implementation

The structured elicitation protocol reduces biases and improves accuracy through a disciplined process. It treats expert judgments with the same rigor you'd apply to operational risk data.

**Phase 1: Preparation**

Identify relevant experts from various disciplines. Note that domain expertise doesn't guarantee unbiased or error-free judgment. Gather relevant information about the problem, including historical data, regulatory context, and comparable cases. Prepare easy-to-understand data presentations. Share information with attendees before the meeting so they arrive informed.

**How to implement:**

Select experts with diverse perspectives. For a GDPR fine estimation, you might include a data protection officer, a legal privacy advisor, a compliance officer, a privacy consultant, a head of compliance, and a head of data governance. Diversity of viewpoint is more valuable than depth in a single perspective.

Prepare calibration questions with known answers related to the risk domain experts will predict. These questions test each expert's accuracy before you ask them to estimate unknowns.

**Original implementation tip:** The quality of your calibration questions determines the quality of your entire process. Calibration questions must be from the same domain as the prediction you're asking experts to make, must have objectively verifiable correct answers, must span a range of difficulty levels, and must not be so obvious that every expert gets them right (which provides no differentiation). I typically prepare five to seven calibration questions per session. Three questions is the minimum for meaningful differentiation. Fewer than three doesn't provide enough signal to separate well-calibrated experts from lucky guessers. For the GDPR fine estimation case, calibration questions might ask about the most common fine amount, the 75th percentile fine, and the probability of exceeding a specific threshold, all based on published regulatory data that can be verified.

**Phase 2: Workshop Opening**

Explain the workshop objectives and outline the problem structure and key uncertainties. Emphasize that exact probability knowledge isn't required. Highlight how distributions allow for uncertainty expression. Present prepared data and information, encouraging open dialogue about variability and uncertainty. Discuss the logical structure and potential correlations, exploring scenarios that could lead to extreme outcomes.

**Original implementation tip:** Spend at least 20 minutes on training experts to think in distributions rather than point estimates. Most professionals are trained to give single numbers: "the fine will be €100,000." Calibrated estimation requires ranges: "I'm 90% confident the fine will fall between €30,000 and €400,000." This is a skill that must be taught. Use a simple warm-up exercise: ask experts to estimate something they can verify immediately, like the distance between two cities or the population of a country, as a 90% confidence interval. Then reveal the answer. Most people's first confidence intervals are far too narrow, capturing the true answer less than 50% of the time instead of 90%. This exercise demonstrates overconfidence viscerally and motivates experts to widen their ranges appropriately. Run this exercise at the start of every calibration session.

**Phase 3: Workshop Facilitation**

Encourage experts to develop their own opinions based on group discussion, giving equal prominence to quiet and dominating experts. Allow time for private consideration and explanation of parameter uncertainty. Emphasize that distributions don't require more knowledge than point estimates.

**Phase 4: Individual Estimations**

Conduct one-on-one interviews with each expert using three-point estimates: minimum (best case), most likely, and maximum (worst case). Gather individual estimates without group influence.

**How to implement:**

The three-point estimate captures the expert's uncertainty range. The minimum represents the lowest plausible outcome. The most likely represents the mode of their mental distribution. The maximum represents the highest plausible outcome. These three points can be fitted to a distribution (triangular, PERT, or beta) for further analysis.

Collect estimates individually to prevent anchoring and conformity bias. Even after a group discussion phase, the actual numerical estimates must be provided privately.

**Original implementation tip:** When collecting three-point estimates, ask for the minimum and maximum first, then the most likely value. If you ask for the most likely value first, experts anchor to it and set their minimum and maximum too close, producing artificially narrow ranges. By asking for extremes first, you force the expert to think about what could go wrong (maximum) and what the best realistic outcome looks like (minimum) before settling on their central estimate. This simple sequencing change consistently produces wider, more realistic ranges. I've tested both sequences with the same expert groups and the extremes-first approach produces ranges that are 30 to 50% wider, which better reflects genuine uncertainty.

**Phase 5: Calibration Feedback**

Compare past estimates to actual outcomes to assess biases or patterns. Identify experts who consistently estimate accurately. Identify large differences in expert opinions and reconvene if necessary to discuss discrepancies. Provide feedback on estimation performance and discuss techniques for improving future estimates.

**Phase 6: Consensus Building**

Facilitate a discussion to reach a shared understanding of risks and uncertainties, avoiding forced agreement on specific numbers. Summarize key points and insights. Outline next steps for using the gathered information in the risk analysis.

**Phase 7: Follow-Up**

Document workshop outcomes and distribute results to participants. Plan for future calibration sessions to track improvement over time. Allow for estimate revisions as new information becomes available.

**Original implementation tip:** The follow-up phase is where most organizations drop the ball. They conduct the workshop, produce the aggregated estimate, use it in the risk assessment, and never revisit it. Without follow-up, there's no learning. Schedule a calibration review six months and twelve months after each session. At the review, compare the aggregated estimate to any actual outcomes that have materialized. Update expert calibration scores. Share the results with the experts. Over time, this feedback loop demonstrably improves estimation accuracy. The Good Judgment Project documented that calibration feedback improved forecasting accuracy by 10 to 15% within the first year. Without feedback, accuracy stays flat or degrades. The feedback loop is what transforms expert judgment from a static input into an improving instrument.

* * *

## Case Study: Estimating GDPR Fines for a Spanish Bank

### Step 1: Gather Historical Data for Calibration

Before asking experts to estimate anything, gather objective data to calibrate their accuracy and provide context.

For GDPR fines related to processing personal data without legal grounds (Article 6(1)) in Spain over the past two years, the data shows 87 fines ranging from €240 to €1,200,000 with a mean of €72,941, a median of €20,000, and a mode of €10,000 (appearing 8 times). The standard deviation of €154,431 indicates a wide spread. The 25th percentile is €6,000, the 75th percentile is €70,000, and the 90th percentile is €200,000. Banking sector fines tend to be higher: €1,200,000, €200,000, and €70,000.

**Original implementation tip:** The statistical analysis of historical data serves two purposes. First, it provides the correct answers for calibration questions. Second, it gives experts an empirical foundation for their estimates. Share the summary statistics with experts before the session. Don't hide the data to "test" their knowledge. The goal isn't to trick experts. It's to produce the most accurate possible estimate of future fines. Informed experts produce better estimates than uninformed ones. However, share the summary statistics, not the raw dataset. Experts who review 87 individual fine records will anchor to memorable outliers. Experts who see percentile distributions develop more balanced mental models. Present the data as distributions and percentiles, not as a list of cases.

### Step 2: Design Calibration Questions

Prepare calibration questions based on the known statistics. Each question has a correct answer derived from the historical data.

**Question 1:** What is the most likely (mode) fine for processing personal data without legal grounds in Spain? Options: €10,000 / €70,000 / €200,000 / €1,200,000. Correct answer: €10,000.

**Question 2:** What do you estimate as the 75th percentile fine for GDPR violations related to insufficient legal grounds? Options: €20,000 / €70,000 / €200,000 / €500,000. Correct answer: €70,000.

**Question 3:** What is the probability a fine will exceed €200,000 for violating Article 6(1) GDPR? Options: 0-10% / 11-30% / 31-50% / 51-70% / 71-90% / 91-100%. Correct answer: 0-10% (the 90th percentile is €200,000, so approximately 10% of fines exceed this level).

**Original implementation tip:** Design calibration questions that test different aspects of the expert's understanding: central tendency (mode or median), distribution shape (percentiles), and tail risk (probability of exceeding a threshold). An expert who correctly identifies the most common fine but overestimates tail risk has a specific bias pattern that the calibration can address. An expert who gets the percentiles right but misidentifies the mode has a different pattern. Three well-designed questions that test different distribution characteristics provide more differentiation than ten questions that all test the same type of knowledge. Also, use multiple-choice format for calibration questions rather than open-ended responses. Open-ended responses are harder to score consistently and create ambiguity about whether a "close" answer should receive partial credit.

### Step 3: Collect Expert Responses

Six experts across different roles respond to the three calibration questions. Their responses are compared to the correct answers.

The Data Processing Officer answers €10,000 (correct), €200,000 (incorrect), 0-10% (correct). The Legal Privacy Advisor answers €70,000 (incorrect), €200,000 (incorrect), 0-10% (correct). The Compliance Officer answers €10,000 (correct), €70,000 (correct), 0-10% (correct). The Privacy Consultant answers €200,000 (incorrect), €500,000 (incorrect), 11-30% (incorrect). The Head of Compliance answers €70,000 (incorrect), €70,000 (correct), 0-10% (correct). The Head of Data Governance answers €70,000 (incorrect), €200,000 (incorrect), 31-50% (incorrect).

**Original implementation tip:** Notice that the Compliance Officer scored 100% on calibration questions while the Privacy Consultant and Head of Data Governance scored 0%. This is a common pattern. Domain expertise and seniority don't predict calibration accuracy. The Privacy Consultant may have deep knowledge of privacy law but poor calibration on quantitative estimates. The Head of Data Governance may understand data governance frameworks but have no feel for regulatory penalty distributions. The Cooke method handles this elegantly by assigning zero weight to experts who demonstrate poor calibration, regardless of their title. The hardest part of implementation is presenting these results to the experts themselves. Do it with transparency and respect. Frame it as "calibration accuracy for this specific question set" rather than "you don't know what you're talking about." Calibration scores measure estimation skill, not domain knowledge. A poorly calibrated expert may still contribute valuable qualitative insights during the discussion phase.

### Step 4: Assign Weights Based on Calibration Performance

Score each expert's responses (1 for correct, 0 for incorrect) and calculate calibration weights.

The Data Processing Officer scores 2 out of 3 (67%), assigned weight 25%. The Legal Privacy Advisor scores 1 out of 3 (33%), assigned weight 12%. The Compliance Officer scores 3 out of 3 (100%), assigned weight 37%. The Privacy Consultant scores 0 out of 3 (0%), assigned weight 0%. The Head of Compliance scores 2 out of 3 (67%), assigned weight 25%. The Head of Data Governance scores 0 out of 3 (0%), assigned weight 0%.

Assigned weights are calculated by dividing each expert's percentage by the total of all non-zero percentages (267%), producing the final weight distribution.

**Original implementation tip:** The weight calculation is simple arithmetic, but its implications are profound. Two of six experts receive zero weight. Their estimates will not influence the final aggregated prediction at all. In a traditional workshop, these two experts would have equal voice with everyone else, potentially pulling the estimate toward their incorrect mental models. The Cooke method eliminates this influence mathematically. When presenting the methodology to stakeholders, emphasize that zero weight doesn't mean the expert's opinion is worthless. It means their quantitative estimation accuracy, as measured by the calibration questions, doesn't support giving their numerical estimates influence over the final aggregate. They can still contribute qualitative context during discussions. But when it comes to the number, calibrated experts drive the result.

### Step 5: Aggregate the Weighted Responses

Multiply each expert's estimate by their assigned weight and sum the results.

Using the calibration question responses for the most common fine, the aggregated estimate is €32,472. This is significantly lower than a simple average of €71,667 because the two experts who estimated high values (Privacy Consultant at €200,000 and Head of Data Governance at €70,000) received zero weight.

For a more accurate bank-specific estimate, ask experts to provide a revised estimate for the specific bank scenario. The aggregated bank-specific estimate is €106,236, driven primarily by the Compliance Officer (37% weight, €100,000 estimate) and the Head of Compliance (25% weight, €150,000 estimate).

**Original implementation tip:** Always collect both a general estimate and a scenario-specific estimate. The general estimate calibrated against historical data tells you how accurate each expert is at reading the base rate. The scenario-specific estimate applies their judgment to the actual case you care about, weighted by their demonstrated accuracy. The general estimate acts as a sanity check. If the scenario-specific aggregated estimate is dramatically different from the historical base rate, you need to understand why. In this case, the bank-specific estimate of €106,236 is higher than the general most-common estimate of €32,472 because experts appropriately adjusted for the banking sector's higher fine profile. That's a reasonable, explainable deviation. If the bank-specific estimate were €5,000,000, you'd need to investigate whether the experts are incorporating genuine sector-specific factors or simply overreacting to headline cases.

* * *

## Using AI as Expert Estimators

### The Method

Large language models can serve as additional "experts" in the calibration process. The approach treats each LLM as an independent estimator whose predictions are weighted by demonstrated accuracy, just like human experts.

**How to implement:**

Use multiple LLMs with diverse training data to estimate potential fines or impacts. Develop standardized prompts that provide consistent information about the risk scenario, relevant regulations, historical data, and the required output format. Calibrate LLM outputs using the same Cooke method applied to human experts: test them against known historical data and assign weights based on accuracy. Combine predictions from multiple LLMs using weighted averaging.

The prompt structure should specify the role the LLM should adopt (such as a Data Protection Officer at a financial institution), the specific regulation and article at issue, the three scenarios to estimate (best case, most common, worst case), the factors to consider (severity, intent, cooperation, mitigation actions), and the requirement to reference historical cases and regulatory guidelines.

**Original implementation tip:** The prompt design is critical. Inconsistent prompts across LLMs make comparison meaningless. Build a standardized prompt template that you use identically across all models. The template should include the exact same scenario description, the exact same historical context, and the exact same output format requirements. The only variable should be the LLM itself. I structure prompts with four sections: role definition, scenario description with specific regulatory context, action steps specifying the required outputs, and outcome expectations specifying the format and evidence requirements. Test the prompt on one model first to verify it produces the expected output structure. Then deploy it across all models simultaneously.

### Calibrating AI Estimates Against Reality

In the GDPR fine case study, five LLMs produced dramatically different estimates for the most common fine.

Llama estimated €200,000. Claude estimated €400,000. Mistral estimated €3,000,000. Gemini estimated €220,000. GPT-4o estimated €60,000.

When calibrated against the actual most common fine of €10,000, GPT-4o was closest (still off by a factor of six), while Mistral was off by a factor of 300.

Using the Cooke method, each LLM's responses were scored against known historical data (best case, most common, worst case). Claude-3.5-sonnet achieved the best calibration (50% assigned weight) because its estimates had the lowest total absolute error percentage. Mistral received 32% weight. Llama received 9%. Gemini received 8%. GPT-4o received only 3% weight despite having the most accurate most-common estimate, because its best-case and worst-case estimates were significantly off.

The aggregated AI estimate for the bank-specific scenario was €1,182,291, compared to the human expert estimate of €106,236.

**Original implementation tip:** The AI estimates in this case were dramatically higher than human expert estimates, with the AI aggregate more than 10x the human aggregate. This divergence itself is valuable information. It suggests either that LLMs are poorly calibrated for regulatory fine estimation in specific jurisdictions (likely, given their training data includes global cases that may skew distributions upward), or that human experts are underestimating tail risk and the LLMs are capturing something the humans miss, or that the LLMs are anchoring to the maximum possible fine under GDPR (4% of global turnover or €20 million) rather than to actual enforcement patterns in Spain. Don't automatically prefer the human estimate or the AI estimate. Investigate the divergence. In this case, the historical data strongly supports the human estimate range: the actual 90th percentile of Spanish GDPR fines is €200,000, making an aggregate estimate above €1 million an outlier relative to enforcement history. The AI models appear to be poorly calibrated for jurisdiction-specific fine estimation. Document this finding and adjust your methodology accordingly.

### When to Use AI Estimators

AI estimation is most valuable when you need rapid preliminary estimates across many scenarios before investing in human expert time, when you want to identify the range of plausible outcomes to inform your calibration question design, when you're looking for scenarios or factors that your human experts might not have considered, and when you want to stress-test human estimates by comparing them to an independent source.

AI estimation is least reliable when jurisdiction-specific enforcement patterns differ significantly from global averages (as in the Spain case), when the scenario involves novel regulatory frameworks with limited enforcement history, when contextual factors (organizational size, cooperation level, remediation speed) heavily influence outcomes, and when you need defensible estimates for regulatory or board reporting.

**Original implementation tip:** Use AI estimates as one input to your calibration process, not as a replacement for it. Include LLM estimates alongside human expert estimates in your aggregation. Apply the same Cooke method to assign weights based on calibration accuracy. In the Spain GDPR case, the AI estimates would receive low aggregate weight because their calibration accuracy was poor relative to the human experts. In a domain where LLMs demonstrate better calibration, perhaps because there's more training data or less jurisdiction-specific variation, they might receive higher weight. Let the calibration data determine the weighting, not your assumptions about whether humans or machines are "better." The Cooke method doesn't care whether the estimator is human or artificial. It cares whether the estimator is accurate.

* * *

## Building a Repeatable Calibration Program

### Institutional Calibration Infrastructure

Individual calibration sessions are valuable. A sustained calibration program is transformative.

**How to implement:**

Maintain a calibration database that records every expert's estimates, every calibration question and correct answer, every weight assignment, every aggregated result, and every actual outcome when it materializes.

Track each expert's calibration score over time. Identify experts who are improving (the feedback loop is working) and those who aren't (they may need additional training or should receive lower weights).

Build a library of calibration questions organized by risk domain: regulatory fines, cybersecurity incidents, operational losses, project overruns, market events. As you accumulate questions with known answers, your calibration testing becomes more robust and differentiated.

Schedule calibration sessions quarterly for your most critical risk domains. Use shorter calibration exercises (three to five questions) as part of regular risk committee meetings to keep estimation skills sharp.

**Original implementation tip:** Measure and report your organization's aggregate calibration improvement over time. If you're running quarterly sessions with calibration feedback, your expert pool's average accuracy should improve measurably within 12 months. Track two metrics. First, the average Brier score across all experts and all questions, which should decrease over time (lower is more accurate). Second, the percentage of experts whose 90% confidence intervals actually contain the true outcome 90% of the time, which should approach 90% from below as calibration training takes effect. Present these metrics to the risk committee as evidence that your risk assessment process is improving in measurable, auditable terms. This is how you move from "we think our risk estimates are reasonable" to "we can demonstrate that our estimation accuracy has improved by X% over the past four quarters." The second statement is what boards and regulators want to hear.

### Brier Scores for Ongoing Accuracy Tracking

A Brier score measures the accuracy of probabilistic predictions. It ranges from 0 (perfect accuracy) to 1 (complete inaccuracy). For each prediction, the Brier score is calculated as the squared difference between the predicted probability and the actual outcome (1 if the event occurred, 0 if it didn't).

**How to implement:**

For each expert's probability estimate, record the predicted probability and the actual outcome. Calculate the Brier score for each prediction. Average Brier scores across multiple predictions to get each expert's overall accuracy metric.

Use Brier scores as an alternative or supplement to the simple correct/incorrect scoring used in the Cooke method. Brier scores capture nuance that binary scoring misses: an expert who assigns 80% probability to an event that occurs is more accurate than one who assigns 51%, even though both would be scored as "correct" under binary scoring.

**Original implementation tip:** Report Brier scores to experts individually and confidentially. Show them how their score compares to the group average without identifying other experts. Competitive benchmarking against an anonymous group average motivates improvement more effectively than abstract accuracy metrics. Frame it as a professional development tool: "Your Brier score this quarter was 0.21 versus the group average of 0.18. Here are the questions where your estimates diverged most from outcomes." This is the same feedback mechanism that the Good Judgment Project used to develop superforecasters. It works because it provides specific, measurable, actionable feedback tied to actual outcomes, which is exactly what most professional development programs lack.

* * *

## Common Implementation Failures and How to Avoid Them

**Failure: Skipping calibration and going straight to estimation.** Without calibration questions, you have no basis for weighting experts. Every expert gets equal weight, which means poorly calibrated experts have as much influence as accurate ones. Always include calibration questions, even if you only have three.

**Failure: Using the same experts for every assessment.** Expert fatigue reduces accuracy over time. Rotate experts across sessions. Bring in fresh perspectives. Maintain a pool of qualified experts for each domain rather than relying on the same three people for every risk assessment.

**Failure: Not providing feedback.** Calibration without feedback is just measurement. Feedback is what drives improvement. Share calibration results with experts after every session. Show them where they were accurate and where they weren't. Discuss techniques for improving (widening confidence intervals, adjusting for known biases, considering base rates before estimating).

**Failure: Treating the aggregated estimate as a point value.** The Cooke method produces a weighted point estimate, but the underlying expert distributions contain information about uncertainty. Report the aggregated estimate as a distribution (using the three-point estimates from each expert, weighted by calibration scores) rather than as a single number. A single number implies false precision.

**Failure: Allowing political override of calibration weights.** When a senior executive receives zero weight because their calibration accuracy was poor, organizational pressure to "adjust" the weights is inevitable. Resist this. Document the calibration methodology before the session and commit to applying it without modification. If you allow political overrides, you've destroyed the method's value and you're back to hierarchy-driven estimation with extra steps.

**Original implementation tip:** Build the calibration methodology into a formal procedure document that your risk committee approves before the first session. The document should specify how calibration questions are selected, how scoring works, how weights are calculated, and that weights are applied mathematically without subjective adjustment. Get this approval once. Then reference it every time someone challenges the weights. The pre-approved procedure document prevents ad hoc political interventions because overriding the weights now requires overriding a committee-approved methodology, which creates its own accountability.

* * *

## Integrating Calibrated Estimates Into Your Risk Framework

### Connecting to Enterprise Risk Management

Calibrated expert estimates should feed directly into your quantitative risk assessment process, not sit in a separate workstream.

**How to implement:**

Use the three-point estimates from calibrated experts to parameterize loss distributions in your risk models. The weighted minimum, most likely, and maximum values define a PERT or triangular distribution that can be input to Monte Carlo simulations.

Report calibrated estimates alongside their uncertainty ranges. The board shouldn't see "€106,236." They should see "€106,236 weighted mean estimate from calibrated experts, with a 90% range of €40,000 to €300,000 based on the distribution of individual estimates."

Track the accuracy of your calibrated estimates against actual outcomes and report the tracking results to the risk committee. This creates a continuous improvement loop that raises confidence in your risk assessment process over time.

**Original implementation tip:** When presenting calibrated estimates to the board, lead with the methodology's credibility, not just the number. Explain that the estimate comes from X experts whose accuracy was tested against Y calibration questions with known answers, that experts were weighted by demonstrated accuracy, and that the method is based on the Cooke Classical Model used by regulators and international agencies for structured expert judgment. This framing differentiates your estimate from the typical "we asked some people and averaged their guesses" approach. Boards increasingly expect quantitative rigor in risk assessment. Calibrated expert judgment, properly documented, meets that expectation. Uncalibrated workshop consensus does not.

* * *

## Key References

**Expert Calibration Methods:**

- Cooke, R.M. (1991). "Experts in Uncertainty: Opinion and Subjective Probability in Science." Oxford University Press.

- Tetlock, P.E. (2015). "Superforecasting: The Art and Science of Prediction." Crown Publishers.

- Kahneman, D. (2011). "Thinking, Fast and Slow." Farrar, Straus and Giroux.

**Structured Expert Judgment:**

- OECD/NRC (2018). "Expert Judgement in Risk and Decision Analysis." (Guidance on the Cooke Classical Model)

- European Food Safety Authority (EFSA) guidance on expert knowledge elicitation (2014, updated 2019)

**Scoring and Accuracy:**

- Brier, G.W. (1950). "Verification of Forecasts Expressed in Terms of Probability." Monthly Weather Review.

- Good Judgment Project documentation (goodjudgment.com)

**AI Risk Estimation:**

- NIST AI RMF 1.0 (2023), Measure function

- ISO/IEC 23894:2023 (AI Risk Management)

**Regulatory Data:**

- AEPD (Agencia Española de Protección de Datos) enforcement decisions database

- GDPR Enforcement Tracker (enforcementtracker.com) for cross-jurisdictional fine data

- EU AI Act, Regulation (EU) 2024/1689, Article 99 (penalties)

* * *

The organizations that treat expert judgment as data, measure its accuracy, and improve it over time will consistently produce better risk estimates than those relying on unstructured workshops and colorful matrices.

The math isn't complex. The discipline is. Calibration requires admitting that credentials don't guarantee accuracy, that feedback is essential for improvement, and that mathematical aggregation produces more defensible results than consensus driven by hierarchy.

The choice between calibrated estimation and uncalibrated guessing is the choice between a risk function that can demonstrate its value quantitatively and one that relies on institutional trust to justify its existence. In an environment where regulators, auditors, and boards increasingly demand evidence, only one of those approaches survives scrutiny.
