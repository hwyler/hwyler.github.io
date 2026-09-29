---
title: "Data Quality Requirements That Decide Whether Your AI Ships or Sinks"
date: 2026-08-14
tags: 
  - "ai"
  - "ai-controls"
  - "ai-data"
  - "ai-development"
  - "ai-training"
  - "ai-training-data"
  - "artificial-intelligence"
  - "chatgpt"
  - "hernan-huwyler"
  - "iso-19157"
  - "iso-42001"
  - "iso-5259"
  - "llm"
  - "technology"
---

The validation accuracy means nothing if the training data is broken. I reviewed a production model with 92% validation accuracy. Training data passed schema checks at more than 99%. The missing percent covered one geography, one device type, and one age group. The model had never seen those records. Average quality scores lied to us.

This article gives you the complete framework: 10 concrete data quality requirements drawn from ISO 5259, ISO 42001, ISO 19157, and NIST guidance. Each requirement includes the controls, metrics, and validation tests that disciplined AI teams run before a single model trains. You will also see exactly where hard gates replace aggregate scores, and why that distinction is the difference between a model that holds up and one that quietly degrades. That distinction saves production systems.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/d6d31621-0966-4be5-8ec1-274cfd3fe968.png?w=1024)

## The Data Quality Contract Covers Four Stages

Your model inherits every defect in the data it touches. That includes data you never directly inspect. Training data shapes learning. Validation data shapes your confidence. Feedback data shapes future updates. Production usage data determines what actually happens after deployment.

Treat these four stages as separate contract areas. One dataset can pass a training check and still destroy a production model. Each stage has its own failure modes, its own controls, and its own owner. Confusing them is how governance failures slip through.

### Training data

Training data is the set of examples, features, and labels used to teach the model. It must be correct, complete, representative, and free of leakage.

My first rule is deduplication before splitting. Never do it afterward. Duplicate records crossing train and test boundaries create inflated scores. Use group-aware splits so all records from one customer, patient, device, household, author, or organization stay in the same split. A group-aware split forces the model to generalize to new entities rather than memorize familiar ones. If every user in your test set also appears in your training set, your offline evaluation is measuring memorization, not generalization.

The second rule is leakage detection. A feature derived from information available after the prediction timestamp will produce outstanding offline accuracy and catastrophic production failure. Random splits conceal this problem entirely. Use time-based splits where deployment involves future cases. For a model intended to predict next-day equipment failure, do not include maintenance records created after the prediction timestamp, even if those records improve offline accuracy. Build a leakage review into your feature documentation process. The dangerous leaks are subtle: a field updated at the time of outcome recording, a derived feature that aggregates future events, or an identifier that correlates with outcome because of how data was collected.

My third role is about representativeness. Draw from a wide range of sources spanning different patterns, perspectives, and scenarios. Use stratified splits so rare classes and important subgroups appear in training with sufficient volume to measure. Do not assume demographic balance proves fairness. Some operational datasets should not mirror population proportions. A model trained to detect rare equipment failures should oversample failure cases, not mirror the natural ninety-nine to one imbalance. Document why your target distribution is appropriate. That justification is both a governance artifact and a defense against audit challenge.

Label quality deserves its own controls. Record who produced or reviewed each label, when they were created, and which labeling guideline version was active. Use a holdout audit sample that annotators never see during preparation. Double-label a statistically justified sample and calculate inter-annotator agreement using Cohen's kappa or Fleiss' kappa. Require independent adjudication for any disputed label. Skipping this audit sample because it feels expensive leads to discovering systematic labeling errors after deployment and spending three times as long rebuilding.

### Validation and test data

Validation and test data measure performance. They must remain independent from training data and cover the same subgroups, edge cases, and failure modes the system will face.

The first rule is independence. Check for train-test overlap before you trust any score. For language or image models, near-duplicate examples in the test set produce artificially high evaluation scores even when the model has poor generalization. Hash-normalize records to catch exact duplicates. Use similarity matching, MinHash, or embedding similarity to catch near-duplicates. Investigate data augmentation that creates near-duplicates in the test set.

The second rule is temporal validity. Use time-based splits when deployment involves future cases. Random splits leak future information into training and hide the exact drift that will appear in production. A high validation score from a random split gives false confidence. Use group-based splits where deployment involves new users, new sites, new organizations, or new devices. If every user in your test set also appears in your training set, you are measuring memorization.

The third rule is subgroup coverage. A model can achieve ninety-two percent accuracy overall while performing at sixty-eight percent for a specific subgroup. That gap will not appear in any aggregate metric. Test intersectional groups where sample sizes permit. Age crossed with gender crossed with region can reveal failure modes that are invisible in single-dimension analysis. Evaluate model outcomes separately by group, subgroup, and intersection. Publish accuracy, false-positive rate, false-negative rate, and calibration separately for each subgroup.

Build a challenge set from known incidents, complaints, adversarial examples, and expert-defined edge cases. Your standard test set reflects what happened. Your challenge set reflects what can happen. A model that passes the standard test set but fails the challenge set is not ready for production.

### Feedback data

Feedback data includes user corrections, thumb ratings, complaint logs, production labels, and reviewer decisions. It is often dirty, unaudited, and adversarial.

Treat feedback as untrusted production input. Scan it for secrets, personal data, prompt injection, and toxic content before any reuse. User inputs can contain prompt injection attempts, personally identifiable information, credentials, and malicious content. None of that should enter a retraining pipeline unsanitized. Feedback pipelines are a significant attack surface. A single poisoned feedback item can corrupt an entire retraining cycle.

Link every feedback item to the model version that generated the output, the specific input, the reviewer decision, and the final disposition. Feedback that cannot be traced to a model version cannot be used to evaluate that model or to construct valid retraining data. Without this linkage, you cannot distinguish between feedback that applies to the old model and feedback that applies to the new one.

Separate feedback stores from raw data stores. The risk profile of user-generated feedback is fundamentally different from the risk profile of a curated training dataset. Apply purpose limitation. Feedback collected for one model should not automatically flow into another model's training pipeline without explicit review.

### Production or usage data

Production data is what the model receives at inference time. It may drift, fail schema checks, arrive late, or contain out-of-domain inputs.

