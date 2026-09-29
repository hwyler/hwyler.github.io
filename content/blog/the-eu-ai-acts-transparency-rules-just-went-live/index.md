---
title: "The EU AI Act's Transparency Rules Just Went Live"
date: 2026-08-03
tags: 
  - "ai"
  - "ai-compliance"
  - "ai-generated-labels"
  - "artificial-intelligence"
  - "chatgpt"
  - "digital-marketing"
  - "eu-ai-act-art-50-transparency-disclosure-compliance"
  - "hernan-huwyler"
  - "technology"
---

## Most AI Managers Think Disclosure and Watermark Requirements Got Cancelled or Delayed

I had a call with a compliance officer at a company that sells software into the Nordics. Smart person. Experienced team. They've been preparing for the EU AI Act for over a year.

She told me they stood down their Article 50 work in early July after reading that the AI Act had been delayed. Her team is now focused on the high-risk system requirements, which don't kick in until December 2027. She seemed confident. Relieved, even.

I asked her what their chatbot says when someone first opens it. She paused. "What do you mean?" I mean does it tell users they're interacting with AI, I said. There was a longer pause. "We're waiting for the final guidelines on that". However, the transparency guidelines have been out since June. The deadline is Sunday August 2nd, 2026. And the penalties start at fifteen million euros.

The EU's Digital Omnibus package (now law) delayed the heavy high-risk AI system obligations, such as the Annex III standalone systems for recruitment, credit scoring, education. These requirements were pushed to December 2027, and systems embedded in regulated products as medical devices, machinery, toys to August 2028. However, Article 50 was untouched. **The transparency obligations, chatbot disclosure, synthetic content marking, deepfake labeling, emotion recognition notification, landed on August 2nd, 2026 as originally scheduled**. The EU AI Office's fining powers switched on the same day.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/e5e98900-bf40-4b7a-b6d4-a5fe39af5b7b-edited.png)

## Core Requirements

I created a summary of the most common controls for AI disclosures.

- **Chatbot Disclosure**  
    Systems interacting directly with people must inform users from the start unless it is obvious. Notifications are skipped only if the AI nature is completely clear to a normal, observant person. Implement a permanent, visible text banner directly on the chat interface stating the user is interacting with an AI. Do not bury this disclosure in a welcome menu or a hidden terms of service link. Ensure the notification is accesible for blind and other disabled users.  
    Give your AI a persistent, non-human identity so users never mistake it for a real person. Label the exact action the system performed using clear verbs instead of dropping a generic badge on the screen. Apply a unique visual style exclusively to synthetic content so it stands apart from human work instantly. Never fake human empathy, and always give your users an immediate mechanism to opt out and reach a real employee.  
    

- **Synthetic Content Marking**  
    Generative audio, image, video, and text must use machine-readable watermarks or labels showing AI manipulation. Embed cryptographic metadata like C2PA Coalition for Content Provenance and Authenticity directly into the exported file right at the generation source. You must build automated tests in your publication pipeline to verify this metadata survives format conversions, image resizing, and social media uploads. Add a visible AI icon in the top right corner of visual media to provide immediate human recognition without requiring the user to click anything. For audio outputs, insert a plain language audible disclaimer at the very beginning of the track stating the content is synthetic.  
    

- **Public Interest Labeling**  
    Deployers publishing text about public interest matters must label it as AI-generated. Place the AI disclosure immediately above the headline or inside the colophon so readers see it before they read the actual article. If you want to claim the editorial exemption, you must formally assign legal editorial responsibility to a specific, named human being in your organization. You must publish the contact details of that responsible editor publicly on your website to ensure accountability.   
    

- **Deepfake Identification**  
    Audio, video, and image deepfakes require clear, human-readable labels. Embed an overlaid label directly onto the video that remains visible through the entire clip, especially after commercial breaks or interruptions. If the deepfake is purely satirical or artistic, place the disclosure in the opening credits or directly adjacent to the frame so it does not ruin the viewing experience. Design the label with high contrast so users with color vision deficiencies can easily perceive it. Provide a simple intake channel for the public to flag missing deepfake labels and assign a team to correct them immediately.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/gemini_generated_image_e1d9gle1d9gle1d9.png?w=1024)

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/untitled-1.png?w=593)

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/screenshot-2026-08-02-221028.jpg?w=265)

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/screenshot-2026-08-02-222621.jpg?w=904)

## What Actually Got Delayed

On June 29, 2026, the European Union approved something called the Digital Omnibus on AI. It pushed back the compliance deadlines for high-risk AI systems. Systems classified under Annex III, which cover things like biometric identification and critical infrastructure, got moved from August 2026 to December 2027. Systems classified under Annex I, which cover AI embedded in regulated products like medical devices, got pushed to August 2028.

