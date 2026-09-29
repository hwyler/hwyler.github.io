---
title: "Practical Post-Market Monitoring for AI Systems"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-systems"
  - "article-72"
  - "artificial-intelligence"
  - "business"
  - "eu-ai-act"
  - "hernan-huwyler"
  - "iso-42005"
  - "iso-5338"
  - "post-market-monitoring"
  - "technology"
---

## How to Build a Control Program That Catches Problems After Launch

Most AI governance programs are strongest before launch and weakest after it. That is backwards. The real risk starts when the system meets live users, changing data, edge cases, workarounds, and business pressure. I have seen AI systems pass pre-launch review cleanly, then drift into risky territory within weeks because usage changed, configs changed, user behavior changed, or the model simply behaved differently at scale. The project team thought governance was done. The hard part had just started.

That is why post-market monitoring matters. It is the operating discipline that tells you whether the AI system is still performing, still lawful, still useful, and still within its approved boundaries. This post shows you how to turn post-market monitoring into a real workflow using both developer controls and user-side controls, not a passive collection of dashboards and incident tickets.

Post-market monitoring for AI is the structured practice of tracking, evaluating, and acting on an AI system's behavior once it's operating in the real world. It requires two distinct sets of controls: developer controls managed by internal staff and user controls managed by external parties. This post covers both sets, with the practical guidance I've gathered from monitoring AI systems across financial services, healthcare, and enterprise technology.

## Why Post-Market Monitoring Is Where AI Governance Gets Real

Pre-deployment testing tells you how a model performs under controlled conditions. Post-market monitoring tells you how it performs under real ones. These are very different things.

Real-world data drifts. User behavior changes. Infrastructure degrades. Access privileges accumulate. New vulnerabilities emerge. Regulatory requirements evolve. Business objectives shift. None of these changes announce themselves. Without structured monitoring, they compound silently until something breaks visibly.

The EU AI Act mandates post-market monitoring for high-risk AI systems. ISO/IEC 42001 includes ongoing monitoring as a core management system requirement. NIST's AI Risk Management Framework positions monitoring as a continuous function, not a periodic activity. These aren't aspirational recommendations. They reflect hard-won understanding that AI systems degrade in ways traditional software doesn't.

A traditional software application does the same thing on day 1,000 that it did on day 1, assuming no code changes. An AI system doesn't. Its relationship with real-world data means its behavior shifts even when nothing in the system itself has changed. The world changes around it, and its performance changes with it.

Post-market monitoring catches this drift before it causes harm. It operates through two complementary control sets: developer controls managed by the team that built and maintains the system, and user controls managed by the organizations and individuals who deploy the system in their business contexts. Both are necessary. Neither is sufficient alone.

Original implementation tip: Establish your post-market monitoring framework before deployment, not after. I know this sounds obvious. But on four of the six AI deployments I've supported, monitoring was designed after the system went live because "we'll figure out monitoring once we see how it behaves in production." That approach guarantees a blind period where the system operates without oversight. On one project, that blind period lasted 47 days. During those 47 days, a data pipeline error caused 6% of inference requests to receive default outputs instead of model predictions. No user complained because the default outputs were plausible. No alarm fired because no alarm existed. Design your monitoring controls during the development phase, test them in staging, and deploy them alongside the model. The monitoring system should go live the same day the model goes live.

## The Two-Party Monitoring Framework

Post-market monitoring requires controls from two distinct parties because each has visibility into different aspects of system behavior.

The developer, your internal team, has visibility into model internals. They can track algorithmic metrics, monitor infrastructure performance, analyze system logs, review access controls, and test for vulnerabilities. They see the system from the inside.

The user, your external stakeholders, has visibility into real-world impact. They see incident reports from end users, observe scope drift in how the system is being applied, experience contractual performance gaps, and can measure business value delivery. They see the system from the outside.

Gaps in post-market monitoring almost always occur at the boundary between these two perspectives. The developer sees that the model is performing within technical parameters. The user sees that business outcomes are declining. Both are looking at the same system and drawing different conclusions because they're measuring different things.

A complete post-market monitoring program bridges this boundary with shared metrics, regular communication cadences, and defined escalation paths.