Compare production input distributions to the training baseline at least weekly. One distribution shift alert matters more than a quarterly aggregate accuracy report. Use Population Stability Index, [Jensen-Shannon divergence,](https://infomeasure.readthedocs.io/en/0.5.0/guide/JSD/) or Wasserstein distance to measure drift. Set retraining or review triggers when drift persists across multiple periods, not just when a single batch looks unusual. A single unusual batch may be noise. Sustained drift means your training distribution and production distribution have separated.

Store event time and processing time separately. Confusing them hides late-arriving data. If your pipeline processes a transaction at 14:00 that occurred at 08:00, the six-hour gap is only visible if you captured both timestamps. Test late-arriving, duplicated, out-of-order, and replayed events explicitly. These are the failure modes that stress-test assumptions baked into most feature engineering pipelines.

Monitor out-of-domain inputs. Use applicability-domain or embedding-distance checks to detect unfamiliar inputs that fall outside the distribution the model was trained on. A model deployed in a new geography or on a new device type may receive inputs it has never seen. Detecting that shift before it produces bad decisions is the difference between a controlled rollout and a production incident.

Keep production data stores separate from training stores. Do not allow a single access control policy to govern both. Production data often contains live sensitive information. Training data should be a governed snapshot with purpose limitations applied. The separation also prevents accidental feedback loops where production outputs get reused as training inputs without the required screening and version linkage.

Each stage has its own minimum validation focus. Training data requires accuracy, completeness, representativeness, leakage detection, deduplication, label quality, privacy controls, and lineage coverage. Validation and test data require independence, subgroup coverage, stable labels, temporal validity, and contamination checks. Feedback data requires authenticity, authorization, injection screening, label confidence, reviewer agreement, and version linkage. Production data requires schema validity, freshness, drift detection, out-of-domain detection, access control, and incident tracking. Running the same generic test suite across all four stages is how quality gates become theater.

## The AI Data Requirements

Industry data readiness frameworks often organize quality around six factors: diversity, timeliness, accuracy, security, discoverability, and consumability. Those factors map directly to the ten requirements below. Representativeness and relevance cover diversity. Timeliness and currentness cover freshness. Accuracy, completeness, and validity cover correctness. Security and compliance cover protection. Traceability and lineage cover discoverability. Consistency and relevance cover consumability.

The requirements below are ordered by how frequently they cause production failures, not by how often they appear in governance documents.

* * *

### 1\. Accuracy

Accuracy from algorrithmic training, validation and usage data means values, labels, and annotations correctly represent reality or an authoritative reference. Errors here propagate directly into every prediction the model makes. A credit model trained on mislabeled repayment outcomes learns to approve the wrong borrowers. A medical imaging system trained on incorrect diagnoses becomes dangerous at exactly the moment clinicians trust it most.

Measurement accuracy and label accuracy are different problems that require different controls. A dataset can contain correct sensor readings with wrong class labels attached to every record. A medical imaging dataset can have pixel-perfect scans with incorrect diagnoses. Treating accuracy as a single dimension means you catch one failure mode while missing the other entirely.

Data scientists should profile source data before any other quality check. Exploratory data analysis reveals characteristics, completeness, distribution, redundancy, and shape that aggregate quality scores hide. Build data quality rules from that profiling and monitor their efficacy continuously. Do not profile once at project start and assume the source system holds constant.

Define tolerances by use case before you profile anything. A two-percent rounding error is acceptable in demand forecasting. That same error is not acceptable in a drug dosage recommendation system or a financial reporting model subject to regulatory audit. Write the tolerance down. Make it part of your data quality gate so it cannot be overridden informally when timelines compress.

The annotation process needs governance separate from technical validation. Record who produced or reviewed each label, when they created it, and which labeling guideline version was active at that time. Without that provenance, you cannot audit a disputed prediction or trace a labeling error back to its source. When a regulator asks which annotator produced a specific label, "we used a crowdsourcing platform" is not an acceptable answer.

Use a holdout audit sample that annotators never see during data preparation. Double-label a statistically justified sample of records. Calculate inter-annotator agreement using Cohen's kappa or Fleiss' kappa. Require independent adjudication for any label where agreement falls below your defined threshold. The adjudication audit sample feels expensive until you discover a systematic labeling error after deployment and spend three times as long rebuilding the dataset from scratch.

Enable lineage and impact analysis so data engineers and scientists can see the downstream consequences of changes before they happen. When a source system changes a field definition, you need to know immediately which models depend on it, not six months later when performance unexpectedly shifts.

For a classifier, one acceptance rule is: at least 98 percent of critical labels must agree with adjudicated expert labels, with no high-severity label error remaining unresolved. The specific percentage depends on your use case and risk profile. What cannot vary is having the rule written down and enforced at the gate, not estimated after training.

* * *

### 2\. Completeness

Completeness measures whether all required records, fields, labels, time periods, and classes are present. Missing data is not a neutral condition. Absence is information, but it is information you did not plan to use. Missing values skew distributions, distort feature importance, and bias model behavior toward the populations and scenarios where data happened to be collected. The model learns what was measured, not what matters.

The most dangerous completeness failure is concentrated missingness, not distributed missingness. A five percent missing rate overall sounds manageable. A five percent missing rate concentrated entirely within a specific demographic group, geography, or outcome class is a bias problem disguised as a data quality score. Your completeness metrics must break down by subgroup, source, and time period, not just by field and dataset.

Set stricter thresholds for critical fields than for optional ones. Zero tolerance for missing mandatory identifiers and labels is a reasonable hard gate. A documented, bounded missingness rate for noncritical features is acceptable when the missingness mechanism is understood and recorded. Undocumented missingness is never acceptable, regardless of the rate.

Imputation does not eliminate the problem. When you fill a missing value, retain an indicator flag showing the value was imputed. That flag is itself a feature the model can use and a governance artifact showing you acknowledged the gap. Imputing without flagging hides the extent of the problem from downstream consumers of the data.

Measure completeness separately for training, validation, test, feedback, and production data. An aggregate completeness score across all four stages hides the fact that your minority class in the test set might have fifty percent label coverage while your majority class has ninety-eight percent. That imbalance will not show in any headline number.

Investigate records that appear complete but contain default values. Zero, "unknown," "N/A", and the Unix epoch date 1970-01-01 are common proxies for missing data that pass completeness checks while carrying no real signal. These records inflate your completeness rate while quietly degrading your model.

Reconcile dataset counts with source system counts and event logs. If your pipeline received 1.2 million records and your source system logged 1.4 million events, that gap is not a rounding difference. It is a completeness failure with a specific cause that needs investigation before you train on anything.

A typical data quality gate requires zero missing values for mandatory identifiers and labels, while allowing a documented, bounded rate of missingness in noncritical features. The key word is documented. Undocumented gaps become undocumented assumptions that become production failures.

* * *

### 3\. Timeliness and Currentness

A weather forecast based on yesterday's conditions is wrong for today's trip. An AI model trained on outdated information produces inaccurate or irrelevant results for exactly the same reason. Timeliness and currentness are related but separate problems, and treating them as one is where most pipelines fail.

Timeliness concerns whether data arrives quickly enough for its intended use. Currentness concerns whether the values still reflect present conditions. A pipeline can be timely, meaning data arrives on schedule, while the data itself is stale because the underlying conditions it describes changed months ago. Both require separate measurement with separate controls.

Define freshness in business terms before setting any technical threshold. "Updated daily" means nothing without context. For fraud detection, daily updates mean your model is twelve to twenty-four hours behind attacker behavior at all times. That is an acceptable lag for some fraud patterns and a catastrophic lag for others. For quarterly financial reporting, daily updates are likely far more than required. The business use case determines the freshness requirement, not the pipeline's default cadence.

Use low-latency data pipelines for time-sensitive AI applications. Change data capture delivers timely data from relational database systems by propagating incremental changes rather than full refreshes. Stream capture handles data originating from IoT devices and other high-velocity sources that require low-latency processing. Once captured, downstream analytical and operational stores should be updated continuously rather than in scheduled batches that create artificial staleness windows.

Store both event time and processing time for every record. Confusing them hides late-arriving data. If your pipeline processes a transaction at 14:00 that occurred at 08:00, the six-hour gap is only visible if you captured both timestamps independently. Relying on a single timestamp means you cannot detect late arrival, replay, or out-of-order delivery.

Test late-arriving, duplicated, out-of-order, and replayed events as part of your standard pipeline validation. These are the failure modes that stress-test assumptions baked into most feature engineering pipelines. A pipeline that handles clean, on-time data correctly will often fail in ways that corrupt model inputs when events arrive late or out of sequence.

Measure distribution drift on a cadence separate from pipeline latency checks. Use Population Stability Index, Jensen-Shannon divergence, or Wasserstein distance to compare current production data against your training baseline. Set retraining or review triggers when drift persists across multiple measurement periods, not just when a single batch looks unusual. A single anomalous batch is often noise. Sustained drift means your training distribution and production distribution have separated and your model is operating outside the conditions it learned from.

Teams often set a single drift alert threshold and then mute it when it fires continuously. That continuous firing is the signal, not the noise. Establish escalation procedures for sustained drift that include a defined review timeline and a retraining decision process, not just a repeated alert that gets ignored.

* * *

### 4\. Consistency

Consistency means the same concepts are represented uniformly across sources, versions, time periods, and processing steps. Inconsistency is invisible until it damages your model, and by that point the damage is already embedded in learned weights that are difficult to inspect and harder to correct.

You will not see a consistency failure in a simple data profile. You see it when your model learns that "1" means true in one data source and "1" means a product category code in another. You see it when temperature features from two sensors suddenly shift because one system reported in Celsius and the other in Fahrenheit, and nobody documented the difference. You see it when referential integrity fails silently and foreign keys resolve to deleted parent records.

Maintain a canonical data dictionary and controlled vocabulary. Version both the dictionary and your schemas. Treat schema changes as deployment events that require review and approval, with the same rigor you apply to code changes. Silent schema changes, the kind where an upstream system silently renames a column or changes a data type, should trigger alerts and halt downstream processing until explicitly approved.

Run contract tests between data producers and consumers. If an upstream system silently changes a column type from integer to string, your pipeline should fail loudly, not silently cast values and continue. Contract tests define the expected shape, types, ranges, and semantics of the data at each interface. When either side of the contract changes, the test fails and humans are notified.

Check units across every numeric field, not just ranges. Kilograms versus pounds. Celsius versus Fahrenheit. Milliseconds versus seconds. Kilometers versus miles. These errors do not appear in range checks because the values are plausible within their own unit system. They appear as feature distributions that look normal but shift model behavior in ways that are extremely difficult to trace without unit metadata.

Test cross-source agreement for shared keys and attributes. When your CRM and transaction system both carry a customer age field, check whether they agree. Systematic disagreement means you have a consistency failure and you need to decide which source is authoritative before any model uses that field. That decision cannot be left to the feature engineering pipeline to resolve implicitly.

Extend consistency checks to multimodal data. Confirm that text metadata corresponds to the correct image, audio clip, or document. Misaligned multimodal pairs corrupt the cross-modal signal the model is trained to learn, and they are nearly impossible to detect through standard quality profiles because each modality passes its own checks independently.

One consistency failure that rarely appears in quality checklists is timezone inconsistency in timestamps. Different source systems default to different timezones, or to UTC in some cases and local time in others. This creates apparent time-of-day patterns in your data that are artifacts of timezone handling, not real behavioral signals. A model trained on this data learns spurious time-of-day effects that disappear or reverse in production when the inference system uses a different timezone convention.

* * *

### 5\. Representativeness and Diversity

Representativeness asks whether the data reflects the populations, environments, conditions, and failure modes where the system will actually operate. Diversity asks whether meaningful variation exists across patterns, perspectives, scenarios, sources, languages, contexts, and edge cases.

Bias in AI systems occurs when applications produce results that reflect human biases, including social inequality. This happens when training data reflects a narrow band of attributes, perspectives, or populations. A credit risk model trained primarily on historical data from a specific geography or demographic group will not generalize fairly to the full population it serves. A hiring model trained on ten years of historical approvals learns to replicate the biases embedded in those approvals, not to identify the best candidates.

Diverse data means drawing from a wide range of sources spanning different patterns, variations, and scenarios relevant to the problem domain. That data might be structured or unstructured, cloud-hosted or on-premises, originating from transaction systems, IoT devices, enterprise applications, software as a service platforms, mainframes, databases, files, or documents. Narrowing your data sources to what is most convenient to access is one of the most reliable ways to build a model that fails the people it was designed to serve.

Do not assume that demographic balance alone proves fairness. Some operational datasets should not mirror population proportions. A model trained to detect rare equipment failures should oversample failure cases, not mirror a ninety-nine to one natural imbalance. A fraud detection model that mirrors the natural fraud rate will have almost no positive examples to learn from. The target distribution must be justified explicitly based on the learning objective, not assumed to be correct because it matches census statistics.

NIST recommends disaggregating evaluations across demographic groups and intersecting subgroups. Aggregate accuracy is not a fairness metric. A model can achieve ninety-two percent accuracy overall while performing at sixty-eight percent for a specific subgroup. That gap will not appear in any headline number. It will appear in user complaints, regulatory reviews, and adverse outcomes.

Test intersectional groups where sample sizes permit. Age crossed with gender crossed with region can reveal failure modes that are entirely invisible in single-dimension analysis. A model that performs equally well for women and equally well for younger users can still fail systematically for young women of a specific ethnicity. Intersectional testing requires adequate sample sizes in each cell, which is itself a representativeness requirement.

Build a challenge set from known incidents, complaints, adversarial examples, and expert-defined edge cases. Your standard test set reflects what happened in historical data. Your challenge set reflects what can happen in the real world. Models that pass standard test sets while failing challenge sets are models that have learned to perform in controlled conditions and generalize poorly to the unexpected.

Use stratified splits so rare classes and important subgroups appear in validation and test sets with sufficient volume to measure. A random split on an imbalanced dataset will often leave your minority class almost entirely in the training split, making it impossible to evaluate performance on exactly the cases that matter most.

A practical enforcement rule is to require every high-impact subgroup to exceed a minimum sample size in the test set and to publish accuracy, false-positive rate, false-negative rate, and calibration separately for each subgroup before the model is approved for deployment. That requirement makes representativeness gaps visible before they cause harm.

* * *

### 6\. Relevance and Fitness for Purpose

Relevance measures whether the data supports the intended task, user group, operating environment, and decision horizon. Irrelevant data adds noise. Future data used as model features creates leakage. Data collected under different conditions than deployment produces a model that works in the lab and fails in the field.

Write an intended-use statement before selecting any data. Define prohibited uses and known out-of-scope populations explicitly. This is not a formality. It forces decisions about what the model is for and, critically, what it is not for. Those decisions constrain which data sources are legitimate inputs. Without an intended-use statement, data selection decisions default to whatever is available and convenient, which is almost never the right answer.

Feature usefulness should be tested empirically, not assumed. Remove or mask a feature and measure whether model performance changes meaningfully on your validation set. A feature that survives permutation importance testing and ablation testing is contributing real signal. A feature that does not survive those tests may be noise, a proxy for a protected attribute, or a leakage vector that inflates offline performance while failing in production.

Temporal leakage is the most dangerous relevance failure because it produces results that look correct by every offline metric and fail completely in deployment. A feature derived from information available after the prediction timestamp will produce outstanding offline accuracy and catastrophic production failure. A maintenance record created at the time of a failure event, when used to predict that failure, tells the model something it cannot possibly know before the event occurs.

Random splits conceal temporal leakage entirely. Use time-based splits where deployment involves future cases. Use group-based splits where deployment involves new users, new sites, new organizations, or new devices. If every user in your test set also appears in your training set, your offline evaluation measures how well the model memorizes individual patterns, not how well it generalizes to users it has never encountered.

Include a "not relevant" rejection category in human labeling instructions. This forces annotators to flag content that does not belong in the dataset at all, rather than forcing an assignment to the nearest available class. Without this category, annotators assign ambiguous or irrelevant examples to whatever class seems closest, introducing noise that the model learns as signal.

The leakage failures that hurt most are subtle, not obvious. Nobody accidentally includes the outcome label as a raw feature. The dangerous cases are a field updated at the time of outcome recording, a derived feature that aggregates events occurring after the prediction timestamp, or an identifier that correlates with outcome because of how data was collected rather than because of any real relationship. Build a leakage review into your feature documentation process as a required step, not an optional check.

* * *

### 7\. Validity

Validity means data conforms to specified syntax, types, ranges, codes, formats, and business constraints. Invalid data corrupts feature engineering, breaks preprocessing pipelines, and introduces errors that propagate through every downstream transformation.

Run validation before data enters any training, feedback, or feature store. Every batch. Without exception. Validation that runs only on initial data load misses every defect introduced by schema changes, pipeline updates, and source system modifications that occur after the initial check.

Quarantine failed records rather than dropping them silently. Silent dropping hides failure rates from everyone downstream, including the model owners who need to know whether the training set shrank, the business owners who need to know whether records are being lost, and the governance team that needs to know whether a systematic problem exists upstream. When your pipeline drops five percent of records from a specific source without logging or alerting, that five percent is invisible to everyone who needs to act on it.

Version your validation rules and retain failure reports. When a model's performance degrades, you need to be able to answer whether the validation rules changed, not just whether the source data changed. A validation rule that became more permissive because a developer found it inconvenient is a governance failure that should appear in the audit trail.

Distinguish between invalid data and valid but unusual data. An outlier is not automatically an error. A transaction amount in the ninety-ninth percentile may be entirely legitimate. An age of two hundred and forty is not. Your validation rules need to encode that distinction explicitly, with separate handling for impossible values and improbable but possible values.

Test adversarially malformed inputs and encoding problems. Validation rules are almost always written against clean, well-formed examples. Real data pipelines receive corrupted files, misencoded characters, truncated records, malformed JSON, and inputs that exploit edge cases in parsing libraries. Your validation layer needs to handle those cases explicitly and fail safely, not pass them to the model to fail on in ways that produce silent incorrect outputs.

The most expensive validity failure is one that produces values that pass individual type and range checks but violate business constraints. A date that is technically valid but falls before the product existed. A transaction amount that is within the allowed range but combined with a currency code that makes it implausible. A combination of age and account creation date that is jointly impossible. These require cross-field and cross-record constraint rules that most teams never write. Building cross-field validations into your quality gate as a required step, not an optional enhancement, catches an entire class of failures that field-level validation misses entirely.

A strong validation pipeline reports both the percentage of records that passed and the exact rejection reasons for every batch, segmented by source, time period, and field. Percentage alone tells you the scale of the problem. Rejection reasons tell you the pattern. Patterns reveal systematic problems upstream that need to be fixed at the source, not repeatedly quarantined at the gate.

* * *

### 8\. Uniqueness and Deduplication

Uniqueness ensures that records represent distinct entities or events when duplicates would distort learning or evaluation. Duplicate records inflate the influence of certain examples, bias learned representations toward overrepresented patterns, and, in the worst cases, contaminate evaluation with examples the model has already memorized.

The deduplication sequencing error is where most teams go wrong. Deduplicate before splitting data, not afterward. If you split first and then deduplicate within splits, you can remove duplicates within each partition while leaving near-identical records across the training and test boundary. That produces train-test contamination that inflates every metric without improving actual generalization.

Use group-aware splits for records belonging to the same customer, patient, device, household, author, or organization. If all records from a given customer land in both training and test sets, your evaluation measures how well the model memorizes customer-specific patterns. When that customer calls a month after deployment with a problem the model should have caught, you discover that your ninety-three percent test accuracy meant nothing because the model never actually generalized.

Train-test contamination is the most damaging uniqueness failure for language and image models. Near-duplicate examples in the test set produce artificially high evaluation scores even when the model has genuinely poor generalization. This is not a theoretical risk. It has produced published benchmark results that failed completely when the models were applied to real tasks. The contamination is invisible until someone runs explicit overlap detection between splits.

Exact duplicate detection requires hashing normalized records after stripping whitespace, punctuation, and case variations. Near-duplicate detection requires similarity matching techniques such as MinHash, locality-sensitive hashing, or embedding similarity. Both are necessary. Exact deduplication misses records that differ only by formatting, encoding, or minor variations that carry identical semantic content.

Investigate whether data augmentation has introduced near-duplicates into your test set. Augmented training examples that are semantically identical to test examples compromise evaluation integrity in exactly the same way as contamination from an external source. The fact that you created the near-duplicates deliberately through augmentation does not make the contamination less real.

The question of what constitutes uniqueness in your specific dataset is a business decision, not a technical one. A customer with two accounts is one entity for churn modeling and two entities for fraud detection. A document that appears in multiple collections is one document for deduplication and multiple entries for citation analysis. That decision must be made explicitly, documented in your quality scorecard, and retained with the matching thresholds used. Duplicate-label conflicts, where the same record received conflicting labels from different annotators or across different dataset versions, introduce contradictory training signal. Check for duplicate keys with conflicting labels before training begins and resolve them through adjudication.

* * *

### 9\. Security, Privacy, Accessibility, and Compliance

AI systems frequently operate on sensitive data. Personal identifiers, financial records, health information, biometric data, proprietary business content. Leaving that data unsecured creates two distinct problems that most teams conflate.

The first problem is privacy. Exposed data compromises the people the model was built to serve and creates legal liability under GDPR, CCPA, HIPAA, and sector-specific regulations. The second problem is model integrity. Manipulated or exposed training data biases outputs in ways that are difficult to detect and potentially permanent. An attacker who can inject records into a training dataset can shift model behavior without ever touching the model itself.

Three controls work together. Data classification automatically detects, categorizes, and tags data by sensitivity level, including sensitive, confidential, and restricted designations. Data protection applies the appropriate controls: masking, tokenization, or encryption for fields that require obfuscation, and access restriction for entire datasets. Access control defines who can access which data under which conditions, enforced through role-based permissions with least privilege as the default.

Apply purpose limitation consistently. Authorized access does not automatically mean authorized use. A data scientist with read access to a training dataset is not automatically authorized to export that dataset to a personal environment, use it for a different model, or share it with a vendor. Purpose limitation requires that every data access decision answers not just "can this person access this data" but "is this access consistent with the documented use of this data."

Separate raw, de-identified, feature, feedback, and production data stores. A single access control policy applied across all five layers cannot adequately protect any of them. The risk profile of a raw dataset containing identifiable health records is fundamentally different from the risk profile of an aggregated feature store derived from those records. Separation reduces blast radius and enables more precise access auditing.

Scan feedback data before reuse in any capacity. Feedback pipelines are a significant and underappreciated attack surface. User inputs can contain prompt injection attempts, personally identifiable information, credentials, malicious content, and adversarial examples designed to corrupt retraining. None of that should enter a retraining pipeline without explicit screening, classification, and authorization.

Test re-identification risk on datasets you intend to share, publish, or move between environments. Linkage attacks and singling-out techniques can recover individual identities from datasets that passed standard anonymization checks. Run those tests before sharing any de-identified dataset. The fact that you removed direct identifiers does not mean the dataset is anonymous.

Log access, export, transformation, and deletion events comprehensively. These logs serve as both a security control and a lineage artifact. They enable you to reconstruct who accessed what data, when, from where, and for what declared purpose. They are also the first artifact a regulator or auditor will request following an incident.

The most underestimated security control in AI data pipelines is encryption of temporary files and intermediate outputs. Teams apply strong encryption to source data and final model artifacts and then leave temporary files, cache directories, intermediate training checkpoints, and experiment logs completely unencrypted. Those files often contain sensitive training records in raw or partially processed form. They must be included in your encryption requirements and in your deletion procedures when their purpose is complete.

* * *

### 10\. Traceability and Lineage

Traceability means you can reconstruct where data came from, how it changed at every step, which model used it, and which outputs or decisions it influenced. Lineage is the artifact that makes that reconstruction possible. Together they enable accountability, reproducibility, and compliance. Without them, you cannot demonstrate that a model was built responsibly, and you cannot investigate a failure after it occurs.

Assign immutable identifiers to every dataset version and snapshot. Record cryptographic hashes for files, partitions, labels, and model inputs where practical. This is what makes reproducibility real rather than theoretical. Without it, you cannot confirm that the model you are investigating used the data you think it used. "We trained on last quarter's data" is not traceability. A versioned dataset identifier with a hash is traceability.

Maintain a lineage graph from source through every transformation to the model and its outputs. When a production prediction is disputed, you need to trace it back to the specific training record, the labeling guideline version, the annotator, and the source system. That trace is only possible if you captured it at every step in the pipeline. Lineage that covers the first and last mile but misses the transformations in between is documentation theater.

The lineage gap that creates the most governance risk is between the feature store and source data. Teams often track lineage through ingestion and initial transformation pipelines and then lose it at the feature store boundary. The model trains on features, not raw data. If you cannot trace a feature value back to the source record that produced it, your lineage is incomplete in exactly the place where failures most often originate.

Link every model artifact to exact training, validation, and test dataset versions, feature engineering code, configuration files, and labeling guideline version. Link user feedback to the model version that generated the response, the specific input, the reviewer decision, and the final disposition. Feedback that cannot be traced to a model version cannot be used to evaluate that model or to construct valid retraining data without introducing unknown confounders.

Preserve rejected data and quality exception reports when legally and operationally appropriate. The records you excluded are as important as the records you included. They document the boundaries of your dataset and enable you to assess, months or years later, whether those boundaries were appropriate and whether they introduced gaps that affected model behavior.

Build a business glossary that maps business terms to technical items in your datasets. Add semantic typing to provide additional meaning for automated systems. Index all metadata in a searchable catalog. Required catalog fields include source, owner, collection time, transformation history, version, intended use, retention period, sensitivity tags, and known bias issues. A dataset that cannot be found or understood is functionally unavailable, regardless of how complete or accurate it is.

Test your lineage by asking an independent reviewer to trace a specific production prediction back to its source records without your help. If they cannot complete that trace in a timeframe appropriate to your risk level, your lineage system is not operational. Set a specific target, such as completing any audit trace within four hours for high-risk models. Measure against it. A lineage diagram that looks complete on a whiteboard but takes three weeks to navigate in practice protects nobody.

NIST emphasizes evaluating data and content provenance, including original sources, transformations, and decision-making criteria. ISO-oriented guidance requires documentation of provenance, update dates, training and validation categories, labeling processes, intended use, quality requirements, retention policies, and known bias issues for every dataset used in an AI system.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/chatgpt-image-aug-14-2026-05_30_55-pm.png?w=1024)