The headlines that followed talked about the AI Act being delayed or watered down. A lot of GRC professionals read those headlines and paused their compliance work. Some stopped entirely.

Here's what actually happened. The high-risk system obligations got deferred. Article 50 transparency obligations did not.

Article 50 covers a different set of requirements. If your AI system interacts directly with people, like a chatbot or virtual assistant, you have to tell users they're talking to AI. If your system generates synthetic content, like images, audio, video, or text, that content has to be marked in a machine-readable format so it can be detected as AI-generated. If you publish deepfakes or AI-generated text on matters of public interest, you have to label it. If you use emotion recognition or biometric categorization systems, you have to inform the people being scanned.

None of that got cancelled. All of it starts Sunday, August 2nd, 2026.

There's one narrow grace period. If you're a provider of a system that was already on the market before August 2nd, and that system generates synthetic audio, image, video, or text, you have until December 2nd, 2026 to get the machine-readable marking in place. That's it. Everything else goes live in five days.

## The Role Problem Nobody Wants to Talk About

The compliance officer I spoke with assumed her vendor was handling Article 50. The vendor assumed she was. Neither of them had read the legal definitions carefully enough to realize they both have obligations.

Under the AI Act, a provider is the entity that develops or places an AI system on the market under its own name. A deployer is the entity that uses the system under its own authority. If you license a third-party chatbot and put it on your website, you're the deployer. Your vendor is the provider. You both have duties.

The provider has to design the system so it can disclose that it's AI. The deployer has to configure it so it actually does.

If you built your chatbot internally, you're both. You carry both obligations. You can't blame the underlying model vendor.

This is where most companies are getting it wrong. They think compliance is something they buy from a vendor. It's not. Compliance is something you implement in your own product, with your own controls, and your own evidence.

I continue to see AI compliance and developing forums claiming that the EU AI Act requires platforms to deploy AI detectors to identify synthetic content uploaded by users. That interpretation is incorrect and risks sending engineering teams in the wrong direction.

Article 50 does not require providers or deployers to scan user uploads with probabilistic AI detection models. Current AI detection tools produce inconsistent results, generate false positives, and cannot reliably distinguish human-created from AI-generated content. The European Commission recognizes these technical limitations and instead emphasizes transparency by design through provenance mechanisms and machine-readable disclosures whenever technically feasible.

For providers of generative AI systems, the obligation is fundamentally different. The focus is on ensuring that content generated by their own systems carries appropriate machine-readable information, such as provenance metadata or other technical markers, that can support downstream transparency. The Commission's guidance identifies approaches, cryptographic provenance, and robust watermarking technologies as examples of technical measures that can help satisfy these obligations, while acknowledging that implementation will continue to evolve as standards mature.

This distinction matters. Detecting AI-generated content after publication is fundamentally different from preserving trustworthy provenance at the moment content is created. The first attempts to infer authorship with uncertain probabilities. The second establishes verifiable evidence within the generation pipeline itself.

For engineering teams, the investment should focus less on unreliable detection products and more on building transparent-by-design systems. Practical implementation starts with assigning AI systems a persistent, distinguishable identity so users immediately recognize they are interacting with software rather than a human. User interfaces should disclose the specific action performed by the AI, such as generating, summarizing, translating, or editing content, instead of displaying vague "AI-powered" labels. Synthetic images, audio, and video should include visible disclosures where required, while preserving machine-readable provenance metadata whenever technically feasible. Organizations should also establish governance controls to verify that metadata survives storage, export, and distribution across supported platforms.

The technical challenge is no longer building better AI detectors. It is designing trustworthy AI systems whose outputs remain transparent, traceable, and verifiable throughout their lifecycle. That is where engineering effort, governance controls, and compliance evidence should be concentrated.

## What Clear and Distinguishable Actually Means

The European Commission's guidelines on Article 50 are detailed. Section 7 in particular matters more than most people realize, because it changes what transparency means in practice.

The guidelines say that information will not be considered clear and distinguishable if it can be easily overlooked or missed by users under normal conditions. That's a user perception test, not a disclosure test. It doesn't matter if you technically provided the information. What matters is whether people actually notice it.

The guidelines explicitly reject disclosures that are buried in user manuals, hidden inside terms and conditions, or accessible only after navigating through several menus. Those might satisfy an internal compliance checklist, but they don't help users understand that they're interacting with AI.

**The information has to be noticeable, easy to understand, accessible, and clearly separated from other content.** Users shouldn't have to search for it, interpret legal jargon, or figure out whether a message is relevant to them. If the disclosure blends into the interface or competes with other visual elements, transparency becomes significantly less effective.

This has real implications. The location matters. The wording matters. Whether it stands out from surrounding content matters. Whether different groups of users, including children and people with disabilities, can realistically understand it matters.

The quality of transparency is determined not only by what you communicate, but by how users experience that communication.  
  