Original implementation tip: Create a shared monitoring dashboard that both developer and user controls feed into. I worked with an organization where the AI vendor tracked 14 internal metrics and the business unit tracked 8 external metrics. Neither party saw the other's metrics. The vendor reported that model performance was stable. The business unit reported that customer complaints about AI-assisted decisions had increased 40%. It took six weeks of finger-pointing before someone put both datasets side by side and discovered that while overall model accuracy was stable, accuracy for a specific product category had degraded by 23%. The vendor's aggregate metrics masked a localized problem that only the user's complaint data could pinpoint. One shared dashboard, reviewed jointly on a biweekly call, would have surfaced this in days rather than weeks.

## Developer Controls: Tracking Algorithmic Metrics Against Acceptance Objectives

The first and most important developer control is tracking algorithmic metrics against predefined acceptance objectives. This is where your deployment criteria become your monitoring criteria.

Every AI system should have documented acceptance objectives established before deployment. These typically include accuracy thresholds, precision and recall targets, false positive and false negative rate limits, and fairness metrics across protected demographic groups. Post-market monitoring means measuring these same metrics continuously on production data and comparing them against the predefined thresholds.

What to track: Set up automated metric computation on production inference data. For a classification model, compute accuracy, precision, recall, F1 score, and demographic parity ratios daily. Compare each metric against its acceptance threshold. Generate automated alerts when any metric falls below threshold or shows a sustained downward trend over a rolling 7-day window.

The challenge is that production data doesn't come with ground truth labels the way test data does. In many applications, you won't know whether a prediction was correct until days, weeks, or months later, when the actual outcome becomes observable. A loan default prediction isn't validated until the loan either defaults or is repaid. A medical diagnosis isn't confirmed until follow-up testing occurs.

This means your algorithmic monitoring needs two tracks. A real-time track monitors input data distributions, output distributions, and prediction confidence scores for signs of drift. A delayed track computes accuracy metrics once ground truth becomes available and compares them against acceptance objectives.

Original implementation tip: Monitor input data distributions as aggressively as you monitor model outputs. The first sign of model degradation is almost always a shift in input data, not a shift in output quality. Output quality degrades as a consequence of input drift, but it degrades with a delay that can mask the problem for weeks. I set up a simple distribution monitoring system that computes the Kolmogorov-Smirnov statistic between today's input distribution and the training data distribution for each feature, daily. When any feature exceeds a predefined divergence threshold, it triggers an investigation. On one deployment, this caught a data provider format change that shifted how income values were reported from annual to monthly figures. The model didn't crash. It just started treating everyone as low-income. The input distribution alert fired on day one of the change. Without it, we would have discovered the problem through output degradation days or weeks later.

## Developer Controls: System Health and Infrastructure Monitoring

Three developer controls address the operational health of your AI system: monitoring system uptime and availability, analyzing user activity in usage logs, and monitoring infrastructure and capacity usage.

System uptime and availability monitoring measures whether the AI system is accessible and responding when users need it. This sounds like basic IT monitoring because it is. But AI systems have availability failure modes that traditional applications don't. A model serving endpoint might be "up" in the sense that it accepts requests and returns responses, but "down" in the sense that it's returning cached or default responses instead of actual model predictions because the model loading process failed silently.

What to put in place: Monitor not just endpoint availability but model health. Include a health check that verifies the correct model version is loaded, that inference is producing outputs within expected ranges, and that the model is actually executing rather than returning fallback responses. A simple canary request, a known input with a known expected output, run every five minutes, catches model loading failures that HTTP health checks miss entirely.

User activity analysis from usage logs reveals how the system is actually being used. This differs from how it was designed to be used. Usage logs show query volumes, query types, user segments, peak usage patterns, and interaction sequences. They reveal whether users are adopting the system as intended or developing workarounds that indicate usability problems or unintended uses.

