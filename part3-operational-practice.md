# AI Doesn't Break the Laws of Software Evolution — Part 3

## Governance disciplines, the verification floor, and harness engineering — what the framework looks like in operational practice

---

[Part 1](part1-laws-and-empirical-record.md) diagnosed the AI coding paradox through Lehman's five structural regularities, with Level 2 spec governance as the operational answer at the code-spec boundary. [Part 2](part2-framework.md) extended this to the two-loop architecture (Laws 1, 6, 8) — Loop 1 calibrating system understanding against runtime reality, Loop 2 calibrating intent against evolving user need and business strategy — and established that two conservation constraints bound the volume of value creation. AI multiplies density per unit of bounded activity rather than volume, lifting four ratios when governance is in place.

This part is the practical companion. Given the framework, what does an organization actually do — at each loop, on each ratio — to convert the structural opportunity into compounding value-density gains. The answer is not a single playbook. It is a set of disciplines applied at two distinct levels of the system, calibrated to where the organization currently is.

## First: Stop Measuring the Conserved Quantity

The single most consequential practical change is reframing what gets measured. Most organizational AI maturity dashboards measure proficiency proxies — tool adoption rates, percentage of code AI-generated, PRs merged per developer, feature velocity. Under Lehman conservation, these are the wrong metrics. Activity volume is bounded; reporting it as a productivity gain confuses redistribution for improvement.

Each of the four ratios has known operational proxies. These are starting points for organizations to build their own value-density measurement, not a ready-to-deploy dashboard. The framework's claim is that these are the right things to triangulate; the work of stitching them into actionable measurement is the organization's, and is itself one of the under-observed durable bets Part 4 identifies (verification infrastructure includes measurement infrastructure).

**Value per unit activity** is the hardest to measure directly but the most important. Proxies: defect rates per PR (lower density of bugs per PR = higher value density); rework rate (PRs that survive without follow-up correction); architectural decisions traceable to documented intent versus drift; time-to-resolution on incidents tied to specific subsystems. None of these are perfect. Together they triangulate.

**Value per unit time** is operationalized as calendar-time-to-business-outcome rather than calendar-time-to-merge. Shipping code faster is not value if the code shipped is the wrong code. The right metric runs from intent-formation to validated business outcome, including the time spent in both loops.

**Value per unit capital** requires honest cost accounting. Total cost includes tooling licenses, developer time at fully loaded cost, review and verification cost, incident response cost, and the carrying cost of complexity debt. Most organizations only count the first. The ratio improves only when the value lift exceeds the full cost stack.

**Value per person involved** depends on whether the strategy is workforce reduction or workforce repurposing. The ratio improves under either; the organizational implications differ profoundly. Be explicit about which path the organization is on.

Without reframed metrics, every other practical step is invisible. Volume metrics actively obscure the dimensions where AI helps. But also: the proxies above remain proxies. The honest organizational stance is to instrument the proxies, watch them over time, and treat the measurement program itself as engineering work that compounds — exactly the verification-infrastructure pattern Part 4 names as a durable bet. The framework gives you the right dimensions to track. Building the measurement that converts those dimensions into operationally useful signals is the organization's own engineering investment, and one that the empirical record suggests very few organizations have made yet.

## Governance at Loop 1: System Understanding

This is the most familiar loop and where most practical AI governance literature focuses. The spec is the primary actionable artifact, but it serves a broader objective: keeping the shared model of how the system should work calibrated against how the system actually does work. Tests, observability, code review, debugging, and post-mortems all serve the same loop. The work here breaks into four disciplines.

**Establish the persistent, bidirectional spec.** Move from CLAUDE.md as super-prompt to spec-anchored architecture as Part 1 described. Concretely: the spec lives in the repo, updates flow back from implementation discoveries, production signals feed in, and the spec is consulted at every generation step rather than only at session start. SLUMP measured the persistence-and-consultation half in benchmark conditions; the writeback half is the engineering work organizations need to build for themselves — light at first (post-incident spec updates, code review notes feeding back into spec sections, periodic spec-vs-reality audits) and progressively more automated as tooling catches up. The work is unglamorous — naming things, documenting decisions, capturing edge cases as they emerge — but the empirical lift on the persistence half alone is substantial, and the writeback half compounds it further.

**Separate WHAT, BOUNDARIES, and HOW into distinct artifacts.** The spec carries WHAT and BOUNDARIES. Skills carry recurring HOW patterns. Code is generated implementation within those constraints. The discipline is to resist the natural pressure, when an agent misbehaves, to add HOW rules to the spec. That path leads to MDA-style bloat. Skills are the pressure valve that protects spec integrity.

