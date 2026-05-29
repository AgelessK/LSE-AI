# References

*Combined bibliography for [AI Doesn't Break the Laws of Software Evolution](README.md). References are organized by topic. Each entry was verified against primary sources where possible; specific empirical magnitudes are reported as benchmark-specific or sample-specific where applicable.*

---

## Lehman's Laws and Software Evolution Theory

Lehman, M. M. (1980). Programs, life cycles, and laws of software evolution. *Proceedings of the IEEE*, 68(9), 1060–1076.

Lehman, M. M., & Belady, L. A. (1985). *Program Evolution: Processes of Software Change*. Academic Press.

Lehman, M. M., Ramil, J. F., Wernick, P. D., Perry, D. E., & Turski, W. M. (1997). Metrics and laws of software evolution—The nineties view. *Proceedings of the 4th International Software Metrics Symposium (METRICS '97)*. (Source of the modern formulation of all eight laws, including Law 8.)


## Critical Engagement with Lehman's Framework

Israeli, A., & Feitelson, D. G. (2010). The Linux kernel as a case study in software evolution. *Journal of Systems and Software*, 83(3), 485–501. Empirical test against Linux finding that Law 6's continuing-growth prediction holds but the sub-linear growth pattern does not.

Herraiz, I., Rodriguez, D., Robles, G., & González-Barahona, J. M. (2013). The evolution of the laws of software evolution: A discussion based on a systematic literature review. *ACM Computing Surveys*, 46(2), Article 28. Comprehensive review concluding uneven validation across the laws — Laws 1, 2, and 7 replicated robustly; Law 6's quantitative formulations contested; Laws 4 and 5 mixed depending on metric choices.

Godfrey, M. W., & German, D. M. (2013). On the Evolution of Lehman's Laws. *Journal of Software: Evolution and Process*. DOI 10.1002/smr.1636. https://plg.uwaterloo.ca/~migod/papers/2013/lehmanPaper.pdf Retrospective on Manny Lehman's intellectual journey and legacy. Discusses Lehman's bio, summarizes the eight laws as currently formulated, restates the social-science framing of "law," and identifies modern trends — emergent software architecture, de-monolithization, open-source and agile development, emergent uses of software via the Internet — that complicate measurement of the laws against contemporary systems. Calls for "new empirical models" but does not extend to governance architecture design. Cited here, alongside Herraiz et al. (2013), as the boundary of the Lehman-validation literature against which this paper positions its governance-architecture contributions.

Cunningham, W. (1992). The WyCash portfolio management system. *Addendum to the Proceedings on Object-Oriented Programming Systems, Languages, and Applications (OOPSLA '92)*. Original "technical debt" metaphor, the dominant operational vocabulary in modern empirical SE for the dynamics Lehman described structurally.


## Empirical Studies on AI Coding Impact

He, H., Miller, C., Agarwal, S., Kästner, C., & Vasilescu, B. (2026). Speed at the Cost of Quality: How Cursor AI Increases Short-Term Velocity and Long-Term Complexity in Open-Source Projects. *23rd International Conference on Mining Software Repositories (MSR '26)*. https://doi.org/10.1145/3793302.3793349 (arXiv:2511.04427). Sample: 806 Cursor-adopting GitHub repositories; staggered difference-in-differences using the Borusyak et al. (2024) imputation estimator. Key findings (ATT, log-transformed outcomes): code complexity (SonarQube cognitive complexity) +41.6%, static analysis warnings +30.3% post-adoption. Velocity gains transient (lines added +281% month 1, +48% month 2, dissipating after).

Liu, Y., Widyasari, R., Zhao, Y., Irsan, I. C., Chen, J., & Lo, D. (2026). Debt Behind the AI Boom: A Large-Scale Empirical Study of AI-Generated Code in the Wild. arXiv:2603.28592. Singapore Management University / Huazhong University of Science and Technology. Sample: 302,600 verified AI-authored commits from 6,299 GitHub repositories across five AI coding assistants (Copilot, Claude, Cursor, Gemini, Devin); commit-level differential static analysis using ESLint, Pylint, and Semgrep; longitudinal tracking of each introduced issue from introducing commit to latest revision. Key findings: 484,366 distinct issues identified, code smells = 89.3% of all issues, more than 15% of commits from every AI coding assistant introduce at least one issue, 22.7% of tracked AI-introduced issues still survive at the latest version, cumulative surviving issues exceed 100,000 by February 2026. Field-evidence complement to He et al.'s controlled DiD study.

Becker, J., Rush, N., Barnes, E., & Rein, D. (2025). Measuring the Impact of Early-2025 AI on Experienced Open-Source Developer Productivity. METR. arXiv:2507.09089. Sample: 16 developers, 246 tasks. Headline finding: AI tools associated with 19% longer task completion despite developers perceiving 20% speedup. February 2026 follow-up acknowledges smaller effect with late-2025 tools, confounded by selection bias.

Agarwal, S., He, H., & Vasilescu, B. (2026). AI IDEs or Autonomous Agents? Measuring the Impact of Coding Agents on Software Development. *23rd International Conference on Mining Software Repositories (MSR '26)*. https://doi.org/10.1145/3793302.3793589 (arXiv:2601.13597).

Yan, L., Chen, X., & Zhang, X. (2026). When the Specification Emerges: Benchmarking Faithfulness Loss in Long-Horizon Coding Agents. arXiv:2603.17104. Purdue University. Introduces the SLUMP (Faithfulness Loss Under eMergent sPecification) benchmark. Sample: 20 ML papers (10 ICML 2025, 10 NeurIPS 2025), 371 atomic verifiable components, interaction scripts of ~60 coding requests, evaluated on Claude Code and Codex under emergent-specification and single-shot-control conditions. Key finding: the ProjectGuard mitigation (external persistent project-state layer) recovers 90% of the semantic-faithfulness (MCF) gap on Claude Code; fully faithful components rise from 118 to 181 out of 371; severe failures decrease from 72 to 49; Wilcoxon signed-rank p=0.0003 on Claude Code for the main SLUMP effect. Scope: ML method implementation with substantial mathematical structure; authors acknowledge in Limitations that "the observed patterns may differ for broader software-engineering tasks." Cited here as a controlled-experiment demonstration of the structural mechanism, not as a generalizable magnitude.

Marri, S. R. (2026). Constitutional Spec-Driven Development: Enforcing Security by Construction in AI-Assisted Code Generation. arXiv:2602.02584. Single-author case study (n=1 project, single developer, two-week sprint, AI assistant: Claude) of a banking microservices example application addressing 10 CWE/MITRE Top 25 vulnerabilities. Reported a 73% reduction in CWE violations under constitutional constraints versus unconstrained AI generation. Author acknowledges in Threats to Validity (Section 6.6): single-project sample size limits statistical power for quantitative claims, Hawthorne effect risk, and that "banking was selected as the example domain" rather than reflecting actual banking sector deployment data. Cited here as a methodology proof-of-concept demonstrating the same structural mechanism as SLUMP applied to security constraints, not as field deployment data.

Gloaguen, T., Mündler, N., Müller, M., Raychev, V., & Vechev, M. (2026). Evaluating AGENTS.md: Are Repository-Level Context Files Helpful for Coding Agents? arXiv:2602.11988. ETH Zurich and LogicStar.ai. First rigorous evaluation of repository-level context files across four coding agents (Claude Code/Sonnet-4.5, Codex with GPT-5.2 and GPT-5.1 Mini, Qwen Code with Qwen3-30B-Coder) on SWE-bench Lite (300 tasks) and a novel AGENTBENCH benchmark (138 real-world tasks from 12 Python repositories with developer-committed context files). Three conditions tested: no context file, LLM-generated context file, developer-written context file. Key findings: context files tend to *reduce* task success rates compared to no repository context, with inference cost increasing by over 20%; LLM-generated context files reduce average resolution rates by 0.5% on SWE-bench Lite and 2% on AGENTBENCH; developer-written files barely improve outcomes. Cited here as empirical evidence that the Level 1 super-prompting pattern (static CLAUDE.md/AGENTS.md as session context) does not reliably help for one-shot SWE tasks, sharpening the Wasowski Level 1 → Level 2 distinction.

Bainbridge, L. (1983). Ironies of Automation. *Automatica*, 19(6), 775–779. (Referenced for the warning that cutting humans performing easy parts of governance leaves remaining humans with the hard parts under exhausted vigilance.)

Ageless (2026, April). Generation Got Cheap. Validation Didn't. *Canaries in the Mind*, Medium. https://medium.com/canaries-in-the-mind/generation-got-cheap-validation-didnt-d0d0e6c897e8 (Cited in the meta-section for the *Generator-Validator coupling thesis* — validation competence is functionally inseparable from sustained generative engagement — and the *Validator Trap* — cheap generation drives the delegation that hollows out validation, making "reviewing harder" structurally unable to escape the trap. Full framework developed in companion preprint: https://github.com/AgelessK/RGAD.)

Shen, A., & Tamkin, A. (2026). Anthropic study on AI-assisted software engineers learning a new async library. Cited via Ageless (2026): AI-assisted participants showed pronounced deficits in debugging skill — the discriminative competence specifically — despite no significant time savings on the task. Patterns of sustained cognitive engagement preserved learning; patterns of full delegation surrendered it.


## The Verification Bottleneck

Catalini, C., Hui, X., & Wu, J. (2026, February). Some Simple Economics of AGI. arXiv:2602.20946. MIT / Washington University / UCLA. Formal economic model of the verification bottleneck. Establishes the Cost to Automate (c_A) vs Cost to Verify (c_H) framework, the Measurability Gap (Δm), and the verifiable share of deployment (s_v) as the binding constraint on AI productivity.

Bainbridge, L. (1983). Ironies of Automation. *Automatica*, 19(6), 775–779. Foundational paper on the paradox that automation increases rather than decreases cognitive demands on remaining human operators. 1,800+ citations as of 2016 and citation rate accelerating in the AI era.

Parasuraman, R., & Riley, V. (1997). Humans and Automation: Use, Misuse, Disuse, Abuse. *Human Factors*, 39(2), 230–253. Classic paper on automation complacency and the rubber-stamp dynamic now visible in AI code review.

Dobe, O., Arora, J., Zetzsche, S., Labai, N., & Delmas, R. (2026, May). Requirements analysis: catching requirement bugs before they become code. Kiro / AWS Applied Science. https://kiro.dev/blog/deep-spec-analysis/ Neuro-symbolic requirements analysis pipeline (refinement, auto-formalization via SMT-lib, logical analysis) catching four classes of requirement bugs — wrong level of detail, ambiguity, inconsistency, incompleteness — before code generation. Cited as operational example of raising the verification floor at the intent-to-spec surface.

Eline, A. (2025, November). Does your code match your spec? Measuring "correctness" with property-based testing. Kiro / AWS. https://kiro.dev/blog/property-based-testing/ Spec-to-executable-property translation using Hypothesis with random input generation and counterexample shrinking. Cited as operational example of raising the verification floor at the spec-to-code surface, and as concrete evidence that AI-assisted verification scales sub-linearly with input space.

spec-kit-canon (2026). Canon-driven (baseline-driven) workflows for GitHub Spec Kit. https://github.com/maximiliamus/spec-kit-canon Maintains a canonical Markdown specification (the "canon") as a project's authoritative baseline and adds agent-run workflows to detect and reconcile spec-code drift across spec-first, code-first (vibecoding), and drift-repair modes. Cited as an early, at-scale-unvalidated open example of the spec-to-code verification surface becoming machine-tractable — an agent comparing the canonical specification against the implementation and flagging divergence.


## Harness Engineering and Spec-Driven Development

Fowler, M. (2026, April 2). Harness engineering for coding agent users. martinfowler.com. https://martinfowler.com/articles/harness-engineering.html Positions harness engineering as the third phase of AI engineering maturity following prompt engineering and context engineering. Frames the harness as a system of guides, sensors, computational and inferential elements.

Lee et al. (2026). Meta-Harness: Automated Search Over Agent Harness Code. Searched harness code while keeping model weights fixed; outperformed the best hand-designed harness by 7.7 points on text classification and achieved top rankings among same-base-model agents on TerminalBench-2. Cited as empirical evidence that harness optimization produces large gains at fixed model capability.

Yan, K., Wang, J., Zhang, Y., et al. (2025). Git Context Controller: Manage the Context of LLM-based Agents like Git. arXiv:2508.00031. Persistent file-system-style memory workspace with COMMIT/BRANCH/MERGE/CONTEXT operations. Reports +13% improvement on SWE-Bench Verified and >80% task resolution rate, outperforming 26 existing open and commercial systems. Cited as the strongest published controlled study of persistent harness state outperforming session-local context.

LangChain Engineering. (2026, March). Terminal Bench 2.0 harness optimization case study. Coding agent moved from 30th to 5th place on Terminal Bench 2.0 through harness changes alone, no model upgrade. Cited as industry example of harness-level leverage at fixed model capability.

Anthropic. (2025). Demystifying evals for AI agents. https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents Discussion of Opus 4.5's score on CORE-Bench moving from 42% to 95% after harness fixes, with the same underlying model. Cited as a documented same-model harness-leverage example from a frontier lab.

Roy, Y. (2026, March). The Kitchen Loop: User-Spec-Driven Development for a Self-Evolving Codebase. arXiv:2603.25697. Open-source implementation at https://github.com/0xagentkitchen/kitchenloop. Framework for autonomous, self-evolving software built on four primitives: a *specification surface* enumerating supported capabilities; an LLM agent ("As a User × 1000") exercising the spec at ~24–48× human cadence per thread (with a 1,000× ceiling under parallelization, framed by the author as "an order-of-magnitude claim, not a precise multiplier"); *Unbeatable Tests* verifying outcomes against ground truth the code author cannot fake; and *Drift Control* with five automated pause gates (regression failure, canary escape, drift threshold, backpressure, starvation). Validated across two production systems — the Almanak SDK (DeFi strategy framework spanning 14 chains, 30+ protocol connectors, and 21 intent types; 122+ iterations, 728+ merged PRs, 10,913 unit tests, 0 regressions, 16 consecutive zero-bug iterations) and Almanak's Edge Signal Intelligence Platform (163 iterations over 2.5 weeks, 366 merged PRs at 97% merge rate, 2,171 tests, 0 regressions). Aggregate across both: 285+ iterations, 1,094+ merged PRs, monotonic quality-gate improvement (76–91% to 100%), ~$0.38 per merged PR, with documented infrastructure self-healing through the same loop. Stated contribution: "the primitives are not new; our contribution is their composition into a production-tested system with the operational discipline that makes long-running autonomous evolution safe." Design principles include Spec-Anchored Improvement ("self-improving agents should optimize toward specification satisfaction, not proxy metrics") and Drift-Before-Failure ("autonomous loops need continuous trend monitoring, not only binary quality gates"). Cited here as the strongest current production-scale evidence for the spec-anchored *testing-and-oracle* mechanism at the spec-to-code surface of the verification floor — conformance verified behaviorally against an un-gameable oracle (spec held as ground truth), with quality-trend drift control. It does not demonstrate an LLM semantic spec-code conformance gate, nor bidirectional spec-code reconciliation; its "Drift Control" detects quality/regression trends, not spec-code divergence. Scope caveats: Roy's limitations section names oracle quality and spec enumerability as explicit boundary conditions; primary case study is a DeFi framework with enumerable specifications. The paper does not cite Lehman or Bainbridge; the Lehman-architecture connection is drawn in the present paper.


## Organizational Case Studies

Dorsey, J., & Botha, R. (2026, March 31). From Hierarchy to Intelligence. Sequoia Capital. https://sequoiacap.com/article/from-hierarchy-to-intelligence/

Prince, M. (2026, May 20). How I Choose Which Cloudflare Employees to Replace With AI. *Wall Street Journal*. Op-ed by Cloudflare CEO framing the May 2026 ~20% workforce reduction as a response to AI's ability to perform measurement and middle-management functions; explicitly applies Peter Drucker's builders/sellers/measurers framework to classify the cuts.

Drucker, P. F. (1954). *The Practice of Management*. Harper & Row. Original source of the builders/sellers/measurers framework Prince applies. Drucker's argument was that customer value is earned through building and selling, and that measurement is necessary but secondary to the value-creating functions.

Siemiatkowski, S. (2024). Klarna AI assistant performance announcement. Klarna press release, February 2024. (Source for "2.3 million customer service conversations in first month" and "work of 700 full-time agents" claims.)

Klarna. (2025, May). Recruitment announcement for human customer service agents. (Source for "Uber-style" gig worker model reversal and CSAT decline figures.)

Bloomberg interview with S. Siemiatkowski, May 2025. (Source for "lower quality" admission and "always a human if you want" repositioning.)

Benioff, M. (2025, September 2). Interview, *The Logan Bartlett Show*. (Source for "I've reduced it from 9,000 heads to about 5,000" and Agentforce 17% support cost reduction figures.)

Salesforce internal acknowledgments, February 2026 (per industry reporting). Source for "too confident in the ability of AI systems to fully replace human judgment" framing and partial reversal narrative.

Tunguz, T. (2026, March 10). The Org Chart Math Behind AI-Native Speed. https://tomtunguz.com/communication-tax-small-orgs/ (Source for communication-channel analysis: 4-layer 150-person org = 11,175 channels; 30-person AI-enabled team = 435 channels.)

ICONIQ Capital. (2025). State of Software Report 2025. (Source for AI-native time-to-$100M ARR data: Cursor 1 year/19 employees; Lovable 8 months/45 employees; traditional SaaS top quartile 18-20 quarters/500-700 employees.)

Dealroom. (2025). AI startup revenue per employee estimates. (Source for revenue-per-employee figures: Cursor $3.3M, Midjourney $2-4.8M, OpenAI $1.5-2.8M, Anthropic $2.5M+, Perplexity $1.8M, Mercor $4.5M.)

Lütke, T. (2025, April). AI usage is now a baseline expectation. Shopify internal memo (subsequently shared publicly by Lütke). (Source for "AI first, headcount second" and "AI exoskeleton" framing.)

von Ahn, L. (2025, April). Duolingo AI-first announcement. (Source for contractor phase-out and AI-first commitment.)

von Ahn, L. (2025, September 17). Interview, Fast Company Innovation Festival. (Source for "no full-time layoffs" and 4-5x content output figures.)

von Ahn, L. (2026, April). Podcast interview, on backtracking AI-use as performance review metric. (Source for tension between proficiency mandate and metric distortion.)


## Industry Reports

Veracode. (2025). 2025 GenAI Code Security Report: Assessing the Security of Using LLMs for Coding. Methodology: 100+ LLMs tested across 80 coding tasks. Headline: 45% of AI-generated code samples introduce OWASP Top 10 vulnerabilities. https://www.veracode.com/resources/analyst-reports/2025-genai-code-security-report/

DORA / Google Cloud. (2024). Accelerate State of DevOps Report 2024. Finding: 25% increase in AI adoption associated with 1.5% decrease in delivery throughput and 7.2% decrease in delivery stability. https://dora.dev/research/2024/dora-report/

Faros AI. (2026). AI Engineering Report 2026: The Acceleration Whiplash. Two years of telemetry from 22,000 developers across 4,000+ teams. Key findings: median PR review time up 441%, PR sizes up 51.3%, 31% more PRs merging with no review, epics-per-developer up 66.2%. https://www.faros.ai/research

Stack Overflow. (2025). 2025 Developer Survey. Sample: 49,000+ developers. Key findings: 66% cite "AI solutions that are almost right, but not quite" as top frustration; 45% report debugging AI-generated code is more time-consuming. https://survey.stackoverflow.co/2025

Veracode. (2025). 2025 GenAI Code Security Report. https://www.veracode.com/resources/analyst-reports/2025-genai-code-security-report/

DORA / Google Cloud. (2024). Accelerate State of DevOps Report 2024. https://dora.dev/research/2024/dora-report/

Stack Overflow. (2025). 2025 Developer Survey. https://survey.stackoverflow.co/2025

Sonar. (2026). State of Code Developer Survey 2026. Sample: 1,149 professional developers. Key findings: 96% don't fully trust AI code accuracy; 48% always verify before committing; 38% report AI code requires more review effort than human code.

Orosz, G., & Nilsson, E. (2026). The impact of AI on software engineers in 2026: key trends (Parts 1–2). *The Pragmatic Engineer* newsletter. Part 1 (April 14, 2026): https://newsletter.pragmaticengineer.com/p/the-impact-of-ai-on-software-engineers-2026 ; Part 2 (May 19, 2026): https://newsletter.pragmaticengineer.com/p/ai-impact-on-software-engineers-part-2 . Reader survey of 900+ software engineers and engineering leaders on AI tooling use, sentiment, and impact. Key qualitative findings cited here: teams benefiting from AI tools are those that already had testing/deployment guardrails, documented practices, and quality codebases, distilled as "AI is an amplifier, not a fixer"; combined sentiment shifted toward "nuanced/mixed" (≈33% in the newsletter's 2024 survey to ≈50% in 2026), with the primarily-negative share falling (≈23% to ≈10%) and primarily-positive roughly flat; senior engineers reallocating to AI the apprenticeship-grade work previously delegated to juniors; less-experienced engineers as disproportionate, unproductive token spenders who find agentic tools stressful for lack of verification experience. Scope: self-selected, senior-skewing, self-report sample; cited as practitioner field evidence in the spirit of the Stack Overflow and Sonar developer surveys, not as a controlled study, with its developer-experience-frame positivity discounted per the three-frames argument in Part 2.


Atlassian. (2025). State of Developer Experience Report 2025. Survey of ~3,500 developers and managers across six countries. https://www.atlassian.com/teams/software-development/state-of-developer-experience-2025 Reports the average developer spends ~16% of the working week writing code; the remainder on review, design, coordination, debugging, and planning. Cited as a macro complement to Faros's activity-distribution telemetry, supporting the volume-conservation argument (automating a ~16% slice cannot expand total throughput). The ~16% figure is stated in Atlassian's report; surfaced for this series via Orosz (2026).

Cortex. (2026). Engineering in the Age of AI: 2026 Benchmark Report. Survey of 50+ engineering leaders plus development-metric analysis across organizations. https://www.cortex.io/report/engineering-in-the-age-of-ai-2026-benchmark-report Reports change failure rate (the share of deployments that cause outages or rollbacks) up ~30% and incidents per pull request up 23.5% year over year, alongside rising PR volume and deployment frequency, and frames AI as "an indiscriminate amplifier" of existing engineering practices, good and bad. Cited as field evidence consistent with the declining-stability signal in DORA (2024) and as independent corroboration of the amplifier thesis; a self-report leader survey paired with metric analysis, not a controlled study. The ~30% and 23.5% figures are verified against the primary report.

## Industry Commentary and Methodology

Wasowski, J. (2026, April 11). Spec Driven Development — Three Maturity Levels Every AI Team Should Know. *Medium*. Source of the three-level SDD maturity ladder framing (spec-first, spec-anchored, spec-as-source) used in Part 1. The article also reports Constitutional SDD figures under the heading "Production Data," which the series cites via the primary source (Marri 2026) instead, since the primary source describes a single-project case study rather than production deployment data. https://medium.com/@wasowski.jarek/spec-driven-development-three-maturity-levels-every-ai-team-should-know-648c93cf1e1d

Salesforce Engineering. (2026). Scaling Code Reviews: Adapting to a Surge in AI-Generated Code. Internal Prizm system case study. https://engineering.salesforce.com/scaling-code-reviews-adapting-to-a-surge-in-ai-generated-code/


Orosz, G. (2026, January 6). When AI writes almost all code, what happens to software engineering? *The Pragmatic Engineer* newsletter. Opinion/synthesis deepdive on the late-2025 capability inflection (Gemini 3, Opus 4.5, GPT-5.2). Cited here (a) for the practitioner refrain that "writing code fast was never the bottleneck," which this paper reads as naming the two-loop bottleneck — verification (Loop 1) and alignment (Loop 2); and (b) as the secondary source via which the Atlassian (2025) and Cortex (2026) figures are reported. A single-author analysis piece, not a study; exact article URL to be confirmed. Distinct from Orosz & Nilsson (2026), the survey-trends articles.

Appleton, M. (2026). One Developer, Two Dozen Agents, Zero Alignment. GitHub Next. https://maggieappleton.com/zero-alignment Conference talk and research-stage prototype arguing that, as AI makes implementation cheap, "agreeing on what to build" becomes the binding constraint — the intent-alignment (Loop 2) bottleneck — and demonstrating a shared multiplayer workspace that brings planning, context-gathering, and agent collaboration together so intent is established before agents act. Cited (Part 4) as an early, at-scale-unvalidated example of tooling targeting the alignment surface, the Loop 2 analog of the verification-floor tooling.

## Notes on Citations

**Note on citations:** Empirical figures from Veracode, DORA, Faros, and the Wasowski article have been verified against primary sources where possible. The Constitutional SDD methodology is now cited directly via Marri (2026), the primary source, rather than via the Wasowski (2026) secondary commentary which framed it as "production data"; the primary source describes a single-project case study (n=1), which is the framing the series adopts. Both SLUMP and Constitutional SDD are presented in the series as supporting examples of one structural mechanism — persistent, machine-readable specs the agent actually consults outperform conversational specs that don't survive across sessions — rather than as generalizable empirical magnitudes. The specific figures are benchmark- and case-study-specific; what generalizes via Lehman's Law 2 is the mechanism.

## Companion Work

Kao, A. (2026). *Recursive Generative-Adversarial Delegation: An Interdisciplinary Synthesis for Human-Governed Multi-Agent AI Systems.* Preprint. [GitHub](https://github.com/AgelessK/RGAD). Develops the Generator-Validator coupling thesis at the cognitive layer; the present paper develops the compound conservation framework at the organizational layer.