What to track: Log every inference request with a timestamp, user identifier, input summary (respecting privacy requirements), output summary, confidence score, and response time. Analyze these logs weekly for patterns. Look for users who submit the same query repeatedly (suggesting they don't trust the output), users who consistently override model recommendations (suggesting accuracy concerns for their use case), and usage spikes from unexpected user groups (suggesting scope drift).

Infrastructure and capacity monitoring tracks compute resources, memory usage, GPU utilization, and storage consumption during production operation. AI systems have different resource profiles than traditional applications. A model that runs efficiently on average may spike to 400% GPU utilization during batch processing windows. A vector database that grows with every interaction will eventually exceed storage limits if not monitored.

Original implementation tip: The usage log analysis is the developer control that produces the most actionable insights per hour of effort invested. I spent years focusing primarily on algorithmic metrics and infrastructure monitoring. Then a colleague suggested we analyze usage patterns. Within the first week of systematic log analysis, we discovered that 34% of queries to our document classification model came from a department that wasn't in our intended user list. They were using the model to classify customer complaints, a use case we'd never tested for and that the model wasn't validated to handle. The model was producing classifications for these inputs, but with significantly lower confidence scores than for its intended document types. Without usage log analysis, this scope drift would have continued indefinitely, with a department making operational decisions based on unvalidated model outputs.

## Developer Controls: Access, Security, and Compliance

Three developer controls address the security and compliance dimensions of post-market monitoring: reviewing and certifying access privileges, performing regular penetration tests and red-team exercises, and conducting compliance audits with external auditors.

Access privilege review ensures that the right people have the right access to AI system components over time. Access privileges accumulate. The data scientist who needed full model access during development may not need it during production operation. The contractor who was granted temporary API access for integration testing may still have that access six months later. The service account created for a one-time data migration may still have write access to the production training data store.

What to put in place: Conduct quarterly access reviews for all AI system components. This includes model artifact repositories, training data stores, inference API credentials, monitoring dashboards, and model management interfaces. For each credential, verify that the person or service still needs the access, that the access level is appropriate for their current role, and that the credential hasn't been shared or compromised. Certify active access and revoke everything else.

Penetration testing and red-team exercises test your AI system's security posture under adversarial conditions. Standard penetration testing covers infrastructure vulnerabilities. AI-specific red-team exercises cover model-specific attack vectors: prompt injection, model extraction, training data reconstruction, adversarial evasion, and safety filter bypassing.

What to put in place: Schedule infrastructure penetration tests quarterly and AI-specific red-team exercises semi-annually. After any major model update, architecture change, or deployment expansion, run an additional targeted assessment. Track findings in a persistent tracker and verify remediation in subsequent assessments.

Compliance audits by external auditors provide independent verification that your AI system meets regulatory and standards requirements. Internal monitoring tells you what you think your compliance posture is. External audits tell you what it actually is.

What to put in place: Engage an external auditor with AI-specific expertise annually. The audit should cover data handling practices, bias and fairness assessments, documentation completeness (model cards, impact assessments, risk registers), incident response readiness, and regulatory compliance across deployment jurisdictions. Address findings within defined timeframes and track closure.

Original implementation tip: Access privilege accumulation is the security risk that everyone acknowledges and nobody consistently addresses. I've conducted access reviews on AI platforms where 40% of active credentials belonged to people who had changed roles or left the organization. One production model serving endpoint had 23 API keys with full access. Only 8 were actively used. The other 15 were orphaned credentials from previous integration projects. Any one of them could have been used to query the model, extract its behavior, or submit adversarial inputs. We revoked the 15 unused keys. Three teams immediately reported that their integrations broke, which meant they were using credentials we had no record of. That's the part that keeps me up at night. The credentials you don't know about are the ones that create real exposure. Build automated credential inventory that cross-references every active key against an approved integration registry. Flag any credential not in the registry for immediate investigation.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/financial-analyst-working-late.png?w=1024)

## User Controls: Incident Reports and Risk Reassessment

User controls provide the external perspective that developer controls cannot. Four user controls address reactive monitoring: reviewing incident and misuse reports, reassessing requirements based on new risks, collecting end-user feedback, and monitoring scope drift.

Incident and misuse report review is the user's primary mechanism for communicating AI system problems back to the developer. End users encounter system behaviors that internal monitoring may not flag: outputs that are technically within accuracy thresholds but practically wrong for a specific context, interactions that feel biased even if aggregate fairness metrics look acceptable, and use patterns that suggest the system is being misused by other users.

What to put in place: Establish a structured incident reporting process. Every report should capture: what happened, when it happened, who was affected, what the user expected versus what the system delivered, and what action the user took in response. Categorize incidents by type (accuracy failure, bias concern, availability issue, misuse observation, safety concern) and severity (critical, major, minor). Review incidents weekly during the first 90 days post-deployment, then biweekly for established systems.

Risk reassessment on new risks acknowledges that the risk landscape changes after deployment. New attack techniques emerge. Regulatory requirements evolve. The user population shifts. Competitive dynamics change how the system is used. The user organization should reassess AI system risks at defined intervals and whenever significant changes occur in the operating environment.

What to put in place: Conduct formal risk reassessments quarterly. Each reassessment should ask: Have new vulnerabilities been disclosed for the underlying model or framework? Have regulatory requirements changed in any deployment jurisdiction? Has the user population or use case expanded beyond the original scope? Have any incidents revealed risks not covered in the original risk assessment?

End-user feedback and survey analysis provides structured input from the people who interact with the AI system daily. In-app surveys, feedback widgets, and periodic structured surveys capture satisfaction, trust, usability, and perceived accuracy.

What to put in place: Deploy an in-app feedback mechanism that allows users to rate each AI interaction as helpful, unhelpful, or harmful. Run a more detailed survey quarterly that assesses overall satisfaction, trust in AI outputs, perceived accuracy for the user's specific use case, and suggestions for improvement. Analyze feedback for patterns that correlate with specific user segments, use cases, or time periods.

Original implementation tip: End-user feedback is the most undervalued signal in post-market monitoring. I used to treat it as a customer satisfaction input, useful for product improvement but not critical for compliance or safety monitoring. I was wrong. On one project, a structured quarterly survey revealed that 28% of users in a specific department reported "often" disagreeing with the AI system's recommendations but following them anyway because "the system is supposed to be better than my judgment." That finding exposed an automation bias problem that no algorithmic metric could detect. The model's accuracy for that department's use case was actually lower than the users' own judgment, but the users had been trained to defer to the system. We restructured the interface to present the AI recommendation alongside the key factors driving it, allowing users to apply their own expertise. User override rates increased from 3% to 17%, and decision quality, measured by downstream outcomes, improved by 11%. Feedback surveys catch human-system interaction problems that technical monitoring is blind to.

## User Controls: Contractual and Business Value Monitoring

Two user controls address the commercial dimension of post-market monitoring: reviewing contractual performance against license and service contracts, and assessing return on investment in business value reviews.

Contractual performance review verifies that the AI system delivers what the vendor promised. Service level agreements typically specify uptime guarantees, response time thresholds, support response standards, and update frequencies. Post-market monitoring means systematically measuring actual performance against these contractual benchmarks.

What to track: Build a contractual compliance tracker that lists each SLA metric, the contractual threshold, the measured performance for each reporting period, and the variance. Review this tracker monthly. When performance falls below contractual thresholds, document the shortfall and raise it with the vendor through the defined escalation process. Don't wait for quarterly business reviews to surface SLA violations. By then, you've accumulated months of substandard performance with limited recourse.

What to look for beyond SLA metrics: Monitor for contractual obligations that are harder to measure but equally important. Is the vendor providing the promised frequency of model updates? Are security patches being applied within agreed timeframes? Is the vendor maintaining the data handling practices specified in the contract? Are reporting and documentation obligations being met?

Return on investment assessment in business value reviews determines whether the AI system is delivering the value that justified its deployment. This is the control that connects technical performance to business outcomes and answers the question that executive sponsors actually care about: "Is this worth what we're paying for it?"

What to track: Define business value metrics during the project planning phase. These might include: processing time reduction (measured in hours saved per week), cost reduction (measured in dollars saved per quarter), revenue impact (measured in additional revenue attributed to AI-assisted processes), error reduction (measured in rework hours eliminated), and customer satisfaction impact (measured through satisfaction scores for AI-assisted versus non-AI-assisted interactions).

Conduct formal business value reviews quarterly. Compare actual business outcomes against the projections in the original business case. If the system is delivering 40% of projected value at the 12-month mark, you need to understand why and decide whether to continue, modify, or discontinue.

Original implementation tip: Scope drift is the user-side monitoring challenge that causes the most damage over time. Scope drift happens when the AI system gradually gets used for purposes beyond its original intended use. A document classification model starts being used for sentiment analysis. A customer service chatbot gets directed at internal HR queries. A fraud detection model gets applied to a new product line it was never validated for. Each individual expansion seems minor. Collectively, they move the system far outside its validated operating envelope. Build a scope drift monitoring process: maintain a living document that records the system's intended uses and approved use cases. Review actual usage patterns quarterly against this document. Any use that doesn't match an approved use case triggers a validation assessment before it's permitted to continue. I've seen scope drift turn a well-governed AI deployment into an ungoverned one over the course of a single year, one small expansion at a time, with nobody making a conscious decision to operate outside validated boundaries.

## Tips for Post-Market Monitoring

These principles apply across both developer and user control sets.

Original implementation tip on monitoring cadence: Match your monitoring frequency to your risk level, not your convenience. High-risk AI systems making consequential decisions about individuals, such as lending, healthcare, or criminal justice applications, need daily automated monitoring of algorithmic metrics, weekly human review of monitoring outputs, and monthly cross-party review meetings between developer and user. Lower-risk systems, such as internal productivity tools, can operate on weekly automated monitoring, monthly human review, and quarterly cross-party meetings. I've seen organizations apply the same monitoring cadence to every AI system regardless of risk. Their high-risk systems were under-monitored, and their low-risk systems consumed monitoring resources that produced minimal value. Right-size your monitoring investment to the risk profile.

Original implementation tip on version change monitoring: Every model version change, configuration change, and infrastructure change should trigger a monitoring verification cycle. Not a full reassessment. A targeted check that confirms monitoring systems are still capturing the right metrics on the right version of the model. I worked with one organization that updated their model from version 4.2 to version 5.0. The monitoring system continued reporting metrics from version 4.2 because the metric computation pipeline hadn't been updated to point to the new model endpoint. For three weeks, the monitoring dashboard showed stable performance for a model that was no longer in production. The new model's actual performance was significantly different. Build a version verification check into your deployment pipeline: after every model update, automatically verify that monitoring systems are connected to the correct model version and producing fresh metrics.

Original implementation tip on the handoff between developer and user monitoring: Define explicitly what the developer monitors, what the user monitors, and what both parties are responsible for. Document this in a monitoring responsibility matrix (a RACI for monitoring activities) and include it in your vendor agreement or internal operating procedures. The most common post-market monitoring failure I encounter is the assumption gap: the developer assumes the user is monitoring business outcomes, the user assumes the developer is monitoring model fairness, and nobody is monitoring either one. One deployment went 14 months before anyone measured demographic performance disparities because the developer thought "that's a business decision" and the user thought "that's a technical measurement." It was both. And it was nobody's assigned responsibility. The monitoring responsibility matrix eliminates assumption gaps by making every monitoring activity someone's explicit obligation.

Original implementation tip on when to stop monitoring and retire a system: Post-market monitoring should include defined criteria for system retirement. When should you stop monitoring and decommission the AI system? When accuracy falls below acceptance thresholds and retraining cannot restore performance. When the business value assessment shows negative ROI for two consecutive quarters. When regulatory changes make the system's approach non-compliant without feasible remediation. When the underlying model or framework reaches end-of-life from the vendor. Define these retirement triggers before deployment. Without them, organizations tend to keep underperforming AI systems running indefinitely because nobody has the authority or the criteria to pull the plug. I've encountered AI systems still in production three years after the team that built them disbanded, with no monitoring, no maintenance, and no documented owner. They continued making decisions that affected real people. Define retirement criteria. Assign someone the authority to enforce them. Monitor accordingly.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/modern-industrial-engineers-at-work-1.png?w=1024)