**Distinguish capability scaffolds from context scaffolds explicitly.** Maintain a register that classifies each rule, skill, or constraint as either compensating for current model limitation (capability) or encoding organizational knowledge the model cannot know (context). Capability scaffolds need quarterly deprecation reviews triggered by model upgrades. Context scaffolds need update reviews triggered by architectural or business change. Conflating them produces governance debt in both directions: scaffolds that were necessary for GPT-4-era models persist past their useful life, while context that should have been captured stays in senior engineers' heads.

**Budget refactoring as an explicit percentage of agent capacity.** The He et al. data implies that AI-generated complexity rises by roughly 41.6% under typical adoption. To hold complexity flat under Law 2, refactoring effort needs to scale proportionally. A practical rule: 20-25% of agent capacity on refactoring and counter-work, treated as non-negotiable rather than as something that gets cut under deadline pressure. Teams that don't enforce this watch complexity compound until velocity collapses on the timeline the He et al. data predicts.

## Governance at Loop 2: Intent Alignment

This loop is rarely owned at the engineering boundary even though it determines whether engineering's output produces value. Most of the practical work is organizational rather than technical, with one major change in 2026: AI as intelligence substrate is now a direct participant in the loop, not just a consumer of its outputs. The frameworks that have served this loop for decades — OKRs, product reviews, customer feedback cycles, build-measure-learn — remain foundational; what AI changes is the achievable cadence and the scale of signal synthesis.

**Assign explicit ownership of intent-need alignment.** Someone has to own the question "does the spec still ask for what users and the business actually need?" In most organizations this is implicit and therefore unowned. Product managers own roadmap; engineering owns implementation; nobody owns the consistency between them at the spec level. The role doesn't need to be new; it needs to be explicit. A senior engineer or technical product manager whose job description includes maintaining spec-need alignment is the minimum viable configuration.

**Wire signals from users, production, and market into intent updates.** Incidents, user behavior signals, adoption metrics, competitive intelligence, regulatory shifts, market trend signals — all are evidence about whether intent still matches need. Most organizations route these to operations or marketing without ever asking whether they indicate the spec itself needs updating. The signals have to reach the people setting intent, not just the people responding to symptoms. AI now extends what is tractable here: continuous customer signal synthesis at scale, pattern detection in usage data, competitive intelligence aggregation, automated theme extraction from support and sales transcripts — work that historically waited for quarterly review can now flow continuously and inform intent in near real time.

**Compress intent review cadence to track the cadence of underlying change.** Annual strategic planning is incompatible with AI-accelerated execution. The activity rate is the same — Law 4 — but the cost of misaligned activity is amplified by proficiency. Quarterly intent reviews are the minimum; monthly is better; continuous (AI-mediated) is now technically feasible for the first time. The cost of running the loop faster is trivial compared to the cost of a quarter of misaligned execution.

**Tie architectural decisions to documented intent.** ADRs are the existing artifact best positioned to carry the intent-decision linkage. Every significant architectural decision should reference the intent it serves. When intent shifts, the ADR is a flag that the decision may need to be revisited. This is the audit trail that makes the loop legible.

**Treat strategic pivots as intent updates, not engineering disruptions.** When the business pivots, the question is not "how do we redirect engineering effort" but "how does the spec change to reflect the new intent." This reframing makes the pivot legible at every downstream level. The spec changes; the implementation reconciles to the new spec through Loop 1; the engineering effort follows naturally. Skipping the spec update produces the worst of all worlds — code drifts independently of both the old intent and the new strategy.

Stepping back: the five disciplines above describe one general operation AI now makes newly tractable — the measurer work Part 2 named via Drucker. Tracking OKR-to-outcome alignment continuously, synthesizing customer feedback at scale, detecting strategic drift in near real time, ensuring intent updates propagate to specs — these are tasks that historically required dedicated humans (middle management, operations, business analysts) to perform episodically. AI as intelligence substrate can perform them continuously and at scales humans alone could not reach. The governance work above is largely the work of deciding *what* to measure and *how* the signals flow into decisions; AI as intelligence substrate performs the measurement and synthesis itself. The same principle applies to Loop 1: the disciplines there decide what spec, what tests, what observability matter; AI performs the continuous reconciliation between them and runtime reality.

## Improving the Four Ratios

The governance work above sets up the conditions for ratio improvement. The actual lift comes from how the conserved activity gets directed within those conditions.

**Value per unit activity.** Concentrate AI on the activities where density gain is highest — design exploration, edge case generation, code review preparation, refactoring analysis. The instinct to use AI for raw code typing is the lowest-leverage application. Typing is rarely the binding constraint on value. Using an agent to surface fifteen alternative architectures during a design discussion produces more density gain than using it to autocomplete fifty CRUD endpoints.

