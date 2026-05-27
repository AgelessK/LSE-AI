# AI Doesn't Break the Laws of Software Evolution

## A 1974 framework explains why AI coding productivity gains evaporate — and where the durable bets really live.

---

Maybe you've had this experience with AI coding tools. You start using Cursor or Claude Code. For a month, the velocity feels electric — you're shipping faster than you ever have. By month four, the codebase feels harder to navigate. By month six, your senior engineers are spending more time debugging AI-generated code than they used to spend writing it from scratch.

The pattern shows up in the data systematically. He et al. (MSR'26) tracked 806 open-source GitHub repositories that adopted Cursor over two years: cognitive complexity rose 41.6%, velocity gains were transient, and the complexity debt they generated cancelled the gains within months. A METR randomized controlled trial of 16 experienced open-source developers using early-2025 tools found they were 19% *slower* than without AI while subjectively believing they were 20% faster — a 40-percentage-point perception-reality gap. (METR's late-2025 follow-up found the slowdown shrinking, but the perception-reality gap is the durable result.) These are studies of unmitigated open-source adoption; what governed enterprise adoption looks like is the question the framework engages.

Here is the surprising part: this pattern was predicted in 1974.

## A theory from punch cards explains the agents of 2026

In 1974, an IBM researcher named Meir Lehman published a set of observations about how software changes over time. He had been watching IBM's OS/360 — a system written by humans, on mainframe terminals, before the internet existed. He could not have predicted Cursor, Copilot, or Claude Code. He could not have imagined coding agents at all. Yet his observations describe what we're seeing remarkably well.

Lehman called them the laws of software evolution. By the late 1990s he had eight of them, derived from decades of empirical observation across many large systems. Five describe structural regularities — patterns that hold robustly across the systems studied, whether software is written by humans, agents, or any combination. Lehman himself was careful to frame these as social-science generalizations rather than physical constants, and empirical replication across all eight laws is uneven. But the regularities are strong enough to be the most coherent macro lens we have on how software evolves. Entropy tends to increase. Comprehension caps how much change a system can absorb. Total activity rate tends to conserve over a system's lifetime. These are not predictions of pathology — they are descriptions of dynamics that have held empirically across software embedded in the real world.

What's happening with AI coding agents in 2024-2026 is broadly consistent with what Lehman's framework predicts. The empirical record from this period — complexity increases in ungoverned environments, AI-generated debt persisting in repositories without refactoring discipline, measured slowdowns alongside perceived speedups in small controlled studies, declining stability in DORA reports — is consistent with a theory that has held for half a century. The framework's prediction is that governance changes this pattern; whether it does at organizational scale is the open question the paper engages directly. AI doesn't appear to break the laws. It compresses the timeline on which the consequences of treating them as optional become visible.

