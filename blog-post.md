# AI Doesn't Break the Laws of Software Evolution

## A 1974 framework explains why AI coding productivity gains evaporate — and where the durable bets really live.

---

Maybe you've had this experience with AI coding tools. You start using Cursor or Claude Code. For a month, the velocity feels electric — you're shipping faster than you ever have. By month four, the codebase feels harder to navigate. By month six, your senior engineers are spending more time debugging AI-generated code than they used to spend writing it from scratch.

The pattern shows up in the data. [He et al. (2026)](https://arxiv.org/abs/2511.04427) tracked 806 open-source projects that adopted Cursor: code complexity rose 41.6% within months, and the velocity gains were transient — cancelled by the debt they created. A [METR controlled trial](https://arxiv.org/abs/2507.09089) found something stranger still: with early-2025 tools, developers using AI were 19% *slower* while believing they were 20% faster. METR's own [2026 follow-up](https://metr.org/blog/2026-02-24-uplift-update/) found the slowdown had mostly closed — to a statistically insignificant level, though it cautioned the newer result is confounded by who opted in. Either way, the durable signal was never the slowdown itself — it's the 40-point gap between *felt* and *real* speed, and that gap is the thread this whole essay pulls on.

Here is the surprising part: this pattern was predicted in 1974.

## A theory from punch cards explains the agents of 2026

In 1974, an IBM researcher named Meir Lehman published a set of observations about how software changes over time. He had been watching IBM's OS/360 — a system written by humans, on mainframe terminals, before the internet existed. He could not have predicted Cursor, Copilot, or Claude Code. Yet his observations describe what we're seeing remarkably well.

Lehman called them the laws of software evolution. By the late 1990s he had eight of them, derived from decades of empirical observation across many large systems. Five describe structural regularities — patterns that hold robustly across the systems studied, whether software is written by humans, agents, or any combination. Lehman framed them as social-science tendencies, not physical constants — and not every law replicates equally well. But the regularities are strong enough to be the most coherent macro lens we have on how software evolves. Entropy tends to increase. Comprehension caps how much change a system can absorb. The effective work rate tends to be conserved over a system's lifetime. These are not predictions of pathology — they are descriptions of dynamics that have held empirically across software embedded in the real world.

What's happening with AI coding agents in 2024-2026 lines up with what Lehman's framework predicts. The empirical record — rising complexity in ungoverned codebases, AI-generated debt that persists without refactoring discipline, measured slowdowns alongside perceived speedups, declining stability in [DORA reports](https://dora.dev/research/2024/dora-report/) — matches a theory that has held for half a century. The framework's claim is that governance changes this pattern; whether it does at organizational scale is the open question the paper takes up. AI doesn't break the laws. It compresses the timeline on which the cost of ignoring them becomes visible.

This essay is the introduction. The full working paper, including all citations, charts, and the operational framework, [is on GitHub](https://github.com/AgelessK/LSE-AI).

## The laws, in plain English

The most important law for understanding AI coding agents is the one Lehman called **Conservation of Familiarity**. As a software system grows, the people involved with it — both engineers and now agents — must maintain mastery of its content and behavior to evolve it productively. The amount of new material the system can absorb in any time window is bounded by how much its custodians can comprehend.

This is not a theoretical claim. It is something every senior engineer has lived. Code you wrote yourself last quarter feels different from code you encountered for the first time yesterday. Codebases you've internalized are workable in a way unfamiliar codebases are not. The difference is comprehension bandwidth — and humans have a roughly fixed amount of it.

AI generates code faster than humans can comprehend it. That single mismatch is the engine driving most of what we see in the data. Velocity gains are real but transient because they consume the slack in the comprehension layer. Once the slack is gone — once the codebase has accumulated more complexity than its custodians can hold — every additional generation produces more debugging burden than productivity benefit. The bottleneck doesn't disappear when AI gets faster. It moves to where Lehman said it would.

The second important law is **Conservation of Organizational Stability**: the total effective work rate sustained on a software system remains roughly unchanged over its lifetime. In plain terms: throwing more typing speed at a system doesn't mean more finished features make it out the door, or more value delivered to the customer and the business.

Why doesn't more speed move the needle? Because of the law just above it: a team can only absorb and keep coherent so much change at once, and the older a system gets, the more of each hour goes to holding its complexity in check — so extra speed gets soaked up rather than banked as output. Speed up one stage and the gain just leaks into the next: more code means more to review, more to integrate, more to debug. The system keeps settling back to the throughput it had before — and that settling-back is what "roughly unchanged over its lifetime" means.

If you add AI to your engineering organization and individual throughput rises — more PRs merged, more features shipped — but organizational delivery metrics stay flat, something is happening that is not "extra work getting done." [Faros's 2026 telemetry](https://www.faros.ai/research) across 22,000 developers shows exactly this: PRs merged nearly doubled, epics per developer rose 66.2%, while organizational delivery rates stayed flat. Faros called it "Acceleration Whiplash." Lehman would have called it Tuesday.

That is the Faros split in one line: individual output soared, delivered value didn't.

Lehman's word for the bounded quantity was *effective* activity, and that qualifier is the whole point: raw motion is cheap and rising now; the value-creating rate is set by absorption and entropy, not typing speed. Measure generation and you'll see gains — but measure value per unit of activity, the *density*, and under ungoverned AI it doesn't hold flat. It falls. You spend more and more effort to deliver the same absorbed change.

There's a deeper reason automating code can't expand the pie: writing code was never the big slice of the work. Atlassian's [*State of Developer Experience 2025*](https://www.atlassian.com/teams/software-development/state-of-developer-experience-2025), a survey of roughly 3,500 developers, found the average developer spends only about 16% of the week actually writing code; the rest goes to review, design, coordination, and debugging. Drive that 16% to zero and you've freed a sliver. Writing *good* code was always hard — it's what earned engineers a decade of premiums — but writing it *faster* was rarely the binding constraint. The real bottlenecks were the other two: building the *right* thing (alignment) and verifying that what got built actually works (verification). AI's headline gift, speed of generation, lands almost entirely on that 16% slice and leaves those two untouched.

## Density, not volume

This is the insight that reframes the conversation about AI productivity. If the conservation tendency holds — and the 2024-2026 record suggests it does — then AI won't increase organizational output by adding capacity. The pie does not get bigger in aggregate. What AI can do is change what each unit of activity *produces* — its value density.

There are three ways density rises. **Efficiency** — the same work performed with less effort. **Effectiveness** — better selection of which work to do at all. And — borrowing from Peter Drucker in 1954 — **measurer work**: the synthesis of signals, detection of drift, accumulation of feedback that organizations historically did slowly and episodically. AI's most novel contribution to software development is probably this third channel. It can compare runtime behavior against specifications at scale, surface patterns in customer behavior that took quarterly reviews to detect, accelerate the calibration between intent and reality from quarters to weeks.

This is what AI is for, if you accept the conservation framing. Not "more code per engineer." But "tighter feedback loops, fewer wasted activity cycles, faster correction of misalignment."

The teams treating AI as a volume multiplier are getting Acceleration Whiplash. The teams treating AI as a density multiplier are getting compound returns. Both observations are real. The difference is whether the organization is using AI to do *more* — or to do *better*.

| Treating AI as… | The focus | The outcome |
|---|---|---|
| **a volume multiplier** | more code, more PRs, faster generation | **Acceleration Whiplash** — complexity debt rises, stability declines, review and debugging pile onto senior engineers |
| **a density multiplier** | higher-value work, tighter feedback loops, verification scaled to the generation rate | **Compound returns** — faster alignment, less rework, sustainable velocity |

But density gains aren't automatic — they depend on what was already there. This is the part practitioners describe most vividly. [The Pragmatic Engineer's 2026 survey](https://newsletter.pragmaticengineer.com/p/ai-impact-on-software-engineers-part-2) of 900+ engineers and engineering leaders found that the teams getting real benefit from AI were the ones that *already* had the fundamentals: tests and deployment automation, documented decisions, and a clean codebase for agents to imitate. Its one-line summary is the whole framework in five words: **AI is an amplifier, not a fixer.** Good engineering practices get multiplied; so do the bad ones.

The same survey caught the mood shifting between 2024 and 2026 — the share of engineers who feel primarily negative about AI fell from roughly a quarter to about one in ten. But positivity barely moved — the largest group now lands on "it's complicated." Two years in, AI feels less alarming and no more miraculous — exactly what a density-not-volume story predicts.

## But the tooling is catching up

There is a structural irony worth naming here. The same technology that creates the drift problem — LLMs generating code faster than humans can verify it — is also the first technology that can check natural-language specifications against code. Until 2024, spec-conformance was a code-review job because there was no other way to do it. Now, for the first time, an LLM can read the spec, read the implementation, and flag the gap — early and unproven at scale, but real.

Open tooling is already attacking it at different layers:

- **Spec quality** — [deep requirement analysis](https://kiro.dev/blog/deep-spec-analysis/) (as in AWS's Kiro) tests whether the spec itself is sound.
- **Spec-versus-code** — [spec-kit-canon](https://github.com/maximiliamus/spec-kit-canon) runs agents against a canonical spec to catch where the code has drifted from it.
- **Behavior** — [property-based testing](https://kiro.dev/blog/property-based-testing/) exercises whether the running system behaves as the spec promises.

Three surfaces, one payoff: machine-tractable checking where there used to be none.

The drift accelerator and the governance solution use the same primitive. Which means the verification floor — the point above which AI output stops being economically valuable because no one can check it — is no longer a fixed biological constraint. It is a moving threshold that verification investment can shift, at the surfaces where machine-tractable checking now applies.

Verification is only one of the two bottlenecks, and the other is drawing the same kind of attention. As implementation gets cheap, *agreeing on what to build* becomes the scarce step — the alignment problem. GitHub Next's ["Zero Alignment"](https://maggieappleton.com/zero-alignment) work (Maggie Appleton) is an early swing at it: pull planning, context, and agents into one shared space so intent is set before the agents run, not reverse-engineered after. Same pattern as verification — the constraint moves, and the tooling chases it.

## What the framework predicts

If this is right, organizational bets on AI sort cleanly into categories that should compound and categories that should invert. The full paper develops five public bets and three under-observed durable ones. A taste of the predictions:

**Replacement bets — likely to invert.** Klarna's 2024 AI-replaces-customer-service initiative reverted in May 2025, with the CEO publicly stating they had cut quality too far. Salesforce's 9,000-to-5,000 customer service headcount reduction partially reversed by February 2026. The framework predicts both. When verification capacity becomes binding, you cannot remove the verifiers and keep output quality without consequence. Both reversals are consistent with that prediction — though, as always with organizational case studies, multiple plausible explanations apply.

**Augmentation bets — likely to compound.** Shopify and Duolingo's "AI required as foundational competence" mandates without role elimination preserve the verification layer while improving generation density. Conservation of Familiarity is not violated. These are the boring, sustainable bets.

**Under-observed durable bets — quietly compounding.** Three kinds of bet compound durably while rarely making headlines. The first is *verification infrastructure*: review tooling, contract and property-based testing, and the new LLM checks that read a spec and flag where the code diverges. The second is *verification skill*: deliberate practice in code review and debugging craft. The third is *feedback synthesis*: using AI to shrink the lag between a strategic shift and the code catching up to it. Visibility, it turns out, is anti-correlated with durability.

The most durable bets rarely make the news. Take [Yannick Roy's March 2026 paper](https://arxiv.org/abs/2603.25697): his system pins an autonomous coding loop to a persistent specification, checks every change against tests the agent can't game, and pauses itself the moment quality starts to drift — spec-anchored verification, running in production rather than on a slide. It logged 1,094+ merged pull requests with zero regressions across two systems, and passed almost without notice in the tech press. The durable bets, true to form.

There is something liberating in this prediction. The most important AI investments your organization can make do not require permission from executives or coverage from analysts. They are operational disciplines anyone with the will to do them can start building tomorrow.

## What this framework lets you ask

Lehman's gift isn't a set of answers. It's a new set of questions about your own situation.

Looking at your team's last six months: what redistributed when AI accelerated generation? Did verification capacity grow to absorb it? If your AI productivity number went up, what number is hiding the offsetting cost? When your senior engineers spend their time differently than they did a year ago, what activity have they shifted *into* — and is that activity producing more value per hour than what they shifted *out of*?

These questions don't require new metrics. They require looking at the metrics you already have through the framework's lens. Once you do, the pattern becomes hard to unsee.

## The full work

The four-part working paper [*AI Doesn't Break the Laws of Software Evolution*](https://github.com/AgelessK/LSE-AI) develops all of this in full: the five structural regularities, the two-loop governance architecture, the compound-conservation argument, the verification floor, the proficiency-governance matrix, and the complete map of organizational bets. It carries the supporting evidence too — the studies above, plus the economic model of verification cost, the cognitive-science work on automation, and the recent benchmarks and production case studies the argument leans on.

A companion essay, [*Generation Got Cheap. Validation Didn't.*](https://medium.com/canaries-in-the-mind/generation-got-cheap-validation-didnt-d0d0e6c897e8), develops the Generator-Validator coupling thesis at the cognitive layer: the relationship between AI-cheap generation and the human judgment work that gets harder, not easier, as generation improves. The two pieces are complementary — that one operates at the level of individual cognition, this one at the level of organizational dynamics.

## The wild part

The technology has changed beyond anything Lehman could have pictured in 1974. The conservation tendencies, so far, haven't — and that's the wild part: what looks like a revolution in *how* we build is playing out on rails laid down fifty years ago. The final twist: the very capability flooding our codebases faster than we can read them is also the first that can read a spec against the code and flag where they've parted ways — the accelerant and the brake, the same engine. Whether AI compounds or corrodes comes down to which way you point it.

---

*The full paper develops the framework formally, engages prior literature in detail, and proposes a falsifiable empirical hypothesis about which organizational AI bets will compound versus invert through 2028. [Available as a preprint](https://github.com/AgelessK/LSE-AI).*

*Written with AI assistance — Claude (Anthropic), via TrendAI's Claude for Enterprise license, used as a research and editorial scaffold. The framework synthesis and substantive arguments are the author's; AI helped with prior-art search, citation verification, structural critique, and prose refinement. While TrendAI provides the licensed AI tool, this work was not commissioned by, reviewed by, or written on behalf of TrendAI or Trend Micro Inc. Full disclosure of working model and competing interests in the [linked preprint](https://github.com/AgelessK/LSE-AI).*