**Value per unit time.** Compress decision latency at every loop level. Continuous loops, as Part 2 argued, are the lever here. The specific tactics: automate the detection side of spec-reality diffs so they surface in near real time; route conflicts to humans in batched but frequent reviews rather than letting them accumulate; reduce the queue depth between loops so signals from Loop 2 reach Loop 1 within weeks rather than quarters.

**Value per unit capital.** Substitute tooling for labor strategically, not uniformly. The capital efficiency gain is largest where the tooling reliably handles the work — well-scoped, well-specified, fast-feedback tasks. The capital cost is highest where governance overhead dominates — novel work, ambiguous requirements, long-horizon judgment. Avoid the trap of measuring tooling ROI in lines of code generated. Measure it in value delivered per dollar of fully loaded cost, including the governance overhead the tooling requires.

**Value per person involved.** Reallocate freed activity toward judgment-dense work — design, architecture, strategic alignment, review, mentorship. This is where individual humans produce disproportionate value and where AI cannot substitute. The opposite move — using freed activity to staff more parallel feature work — runs into the second conservation (absorbable content) and produces the Faros 2026 pattern of unreviewed PRs and quality degradation. The teams getting compounding value per person are the ones moving their humans up the abstraction stack as agents handle more of the routine implementation.

## The Verification Floor

There is a constraint underneath all four ratios that the series has only implied: value density only rises to the extent that AI's output is actually verified and absorbed. Unverifiable output doesn't carry value regardless of how much agent activity produced it.

The formalization comes from a recent paper by Catalini, Hui, and Wu (MIT / Washington University / UCLA, February 2026). They model the transition to advanced AI as the collision of two cost curves: a Cost to Automate that falls exponentially with compute and accumulated knowledge, and a Cost to Verify that is "biologically bottlenecked" — bounded by human time and embodied experience. The asymmetry creates what they call a Measurability Gap: a widening difference between what AI can execute and what humans can afford to verify. The verifiable share of agent output (s_v in their notation) is what separates truly productive output from merely plausible output.

A scope note. Catalini, Hui, and Wu's model operates at macroeconomic scale: it characterizes the transition where AI capability outruns human-bottlenecked verification across the economy as a whole. This paper applies their structural insight at organizational scale — the third novelty contribution signposted in the introduction, the *compound conservation extension* that combines Catalini-Hui-Wu's verification floor with Lehman's Laws 4 and 5 read as compound conservation tendencies — which is a meaningful scope change. The intra-organizational verification floor described here, and the multi-surface refinement developed below, are analogical extensions of Catalini et al.'s framework, not derivations from it. They inherit the *direction* of the conclusion — that verification cost is the binding constraint where execution becomes cheap — but not the formal proof. The 2024-2026 organizational evidence (He et al.'s complexity accumulation, Liu et al.'s debt persistence, Faros's review-time inflation, METR's experience reports) is consistent with the analogical extension; a formal model at organizational scale — measuring s_v inside teams, characterizing how it shifts with governance, calibrating where the floor sits for a given codebase — does not yet exist. Building that model is itself one of the verification-infrastructure durable bets Part 4 identifies.

![The verification floor: where AI-generated output stops being economically valuable, and how verification skill shifts that floor to the right](charts/part3_verification_floor.png)

*Illustrative. The verification floor is where cost to verify equals cost to automate. Below it, the verifiable share is high and automation pays off; above it, verification cost dominates and AI loses economic value. The dashed curve shows the framework's central practical claim: verification skill (and AI-assisted verification infrastructure) flattens the verification cost curve, shifting the floor substantially to the right. Model capability improvements move the red curve down; verification investment moves the floor.*

This is Lehman's Law 5 (Conservation of Familiarity) restated in economic terms. Lehman observed in the 1970s that sustainable software evolution was bounded by the comprehension bandwidth of those involved. Catalini et al. derive the same constraint from cost dynamics: verification capacity is the binding constraint when execution becomes cheap. Two paths to the same conclusion, forty-three years apart.

The cognitive-psychology foundation is older still. Lisanne Bainbridge's "Ironies of Automation" (1983) identified the paradox: automating the easy parts of a task leaves humans with the hard parts (judgment, exception handling, monitoring), and cognitive demands on remaining humans paradoxically increase rather than decrease. Skills atrophy from disuse precisely when they're most needed for intervention. Forty-three years later, the AI code review pattern matches Bainbridge's prediction — Sonar 2026 finds 96% of developers don't fully trust AI code accuracy while only 48% always verify, and Faros 2026 measures median PR review time up 441% with 31% of PRs merging without review.

