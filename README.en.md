# amber-claude

Benchmarking **Anthropic Claude** models against the private **AMBER** suite — results only, never the questions.
中文: [README.md](README.md)

> **In one line**: this repo holds AMBER report cards for Anthropic Claude. A case is one scored task. claude-sonnet-5-5's first sitting in W40 scored **19/24** (19 wins · 5 losses · 0 NA), tying the top total; claude-opus-5-5's first sitting in W39 scored **17'/24**. Both models lose most of their points on three axes: defense, attribution and review. The table below has every axis.
>
> **Correction**: claude-opus-5-5 in W39: 17 wins · 6 losses · 1 test-harness infrastructure NA. The original answer was not saved; the zero-traffic gate misclassified the attempt. The refusal observation remains a diagnostic note only; the owner has withdrawn the safety-boundary deployment advice. [Correction](results/2026-W39-correction.en.md).

## Scoreboard

<!-- scoreboard:start -->

![amber-claude scoreboard: cases passed per axis for claude-sonnet-5-5, claude-opus-5-5](results/assets/scoreboard.en.png?v=20261002)

| Group | Axis | What it tests | claude-sonnet-5-5 · [W40](results/2026-W40.en.md) | claude-opus-5-5 · [W39](results/2026-W39.en.md) |
|---|---|---|:-:|:-:|
| Building | Coding | Implement the spec correctly | 6/6 | 5/6 |
|  | Delivery | Done means handed in | 3/3 | 2/3 · 1 NA |
|  | Ops | Follow the runbook | 6/6 | 5/6 |
|  | Requirements | Ship A when A was asked | 1/1 | 1/1 |
|  | Convergence | Finish, don't spin | 1/1 | 1/1 |
| Judging | UI | Build the page to the mock | 1/1 | 1/1 |
|  | Vision | Spot defects in screenshots | 1/1 | 1/1 |
|  | Defense | Plug every hole in the validator | 0/2 | 0/2 |
|  | Attribution | Pin defects to their root cause | 0/1 | 0/1 |
|  | Review | Inspect someone else's work | 0/2 | 1/2 |
|  | **Total** |  | **19/24** | **17'/24** |

- **Full marks for all**: Requirements, Convergence, UI, Vision.
- **None passed by any**: Defense 0/2, Attribution 0/1.
- **Where they differ**: Coding 6/6 vs 5/6, Delivery 3/3 vs 2/3 · 1 NA, Ops 6/6 vs 5/6, Review 0/2 vs 1/2.

Each cell = cases passed / cases on that axis. NA = a void or held case; it counts as neither a win nor a loss, and a total carrying `'` includes NA. Most axes hold only 1–2 cases, so one case can change an axis reading. Sittings are from different weeks; every number is a snapshot.

<!-- scoreboard:end -->

## What this is

- One `results/YYYY-Www.md` per period: same questions, same harness (the program that runs the exam and scores it), full-library runs; same-named models compared across vendors.
- Each report pins: suite size and hashes (a hash is the fingerprint that proves questions were not swapped), per-case d2 scores (our own scoring; the algorithm stays private) and pass/fail, terminal states, token usage and cost (real prices on pay-as-you-go lanes; subscription lanes have no price sheet, so no dollar cost), latency, environment fingerprints, and qualitative verdicts written under evidence discipline.
- Questions, oracles (the graders), transcripts (full answer logs), and intermediate artifacts are **never published** (see "Publication rules").
- AMBER is an agentic, real-work suite (build / ops / review / vision / requirement-drift — the requirements change mid-task). Spec and tooling: [getaskclaw/amber](https://github.com/getaskclaw/amber); the question bodies stay private.
- A "lane" is one vendor's shop/API for a model name; "effort band" is the thinking-effort setting we give the model. The same model name on different lanes may be a different endpoint, so cross-repo references always carry date and band declarations.

## Sibling repos

[amber-gpt](https://github.com/getaskclaw/amber-gpt) · [amber-kimi](https://github.com/getaskclaw/amber-kimi) · [amber-commandcode](https://github.com/getaskclaw/amber-commandcode) · [amber-nous](https://github.com/getaskclaw/amber-nous) · [amber-deepseek](https://github.com/getaskclaw/amber-deepseek) · [amber-doubao](https://github.com/getaskclaw/amber-doubao) · [amber-stepfun](https://github.com/getaskclaw/amber-stepfun) · [amber-ollama](https://github.com/getaskclaw/amber-ollama) · [amber-crof](https://github.com/getaskclaw/amber-crof) · [amber-opencode](https://github.com/getaskclaw/amber-opencode) · [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy) · [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato) · [amber-devin](https://github.com/getaskclaw/amber-devin)

## Results by issue

- **2026-W40** — claude-sonnet-5-5 **19/24**: 19 wins · 5 losses · 0 NA. Full marks on build and ops; weak spots are review and verification. See [the issue](results/2026-W40.en.md).
- **2026-W39** — claude-opus-5-5 **17'/24**: 17 wins · 6 losses · 1 case void due to infrastructure. ' = contested (held for safety refusal) or invalid (infrastructure-related (test harness or scoring environment) cases: held, void or awaiting re-scoring); neither counts as a win or a loss. Every lane with NA carries an apostrophe, including frozen display rows; a hold does not settle the cause. [Correction](results/2026-W39-correction.en.md) · [original report](results/2026-W39.en.md).

The W39 ten-axis completion profile (claude-opus-5-5 vs k3) is on the [correction](results/2026-W39-correction.en.md) page.

## Publication rules (hard lines)

1. Publish only: scores and aggregates, token usage and cost, speed, qualitative verdicts.
2. Never publish: question content, oracles/graders, transcripts, candidate workspaces, or any intermediate artifact that could reconstruct a question.
3. Every issue pins: model ID, effort band, date (UTC), harness version, per-case content hash (bundle_sha), cross-checked against the public hash index in [amber](https://github.com/getaskclaw/amber).
4. Case numbers and suite structure are private: public results use stable aliases (A-xxxxxxxx, hash-derived) plus bundle hashes only; internal case IDs, variant names, and question descriptions never appear.
5. Tone: this is community measurement, not an attack on vendors. Data talks; wording stays restrained.

## One methodological note

Same model, same provider, two runs can still score differently — sampling settings, load, and server-side versions all drift. Every claim here carries a date and a band, and we re-test regularly. A single day's number is a snapshot, not a law.
