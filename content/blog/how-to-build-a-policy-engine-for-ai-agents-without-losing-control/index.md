---
title: "How to Build a Policy Engine for AI Agents Without Losing Control"
date: 2026-06-27
tags: 
  - "agentic-ai"
  - "agentic-controls"
  - "ai"
  - "ai-governance"
  - "ai-governance-policy"
  - "artificial-intelligence"
  - "business"
  - "chatgpt"
  - "hernan-huwyler"
  - "iso-42001"
  - "iso-23894"
  - "llm"
  - "technology"
---

You cannot govern an enterprise AI system with a polite text prompt. I learned this through several close calls where agents interpreted user requests in technically correct but organizationally dangerous ways. The most unnerving part was not the mistakes themselves. It was realizing a carefully constructed system prompts can easly become a security theater.

For months, I treated [AI governance](https://hernanhuwyler.wordpress.com/2026/06/17/the-pren-18286-reality-check/) like a communication problem. I wrote clearer instructions. I added strict safety rules to the context window. I tested edge cases in isolation. It felt like rigorous work at the time. But language models are probabilistic by nature. They interpret. They weigh competing instructions. They will always find creative ways around your rules because they are not following rules at all. They are predicting tokens.

Prompts are suggestions. Policy engines are law.

I recommend building deterministic enforcement before you scale any AI agent system. The right policy engine makes your agents faster, safer, and actually trustworthy in production. This is not about creating the infrastructure that lets you move faster because you know what your agents cannot break.

This guide shows you how to build that system. You will learn how to intercept agent actions before they execute, how to write path-aware policies that catch multi-step risks your prompts cannot see, and how to roll out enforcement without blocking legitimate work. I cover patterns grounded in formal research and production architectures from teams running agents at scale. You get working code, real YAML policy examples, and the three-phase rollout process I use to deploy governance layers without breaking existing workflows.

If you are a CAIO, engineering lead, or platform architect responsible for AI systems touching production data, customer interactions, or external APIs, this will change how you think about control. You will stop asking "how do I write better prompts?" and start asking "how do I build infrastructure that enforces what matters?".

That shift is the difference between hoping your agents behave and knowing they cannot misbehave.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/06/chatgpt-image-jun-27-2026-08_22_16-am.png?w=1024)

* * *

## Why Prompts Alone Cannot Govern AI Agents

Prompts are non-deterministic by nature. The same instruction produces different behavior across different contexts, temperatures, and model versions. This is fine for creative tasks. It is dangerous for compliance. Prompt-level instructions shape the distribution over possible agent paths. They do not evaluate those paths. There is a fundamental difference between influencing behavior and enforcing it.

Static role-based access control has the opposite problem. It is deterministic but path-blind. It can block an agent from accessing a table directly, but it cannot detect when an agent reads from a CRM, combines that data with another API call, and then emails the result externally. Each individual step looks permitted. The combined path is a data breach.

Your policy engine needs to solve both problems. It needs to be deterministic like access control and path-aware like a runtime monitor.

* * *

## The Core Architecture: Three Layers You Need

Security for agentic systems requires three distinct layers working together: Identity, Topology, and Semantics.

- **Identity** answers who is asking. This means not just the user, but the agent identity, the task context, the session state, and the trust level assigned to that agent in this particular workflow. Most teams skip agent-level identity entirely. That is the gap attackers and runaway agents both exploit.

- **Topology** answers what path has been taken. A policy engine without path awareness cannot catch multi-step risk. If your agent reads user records and then tries to send an email, the email action should be evaluated in the context of what just happened, not as an isolated request.

- **Semantics** answers what is actually being attempted. An agent calling /api/data to read a public report is different from the same agent calling /api/data with filters that expose private user records. The endpoint is identical. However, you cannot perform live LLM-based intent classification in the critical path without destroying latency. Instead, semantics must be evaluated using pre-computed metadata, regex patterns on payloads, or asynchronous LLM controls that tag session context before the deterministic policy engine runs.

* * *

