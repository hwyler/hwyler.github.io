---
title: "I Implemented ISO 42001 For Global Companies"
date: 2026-03-12
tags: 
  - "ai"
  - "ai-governance"
  - "artificial-intelligence"
  - "business"
  - "chatgpt"
  - "iso-42001"
  - "technology"
---

You cannot audit a neural network using an IT security checklist.

# Here Are 4 Ways You Are Doing It Wrong.

I see compliance officers try to do this every week. They treat artificial intelligence like a standard enterprise database. They document who has password access to the system. They check the encryption standards. Then they tell their board the AI is secure and compliant.

They are completely wrong.

Traditional software does what you program it to do. Artificial intelligence acts probabilistically. It learns. It drifts. It makes decisions based on hidden statistical weights. If you apply traditional governance frameworks to AI, you leave your company exposed to massive regulatory and legal liability.

The International Organization for Standardization released ISO 42001 to solve this exact problem. It is the first certifiable AI management system standard.

Here is how you actually implement it without wasting time on useless paperwork.

## Stop Guessing and Start Measuring Impact

Most risk registers fail because they rely on executive opinions. Someone guesses that a new AI tool poses a "medium" risk.

ISO 42001 requires formal AI System Impact Assessments. You must stop guessing. You must systematically assess how your AI system affects individuals, groups, and society.

You need to define strict triggers for these assessments. Do not evaluate every basic algorithm. Focus on systems where the complexity of the technology, the sensitivity of the data, or the criticality of the business purpose crosses a defined threshold.

If your AI system impacts the physical well-being, legal rights, or life opportunities of a human being, you must document it. You have to document predictable failures. You must identify the specific demographic groups your system affects. Then you must document the exact human oversight mechanisms you built to prevent harm.

This documentation becomes your primary defense when a regulator knocks on your door.

## Data Provenance Is Your Only Defense

Garbage in means liability out.

I recently audited an enterprise deploying a machine learning model for credit scoring. I asked the engineering team where they got their training data. They told me they scraped it from various public financial forums over three years. They had no records of the data changes, no metadata, and no quality metrics. We had to shut the project down.

ISO 42001 demands rigorous data management. You cannot just feed random data into a model.

You must document the exact provenance of your data. You need to know exactly when it was created, updated, and transformed. You must measure the data quality and document known biases.

If you use supervised machine learning, you must separate your training, validation, and testing data. You must prove that your training data accurately represents the real-world operational domain where the AI will actually function. If you cannot prove where your data came from, you cannot prove your AI is fair.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/03/some-photos-of-googles-new-ironwood-tpu-based-ai-superpods-v0-wjcm913lfxzf1.webp?w=1024)

## Stop Giving Vendors a Free Pass

Most companies do not build their own AI models. They buy them from third-party suppliers.

Procurement teams regularly buy software simply because the vendor slaps an "AI-powered" label on the website. They sign the contract without asking a single question about algorithmic transparency.

ISO 42001 explicitly requires you to manage supplier relationships based on AI-specific risks. You assume the liability when you deploy a vendor's black-box model inside your operations.

You must force your suppliers to show their work. Require them to provide adequate technical documentation. Demand explanations of their algorithmic design choices. If a vendor's system performs poorly or produces biased outputs, your contract must give you the authority to demand immediate corrective actions.

If a supplier refuses to explain how their model works, you must disqualify them.

## Kill the Annual Audit

You cannot monitor an AI system once a year.

A model can drift out of its acceptable performance range in three days if the incoming production data changes. ISO 42001 requires continuous monitoring and evaluation.

You must establish specific, measurable performance criteria. You need to determine acceptable error rates based on the real-world impact of false positives and false negatives. You might determine that an F1 score is your primary metric. Once you set that baseline, you must continuously monitor the system against it.

You also need automated event logging. You must record the exact time the AI runs, the specific production data it processes, and any outputs that fall outside your intended operating conditions.

You must provide a reporting mechanism for users to flag unexpected behaviors instantly. Do not wait for a quarterly compliance review to discover your customer service bot is hallucinating refund policies.

Governance is no longer about writing policies. It is about engineering continuous control systems.

When was the last time you verified the data provenance for your most critical AI vendor?

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative risk modeling, predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and internationally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance landscapes.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