Summary of requirements and compliance actions

| **Article 50 Requirement** | **What the Requirement Means**      **Developer and Deployer Responsibilities** | **How to Comply**      **Since August 2nd, 2026** |
| --- | --- | --- |

| **Article 50(1)**      **Disclosure that Users Are Interacting with an AI System (Chatbots)** | Users must be informed when they interact with an AI system instead of a human, unless this is obvious from the context. The provider must design the system to support clear disclosure. The deployer must ensure the disclosure appears before or at the start of the interaction. The notice should use plain language that users can easily understand. Users should not have to search for the information. Example: "You are chatting with an AI assistant that can make mistakes. You may request a human representative at any time". | Add a clear disclosure message before the first interaction. Display the notice consistently across web, mobile, voice, and messaging channels. Include the disclosure in the user interface design and product requirements. Test that users can easily see and understand the message. Document where and how the disclosure appears. Keep screenshots, user interface specifications, and test evidence. Maintain version control showing when the disclosure was introduced. Review disclosures after major system updates. Train product owners and customer support teams on the requirement. |
| --- | --- | --- |

| **Article 50(2)**      **Disclosure of AI-Generated or Manipulated Synthetic Content** | Providers must ensure that AI-generated image, audio, video, or text content is marked in a machine-readable manner whenever technically feasible. The purpose is to improve traceability of synthetic content rather than informing end users directly. The deployer should preserve these technical markers whenever content is distributed. The marking should remain attached during normal processing whenever possible. Exceptions apply where other Union law provides different requirements. Example: an AI-generated image contains embedded provenance metadata following the C2PA standard. | Embed machine-readable provenance metadata into generated content. Use recognized technical standards such as C2PA or digital watermarking where appropriate. Validate that metadata remains after export and distribution whenever feasible. Record the technical method used for marking. Maintain technical documentation describing the implementation. Perform testing to verify metadata persistence across supported platforms. Monitor whether downstream processes remove metadata. Keep engineering records, validation reports, and change logs as compliance evidence. Update implementation as standards evolve. |
| --- | --- | --- |

| **Article 50(3)**      **Disclosure of Emotion Recognition and Biometric Categorization Systems** | People exposed to emotion recognition or biometric categorization systems must be informed before or at the time the system operates, unless an exception applies under the AI Act. The provider should enable the deployer to provide this information. The deployer is responsible for notifying affected individuals in practice. The notice should explain that AI is analyzing emotional expressions or biometric characteristics. The information should be clear and visible before data collection begins. Example: a sign at the entrance of a customer service area explains that AI analyzes facial expressions to measure customer satisfaction. | Display notices before the system collects or analyzes data. Update privacy notices and operational procedures to include the AI transparency statement where applicable. Ensure notices appear in physical locations, applications, or websites depending on deployment. Document where disclosures are presented. Keep copies of signs, interface screenshots, and notification text. Train employees operating these systems on when disclosures are required. Verify during audits that notices remain visible and accurate. Maintain records showing the notification process has been reviewed and approved. Coordinate compliance with GDPR and other applicable privacy requirements. |
| --- | --- | --- |

| **Article 50(4)**      **Disclosure of Deepfakes and AI-Generated Public Content** | AI-generated or manipulated image, audio, or video that resembles real persons, objects, places, or events must be clearly disclosed as artificially generated or manipulated, unless an exception applies. This disclosure is intended for people who view or consume the content. Providers should support deployers with technical capabilities to apply labels. Deployers are responsible for presenting clear disclosures when publishing the content. The disclosure should remain associated with the content whenever reasonably possible. Example: a synthetic executive video displayed on a company website includes the label "AI-generated video" visible during playback and in the accompanying description. | Apply a clear human-readable label directly on or alongside the content before publication. Keep the disclosure visible throughout playback when practical. Combine visible labels with machine-readable provenance metadata whenever possible. Define organizational procedures for identifying deepfake content before release. Maintain approval workflows requiring verification that labeling has been applied. Keep copies of labeled content as compliance evidence. Document the technical tools used to generate and label the content. Periodically review published materials to verify labels remain present after distribution. Retain records demonstrating compliance with Article 50 and supporting technical documentation. |
| --- | --- | --- |

## The Obvious Exception Is Not a Loophole

Article 50 says you don't have to inform people when it's obvious they're interacting with an AI system. A lot of organizations are reading that exception as a way out. The Commission's guidelines make it clear that interpretation is wrong.

The exception has to be interpreted restrictively because it removes an important safeguard for users. In practice, you shouldn't ask whether you believe the AI nature of the interaction is obvious. You should ask whether an average person who is reasonably well-informed, observant, and circumspect would immediately recognize that they're interacting directly with an AI system.

If the answer is uncertain, you disclose.