## How to Set Quality Gates That Actually Block Bad Data

Quality gates block defective data from entering training or feedback stores. The design of those gates determines whether they protect your model or simply generate paperwork.

Use hard gates for safety, privacy, schema, leakage, and lineage. Hard gates are binary. The data either passes or it does not. A dataset that fails a hard gate does not enter the training pipeline regardless of its performance on other dimensions. Use monitoring thresholds with defined escalation procedures for drift, freshness, subgroup balance, and performance degradation. Monitoring thresholds trigger human review and a defined response timeline. They do not automatically halt processing.

Never let a high composite quality score mask a single unacceptable hard-gate failure. A composite score of 88 percent looks strong. A security dimension score of 22 percent within that composite means the model has access to unmasked personal data. The composite hides the single failure that matters most. Hard gates must be reported separately and evaluated independently. They cannot be averaged into an aggregate score.

Do not copy thresholds from other systems. ISO/IEC 5259-2 treats data quality measures as context-dependent, and ISO/IEC 42001 requires requirements appropriate to the system's intended use. A ninety-five percent label accuracy rate is a catastrophic failure for a clinical AI system. It may be entirely acceptable for an internal content recommendation system. Define your thresholds before training begins, document the justification for each one, and revisit them at every major model version.

## Requirements That Apply at Every Stage