## References and Authoritative Frameworks

Your post-market monitoring program should align with these established standards:

- EU AI Act, Article 72 on post-market monitoring obligations for high-risk AI systems

- ISO/IEC 42001:2023, AI Management System (monitoring and measurement requirements)

- ISO/IEC 42005, AI Impact Assessment (ongoing monitoring provisions)

- NIST AI Risk Management Framework, Measure and Manage functions

- ISO/IEC 5338, AI System Life Cycle Processes (post-deployment monitoring)

- ISO/IEC 27001:2022, Information Security Management (access review and audit requirements)

- OECD AI Principles, particularly accountability and robustness provisions

- FDA guidance on AI/ML-based Software as a Medical Device (post-market requirements)

- ECB guidance on AI in banking supervision (ongoing monitoring expectations)

- NIST SP 800-137, Information Security Continuous Monitoring

If you treat post-market monitoring as a passive reporting exercise, generating dashboards that nobody reviews and filing metrics that nobody acts on, your AI system will degrade in ways you won't detect until an incident forces attention. The model will drift. The access privileges will accumulate. The scope will expand beyond validated boundaries. The business value will erode. And when the regulator, the auditor, or the affected individual asks what you were monitoring and what you did about what you found, your dashboards full of green indicators won't explain why the system was producing biased outputs for the last nine months.

When you build post-market monitoring as an active, structured, dual-party discipline, with defined metrics tied to acceptance objectives, assigned responsibilities across developer and user organizations, automated alerts tied to action protocols, and regular human review that looks for the patterns automation misses, you create the feedback loop that keeps AI systems trustworthy over time. You catch drift before it becomes degradation. You catch misuse before it becomes a headline. You catch value erosion before it becomes a write-off.

An AI system without post-market monitoring is a decision-making machine that nobody is watching. Eventually, it will make a decision that someone should have caught.

Which of your deployed AI systems has the weakest post-market monitoring? Start building the monitoring framework for that system today.

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and globally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