This is the verification floor. Below it, the four ratios cannot improve regardless of how proficient the tooling becomes, because the value at the numerator depends on the work being correct, integrated, and absorbed — not just generated. Unverified output adds to the codebase but not to the value-producing portion of it. The He et al. complexity-accumulation data is essentially what happens when generation runs above the verification floor: the unverified portion comes back as defects, rework, and compounding entropy on the timeline the data documents.

The practical implication reframes Part 3's earlier advice. Verification infrastructure is not optional supporting infrastructure for governance — it is the binding constraint determining whether AI investments produce density gains or verification debt. Teams that scale AI generation faster than verification capacity are not getting more value per unit activity; they are accumulating unverified output that will manifest as Lehman-predicted entropy within months.

This sharpens which investments actually compound. Three categories matter most.

**Automated checks that genuinely substitute for human verification.** Static analysis, type systems, comprehensive test coverage, formal verification where applicable, contract testing at module boundaries. The goal is to raise the floor — increase the share of AI output that can be verified without consuming human cognitive load. Every unit of verification that can be performed mechanically is a unit of human capacity freed for higher-leverage judgment.

**Differential review concentration.** Apply scarce human verification to the highest-leverage portion of agent output (architectural decisions, security-critical paths, novel logic, anything touching invariants) rather than spreading it uniformly. Auto-approve low-risk changes with full automated coverage; deep-review high-risk ones with concentrated human attention. This is Salesforce Engineering's Prizm approach and the emerging best practice in the field. It treats human attention as the scarce resource it is.

**Verification skill development.** Bainbridge's skill-atrophy warning matters. If humans only ever rubber-stamp AI output, they lose the skills needed to catch the cases where the rubber stamp would have failed. Treating verification as a craft to invest in — through deliberate practice, rotation through high-stakes reviews, deep code reading exercises — preserves the capability the framework depends on. Verification expertise is an organizational asset, and Bainbridge's 1983 paper is essentially a warning about under-investing in it.

**An operational example.** AWS's Kiro IDE shipped two pieces in 2025-2026 that operationalize the verification floor framework directly. Requirements analysis (Dobe et al., AWS Applied Science, May 2026) uses neuro-symbolic techniques — LLMs paired with SMT solvers — to detect requirement-level bugs (ambiguity, inconsistency, completeness gaps, wrong level of detail) before any code is generated, surfacing problems as two-choice clarification questions for the user. Property-based testing (Eline, AWS, November 2025) translates specifications into executable Hypothesis tests with random input generation and counterexample shrinking, so verification scales sub-linearly with input space rather than linearly with hand-written test cases. Both are AI doing the measurer work humans historically did episodically: checking spec quality, generating tests, exploring input distributions. Both are deliberate engineering against the verification cost curve.

These pieces also surface a refinement worth naming: the verification floor isn't a single position but a stack of positions across multiple verification surfaces. Requirements analysis raises the floor at the *intent-to-spec* surface; property-based testing raises it at the *spec-to-code* surface; observability raises it at the *code-to-runtime* surface. Each layer's improvement amplifies the next — clearer specs make property-based testing more effective, better testing makes observability cheaper, cleaner runtime signals feed back into spec updates. Verification investment compounds multiplicatively across these surfaces. This is what the durable-bet category in Part 4 looks like operationalized at the infrastructure level — and why the framework predicts it.

**The internal structure of the floor.** The three surfaces are not equally hard to raise. Catalini et al.'s "biologically bottlenecked" characterization is accurate for the *code-to-runtime* surface, where review of judgment-dense paths and the cognitive work of integrating runtime signals with mental models depend on the comprehension bandwidth Law 5 names. Bainbridge's irony applies in full force here, and Shen and Tamkin's debugging-skill deficits in AI-assisted participants are field evidence of exactly this. The *spec-to-code* surface has a different cost-curve structure: an LLM reasoning about whether an implementation deviates from a documented specification — a semantic conformance check on every PR — is not biologically bottlenecked, runs at machine speed, scales with compute, and has a cost curve falling with model capability. The *intent-to-spec* surface sits between: the formal-methods machinery runs at machine speed, but the irreducible human input of knowing what the system is for remains bounded.

| Verification surface | Primary mechanism | Cost curve | Bottleneck type |
|---|---|---|---|
| Intent-to-spec | Spec quality discipline + LLM/SMT requirements analysis (Dobe et al., 2026) | Declining at the analysis layer | Human intent ownership |
| Spec-to-code | LLM semantic CI gate + property-based testing (Eline 2025; Roy 2026) | Declining with AI capability | Spec quality as upstream dependency |
| Code-to-runtime | Observability + human review of judgment-dense paths | Biologically bounded | Human comprehension bandwidth (Law 5) |