Several requirements cut across all ten dimensions and all four data stages. These are not additional checks. They are the operating conditions that make the ten requirements enforceable over time.

Version everything that touches the data. Schemas. Validation rules. Transformation code. Labeling guidelines. Annotation team composition. Sampling plans. Quality thresholds. Build your versioning cadence around deployment events, not calendar dates. Every time a model is deployed, create a snapshot of every artifact that contributed to it. That snapshot is your reproducibility baseline. When something fails in production three months later, you are not guessing what the training environment looked like. You have a record.

Separate data preparation from data approval. The person who prepares the data should not be the only person who certifies it. Data stewards approve remediation strategies. Model owners cannot self-approve test data independence. Separation of duties is a control, not a bureaucratic inconvenience. When the same person who selected the data also signs off on its quality, the approval is not independent and the governance is not real.

Document every rejected decision, not just the accepted ones. Preserve rejected data and quality exception reports when legally and operationally appropriate. When a model failure occurs, those rejected records often contain the earliest visible signal. They also provide evidence for regulators that you discovered, quarantined, and escalated the issue through a defined process rather than ignoring it.

Require explicit written approval for every new data source added to a retraining pipeline. Teams add new sources without formal review because each addition feels incremental. Collectively, those additions shift the training distribution, introduce new privacy considerations, and alter model behavior in ways that were never assessed. The retraining approval gate is where governance fails most quietly, and it is where a formal requirement has the most leverage.