This assessment depends on context. A conversational AI assistant with a clearly synthetic voice or an interface explicitly branded as an AI chatbot might satisfy the obvious exception in some situations. The same assumption would be much harder to justify where AI is embedded into existing customer service channels, professional workflows, or other environments where users could reasonably expect to interact with a human.

The obvious exception should not be treated as a convenient way to avoid transparency notices. It should be treated as a narrow exception you can rely on only where you can confidently demonstrate that the average user would immediately recognize the AI nature of the interaction.

When in doubt, the Commission's message is clear. Transparency remains the safer and more compliant approach.

## Disclosure Is Continuous, Not a One-Time Event

Another common assumption is that transparency is achieved by displaying a disclosure once, at the beginning of an interaction. The guidelines make it clear this is not always sufficient.

The Commission recognizes that people don't always experience AI content from the beginning. They may join a conversation halfway through, start watching a video after it's already begun, encounter AI-generated content while scrolling through a social media feed, or enter increasingly immersive digital environments where the boundary between human and AI interaction becomes less obvious.

In these situations, a disclosure shown only once may never achieve its intended purpose.

The practical implication is to identify the moments when users are most likely to need the information and consider whether additional disclosures are necessary to maintain awareness throughout the interaction.

Transparency has its own lifecycle. It may begin before the interaction starts, appear again when users enter a new context or reach an important decision point, and continue for as long as it's needed to ensure meaningful awareness.

The objective is not to maximize the number of disclosures. It's to maximize the likelihood that users actually recognize when they're interacting with AI.

## The Code of Practice Is Not Immunity

On July 8, 2026, the European Commission concluded that the Code of Practice on Transparency of AI-Generated Content adequately covers key Article 50 obligations for marking, labeling, and disclosure of AI-generated content. Signatories can rely on the Code's measures to demonstrate compliance and may benefit from a more predictable, EU-wide implementation framework.

A lot of companies are treating that like a safe harbor. It's not.

The Code does not replace the AI Act. It does not replace the Commission's Article 50 guidelines. And adherence to the Code does not constitute conclusive evidence of compliance. It creates a recognized compliance pathway, not a shield from examination.

Companies that treat Code signature as the end of compliance are likely to be exposed when authorities look for actual implementation. AI interaction disclosures, machine-readable marking, deepfake labels, public-interest text disclosures, accessibility, timing, and evidence that the notices were clear and distinguishable at first interaction or exposure.

A recognized compliance pathway is not the same as evidence of implementation. The market is about to learn the difference.

## Who This Actually Affects

The Article 50 obligations apply to any provider or deployer of an AI system that reaches EU users, regardless of where the company is based. A US company selling a chatbot product used by European customers is subject to Article 50. A US company deploying AI-generated content that reaches European audiences is subject to Article 50.

The territorial scope is deployment, not incorporation.

The enforcement mechanism operates through national market surveillance authorities in each EU member state. Fines are set at up to fifteen million euros or up to three percent of global annual turnover, whichever is higher. For a company with five hundred million euros in global revenue, the headline fine tier reaches fifteen million. For companies above that revenue level, the potential maximum scales with global turnover.

Enforcement is not going to be immediate for every non-compliant deployment. National authorities will prioritize investigations, and the first cases will likely target visible violations in high-attention sectors. But the enforcement infrastructure activates Sunday, and the evidentiary record of non-compliance begins accumulating at the same moment.

## What You Should Be Doing for AI Transparency Compliance

I'm going to be direct about what needs to happen between now and Sunday.

**First, inventory every AI interface your organization operates. Internal and external. Customer-facing chatbots, employee-facing tools, AI agents, anything that interacts directly with people or generates content that people see.**

Second, add the disclosure. A visible, plain-language notice at first interaction. Not in your terms and conditions. Not in a footer. Not hidden behind a menu. At the point where the user first encounters the AI.

**Good disclosure: "You are interacting with an AI assistant. This tool generates responses based on our internal documents. Always verify critical information."**

Bad disclosure: "AI-enhanced experience" buried in the footer of your website. A mention in your forty-page privacy policy. "Powered by Vendor Name" with no indication it's AI. Relying on users figuring it out from the conversation style.

Third, document it. Screenshot the interface. Date it. File it. You need evidence that the disclosure was in place, visible, and clear.

Fourth, assess synthetic content generation. Does your system create new text, images, audio, or video, or does it just retrieve existing content? If it creates, you need a plan for machine-readable marking. That's the watermarking and metadata work. You have until December for that piece if your system was already on the market, but you should start now.

Fifth, review your vendor contracts. If a vendor provides your AI, make sure their roadmap includes disclosure and marking capabilities. Make sure the contract clearly allocates who is responsible for what. If the vendor can't or won't comply, that's a procurement problem, and it's still your compliance risk.