This essay is the introduction. The full working paper, including all citations, charts, and the operational framework, [is on GitHub](https://github.com/AgelessK/LSE-AI).

## The laws, in plain English

The most important law for understanding AI coding agents is the one Lehman called **Conservation of Familiarity**. As a software system grows, the people involved with it — both engineers and now agents — must maintain mastery of its content and behavior to evolve it productively. The amount of new material the system can absorb in any time window is bounded by how much its custodians can comprehend.

This is not a theoretical claim. It is something every senior engineer has lived. Code you wrote yourself last quarter feels different from code you encountered for the first time yesterday. Codebases you've internalized are workable in a way unfamiliar codebases are not. The difference is comprehension bandwidth — and humans have a roughly fixed amount of it.

AI generates code faster than humans can comprehend it. That single mismatch is the engine driving most of what we see in the data. Velocity gains are real but transient because they consume the slack in the comprehension layer. Once the slack is gone — once the codebase has accumulated more complexity than its custodians can hold — every additional generation produces more debugging burden than productivity benefit. The bottleneck doesn't disappear when AI gets faster. It moves to where Lehman said it would.

The second important law is **Conservation of Organizational Activity**: the total effective work rate sustained on a software system is roughly invariant over its lifetime. This sounds abstract until you see what it predicts.

If you add AI to your engineering organization and individual throughput rises — more PRs merged, more features shipped — but organizational delivery metrics stay flat, something is happening that is not "extra work getting done." Faros's 2026 telemetry across 22,000 developers shows exactly this: PRs merged nearly doubled, epics per developer rose 66.2%, while organizational delivery rates stayed flat. Faros called it "Acceleration Whiplash." Lehman would have called it Tuesday.

The activity is conserved. What changes is the *distribution* of that fixed activity — more raw generation, more review burden, more refactoring need, more incident response. If you measure only the part that accelerated — generation — you see productivity gains. If you measure end to end — generation plus verification plus integration plus debugging — the gains net out.

## Density, not volume

This is the insight that reframes the conversation about AI productivity. If the conservation tendency holds — and the 2024-2026 record is consistent with it, though the question is open — then AI is not predicted to increase organizational output by adding capacity. The pie does not get bigger in aggregate. What AI can do is change what each unit of activity *produces* — its value density.

There are three ways density rises. **Efficiency** — the same work performed with less effort. **Effectiveness** — better selection of which work to do at all. And — borrowing from Peter Drucker in 1954 — **measurer work**: the synthesis of signals, detection of drift, accumulation of feedback that organizations historically did slowly and episodically. AI's most novel contribution to software development is probably this third channel. It can compare runtime behavior against specifications at scale, surface patterns in customer behavior that took quarterly reviews to detect, accelerate the calibration between intent and reality from quarters to weeks.

This is what AI is for, if you accept the conservation framing. Not "more code per engineer." But "tighter feedback loops, fewer wasted activity cycles, faster correction of misalignment."

The teams treating AI as a volume multiplier are getting Acceleration Whiplash. The teams treating AI as a density multiplier are getting compound returns. Both observations are real. The difference is whether the organization is using AI to do *more* — or to do *better*.

## What the framework predicts

If this is right, organizational bets on AI sort cleanly into categories that should compound and categories that should invert. The full paper develops five public bets and three under-observed durable ones. A taste of the predictions:

**Replacement bets — likely to invert.** Klarna's 2024 AI-replaces-customer-service initiative reverted in May 2025, with the CEO publicly stating they had cut quality too far. Salesforce's 9,000-to-5,000 engineering headcount reduction partially reversed by February 2026. The framework predicts both. When verification capacity becomes binding, you cannot remove the verifiers and keep output quality without consequence. Both reversals are consistent with that prediction — though, as always with organizational case studies, multiple plausible explanations apply.

**Augmentation bets — likely to compound.** Shopify and Duolingo's "AI required as foundational competence" mandates without role elimination preserve the verification layer while improving generation density. Conservation of Familiarity is not violated. These are the boring, sustainable bets.

**Under-observed durable bets — quietly compounding.** Three categories the framework predicts compound durably while rarely generating headlines: verification infrastructure (review tooling, contract testing, property-based testing platforms), verification skill development (deliberate practice in code review and debugging craft), and business-environment feedback synthesis (using AI's measurer capacity to compress the latency between strategic shift and intent update). Visibility, it turns out, is anti-correlated with durability. The most durable bets rarely make the news.

There is something liberating in this prediction. The most important AI investments your organization can make do not require permission from executives or coverage from analysts. They are operational disciplines anyone with the will to do them can start building tomorrow.

## What this framework lets you ask

Lehman's gift isn't a set of answers. It's a new set of questions about your own situation.

Looking at your team's last six months: what redistributed when AI accelerated generation? Did verification capacity grow to absorb it? If your AI productivity number went up, what number is hiding the offsetting cost? When your senior engineers spend their time differently than they did a year ago, what activity have they shifted *into* — and is that activity producing more value per hour than what they shifted *out of*?

These questions don't require new metrics. They require looking at the metrics you already have through the framework's lens. Once you do, the pattern becomes hard to unsee.

## The full work

The four-part working paper [*AI Doesn't Break the Laws of Software Evolution*](https://github.com/AgelessK/LSE-AI) develops the full framework: the five structural regularities of E-type systems, the two-loop governance architecture (system understanding and intent alignment), the compound conservation argument, the verification floor where AI value creation is predicted to hit a binding economic constraint, the proficiency-governance matrix, and the full positioning of organizational bets. It contains the supporting empirical evidence — the studies referenced above, plus Catalini-Hui-Wu's cost-to-verify formalization, Bainbridge's 1983 paper on automation paradoxes, Yan/Chen/Zhang's SLUMP benchmark, Marri's Constitutional SDD work, and the recent pieces from AWS on Kiro that operationalize the verification floor in shipping product.

A companion essay, [*Generation Got Cheap. Validation Didn't.*](https://medium.com/canaries-in-the-mind/generation-got-cheap-validation-didnt-d0d0e6c897e8), develops the Generator-Validator coupling thesis at the cognitive layer: the relationship between AI-cheap generation and the human judgment work that gets harder, not easier, as generation improves. The two pieces are complementary — that one operates at the level of individual cognition, this one at the level of organizational dynamics.

## The wild part

A computer scientist watching IBM's OS/360 evolve in 1974 worked out structural properties of software that describe what we see when Claude Code is pointed at a codebase in 2026 with uncanny accuracy. He could not have known what was coming. He didn't need to. The dynamics were already there in the structure of what software is.

The technology has changed. The conservation tendencies, so far, haven't.

If the framework is right, the most important AI bets your organization makes will be the ones that don't generate press releases. The companies that win the next decade with AI will be the ones investing in verification infrastructure, verification skill, and the feedback loops between users and intent — work that looks like operational continuity, not strategic positioning. The work nobody's asking about is the work that matters most.

That is the inspiration this framework offers. Not a productivity boost. Not a competitive moat anyone is talking about. A way of seeing what's actually happening when software changes, that has held for fifty years and is now playing out in compressed time on every team using AI agents. The lens makes the noise quieter. What's left is the signal of what to build, what to invest in, and what to stop pretending will work.

---

*The full paper develops the framework formally, engages prior literature in detail, and proposes a falsifiable empirical hypothesis about which organizational AI bets will compound versus invert through 2028. [Available as a preprint](https://github.com/AgelessK/LSE-AI).*

*Written with AI assistance — Claude (Anthropic), via TrendAI's Claude for Enterprise license, used as a research and editorial scaffold. The framework synthesis and substantive arguments are the author's; AI helped with prior-art search, citation verification, structural critique, and prose refinement. While TrendAI provides the licensed AI tool, this work was not commissioned by, reviewed by, or written on behalf of TrendAI or Trend Micro Inc. Full disclosure of working model and competing interests in the [linked preprint](https://github.com/AgelessK/LSE-AI).*
