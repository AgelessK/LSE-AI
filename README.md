# AI Doesn't Break the Laws of Software Evolution (LSE-AI)

*A Lehman-framework synthesis of AI coding agent dynamics, 2024-2026.*

This repository contains the preprint, source markdown, supplementary charts, and accessible blog version of the working paper *AI Doesn't Break the Laws of Software Evolution: A Lehman-Framework Synthesis of AI Coding Agent Dynamics, 2024-2026*.

## Quick links

- **Paper (PDF):** [preprint.pdf](preprint.pdf)
- **Paper source (Markdown):** [preprint-source.md](preprint-source.md)
- **Bibliography:** [references.md](references.md)
- **Blog post (accessible intro):** [blog-post.md](blog-post.md)
- **Charts:** [charts/](charts/)

The paper is also organized as four sequential parts for those who prefer to read it in installments:

- [Part 1 — The Laws and the Empirical Record](part1-laws-and-empirical-record.md)
- [Part 2 — The Framework](part2-framework.md)
- [Part 3 — Operational Practice](part3-operational-practice.md)
- [Part 4 — Organizational Bets](part4-organizational-bets.md)

## What this paper proposes

Meir Lehman's 1974 Laws of Software Evolution — derived from empirical observation of IBM's OS/360 across multiple releases over years — appear to hold under AI coding agents in 2024-2026 to a substantial degree. The empirical record of this period is broadly consistent with theory that has held for half a century: 41.6% complexity increases in 806 Cursor-adopting GitHub repositories (He et al., MSR'26), 22.7% AI-introduced debt persistence across 302,600 commits and 6,299 repositories (Liu et al., 2026), and METR's randomized controlled trial of 16 experienced open-source developers showing 19% measured slowdowns alongside 20% perceived speedups in early-2025 tooling (Becker et al., 2025; the gap, not the absolute number, is the durable signal) are all consistent with patterns Lehman's framework would lead one to expect. A scope note: the He et al. and Liu et al. studies measure open-source public GitHub repositories operating without enterprise governance; what the framework's prescribed governance does to these dynamics at organizational scale is predicted but not directly measured by these studies.

The paper develops a unified framework from this observation. Five of Lehman's eight laws are framed as **structural regularities** of E-type systems — entropy accumulation, self-regulation, conservation of organizational activity, conservation of familiarity, declining quality — that have held empirically across the systems Lehman studied, with strength and exact magnitude varying by context (Lehman framed these as social-science generalizations, not physical constants; Herraiz et al., 2013, find uneven empirical support across the eight laws). The remaining three laws (continuing change, continuing growth, feedback systems) prescribe a **two-loop governance architecture**: *system understanding* (the continuous calibration between how the system should work and how it actually works) and *intent alignment* (the continuous calibration between the should-work model and evolving user need and business strategy). The structure has surface similarity to the DevOps infinity loop, but DevOps centers operational health (DORA metrics, deploy frequency, error rates) rather than spec-reality calibration; the disciplines that do calibrate exist as scattered point practices rather than as a coherent loop.

**Compound conservation** (combining Laws 4 and 5) leads the framework to predict that AI is not expected to increase organizational throughput in aggregate; it is predicted to redistribute fixed activity, making **value density** — not volume — the lever the framework points to. The **verification floor** from Catalini, Hui, and Wu (2026), refined here as a multi-surface stack (intent-to-spec, spec-to-code, code-to-runtime), names where AI value creation is predicted to hit a binding economic constraint; the cost-to-verify curve dominates the cost-to-automate curve above a complexity threshold that current AI capability does not appear able to move on its own.

The framework predicts which organizational AI bets compound and which invert. Replacement bets (Klarna 2024, Salesforce 2025) are predicted to sit below the verification floor and revert; the empirical record now shows both have partially reverted (Klarna fully, Salesforce partially), which is consistent with the framework's prediction though not conclusive evidence for it given alternative explanations. Augmentation bets (Shopify, Duolingo) preserve verification capacity and compound. Three under-observed durable bets — verification infrastructure, verification skill development, business-environment feedback synthesis — quietly compound while rarely generating headlines. The paper names this explicitly: **visibility is anti-correlated with durability**. The most durable bets rarely make the news.

The paper's contribution is not the structural regularities themselves (Lehman's), nor the recent empirical findings (others'), but the synthesis: that a 1974 theory explains 2024-2026 AI coding patterns precisely, and the framework derived from it predicts organizational outcomes already partially observable in the empirical record. A companion paper by the same author, *Recursive Generative-Adversarial Delegation* ([AgelessK/RGAD](https://github.com/AgelessK/RGAD)), develops the Generator-Validator coupling thesis at the cognitive layer; this paper develops the compound conservation framework at the organizational layer.

## Keywords

Software evolution · Lehman's laws · AI coding agents · E-type systems · Verification floor · Conservation laws · Two-loop governance · Spec-driven development · Value density · Generator-Validator coupling · Organizational bets · Software engineering economics

## Citing this work

If you cite this preprint, please use:

```
@misc{kao2026lsefai,
  author = {Kao, Ageless},
  title  = {AI Doesn't Break the Laws of Software Evolution:
            A Lehman-Framework Synthesis of AI Coding Agent Dynamics, 2024-2026},
  year   = {2026},
  howpublished = {Preprint},
  note   = {\url{https://github.com/AgelessK/LSE-AI}}
}
```

## Building the paper from source

The paper is written in Markdown and compiled to PDF via Pandoc with XeLaTeX as the PDF engine. To rebuild:

```bash
pandoc preprint-source.md \
  -o preprint.pdf \
  --pdf-engine=xelatex \
  --toc \
  --toc-depth=3 \
  -V geometry:margin=1in \
  -V documentclass=article \
  -V fontsize=11pt \
  -V mainfont="DejaVu Serif" \
  -V sansfont="DejaVu Sans" \
  -V monofont="DejaVu Sans Mono" \
  -V linkcolor=blue \
  -V urlcolor=blue \
  -V colorlinks=true
```

Requires Pandoc 3.x and a TeX Live distribution with `xelatex` and the DejaVu fonts (or substitute any TrueType serif/sans/mono fonts available on your system).

## Repository structure

```
LSE-AI/
├── README.md                              This file
├── LICENSE                                Creative Commons Attribution 4.0
├── preprint.pdf                           The paper (compiled PDF, 45 pages)
├── preprint-source.md                     Combined Markdown source
├── references.md                          Combined bibliography (50+ entries)
├── blog-post.md                           Medium-ready accessible intro (~2,000 words)
├── part1-laws-and-empirical-record.md     Part 1 standalone
├── part2-framework.md                     Part 2 standalone
├── part3-operational-practice.md          Part 3 standalone
├── part4-organizational-bets.md           Part 4 standalone
└── charts/                                SVG sources and PNG renders
    ├── part1_conservation_chart.{svg,png}
    ├── part2_two_loops.{svg,png}
    ├── part3_verification_floor.{svg,png}
    └── part4_five_bets_map.{svg,png}
```

## License

This work is licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You may share and adapt the material for any purpose, including commercially, with appropriate attribution.

## Author

**Ageless Kao**
Group Product Manager, TrendAI, Trend Micro Inc.
Ottawa, Canada
`ageless_kao@trendmicro.com`

## Acknowledgments

This paper was developed in extended dialogue with Claude (Anthropic), accessed via TrendAI's Claude for Enterprise license, used as a research and editorial scaffold rather than as a substitute for the author's own thinking. The framework synthesis, the structural arguments, and the predictions are the author's; Claude assisted with prior-art search across literatures (Lehman's laws, software-engineering economics, automation psychology, AI-coding empirical studies), citation verification, structural critique of successive drafts, and prose refinement. While TrendAI provides the licensed AI tool, this work was not commissioned by, reviewed by, or written on behalf of TrendAI or Trend Micro Inc. The empirical findings cited from external studies (He et al. 2026, Liu et al. 2026, METR 2025, Catalini-Hui-Wu 2026, and others) were retrieved and verified against primary sources; specific magnitudes are reported as benchmark-specific or sample-specific where applicable.

## Status

This work is a preprint, not yet peer-reviewed. The framework is offered as a synthesis lens and a set of falsifiable predictions about organizational AI outcomes through 2028. Comments, critiques, and engagement are welcome — please open an issue or contact the author by email.