Make data consumable as a functional requirement, not an afterthought. Traditional machine learning workflows favor well-formed tabular structures and feature stores where SQL is a first-class language. Generative AI workflows require text from unstructured sources to be split into manageable chunks, converted into embeddings, and stored in a vector index. Each chunk must carry lineage back to the source document. Without that lineage, retrieval results cannot be audited and retrieved content cannot be verified. Consumability requirements must be specified alongside quality requirements, not treated as a separate concern belonging only to the engineering team.

## Controls, Metrics, and Validation Guidance

Use this table during data quality gate reviews. The metrics and tests are starting points calibrated to common practice. Adjust thresholds to match your specific use case, risk profile, and regulatory context. Do not treat any threshold here as universal.

| AI Data Requirement | Key Metrics and Validation Tests | Recommended Controls | Guidance and Acceptance Criteria |
| --- | --- | --- | --- |
| Accuracy | Value accuracy rate: correct values divided by inspected values. Label accuracy and label error rate. Numeric error: mean absolute error, root mean squared error, percentage error. Entity resolution precision and recall. Annotation confidence and adjudication rate. Compare samples against authoritative systems, original documents, instruments, or expert-reviewed ground truth. Double-label a statistically justified sample and calculate Cohen's kappa or Fleiss kappa. Reconcile records with source-of-record systems and investigate discrepancies above a defined tolerance. Require independent review for low-confidence or disputed labels. | Separate measurement accuracy from label accuracy. Define tolerances by use case before profiling. Record who produced or reviewed labels, when they were created, and which labeling instructions were used. Use a holdout audit sample that annotators cannot see during data preparation. Profile source data with exploratory data analysis to understand characteristics, completeness, distribution, redundancy, and shape. Operationalize remediation strategies with data quality rules and monitor them continuously. Enable lineage and impact analysis to trace origins and prevent accidental modification. | For a classifier, one acceptance rule is at least 98 percent of critical labels must agree with adjudicated expert labels, with no high-severity label error remaining unresolved. A small rounding error may be acceptable in forecasting but unacceptable in safety-critical control. The audit sample is not optional. Build it into the data preparation budget from day one. |
| Completeness | Field completeness: 1 minus missing values divided by expected values. Record completeness: received records divided by expected records. Label coverage: labeled records divided by records intended for supervised learning. Time period coverage. Class coverage and minority group coverage. Missingness rate by subgroup, source, and time period. Profile every column by dataset version and compare with thresholds. Reconcile dataset counts with source-system counts, event logs, or control totals. Reject or quarantine unlabeled records unless an explicit missing-label policy exists. Check for missing dates, gaps in event sequences, and unexplained inactivity. | Set stricter thresholds for critical fields than optional fields. Do not treat imputation as elimination of the problem. Retain indicators showing which values were imputed. Measure completeness separately for training, validation, test, feedback, and production data. Investigate complete records that contain default values such as 0, unknown, or 1970-01-01. | A typical data quality gate requires zero missing values for mandatory identifiers and labels, while allowing a documented, bounded rate of missingness in noncritical features. Concentrated missingness is more dangerous than distributed missingness. Five percent missing overall can hide fifty percent missing in a specific demographic group, geography, or outcome class. Always break completeness metrics down by subgroup before accepting any overall figure. |
| Timeliness and currentness | Data age: current time minus event time or last update time. Pipeline latency: ingestion time minus source event time. Freshness compliance rate. Update frequency and interval variance. Staleness rate. Distribution drift: Population Stability Index, Jensen-Shannon divergence, Wasserstein distance, population mean or variance change. Concept drift indicators comparing delayed outcomes, error rates, and label distributions over time. Enforce maximum allowed age for each source and use case. Run end-to-end latency tests from source generation to model availability. Alert when records or batches exceed service-level objectives. Check whether feeds arrive according to documented schedules. Identify records unchanged beyond a defined period. | Define freshness in business terms, not technical terms. Store both event time and processing time separately. Test late, duplicated, out-of-order, and replayed events. Establish retraining or review triggers when drift persists rather than reacting to a single unusual batch. Use change data capture for relational sources and stream capture for low-latency sources such as IoT devices. Update downstream stores continuously. | Document the last update, intended use, data category, and quality requirements for each dataset. Updated daily may be adequate for demand planning but not fraud detection. Sustained drift is the signal, not noise. Establish escalation procedures for persistent drift, not just individual alerts. |
| Consistency | Cross-source agreement rate. Schema conformity rate. Unit consistency rate. Referential integrity rate. Business rule violation rate. Cross-version reproducibility. Contradiction rate. Compare shared keys and attributes across systems of record. Validate column names, types, units, encoding, and allowed nullability. Detect incompatible units such as kilograms versus pounds or Celsius versus Fahrenheit. Confirm foreign keys resolve to valid parent records. Test constraints such as shipment date greater than or equal to order date. Re-run transformations and compare hashes, counts, and summary statistics. Find records where two fields or sources assert incompatible facts. | Maintain a canonical data dictionary and controlled vocabulary. Version schemas and transformation code. Use contract tests between producers and consumers. Treat silent schema changes as deployment failures, not merely warnings. Test consistency within multimodal data such as text metadata corresponding to the correct image or audio file. | Example rules: every transaction must reference an existing account. Currency must be explicit. Timestamps must contain a timezone. Monetary values must use the declared currency and precision. The most common hidden consistency failure is timezone inconsistency across sources. Validate timezone handling explicitly in every pipeline. |
| Representativeness and diversity | Population coverage by group, region, language, device, environment, and use case. Distribution distance measures: standardized mean difference, KL divergence, Population Stability Index, Wasserstein distance. Class balance metrics and minority class share. Group-specific label rates and outcome rates. Coverage of known failure modes and edge cases. Fairness metrics: demographic parity difference, disparate impact, equal opportunity difference, equalized odds difference, group-specific error rates. Compare dataset proportions with the target deployment population or a justified sampling frame. Compare training, validation, test, and production distributions. Test whether rare but important classes are sufficiently represented. Investigate unexplained differences before training. Build a challenge set from incidents, complaints, expert scenarios, and adversarial examples. Evaluate model outcomes separately by group, subgroup, and intersection. | Do not assume demographic balance alone proves fairness. Document why the target distribution is appropriate. Some operational datasets should not mirror population proportions. Test intersectional groups such as age crossed with gender crossed with region where sample sizes permit. Include domain experts and affected communities when selecting fairness criteria. Use stratified splits so important groups and rare events appear in validation and test sets. Draw from structured and unstructured sources across cloud, on-premises, operational databases, enterprise resource planning systems, software as a service applications, files, and documents. | A practical test is to require every high-impact subgroup to exceed a minimum sample size and to publish accuracy, false-positive rate, false-negative rate, and calibration separately for each subgroup. Diverse data means drawing from a wide range of sources spanning different patterns, perspectives, variations, and scenarios. Narrowing data sources to what is convenient reliably builds biased models. |
| Relevance and fitness for purpose | Feature usefulness: mutual information, permutation importance, or task-specific ablation impact. Label feature time alignment. Coverage of intended use cases. Out-of-domain rate using applicability domain or embedding distance checks. Leakage rate searching for post-outcome fields, future timestamps, duplicated labels, or target-derived variables. Signal-to-noise indicators measuring unusable, irrelevant, corrupted, or unrelated content. Remove or mask a feature and determine whether it contributes meaningful validated performance. Test that features were available before the prediction point. Map each record to a documented use case, workflow, or scenario. | Write an intended use statement before selecting data. Define prohibited uses and known out-of-scope populations. Test temporal leakage rigorously because random splits can conceal it. Use time-based or group-based splits where deployment involves future cases, users, sites, or organizations. Include a not relevant rejection category in human labeling. | A model intended to predict next-day equipment failure should not use maintenance records created after the prediction timestamp, even if those records improve offline accuracy. The dangerous leakage cases are subtle. Build a leakage review into the feature documentation process. |
| Validity | Schema validation pass rate. Type conformance rate. Range conformance rate. Pattern conformance rate. Vocabulary conformance rate. Constraint violation rate. Parsing or tokenization failure rate. Validate every batch against a versioned schema. Check dates, numerics, booleans, categorical codes, encodings, and nested structures. Reject impossible values such as negative age or humidity above physical limits. Validate identifiers, email formats, country codes, and timestamp formats. Check categorical values against approved code lists. Apply domain rules and cross-field validations. Test whether documents, images, audio, and structured records can be consumed correctly. | Run validation before data enters training or feedback stores. Quarantine failed records rather than silently dropping them. Version validation rules and retain failure reports. Distinguish invalid data from valid but unusual data. Outliers are not automatically errors. Test adversarially malformed inputs and encoding problems. | A strong pipeline reports both the percentage that passed and the exact rejected record reasons, enabling remediation and audit. The most expensive validity failures pass type and range checks but violate business constraints. Build cross-field and cross-record constraint rules into the quality gate as a first-class requirement. |
| Uniqueness and deduplication | Exact duplicate rate. Near-duplicate rate using similarity matching, MinHash, locality-sensitive hashing, or embedding similarity. Duplicate entity rate using deterministic and probabilistic rules on names, addresses, identifiers, images, or documents. Event uniqueness rate checking event IDs, timestamps, sequence numbers, and source offsets. Train test overlap rate searching identical or near-identical examples across splits. Duplicate label conflict rate identifying the same item receiving conflicting labels. Hash normalized records and count repeated hashes. Use similarity matching and entity resolution tests. | Deduplicate before splitting data, not afterward. Use group-aware splits for records belonging to the same customer, patient, device, household, author, or organization. Avoid deleting legitimate repeated events before determining what constitutes uniqueness. Investigate data augmentation that creates near-duplicates in the test set. Retain duplicate decisions and matching thresholds. | For language or image models, train test contamination can produce deceptively high evaluation scores even when the model has poor generalization. Deduplicate before splitting. Check for duplicate keys with conflicting labels before training begins and resolve them through adjudication, not arbitrary selection. |
| Security, privacy, accessibility, and compliance | Unauthorized access incidents and access denial rate. Encryption coverage at rest and in transit. Sensitive field discovery and masking coverage. Re-identification risk using linkage and singling-out tests. Consent and legal basis coverage. Data retention compliance rate. Dataset availability and recovery time. Data access latency and availability. Test role-based access control with least privilege and negative authorization cases. Verify encryption configuration, certificates, key rotation, backups, and temporary files. Scan for personal, financial, health, confidential, or credential data and verify masking or tokenization. Reconcile records with consent, purpose, retention, geographic, and contractual restrictions. Test automatic deletion, archival, and legal hold rules. Perform restore tests and measure recovery point and recovery time objectives. Verify that authorized training and inference jobs can reliably obtain required data. | Apply purpose limitation. Authorized access does not automatically mean authorized use. Separate raw, de-identified, feature, feedback, and production stores. Scan feedback data for prompt injection, secrets, personal data, and malicious content before reuse. Log access, export, transformation, and deletion events. Test whether sensitive attributes can be inferred from supposedly anonymized records. Classify data by sensitivity tier such as sensitive, confidential, or restricted. Apply protection policies such as masking, tokenization, or encryption. Use access control policies based on least privilege. | ISO/IEC 42001 is an organizational management system standard for developing, providing, and using AI systems, including managing data quality and system performance. The underestimated security control is encryption of temporary files, cache directories, and intermediate training checkpoints. Those files can contain sensitive training records. Include them in encryption and deletion procedures. |
| Traceability and lineage | Lineage coverage: records or datasets with complete provenance divided by total. Transformation reproducibility rate. Metadata completeness rate for catalog fields, data dictionary entries, licensing, retention, and sensitivity tags. Label provenance coverage confirming annotator, guideline version, timestamp, confidence, and adjudication status. Version linkage coverage connecting each model artifact to exact training, validation, test, feature, code, and configuration versions. Audit query success rate and time to reconstruct. Change detection latency. Require source, owner, collection time, transformation, version, and intended use metadata. Rebuild a dataset from source snapshots and compare checksums and quality statistics. Ask an independent reviewer to trace a production prediction back to source records. | Assign immutable dataset and snapshot identifiers. Record hashes for files, partitions, labels, and model inputs where practical. Maintain a data lineage graph from source through transformations to model and output. Link user feedback to the model version, prompt or input, response, reviewer decision, and final disposition. Preserve rejected data and quality exceptions when legally and operationally appropriate. Build a business glossary that maps business terms to technical items. Use semantic typing to provide extra meaning for automated systems. Index metadata in a searchable catalog. | NIST emphasizes evaluating data and content provenance, including original sources, transformations, and decision-making criteria. ISO-oriented guidance highlights provenance, update date, training and validation and test and production categories, labeling processes, intended use, quality, retention, and known bias issues. The lineage failure that creates the most governance risk is the gap between feature store and source data. Extend the lineage graph through the feature engineering layer. |
| Consumability for machine learning and generative AI | For traditional ML: well-formed, high-quality, tabular data structures with SQL as a first-class language for data scientists. For generative AI: unstructured sources such as presentations, mail archives, text documents, PDFs, and transcripts split into manageable chunks, converted into embeddings, and stored in a vector database for similarity search. Each chunk must carry lineage back to the source file. | For ML: use lakehouse-based feature stores and database-like structures. For GenAI: enforce quality controls upstream before ingestion. Trusted, secure, governed data becomes input to embedding pipelines. | Retrieval augmented generation outputs cannot be audited without lineage from chunk back to source file. That is the only defensible order of operations. |
| Minimum validation focus by data stage | Training data: accuracy, completeness, representativeness, leakage, duplication, label quality, privacy, and lineage. Validation and test data: independence from training data, representative coverage, stable labels, subgroup metrics, temporal validity, and contamination checks. Feedback data: authenticity, user authorization, toxicity and injection screening, label confidence, reviewer agreement, and linkage to the relevant model version. Production or usage data: freshness, schema validity, drift, out-of-domain inputs, access control, incident rates, and outcome-based accuracy once labels become available. Retraining data: provenance, change impact, regression tests, fairness comparison with the previous model, and approval of newly added sources. | Use the minimum validation focus table as a starting point. Add tests that match the specific risk profile. For training data, always run leakage detection and group-aware split verification. For validation data, always check independence and subgroup coverage. For production data, always check schema drift and out-of-domain rates. For feedback data, always scan for injection and personal data. | Pair data quality tests with model-level tests. A fresh, valid, complete dataset can still corrupt a retrained model if the source distribution shifted. Before retraining, run a regression suite against the incumbent model. Compare subgroup false-positive rates and calibration. Approve new sources only after they improve at least one intended outcome without degrading protected groups. |
| Quality gate design and composite trust score | Each dataset needs a versioned scorecard containing intended use, unacceptable uses, required dimensions, metric definitions, thresholds, tolerances, severity levels, test frequency, responsible owner, sampling method, confidence intervals, quarantine and escalation procedures, dataset and label and code and model versions, and retained audit evidence. | Define hard gates for safety, privacy, schema, leakage, and lineage. Use monitoring thresholds for drift, freshness, subgroup balance, and performance degradation. Quarantine failed records instead of silently dropping them. Preserve rejected data when legally and operationally appropriate. Recalculate the composite score regularly. Treat any hard-gate failure as zero readiness even if the composite looks acceptable. | Never approve average quality scores without per-subgroup evidence. A 99.7 percent schema pass rate can hide all records from one geography and one device type. A composite score of 82 percent can pass review while the security dimension sits at 22 percent. Hard gates must be reported separately and cannot be averaged away. |
| Cross-cutting controls | Version everything that touches the data: schemas, validation rules, transformation code, labeling guidelines, annotation team composition, sampling plans, and quality thresholds. Build versioning cadence around deployment events. Document decisions, not just outcomes. Separate data preparation from data approval. The person who prepares the data should not be the only person who certifies it. Data stewards approve remediation strategies. Model owners cannot self-approve test data independence. Protect feedback channels like production input. Scan feedback for prompt injection, secrets, personal data, and malicious content before reuse. | Do not use universal thresholds. ISO/IEC 5259-2 treats data quality measures as context-dependent. ISO/IEC 42001 requires requirements appropriate to the intended use. A medical diagnosis system, a recommendation engine, and an internal search tool need different thresholds. | A ninety-five percent label accuracy rate is catastrophic in clinical AI and acceptable for a recommendation engine. Define thresholds explicitly before training begins. Document the justification. Revisit them at each major model version. |
|  |  |  |  |