**The LLM as both problem and solution.** This distinction has a structural consequence. LLMs are simultaneously the mechanism that lowers the cost-to-automate — creating the drift acceleration the He et al. and Liu et al. data measure — and the first technology capable of lowering the cost-to-verify at the semantic specification layer, where natural-language specs were previously unparseable by automated CI systems. The same technology creates the governance problem and provides the governance solution. This changes the character of the verification floor from a fixed biological constraint into a moving threshold that verification-infrastructure investment can shift — but only at the surfaces where the machine-tractable mechanism applies. The floor at the *code-to-runtime* surface still moves only at the rate of human comprehension; the floor at the *spec-to-code* surface moves with model capability and engineering investment. Conflating the two understates what is now possible at the spec-conformance surface and overstates what is now possible at the runtime-review surface.

**Production-scale evidence: the Kitchen Loop.** The clearest current production-scale evidence for what a spec-anchored CI gate looks like in operation comes from Roy's (2026) Kitchen Loop, validated across two production systems — the Almanak SDK, a DeFi strategy framework spanning 14 chains, 30+ protocol connectors, and 21 intent types (~1,000 coverage combinations), and Almanak's Signal Intelligence Platform — over 285+ iterations producing 1,094+ merged pull requests with zero regressions detected by the regression oracle. The Kitchen Loop's four primitives — a specification surface enumerating supported capabilities, an LLM synthetic user exercising that surface at ~24–48× human cadence per thread (with a 1,000× ceiling under parallelization, in the paper's own framing as "an order-of-magnitude claim, not a precise multiplier"), Unbeatable Tests that the code author cannot fake, and Drift Control monitoring quality trends with automated pause gates — operationalize at production scale what this paper prescribes as the spec-to-code surface of the verification floor. Roy's case studies achieved monotonic quality-gate improvement (76–91% to 100%) at roughly $0.38 per merged PR, with documented infrastructure self-healing through the same loop — the system fixing its own merge automation, memory allocation, and cooldown failures via the standard cycle — a direct illustration of Lehman's Law 8 multi-loop feedback architecture operating at AI generation velocity. The framework's "agents do detection, humans do judgment" division of labor from Part 1 is what Kitchen Loop's Drift Control gates implement structurally: the loop pauses or warns on regression, drift, canary escape, backpressure, and starvation thresholds, but resolution of what each pause means is left to human operators. SLUMP and Constitutional SDD remain the controlled-experiment and methodology proof-of-concept demonstrations of the same structural claim; Kitchen Loop is the production-validated data point that lets the framework's verification-floor prescription move from prediction to demonstrated practice at the spec-to-code surface. A scope note carries here as it did for SLUMP and Constitutional SDD: Kitchen Loop's primary case study is a DeFi framework with enumerable specifications and a strong regression oracle, and Roy's own limitations section names oracle quality and spec enumerability as the boundary conditions for the approach. The structural mechanism generalizes; the specific magnitudes are case-study-specific.

**Spec quality as the upstream dependency.** Across all three surfaces, spec quality is the upstream dependency that determines how much downstream surfaces can contribute. An LLM CI gate checking conformance against a stale, ambiguous, or absent specification catches nothing. Property-based testing on under-specified contracts surfaces test failures without resolving which side is wrong. Observability on code whose intent is unclear produces signals nobody can interpret. The Level 1 → Level 2 → Level 3 spec maturity ladder from Part 1 (drawn from Wasowski 2026) is therefore not only the mechanism for closing Loop 1 in the framework's terms — it is also the upstream gate determining whether verification-floor investment downstream actually produces lift. A team at Level 1 buying a sophisticated spec-to-code CI gate is buying compute against a missing input. The sequencing this implies is uncomfortable: spec persistence and consultation discipline (the Level 1 → Level 2 transition) precedes verification-infrastructure investment, even though the latter is more visible and easier to procure.

The verification floor is not theoretical: Catalini et al. derived it from cost dynamics, Bainbridge from cognitive psychology, and the 2024-2026 empirical record measures it directly. Below it, the four ratios don't improve — they invert. Part 4 examines what happens when organizations bet against this floor — Cloudflare's role-elimination thesis being one of several test cases currently in flight.

## Harness Engineering: The Operational Synthesis

The disciplines above are abstract until they're embedded somewhere. Part 2 named the convergence: the industry's "harness engineering" is the operational form of Lehman's Law 8 multi-loop feedback architecture — what Lehman articulated theoretically in 1996 is what practitioners are now building from empirical necessity. This section operationalizes it.

A production harness has five typical layers, each mapping to a governance discipline already named in this series.