Sixth, train your teams. Article 4 of the AI Act requires AI literacy for people working with AI systems. That obligation also goes live Sunday. Employees need to understand what AI is, what it isn't, and what the transparency requirements mean in practice.

Seventh, if you haven't already, sign the Code of Practice. It takes twenty minutes. Download the signatory form from the EU Digital Strategy website, have a senior executive sign it, email it to the Commission. You'll be publicly listed as a signatory. That gives you a recognized compliance pathway and reduces enforcement scrutiny. It's not a substitute for actual implementation, but it's a useful signal that you're taking this seriously.

## Start With the System Inventory, Not the Policy

Every Article 50 implementation I've seen that actually works starts the same way. Someone sits down and makes a list of every AI system the organization develops, deploys, or procures. Not categories of systems. Actual systems. With names, owners, and current production status.

For each one, you answer four questions.

- _Does it interact directly with people?_ Chatbots, virtual assistants, AI customer service agents, conversational tools in apps, AI-powered phone systems. If yes, Article 50(1) applies.

- _Does it generate synthetic content?_ Text, images, audio, video. If yes, Article 50(2) applies.

- _Does it perform emotion recognition or biometric categorization?_ If yes, Article 50(3) applies. But check Article 5 first, because some of these uses have been entirely prohibited since February 2, 2025. If your system falls under the workplace or education prohibition, compliance with Article 50 won't save you. The use is banned.

- _Could it be used to create deepfakes, or does it generate text published on matters of public interest? I_f yes, Article 50(4) applies.

Then for each system, you determine whether you're the provider, the deployer, or both. The provider is the entity that develops the system or places it on the market under its own name. The deployer is the entity that uses it under its own authority. If you built it internally, you're both. If you licensed it from a vendor and put it on your website, your vendor is the provider and you're the deployer. You both have obligations, and your vendor's compliance does not automatically cover yours.

I've seen teams spend weeks debating the definitions. Don't. The definitions are in the regulation. If you're genuinely uncertain about a specific system, document the uncertainty and apply the more conservative interpretation. You can refine it later. What you can't do is leave it unclassified and hope nobody asks.

The inventory is not a nice-to-have. It's the foundation everything else sits on. If you don't know what systems you have, you can't know what controls apply.

## Control Set 1: AI Interaction Disclosure

If your system interacts directly with people, Article 50(1) requires you to inform them they're interacting with AI. This applies to providers. If you're the deployer of a third-party system, make sure your vendor has built this capability and you've actually turned it on.

The control is simple. Display a visible notice before or at the start of the interaction. The notice has to be clear and distinguishable, which the Commission's guidelines define as noticeable, easy to understand, accessible, and clearly separated from other content.

Good examples:

"You are chatting with an AI assistant. Responses are generated automatically and may contain errors. Verify critical information before acting on it."

"This is an automated AI system. For questions requiring human judgment, type 'agent' to reach a person."

Bad examples:

"AI-enhanced experience" in your website footer with no indication when the AI is actually active.

A mention buried in your forty-page privacy policy.

"Powered by \[Vendor Name\]" with no explanation that it's AI.

A disclosure that only appears after the user has already typed their first message.

The notice has to meet accessibility requirements. That means WCAG compliance and European Accessibility Act standards. If a user with a screen reader or visual impairment can't perceive the disclosure, it doesn't count.

There's an exception for situations where the AI nature of the interaction is obvious. The guidelines make it clear this exception is narrow. Obvious means obvious to a reasonably well-informed, observant, and circumspect person. Not to your engineering team. Not to people who work in AI. To a regular user encountering the system for the first time.

A chatbot widget clearly labeled "AI Assistant" might qualify. A human-sounding voice assistant probably doesn't, even if the voice sounds slightly synthetic. A conversational tool embedded in an existing customer service workflow almost certainly doesn't.

If you're relying on the obvious exception, document why. Write down the facts that support the conclusion. Include screenshots of the interface. Get a second opinion from someone outside your team. If a regulator questions it later, you'll need to show you made a good-faith assessment, not a convenient assumption.

There's also an exception for law enforcement use, where the system is authorized by law to detect, prevent, investigate, or prosecute criminal offenses. That exception does not apply if the system is available for the public to report crimes. Document whether your use qualifies, and if it does, document the legal basis.

The implementation steps are straightforward.

- Add the disclosure to the interface. Make it visible. Make it appear before the user interacts.

- Test it with actual users, including users with disabilities.

- Document it. Screenshot the interface. Record the date. File the evidence.

- Train the people responsible for maintaining the system. They need to know the disclosure requirement exists and what happens if it breaks.

- Set up monitoring. Verify the disclosure is still showing up correctly after every product update, every vendor patch, every configuration change.

- Prepare the documentation for inspection. National market surveillance authorities can request evidence of compliance. You need to be able to show them the disclosure, explain how it works, and prove it's been in place since August 2.