## Versioned Quality Scorecard and What to Capture for Every Dataset

For each dataset, maintain a versioned scorecard that includes the following fields.

The intended use and explicitly excluded uses, written as specific statements rather than general descriptions. Required quality dimensions with metric definitions and the rationale for each inclusion. Thresholds and tolerances organized by severity level, with the justification for each threshold documented. Test frequency and responsible owner for each dimension. Sampling method, sample size, and confidence intervals for each metric. Quarantine, escalation, and remediation procedures with defined response timelines. Dataset version, label version, transformation code version, and model version references. Evidence retained for audit and reproducibility, including failure reports, adjudication records, and approval decisions.

This scorecard is a living governance artifact. Update it at every dataset version. Review it at every model deployment gate. Audit it when something goes wrong. The scorecard that is never touched after initial completion is the strongest signal that data quality governance is not operational.

## Recommended Additional Articles

Read more about training, validation and usage data requirements including lifecycle-specific validation, measurable controls, hard deployment gates, monitoring thresholds, data leakage prevention, lineage, privacy, and common implementation failures. My following articles provide more related guidance on governing AI data, systems, vendors, and operational risk.

### Practical AI Assessments

This framework connects data readiness with formal AI lifecycle gates, requiring measured accuracy, completeness, representativeness, provenance, privacy compliance, testing, monitoring, and documented go/no-go decisions.