**Tool orchestration** — what tools the agent can access, how they're described, when they're invoked. The proficiency-governance distinction shows up immediately here: a powerful model with poorly-orchestrated tools underperforms a weaker model with well-orchestrated tools. The empirical signal is striking and converging. LangChain's coding agent moved from 30th to 5th place on Terminal Bench 2.0 in March 2026 through harness optimization alone, no model change. Anthropic's Opus 4.5 went from 42% to 95% on CORE-Bench after fixing harness issues with the same underlying model. Meta-Harness (Lee et al., 2026) automatically searched harness code while keeping model weights fixed and outperformed the best hand-designed harness by 7.7 points. Three independent measurements, same pattern: at fixed model capability, harness changes produce large outcome swings.

**Verification loops** — automated checks on agent output before acceptance. This is the verification floor in operational terms: static analysis, type systems, test coverage, contract testing at module boundaries. The verifiable share s_v in Catalini-Hui-Wu's economic model is determined here. Investment in this layer directly determines whether AI generation produces value or verification debt.

**Context and memory** — persistent state the agent consults. SLUMP's ProjectGuard, GitHub Spec Kit, and the Git Context Controller (Yan et al., 2025 — persistent file-system-style memory delivering over 13% improvement on SWE-Bench Verified) all live in this layer. The Level 1 → Level 2 SDD upgrade described in Part 1 is concretely this layer's evolution: from session-local prompts to persistent state with consultation discipline, with the next step being bidirectional writeback into that state. The Gloaguen et al. finding that naive context files don't help is essentially a finding about persistence-without-consultation in the wild; the SLUMP and GCC findings are about persistence-with-consultation in controlled conditions. None yet measures the bidirectional writeback half — runtime → spec updates — which is the open engineering frontier the framework predicts will compound next.

**Guardrails** — runtime constraints on what the agent can do. Constitutional SDD's CWE-derived security principles live here. Permission systems for irreversible actions live here. The "what can the agent never do" constraints are encoded as runtime guardrails, not just as documentation that may or may not be consulted.

**Observability** — visibility into what the agent did and why. The detection side of Part 1's "agents do detection, humans do judgment" requires observability infrastructure. You cannot govern what you cannot observe. The harness must surface what the agent saw, what it decided, and what changed — at a granularity humans can audit when needed.

Martin Fowler's April 2026 framing positions harness engineering as the third phase of AI engineering maturity, following prompt engineering and context engineering. Faros AI's 2026 engineering report identifies it as the main focus of engineering investment in 2026. This is not terminology fashion. It is the field converging on what Lehman's Law 8 named decades earlier: the multi-loop feedback infrastructure is where evolution actually happens.

For this framework: the harness is where governance becomes concrete. Each practical discipline in this part operates through some layer of the harness. The four ratios from Part 2 determine what value the harness produces; the harness determines whether the four ratios actually improve under conserved activity, or stay flat. Organizations treating the harness as default infrastructure that comes with the agent tool are running at the floor of what the technology can deliver. Organizations treating the harness as a custom-engineered governance system are the ones extracting the compounding density gains the framework predicts.

## Anti-Patterns to Avoid

Regardless of which way large-scale AI bets like Cloudflare's go, certain patterns consistently invert the framework's predictions. They look like governance improvements but actively work against it.

**Measuring AI proficiency without measuring governance.** Dashboards showing tool adoption, AI-generated code percentage, or agent-PR throughput look like maturity signals but capture only the proficiency axis. Without governance instrumentation on the same dashboard, the proficiency numbers are uninterpretable — they could indicate compounding value or compounding debt, with no way to distinguish.

**Letting agents commit to context without comprehension.** When the agent writes code nobody reviews and nobody understands, the codebase accumulates what Part 1 called comprehension debt. This is locally efficient and globally corrosive. The discipline is that nothing merges that no human can explain at the level of "what does this do and why does it do it this way." This is not a code review checklist item — it is the boundary between Level 1 and Level 2.

**Letting the spec become an implementation manual.** The MDA failure mode, discussed throughout the previous parts. Every HOW rule added to the spec under pressure is a step toward making the spec a worse programming language than the actual programming language. Resist it. When agents misbehave on a recurring pattern, the question to ask is whether the WHAT and BOUNDARIES are precise enough — not whether a more specific HOW rule is needed.

**Running fast loops and slow loops without bridging them.** Loop 1 runs continuously while Loop 2 runs annually is not a two-loop governance structure — it is one fast loop and one slow loop with nothing connecting them. The bridging mechanisms (explicit detection signals, ADR-to-intent traceability, ownership of spec-need alignment) are what make the structure function. Without them, Loop 1 efficiency is wasted on Loop 2 misalignment.