## Control Set 2: Synthetic Content Marking

If your system generates synthetic audio, image, video, or text, Article 50(2) requires you to mark that content in a machine-readable format and make it detectable as artificially generated. This applies to providers, including providers of general-purpose AI models.

This is the most technically demanding obligation in Article 50, and it's the one most companies are handling badly.

The European Commission's Code of Practice on Transparency of AI-Generated Content, published June 10, 2026, lays out a multi-layer technical approach. The Code creates a presumption of conformity. If you adhere to it, regulators have to prove you're non-compliant, not the other way around. If you don't adhere to it, you can use alternative technical approaches, but you'll carry the burden of proving they meet the same effectiveness, interoperability, robustness, and reliability requirements.

Most companies should sign the Code. The compliance benefit outweighs the implementation cost.

The Code specifies three layers.

Layer one is C2PA Coalition for Content Provenance and Authenticity metadata. You embed cryptographically signed provenance information directly in the content file. The metadata has to be interoperable, verifiable, and human-inspectable. C2PA is a technical standard developed by the Coalition for Content Provenance and Authenticity. It's supported by Adobe, Microsoft, Google, and most of the major platforms. If you're generating images, video, or audio at scale, this is the baseline.

Layer two is imperceptible watermarking. You embed invisible markers that survive format conversion, compression, and basic editing. Google's SynthID is one implementation. There are others. The watermark has to be robust enough that it doesn't disappear the moment someone resizes an image or re-encodes a video.

Layer three is visible labeling. This is recommended but not strictly required under the Code. It means user-facing indicators like icons, badges, or text labels that identify AI-generated content. A visible label makes it easier for users to calibrate their trust without needing technical tools to read metadata or detect watermarks.

The technical solutions you implement have to meet four criteria: effective, interoperable, robust, and reliable, as far as technically feasible given the state of the art. That language is important. You're not required to achieve perfection. You're required to use the best available methods and document why you chose them.

There's an exception for systems that perform only standard editing. Spelling, grammar, formatting, basic transformations that don't substantially alter the input data or its semantics. A spell checker doesn't trigger Article 50(2). A tool that rewrites a paragraph to change its tone probably does.

If you're uncertain whether your system qualifies for the assistive function exception, document the analysis. Describe what the system does. Explain why you believe it falls under standard editing. Get technical input. Get legal input. File the conclusion. If a regulator disagrees, you'll at least be able to show you thought about it.

There's a transitional deadline for this obligation. AI systems already on the market before August 2, 2026 have until December 2, 2026 to comply with content marking requirements. New systems placed on the market after August 2 have to comply immediately.

The implementation steps are more involved than the disclosure controls.

- Evaluate technical solutions. C2PA, SynthID, IPTC metadata. Pick the combination that works for your content types and your distribution channels.

- Implement the marking at the point of generation. The metadata and watermark have to be embedded when the content is created, not added later as a post-processing step.

- Test robustness. Verify that the watermark survives format conversion, compression, and basic editing. Take a generated image, resize it, convert it to a different file format, compress it, and check whether the watermark is still detectable. If it's not, your implementation doesn't meet the robustness requirement.

- Test the full publication path. Generate a piece of content, mark it, then follow it all the way through your CMS, API, export process, platform upload, whatever route it actually takes to reach users. Verify the mark is still detectable at the endpoint. I've seen implementations where the generation-time marking worked perfectly, but the CMS stripped the metadata during publication. That's a silent failure. The only way to catch it is to test the real path.

- Document the compliance changes. Record which technical solutions you implemented, how they work, which content types they cover, what testing you performed, and what the results were.

- Set up monitoring. Verify that marking continues to work correctly after every system update.

- Prepare for inspection. Regulators can request evidence that your content is being marked and that the marking is detectable. You need to be able to demonstrate both.

## Control Set 3: Emotion Recognition and Biometric Categorization Notification

If you deploy emotion recognition or biometric categorization systems, Article 50(3) requires you to inform the people exposed to them. This applies to deployers.

Before you implement this control, check Article 5. Emotion recognition in workplaces and educational institutions has been entirely prohibited since February 2, 2025. There are narrow exceptions for medical or safety purposes, but the default is a ban. If your use falls under Article 5(1)(f), compliance with Article 50 won't help. The use is illegal.

Assuming your use is permitted, the control is notification. You have to inform natural persons that the system is in operation, before or during their exposure.

This usually means updating your privacy notices. The notice has to be clear, accessible, and provided at a time when the person can actually see it before the system processes their data.

Good example: "This facility uses AI-based biometric categorization for access control. By entering, you consent to the processing of your biometric data in accordance with our privacy policy."

Bad example: A privacy notice posted on a website that people read weeks before they ever encounter the system.