[Read Practical AI Assessments](https://hernanhuwyler.wordpress.com/2026/03/12/practical-ai-assessments/)

### Practical ISO 42001 Certification Guidance

Huwyler explains how to operationalize AI governance through data cards, provenance records, lifecycle-specific data controls, quality metrics, bias analysis, validation evidence, monitoring, and accountable approval processes.

[Read Practical ISO 42001 Certification Guidance](https://hernanhuwyler.wordpress.com/2026/03/12/practical-iso-42001/)

### ISO 42001 Implementation for Companies

This article shows why AI governance must separate training, validation, and testing data while continuously measuring provenance, quality, bias, production performance, and outputs outside approved operating conditions.

[Read I Implemented ISO 42001 for Global Companies](https://hernanhuwyler.wordpress.com/2026/03/12/i-implemented-iso-42001-for-global-companies/)

### AI Contract Clauses and Data Controls

Huwyler translates data quality and governance principles into procurement requirements covering provenance, representativeness, labeling, bias, privacy, retention, supplier accountability, model updates, drift, audit rights, and exit controls.

[Read AI Contract Clauses That Reduce Vendor, Data, and Liability Risk](https://hernanhuwyler.wordpress.com/2026/03/12/ai-procurement-controls/)

### The prEN 18286 Reality Check

This detailed regulatory analysis links AI quality management with data governance, dataset quality, traceability, verification, validation, lifecycle evidence, risk controls, post-market monitoring, and auditable conformity obligations.

[Read The prEN 18286 Reality Check](https://hernanhuwyler.wordpress.com/2026/06/17/the-pren-18286-reality-check/)

### AI Isn’t Coming for GRC Jobs

This executive perspective explains how weak data governance undermines AI-enabled risk management, compliance, audit analytics, monitoring, and control assurance across the organization.

[Read AI Isn’t Coming for GRC Jobs. It’s Coming for the Manual Work](https://mydailyexecutive.blogspot.com/2026/07/ai-isnt-coming-for-grc-jobs-its-coming.html)

### SAP S/4HANA AI, Analytics, and Continuous Monitoring

This article applies data-driven control testing to GRC, showing how organizations can identify risk patterns, design analytic tests, monitor evidence, and connect AI performance with governance controls.

[Read SAP S/4HANA, AI, Analytics, and Continuous Monitoring](http://mydailyexecutive.blogspot.com/2026/03/ap-s4hana-ais-analytics-continuous.html)

## External References

[ISO/IEC 5259-2:2024](https://www.iso.org/standard/81860.html) provides a formal data quality model and measurable characteristics for analytics and machine learning, treating quality measures as context-dependent rather than universal.

[ISO/IEC 5259-4:2024](https://www.iso.org/standard/81093.html) addresses organizational processes for data quality in machine learning training and evaluation, defining process requirements for maintaining quality across the data lifecycle.

ISO/IEC 42001:2023 is a management system standard for AI systems covering development, provision, and use. It requires organizations to define data quality requirements appropriate to the intended use of each AI system and verify them throughout the lifecycle.

[ISO/IEC 19157](https://www.iso.org/standard/78900.html) provides foundational data quality dimensions for geographic information that have been adapted in broader AI data quality frameworks.

NIST AI Risk Management Framework version 1.0 provides guidance on assessing representativeness, suitability, relevance, and fairness metrics across demographic groups and intersecting subgroups across different AI lifecycle stages.

NIST SP 1270, Towards a Standard for Identifying and Managing Bias in Artificial Intelligence, defines statistical parity, error-rate equality, equal opportunity, and related measures as context-specific evaluation metrics.

* * *

When organizations treat these ten requirements as compliance artifacts, the result is a folder full of scorecards and a production incident they cannot trace. Teams fill in fields to satisfy review boards. Data drifts between gate reviews. Labels lose their provenance when annotators turn over and guidelines are not versioned. A model retrains on duplicated, stale records from a source that was deprecated six months ago. The composite scorecard reads 91 percent. The production system misclassifies the users who needed it most. Nobody can explain why, because the lineage was incomplete and the thresholds were never calibrated to actual risk.

Treat these requirements as an operational discipline and the result is different. Data owners know exactly which failure modes block a release and why. Subgroup gaps surface before training, not after complaints arrive. Audit questions take hours rather than weeks. Retraining follows versioned evidence, regression tests, and documented fairness comparisons. Every threshold has a recorded justification. Every rejected dataset has a preserved exception report. Quality becomes a measurable engineering practice with defined owners, defined gates, and defined escalation paths.

The model is only as trustworthy as the data contract you can prove you kept.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative [risk modeling,](https://github.com/hwyler/risk-model-app) predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and internationally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance, technical and business requirements.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