**Treating governance investment as overhead rather than infrastructure.** This is the most consequential framing error. Under conservation, you cannot do more work — only more accurate work. The infrastructure that maintains accuracy is the infrastructure that produces value. Teams treating it as overhead see their AI investments compound negatively; teams treating it as core see the value-density gains the framework predicts.

## Where to Start, Calibrated to Maturity

The work above is too much to attempt all at once. The realistic question is what to do first, given where the organization currently is.

**At Level 1 (CLAUDE.md / .cursorrules / AGENTS.md as super-prompt, no persistent spec):** the single highest-leverage move is establishing one persistent spec with consultation discipline in one repository — and adding lightweight writeback discipline as soon as the persistence layer is stable. Pick the codebase where AI use is most active and start there. SLUMP demonstrates a large faithfulness recovery from the persistence-and-consultation change in controlled conditions; bidirectional updates are the next layer of work, but the persistence step alone delivers substantial lift. The structural mechanism generalizes via Lehman's Law 2 even where the specific magnitude will not. It is the easiest large win available and the prerequisite for everything that follows.

**At Level 2 (spec-anchored in some repositories, partial governance):** instrument both loops explicitly. Assign ownership of intent-need alignment. Wire production and user signals back to spec updates. Compress intent review cadence. The work shifts from technical infrastructure to organizational infrastructure, which is harder but where the next compounding gain lives.

**At Level 2 with both loops instrumented:** optimize across the four ratios systematically. Move humans up the abstraction stack. Concentrate AI on density-improving activities. Reframe metrics around the ratios that can actually improve. Treat capability scaffolds as deprecation candidates and context scaffolds as permanent investments. This is the regime where the compounding value-density gains the framework predicts actually materialize.

**Beyond Level 2:** the boundary between governance discipline and competitive advantage starts to dissolve. Organizations operating consistently at this maturity are the ones extracting the 30%+ value-density gains that compound over years. They are also the organizations most likely to be misunderstood by competitors and analysts measuring the volume conservation, who will see flat throughput and conclude AI hasn't worked — while missing the ratio improvements that are the actual point.

## The Discipline Is the Strategy

The framework Lehman left in 1974 and refined through 1996 predicted patterns the empirical record from 2024-2026 is consistent with. The volume of value creation through software appears to be bounded by conservation tendencies that operate at the system and organizational level. The density of value extracted from that bounded volume is, on the framework's account, unbounded — but only conditionally accessible, through governance that respects the regularities and prescribes the structural architecture (the two loops) that those regularities require.

AI does not change what good engineering looks like. It changes the cost of mediocre engineering. Under Lehman conservation, the only available offensive lever for productivity is accuracy — and accuracy at every loop level, sustained continuously, is what the practical disciplines in this part are for.

The work is real, ongoing, and unglamorous. None of it is the productivity revolution the marketing claims. All of it is what the empirical record actually rewards. Lehman's laws were always there; the architecture they required was always there. What changed is the cost of ignoring them, which scales now with how good the tools become. Organizations that internalize this — and instrument accordingly — will compound advantages durably.

The rest will keep measuring volume.

---

*Part 4 examines how this framework predicts the outcomes of five distinct organizational bets currently underway — including Block's architectural substitution, Cloudflare's role elimination, Klarna and Salesforce's full-replacement strategies (and their partial reversals), AI-native startups operating at radically different revenue-per-employee ratios, and Shopify and Duolingo's augmentation mandates.*

---

## References

**Lehman's Laws**

Lehman, M. M. (1980). Programs, life cycles, and laws of software evolution. *Proceedings of the IEEE*, 68(9), 1060–1076.

Lehman, M. M., & Belady, L. A. (1985). *Program Evolution: Processes of Software Change*. Academic Press.