The notification has to comply with GDPR. That means lawful basis, transparency, data minimization, purpose limitation, and all the rest. Article 50(3) doesn't replace GDPR. It adds to it.

There's an exception for law enforcement use, where the system is used for detecting, preventing, or investigating criminal offenses and the use is permitted by law with appropriate safeguards. Document the legal basis if you're relying on this exception.

The implementation steps are similar to the AI interaction disclosure controls.

- Update your privacy notices. Make sure they explicitly mention emotion recognition or biometric categorization.

- Post physical notices if the system operates in a physical location.

- Test accessibility. Make sure people with disabilities can perceive the notice.

- Document the notification mechanism and when it was implemented.

- Train staff on the data protection responsibilities.

- Set up monitoring to verify the notices remain in place.

- Prepare for inspection.

## Control Set 4: Deepfake and AI-Generated Text Disclosure

Article 50(4) has two parts. One applies to deepfakes. The other applies to AI-generated text published on matters of public interest.

For deepfakes, the deployer has to disclose that the content has been artificially generated or manipulated. A deepfake is AI-generated or manipulated image, audio, or video content that resembles existing persons, objects, places, or events and would falsely appear to a person to be authentic or truthful.

Three criteria have to be met. The content has to resemble something that exists or could plausibly exist. It has to create a false appearance of being authentic or truthful. And a person viewing it has to reasonably be deceived.

The guidelines allow you to consider the deployment context and the audience's expectations. Background scenes and special effects in a clearly fictional movie probably don't constitute deepfakes because the audience doesn't expect them to be real. A synthetic news anchor in a video that looks like a legitimate news broadcast probably does.

The disclosure has to be clear and distinguishable. It has to be visible or audible. It can't rely solely on the machine-readable mark embedded by the provider under Article 50(2). Users have to be able to see it without technical tools.

There's a limited exception for artistic, creative, satirical, fictional, or analogous works. For these, the disclosure requirement is lighter. It has to exist, but it can't hamper the display or enjoyment of the work. A watermark or end-credit notice might be sufficient.

For AI-generated text on matters of public interest, the deployer has to disclose that the text was artificially generated or manipulated. Matters of public interest include politics, public administration, justice, law enforcement, fundamental rights, public security, public health, environmental protection, consumer safety, and economic, financial, political, scientific, or cultural developments relevant to public debate.

There's an exception if the text has undergone human review or editorial control and a natural or legal person holds editorial responsibility. Human review means deliberate examination of the substance by someone with relevant knowledge and professional judgment. Editorial control means a responsible editorial entity has the authority to approve, alter, or reject the substance based on factual accuracy and trustworthiness of sources.

Superficial checks like spell-checking or grammar correction don't count.

If you're relying on the editorial control exception, document who performed the review, what their qualifications are, who holds editorial responsibility, and what the review process involved.

The implementation steps are similar to the other controls.

- Create workflows for identifying content that requires disclosure. Is it a deepfake? Is it AI-generated text on a public-interest topic? Does an exception apply?

- Add the disclosure mechanism. For deepfakes, that usually means a visible label or audible notice. For AI-generated text, it might be a byline, a notice at the top of the article, or a label in the publication interface.

- Document the process. Record which content was disclosed, when, and how.

- Train content creators, editors, and publishers on the disclosure requirements.

- Monitor compliance after publication.

- Prepare for inspection.

## Cross-Cutting Controls That Apply to Everything

There are five controls that cut across all four Article 50 obligations.

First, accessibility. Every disclosure, notice, label, and notification you implement has to meet WCAG standards and European Accessibility Act requirements. If a person with a disability can't perceive it, it doesn't satisfy the legal obligation.

Second, documentation. You need records of every AI system subject to Article 50, its classification, which sub-obligations apply, whether you're the provider or deployer, what transparency measures you implemented, what technical solutions you used, what exceptions you relied on, who you trained, and what monitoring you performed. If a regulator asks, you need to be able to produce the evidence quickly and completely.

Third, staff training. The people responsible for maintaining these systems need to know the requirements exist, what they mean, and what happens if something breaks. This isn't a one-time exercise. New hires need to be trained. Product updates need to be reviewed. Vendor changes need to be assessed.

Fourth, monitoring. You need ongoing verification that the controls are still working. Disclosures are still showing up. Marks are still detectable. Notices are still posted. Workflows are still being followed. Set up automated checks where possible. Do manual spot checks where automation isn't feasible.

Fifth, inspection readiness. Article 50 is enforced by national market surveillance authorities. They can request documentation, test your systems, and verify compliance. You need to be able to respond quickly with complete, organized, defensible evidence.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/08/chatgpt-image-aug-2-2026-08_13_40-pm.png?w=1024)

## The First Real Test