Python`# Minimal policy context structure @dataclass class PolicyContext:     agent_id: str     user_id: str     session_id: str     trust_level: str          # "low", "medium", "high"     path_history: list        # previous tool calls this session     proposed_action: dict     # what the agent wants to do next     shared_state: dict        # accumulated facts (sensitivity tags, etc.)     timestamp: datetime`

Build your context aggregator first. Every other component depends on having this data available at evaluation time.

* * *

## How the Policy Function Works in Practice

A policy is a deterministic function. It takes the agent identity, the partial path so far, the proposed next action, and the current organizational state. It returns a violation probability.

That is it. That is the whole idea.

In practice, you compile your policies at deployment time rather than evaluating raw text at runtime. This matters enormously for latency. Compiled IF-THEN policies with Redis caching can evaluate in under 10 milliseconds, provided they are evaluating deterministic state tags rather than running live natural language processing. Runtime text parsing is nowhere near that fast.

Below is a simplified implementation of the evaluation loop. This code acts as a security checkpoint. It intercepts an AI [agent's proposed action](https://hernanhuwyler.wordpress.com/2026/03/31/guide-to-ai-agent-risk-and-control-management-across-the-full-lifecycle/) and evaluates it against a registry of safety and compliance policies. It checks a 60-second cache to avoid redundant processing, then fetches only the specific rules applicable to the agent's identity and task.  
Fails fast on critical threats: As it loops through the rules, it instantly aborts and blocks the action if any single policy returns a critical severity violation. For non-critical issues, it calculates the combined statistical [probability of risk](https://hernanhuwyler.wordpress.com/2026/05/08/the-pren-18228-problem-why-your-ai-risk-assessment-will-fail-the-first-real-test/) to decide whether to allow, log, flag for human approval, or block the action.

```
import mathclass PolicyEngine:    def __init__(self, policy_registry, state_store, cache):        self.policies = policy_registry        self.state = state_store        self.cache = cache    def evaluate(self, context: PolicyContext) -> PolicyDecision:        # Step 1: Check cache        cache_key = self._build_cache_key(context)        cached = self.cache.get(cache_key)        if cached:            return cached        # Step 2: Get applicable policies        applicable = self.policies.get_applicable(            agent_id=context.agent_id,            action_type=context.proposed_action["type"],            trust_level=context.trust_level        )        # Step 3: Evaluate each policy        violations = []        for policy in applicable:            result = policy.evaluate(context)            if result.violated:                violations.append(result)                if result.intervention == "block" and result.severity == "critical":                    return PolicyDecision(                        action="block",                        reason=result.reason,                        policy_id=policy.id                    )        if not violations:            decision = PolicyDecision(action="allow")            self.cache.set(cache_key, decision, ttl=60)            return decision        # Step 4: Composite risk score        combined_violation = 1 - math.prod(            1 - v.probability for v in violations        )        # Step 5: Threshold decision + cache        decision = self._apply_thresholds(combined_violation, violations)        self.cache.set(cache_key, decision, ttl=60)        return decision    def _apply_thresholds(self, probability, violations):        if probability > 0.8:            return PolicyDecision(action="block", violations=violations)        elif probability > 0.4:            return PolicyDecision(action="require_approval", violations=violations)        elif probability > 0.1:            return PolicyDecision(action="log_and_continue", violations=violations)        return PolicyDecision(action="allow")
```

The composite probability formula deserves attention. You do not want a single low-risk policy to block otherwise safe work. You also do not want twelve small risks to add up without visibility. The multiplicative formula captures this cleanly by calculating the probability that at [least one risk materializes](https://hernanhuwyler.wordpress.com/2026/03/28/how-to-actually-use-iso-iec-23894-for-ai-risk-management/). However, be aware of the statistical assumption here: this formula assumes violations are independent. If your policies are highly correlated (e.g. read\_pii and export\_data), they may artificially inflate the score. In mature systems, you may need to apply correlation weights. Even so, as a baseline, two 30% independent risks combine to about 51% total, which correctly triggers approval rather than a hard block.

To truly operationalize this policy loop, we have to stop treating AI security like a game of whack-a-mole. Most companies today make a critical architectural mistake: they evaluate AI actions in isolation, relying on flimsy system prompts to enforce good behavior. But real enterprise risk rarely happens in a single, isolated step, it happens in the sequence. Imagine an AI customer service agent that reads a highly confidential medical record (a perfectly legitimate internal action) and then attempts to send an email summary to an external vendor (a standard workflow step). Evaluated separately, both actions look completely fine to a basic security filter. Evaluated together, they constitute a catastrophic data breach. From a business perspective, your control architecture must shift from "stateless permission checks" to tracking the AI's behavior and context over time.

This brings us to a foundational control concept that protects the business without killing innovation: asymmetric scrutiny based on reversibility. In plain terms, [not all AI actions carry the same risk](https://hernanhuwyler.wordpress.com/2026/03/15/ai-threat-and-vulnerability-assessment/), so your policy engine shouldn't paralyze operations by blocking them all equally. If our AI assistant summarizes that sensitive medical record into an internal, secure case-management draft, the action is reversible; if something goes wrong, a human can simply delete the draft. The policy engine should allow and log this to maintain business velocity. However, if the AI tries to fire off an external email or trigger a financial API with that same data, the action is irreversible, the data has left the building. Your policy engine must understand this difference, applying hard, automated blocks to irreversible actions while applying lighter friction to internal, reversible simulations.

Under the hood, enforcing this requires the policy evaluation loop to implement a modernized adaptation of the classic Bell-LaPadula security model used by intelligence agencies since the 1970s. When an AI accesses a high-risk data source, the system is no longer path-blind. Instead, the policy engine attaches a persistent taint tag to the agent’s session state. As the AI moves through its workflow, this risk state travels with it. If the tainted agent subsequently attempts to push data to a public-facing API or a lower-security environment, the policy engine instantly detects a Bell-LaPadula violation, the cardinal rule of "no writing sensitive data to unclassified zones". Because this is tracked via lightweight state tags rather than heavy runtime text analysis, the Redis-backed evaluation loop catches the taint and kills the process in milliseconds.

The ultimate technical stress test for this architecture is the multi-agent gap. Enterprise AI is rapidly moving away from single monolithic chatbots toward automated swarms, where specialized agents hand off tasks to one another. Agent A might securely ingest sensitive financial data, process it, and hand the plain text over to Agent B, whose only job is to format and send external emails. If your policy function only monitors individual agents, the risk state artificially disappears the moment the data changes hands; Agent B has no idea the text is highly confidential, creating an invisible, disastrous data leak. To prevent this, your control architecture must operate at the orchestration layer. The policy function must continuously pass the taint and shared context across all agents, systems, and tools, ensuring that zero-trust compliance is an unbroken chain from the first data pull to the final automated execution.

* * *

## Writing Policies That Actually Work

This is where most teams go wrong. They write policies that are either too broad (blocking legitimate work constantly) or too narrow (missing the actual risks).

Three principles matter above everything else.

**Only encode rules** that are genuinely non-negotiable into hard policies. Business logic that changes, preferences, and stylistic constraints belong in prompts. Compliance rules, security boundaries, and irreversible controls belong in the policy engine.

**Sstructure your policies in layers.** Organizational baseline policies apply to every agent. Department or team policies narrow further. Agent-specific policies handle edge cases.

**Make violations explainable**. The agent needs to understand why something was blocked so it can replan. A policy that just returns "denied" creates confusion. A policy that returns "denied: external email action requires manager approval because user data was read earlier in this session" gives the agent a path forward.

```
YAML# policies/data-exfiltration-prevention.ymlid: DEP-001name: Data Exfiltration Preventionversion: 2.1severity: criticalpath_aware: truetrigger:  action_types:    - email_send    - file_export    - api_write_external    - webhook_postpath_conditions:  operator: ANY            prior_actions_include:    - read_user_records    - read_payment_data    - read_health_records    - query_pii_fieldsevaluation:                  mode: require_approval  approver: data_protection_officer  timeout_hours: 24  on_timeout: blockviolation_message: |        This action is blocked because sensitive data was accessed  earlier in this session. Sending data externally after  accessing PII requires explicit approval.  Session path: {path_summary | default: "unavailable"}  Accessed data types: {sensitivity_tags | default: "unknown"}violation_message_fallback: |  This action is blocked because sensitive data was accessed  earlier in this session. Review session logs for details.audit:  log_full_path: true  include_evidence: true  retention_days: 2555     # 7 years for compliance
```

Notice the path condition. A plain email action is not blocked. The same email action after reading user records is blocked. That is [path-aware governance](https://hernanhuwyler.wordpress.com/2026/03/15/ai-governance-from-compliance-task-to-operations/) doing what prompts cannot.

* * *

## Intercepting Agent Actions Before They Execute

The policy engine is useless if agents can route around it. The interception layer is your enforcement point, and it needs to be architectural rather than optional.

The SELinux-inspired approach described in several open-source implementations treats the policy engine as a mandatory kernel layer. Every tool call passes through it. There is no bypass. The agent framework does not get to decide whether to check policies. The infrastructure enforces the check.

In practice, this means placing the policy engine between your agent orchestrator and your tool registry:

```
from datetime import datetime, timezoneclass PolicyEnforcedToolRegistry:    def __init__(self, tool_registry, policy_engine, state_manager):        self.tools = tool_registry        self.engine = policy_engine        self.state = state_manager    def execute_tool(self, agent_id: str, tool_name: str,                     parameters: dict, session_context: dict) -> ToolResult:        # Build evaluation context        context = PolicyContext(            agent_id=agent_id,            session_id=session_context["session_id"],            user_id=session_context["user_id"],            trust_level=session_context.get("trust_level", "low"),            path_history=self.state.get_path(session_context["session_id"]),            proposed_action={                "type": tool_name,                "parameters": parameters            },            shared_state=self.state.get_shared(session_context["session_id"]),            timestamp=datetime.now(timezone.utc)           )        # Evaluate before execution        decision = self.engine.evaluate(context)        if decision.action == "block":            return ToolResult(                success=False,                error=decision.reason,                audit_entry=self._create_audit_entry(context, decision)            )        if decision.action == "require_approval":            audit_entry = self._create_audit_entry(context, decision)            self.state.record_pending_action(                session_id=session_context["session_id"],                action=tool_name,                parameters=parameters,                status="pending_approval",                audit_entry_id=audit_entry.id            )            return self._request_human_approval(context, decision)        try:            result = self.tools.execute(tool_name, parameters)        except Exception as e:            self.state.record_action(                session_id=session_context["session_id"],                action=tool_name,                parameters=parameters,                result_summary="FAILED",                sensitivity_tags=[],                error=str(e)            )            return ToolResult(                success=False,                error=f"Tool execution failed: {str(e)}",                audit_entry=self._create_audit_entry(context, decision)            )        # Update path state after execution        self.state.record_action(            session_id=session_context["session_id"],            action=tool_name,            parameters=parameters,            result_summary=result.summary,            sensitivity_tags=result.sensitivity_tags        )        if decision.action == "log_and_continue":            self._log_risk(context, decision, result)        return result    def _request_human_approval(self, context, decision):        approval_id = self._create_approval_request(context, decision)        return ToolResult(            success=False,            pending_approval=True,            approval_id=approval_id,            message=f"This action requires approval. Request ID: {approval_id}"        )    def _log_risk(self, context, decision, result=None):        self.audit_log.write({            "session_id": context.session_id,            "agent_id": context.agent_id,            "action": context.proposed_action,            "decision": decision.action,            "violations": decision.violations,            "result_summary": result.summary if result else "unknown",            "sensitivity_tags": result.sensitivity_tags if result else [],            "timestamp": datetime.now(timezone.utc).isoformat()        })
```

The state update after execution is critical. This is how path history accumulates. Each tool call records what happened, what data was touched, and what sensitivity tags apply. The next tool call evaluation uses this history.

* * *

## Progressive Rollout: Why You Should Not Start With Enforcement

Starting with hard enforcement is a mistake. You will block legitimate work, frustrate your team, and lose confidence in the system before it has a chance to prove itself.

I have found this three-phase genuinely effective.

### Phase One: Observation Only

Deploy the policy engine with all interventions set to "log". Run it for two to four weeks. Collect data on what would have been blocked, what would have required approval, and what would have passed. Use this data to calibrate your thresholds and fix policies that fire too broadly.

**Start by instrumenting your existing agent workflows without changing any behavior.** Set up your `PolicyEnforcedToolRegistry` to wrap every tool call, but configure the engine to return `action="allow"` for every decision while logging the full evaluation result. This means agents work exactly as they did before, but now you can see every policy violation that would have triggered in production. Create a daily dashboard that shows violation counts by policy ID, agent ID, and severity level. Pay special attention to policies that fire more than 10 times per day. Those are either protecting something genuinely risky or misconfigured to be too broad.

**The real work in phase one is pattern analysis, not policy enforcement.** After the first week, export your violation logs and group them by policy and violation reason. Look for false positives first. If your `data-exfiltration-prevention` policy fires 47 times because your documentation bot sends daily wiki updates via email, that is not a security risk. That is a bot doing its job. Either add an exception for that specific agent's trust level or refine the `prior_actions_include` condition to distinguish between public wiki reads and private user record reads. Run this analysis weekly. By week three, you should see violation rates drop by 40 to 60 percent as you tune out the noise. If your rates are not dropping, your policies are either perfectly calibrated from day one (unlikely) or you are not refining them aggressively enough.

* * *

### Phase Two: Soft Enforcement

Enable blocks for critical-severity policies only. Everything else stays at "log and alert". Your team gets used to seeing policy feedback without being constantly interrupted.

**At the start of phase two, communicate the change clearly to your team before flipping the switch.** Send a message explaining that critical-severity policies will now actively block agent actions, and include the specific list of which policies qualify as critical. In most organizations, this means four to six policies: production database writes without approval, external data exfiltration after PII access, authentication or authorization changes, and financial transactions above a threshold. Announce a two-week grace period where blocks will be reviewed within four hours and overrides will be granted liberally if the block was inappropriate. This builds trust. Your team needs to know they will not be stuck for days waiting on a policy decision while a deadline passes.

**Use this phase to test your approval workflow under real load.** When a critical policy blocks an agent action and requires human approval, measure three things: time to first response, approval or rejection rate, and whether the requester understood why the block happened. If your average response time is over two hours, your approval process is too slow for production use. If your rejection rate is under 10%, your critical policies are probably too sensitive and should be downgraded to medium severity. If more than 20 % of approval requests include a comment like "why was this blocked?" your violation messages are not clear enough. Fix those messages now, before phase three. Also track how often the same agent and action pair gets blocked repeatedly. If the same bot tries to export user data five times in a week and gets approved every time, that is not a policy working correctly. That is a poorly scoped policy annoying your team.

* * *

## Phase Three: Full Enforcement

Enable all interventions. By this point, you have enough data to know your policies are accurate, and your team has enough familiarity that the guardrails feel helpful rather than hostile.

**Full enforcement means turning on medium and low-severity policies in addition to the critical ones you enabled in phase two.** But do not enable them all on the same day. Roll out one new severity tier per week. Start with high-severity policies in week one of phase three, then medium-severity in week two, then low-severity in week three. This staged approach gives you time to catch any policy that was undertested during observation. Watch your metrics closely during each new tier activation. If you see a sudden spike in blocks for a specific policy, pause that policy immediately, review the last 10 violation cases, and decide whether the policy needs refinement or your team needs training on how to work within the constraint.

**Phase three is also when you introduce policy version control and change management.** By now, your policies are live and affecting real work. Any change to a policy can either improve or degrade your system's usability. Treat policy changes like code changes. Require pull requests for policy updates, include a changelog entry explaining why the change was made, and run a policy diff tool that shows exactly which actions will be affected by the new version. Before merging, test the updated policy against the last 30 days of agent activity logs to simulate how it would have behaved. If the simulation shows the updated policy would have blocked 15 percent more actions than the current version, that is a red flag. Review those cases manually before deploying. Finally, add a rollback plan. If a new policy version causes problems in production, you need a one-command way to revert to the previous version while you investigate. I keep the last three policy versions in the registry with feature flags controlling which version is active. That saved me twice when a policy update had unintended side effects.

Always build a break-glass procedure for your infrastructure team. Production systems fail in completely unpredictable ways. I learned this the hard way when a database migration failed and the engine blocked our automated rollback script. You must give administrators a secure way to temporarily bypass the rules during a severe outage.

![](https://hernanhuwyler.wordpress.com/wp-content/uploads/2026/06/a9b048b9-da91-470e-be51-504507823866-edited.png)

* * *

## The Audit Trail: Your Most Important Compliance Output

Every policy decision needs a “why trail". This is not optional if you are building in a regulated environment. The EU AI Act Article 12 explicitly requires that high-risk AI systems generate logs sufficient to reconstruct how each decision was produced.

This requirement is not satisfied by the mere ability to assemble events after the fact. Article 12(1) requires the automatic recording of events over the lifetime of the system, which implies contemporaneous capture at the moment the decision occurs. In practice, that means logs must be generated by design, not retrospectively derived from accumulated system data. More importantly, those records must be reliable, secure, and protected against alteration if they are to withstand regulatory scrutiny. A mutable audit log undermines the very reconstruction capability it claims to provide.

Trustworthiness frameworks such as prEN 18229‑1 and governance standards like ISO42001 reinforce this principle: accountability depends not only on retaining records, but on ensuring their integrity and verifiability. In evidentiary terms, there is a material difference between reconstructing a decision from stored artifacts and producing a contemporaneous, tamper‑evident record created at the point of interception. Regulators assessing serious incidents or malfunctions will examine whether the record was sealed at creation, access-controlled, and protected through appropriate retention and integrity safeguards. Implementing cryptographic controls, secure timestamping, write‑once storage, and controlled access mechanisms transforms a technical log into defensible compliance evidence aligned with Article 12, NIS2 logging expectations, GDPR accountability principles, and digital evidence guidance such as ISO 27037.

Even if you are not in a regulated industry, audit trails catch bugs in your policies and prove to stakeholders that the system works.

Python`@dataclass   class AuditEntry:       entry_id: str       timestamp: datetime       session_id: str       agent_id: str       user_id: str       proposed_action: dict       path_summary: list          # what happened before this action       policies_evaluated: list    # which policies ran       policy_versions: dict       # exact version of each policy       decision: str               # allow, block, require_approval       violation_details: list     # which policies fired and why       evidence: dict              # the facts that led to the decision       intervention_taken: str     # what actually happened       confidence_score: float     # how certain the engine was      `def create\_audit\_entry(context, decision, policies\_evaluated):  
    return AuditEntry(  
        entry\_id=generate\_uuid(),  
        timestamp=datetime.now(timezone.utc),  
        session\_id=context.session\_id,        `agent_id=context.agent_id,           user_id=context.user_id,           proposed_action=context.proposed_action,           path_summary=summarize_path(context.path_history),           policies_evaluated=[p.id for p in policies_evaluated],           policy_versions={p.id: p.version for p in policies_evaluated},           decision=decision.action,           violation_details=decision.violations,           evidence=extract_evidence(context, decision),           intervention_taken=decision.action,           confidence_score=decision.confidence       )`

Store audit entries separately from application logs. They need longer retention, different access controls, and tamper-evident storage if you are in a regulated context. Seven years is a common retention requirement in financial services.

* * *

## The Tradeoff Nobody Talks About

More policies mean more safety and less agent capability. This is real and you have to manage it.

The Commonwealth Bank team found that over-constraining their ReAct agents produced worse outcomes than under-constraining them. When the agent could not plan flexibly because too many intermediate steps were blocked, it either failed the task or produced low-quality results that required more human intervention.

The right mental model is surgical precision. Your policy engine should have clear opinions about a small number of high-stakes decisions: external data exfiltration, production database writes, financial transactions, authentication changes, and irreversible actions. For everything else, trust the agent and log the results.

Yeah, this sounds obvious. But watch how many teams apply their entire security checklist as hard policy blocks and then wonder why their agents are useless.

Policies are force multipliers for human judgment. They should encode the decisions where human oversight is mandatory, not the decisions where human oversight would be nice to have.

* * *

## Where to Start Today

You do not need to build this entire system in week one.

Start with the interception layer and a single policy file covering your three highest-risk action types. Deploy in observe mode. Let it run for two weeks and look at the data. Your first policy file will be wrong. That is expected and fine.

The open-source repos from the Commonwealth Bank team (github.com/smartnose/policy-enforcer and github.com/WeiOnThePike/policy-enforcer-sk) give you working implementations for LangChain and Semantic Kernel. Start there rather than from scratch.

For production systems, the Microsoft Agent Governance Toolkit includes a full Agent OS kernel with YAML policy support, 34 tutorials, and integration with Open Policy Agent. It is worth the investment if you are running multiple agents in a shared environment.

The core insight from all of this research is straightforward. AI agents produce real consequences in the real world. Prompts are suggestions. Policy engines are law. Build the law first, then give your agents the freedom to work within it.

By Prof. Hernan Huwyler, CAIO MBA CPA  
[Hernan Huwyler (0009-0002-1249-7387) - ORCID](https://orcid.org/0009-0002-1249-7387)  
[ResearchID.co - Hernan Huwyler](https://researchid.co/hewyler)  
[https://www.researchgate.net/profile/Hernan-Huwyler](https://www.researchgate.net/profile/Hernan-Huwyler)

## About the Author

The frameworks, tools, and implementation guidance described in this article are part of the applied research and advisory work of Prof. Hernan Huwyler, MBA, CPA, CAIO. These materials are freely available for use, adaptation, and redistribution in your own AI governance, risk management, and compliance programs. If you find them valuable, the only ask is proper attribution. If you like the content, please like the article and share it.

Prof. Huwyler serves as AI GRC Consultancy Director, AI Risk Manager, and Quantitative Risk Lead, working with organizations across financial services, technology, healthcare, and public sector to build practical AI governance frameworks that survive contact with production systems and regulatory scrutiny. His work bridges the gap between academic AI risk theory and the operational controls that organizations actually need to deploy AI responsibly.

As a Speaker, Corporate Trainer, and Executive Advisor, he delivers programs on AI compliance, quantitative [risk modeling,](https://github.com/hwyler/risk-model-app) predictive risk automation, and AI audit readiness for executive leadership teams, boards, and technical practitioners. His teaching and advisory work spans IE Law School Executive Education and corporate engagements across Europe and internationally.

Based in the Copenhagen Metropolitan Area, Denmark, with professional presence in Zurich and Geneva, Switzerland, Madrid, Spain, and Berlin, Germany, Prof. Huwyler works across jurisdictions where AI regulation is most active and where organizations face the most complex compliance, technical and business requirements.

His code repositories, risk model templates, and Python-based tools for AI governance are publicly available at [https://hwyler.github.io/hwyler/](https://hwyler.github.io/hwyler/). His ongoing writing on Governance, Risk Management and Compliance appears on his blogger website at [https://mydailyexecutive.blogspot.com/](https://mydailyexecutive.blogspot.com/) (more than 500k views).

Connect with Prof. Huwyler on LinkedIn at [linkedin.com/in/hernanwyler](https://linkedin.com/in/hernanwyler) to follow his latest work on AI risk assessment frameworks, compliance automation, model validation practices, and the evolving regulatory landscape for artificial intelligence.

If you're building an AI governance program, standing up an AI risk function, preparing for EU AI Act compliance, or looking for practical implementation guidance that goes beyond policy documents, reach out. The best conversations start with a shared problem and a willingness to solve it with rigor.