Lehman, M. M., Ramil, J. F., Wernick, P. D., Perry, D. E., & Turski, W. M. (1997). Metrics and laws of software evolution—The nineties view. *Proceedings of the 4th International Software Metrics Symposium (METRICS '97)*.

**The Verification Bottleneck**

Catalini, C., Hui, X., & Wu, J. (2026, February). Some Simple Economics of AGI. arXiv:2602.20946. MIT / Washington University / UCLA. Formal economic model of the verification bottleneck. Establishes the Cost to Automate (c_A) vs Cost to Verify (c_H) framework, the Measurability Gap (Δm), and the verifiable share of deployment (s_v) as the binding constraint on AI productivity.

Bainbridge, L. (1983). Ironies of Automation. *Automatica*, 19(6), 775–779. Foundational paper on the paradox that automation increases rather than decreases cognitive demands on remaining human operators. 1,800+ citations as of 2016 and citation rate accelerating in the AI era.

Parasuraman, R., & Riley, V. (1997). Humans and Automation: Use, Misuse, Disuse, Abuse. *Human Factors*, 39(2), 230–253. Classic paper on automation complacency and the rubber-stamp dynamic now visible in AI code review.

Dobe, O., Arora, J., Zetzsche, S., Labai, N., & Delmas, R. (2026, May). Requirements analysis: catching requirement bugs before they become code. Kiro / AWS Applied Science. https://kiro.dev/blog/deep-spec-analysis/ Neuro-symbolic requirements analysis pipeline (refinement, auto-formalization via SMT-lib, logical analysis) catching four classes of requirement bugs — wrong level of detail, ambiguity, inconsistency, incompleteness — before code generation. Cited as operational example of raising the verification floor at the intent-to-spec surface.

Eline, A. (2025, November). Does your code match your spec? Measuring "correctness" with property-based testing. Kiro / AWS. https://kiro.dev/blog/property-based-testing/ Spec-to-executable-property translation using Hypothesis with random input generation and counterexample shrinking. Cited as operational example of raising the verification floor at the spec-to-code surface, and as concrete evidence that AI-assisted verification scales sub-linearly with input space.

**Empirical Studies on AI Coding Impact**

He, H., Miller, C., Agarwal, S., Kästner, C., & Vasilescu, B. (2026). Speed at the Cost of Quality: How Cursor AI Increases Short-Term Velocity and Long-Term Complexity in Open-Source Projects. *MSR '26*. https://doi.org/10.1145/3793302.3793349

Yan, L., Chen, X., & Zhang, X. (2026). When the Specification Emerges: Benchmarking Faithfulness Loss in Long-Horizon Coding Agents. arXiv:2603.17104. (SLUMP benchmark.)

**Harness Engineering**

Fowler, M. (2026, April 2). Harness engineering for coding agent users. martinfowler.com. https://martinfowler.com/articles/harness-engineering.html Positions harness engineering as the third phase of AI engineering maturity following prompt engineering and context engineering. Frames the harness as a system of guides, sensors, computational and inferential elements.

Lee et al. (2026). Meta-Harness: Automated Search Over Agent Harness Code. Searched harness code while keeping model weights fixed; outperformed the best hand-designed harness by 7.7 points on text classification and achieved top rankings among same-base-model agents on TerminalBench-2. Cited as empirical evidence that harness optimization produces large gains at fixed model capability.

Yan, K., Wang, J., Zhang, Y., et al. (2025). Git Context Controller: Manage the Context of LLM-based Agents like Git. arXiv:2508.00031. Persistent file-system-style memory workspace with COMMIT/BRANCH/MERGE/CONTEXT operations. Reports +13% improvement on SWE-Bench Verified and >80% task resolution rate, outperforming 26 existing open and commercial systems. Cited as the strongest published controlled study of persistent harness state outperforming session-local context.

LangChain Engineering. (2026, March). Terminal Bench 2.0 harness optimization case study. Coding agent moved from 30th to 5th place on Terminal Bench 2.0 through harness changes alone, no model upgrade. Cited as industry example of harness-level leverage at fixed model capability.

Anthropic. (2025). Demystifying evals for AI agents. https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents Discussion of Opus 4.5's score on CORE-Bench moving from 42% to 95% after harness fixes, with the same underlying model. Cited as a documented same-model harness-leverage example from a frontier lab.

**Industry Reports**

Faros AI. (2026). AI Engineering Report 2026: The Acceleration Whiplash. Two years of telemetry from 22,000 developers across 4,000+ teams. https://www.faros.ai/research

Sonar. (2026). State of Code Developer Survey 2026. Sample: 1,149 professional developers. Key findings: 96% don't fully trust AI code accuracy; 48% always verify before committing; 38% report AI code requires more review effort than human code.

Veracode. (2025). 2025 GenAI Code Security Report. https://www.veracode.com/resources/analyst-reports/2025-genai-code-security-report/

DORA / Google Cloud. (2024). Accelerate State of DevOps Report 2024. https://dora.dev/research/2024/dora-report/

**Industry Commentary**

Wasowski, J. (2026, April 11). Spec Driven Development — Three Maturity Levels Every AI Team Should Know. *Medium*. https://medium.com/@wasowski.jarek/spec-driven-development-three-maturity-levels-every-ai-team-should-know-648c93cf1e1d

Salesforce Engineering. (2026). Scaling Code Reviews: Adapting to a Surge in AI-Generated Code. Internal Prizm system case study. https://engineering.salesforce.com/scaling-code-reviews-adapting-to-a-surge-in-ai-generated-code/