Sunday is the first live transparency test of what EU AI Act enforcement will look like in practice. It's not the biggest test. The high-risk system deadlines in December 2027 and August 2028 will produce much larger enforcement stakes, because the systems covered are more consequential and the penalties for non-compliance under those provisions will be more severe.

But Sunday is when the enforcement muscle first activates. The AI Office begins operating. National authorities gain formal powers. The first investigations can begin. Informal warnings may follow. Formal enforcement actions will come after that.

Companies operating in the European market that spent the last six weeks assuming the deadline was cancelled will discover in the next six weeks that it was not. Companies that took the Digital Omnibus as an opportunity to strengthen their compliance infrastructure will have documented, defensible evidence when the first examinations begin.

Companies that treated it as an opportunity to stand down will not.

The compliance officer I spoke with yesterday is now scrambling. Her team has five days to add disclosures to three different products, document the implementation, train the support team, and get legal sign-off. It's doable, but it's tight, and it didn't need to be this way.

A lot of companies are in the same position. They read the headlines, not the regulation. They assumed delay meant cancellation. They stood down when they should have been building.

The deadline is Sunday. The penalties start at fifteen million euros. And whether you knew about it or not stopped mattering the moment the regulation entered into force.

Are your AI systems ready for August 2nd, 2026?

  
Relevant publications on AI disclosure and the EU AI Act

* * *

**1\. Responsible AI Policy Categories**

Covers the transparency principle as one of eight AI policy foundations, explicitly mapping it to EU AI Act Article 13 on transparency for high-risk systems, the notification requirements for AI-human interaction and synthetic content disclosure (originally referenced as Article 52, now Article 50), and ISO 42001 transparency control objectives — including proactive disclosure before or during interaction, explainability at audience-appropriate levels, and security testing for prompt injection, data poisoning, and privacy leakage.

https://hernanhuwyler.wordpress.com/2026/03/16/responsible-ai-policy-categories/

* * *

**2\. Rules for AI Use, Accountability, BYOAI, Safety by Design, and Content Provenance**

Defines a dedicated content provenance policy requiring organizations to identify and disclose AI-generated or AI-modified content in external communications, implement C2PA verification mechanisms to protect against deepfakes and misinformation, disclose AI tool usage in client agreements, and prohibit presenting AI-generated analysis as human analysis without disclosure, mapped to EU AI Act transparency requirements, OECD AI Principles, and GDPR Articles 13-15 and 22.

https://hernanhuwyler.wordpress.com/2026/03/16/rules-for-ai-use-accountability-byoai-safety-by-design-and-content-provenance/

* * *

**3\. Practical Implementation Tips for a Fundamental Rights Impact Assessment for High-Risk AI Systems**

Directly implements EU AI Act Article 27 (fundamental rights impact assessment for deployers of high-risk AI), with a dedicated transparency section covering traceability of AI system decisions, explainability requirements, communication to affected persons, and a recommended public-facing AI transparency register, cross-referencing Articles 9, 13, 14, and 15 on risk management, transparency obligations, human oversight, and accuracy/robustness.

https://hernanhuwyler.wordpress.com/2026/03/12/practical-implementation-tips-for-a-fundamental-rights-impact-assessment-for-high-risk-ai-systems/

* * *

**4\. How to Actually Use ISO/IEC 23894 for AI Risk Management**

Provides step-by-step implementation of the ISO 23894 AI risk management standard, which maps directly to EU AI Act Article 9 risk management requirements covering AI system inventory (the foundation for all disclosure obligations), stakeholder mapping, risk identification across organizational/individual/societal impact levels, documentation and recording requirements with persistent risk IDs and version-controlled risk registers for audit traceability, and the seven treatment options including the AI-specific risk-benefit analysis for residual risk disclosure.

https://hernanhuwyler.wordpress.com/2026/03/28/how-to-actually-use-iso-iec-23894-for-ai-risk-management/

* * *

**5\. Your Vendor's "We Don't Train On Your Data" Promise Is a Sentence, Not A Data Architecture**

Addresses the contractual disclosure gap between AI vendors and buyers, requiring vendors to disclose in signed contracts what happens to prompts, outputs, logs, retrieval embeddings, fine-tuned model weights, telemetry, and behavioral patterns after sessions end and after contract termination, directly relevant to the provider transparency obligations under EU AI Act Article 13 and the technical documentation requirements under Annex IV, where providers must document data governance, training methodologies, and third-party component usage.

[https://hernanhuwyler.wordpress.com/2026/07/21/your-vendors-we-dont-train-on-your-data-promise-is-a-sentence-not-a-data-architecture/](https://hernanhuwyler.wordpress.com/2026/07/21/your-vendors-we-dont-train-on-your-data-promise-is-a-sentence-not-a-data-architecture/)

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and consulting work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative [risk modeling,](https://github.com/hwyler/risk-model-app) predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and internationally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance, technical and business requirements.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
