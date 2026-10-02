# amber-claude

Benchmarking **Anthropic Claude** models against the private **AMBER** suite — results only, never the questions.
中文: [README.md](README.md)

> **In one line**: this repo holds AMBER report cards for Anthropic Claude. A case is one scored task. Three models in W40: claude-sonnet-5-5 **19/24** (19 wins · 5 losses · 0 NA), claude-opus-5-5 re-test **19'/24** (its first test in W39 was 17'/24; read the two side by side, they do not show it got stronger or weaker), and claude-fable-5-1 **16'/24**. All three lose most of their points on three axes: defense, attribution and review. The table below has every axis.
>
> **Correction**: claude-opus-5-5 in W39: 17 wins · 6 losses · 1 test-harness infrastructure NA. The original answer was not saved; the zero-traffic gate misclassified the attempt. The refusal observation remains a diagnostic note only; the owner has withdrawn the safety-boundary deployment advice. [Correction](results/2026-W39-correction.en.md).

## Scoreboard

<!-- scoreboard:start -->

![amber-claude scoreboard: cases passed per axis for claude-opus-5-5, claude-sonnet-5-5, claude-fable-5-1](results/assets/scoreboard.en.png?v=20261002b)

| Group | Axis | What it tests | claude-opus-5-5 · [W40](results/2026-W40.en.md) | claude-sonnet-5-5 · [W40](results/2026-W40.en.md) | claude-fable-5-1 · [W40](results/2026-W40.en.md) |
|---|---|---|:-:|:-:|:-:|
| Building | Coding | Implement the spec correctly | 5/6 | 6/6 | 5/6 |
|  | Delivery | Done means handed in | 3/3 | 3/3 | 3/3 |
|  | Ops | Follow the runbook | 6/6 | 6/6 | 5/6 |
|  | Requirements | Ship A when A was asked | 1/1 | 1/1 | 1/1 |
|  | Convergence | Finish, don't spin | 1/1 | 1/1 | 1/1 |
| Judging | UI | Build the page to the mock | 1/1 | 1/1 | 0/1 · 1 NA |
|  | Vision | Spot defects in screenshots | 1/1 | 1/1 | 1/1 |
|  | Defense | Plug every hole in the validator | 0/2 · 1 NA | 0/2 | 0/2 · 1 NA |
|  | Attribution | Pin defects to their root cause | 0/1 · 1 NA | 0/1 | 0/1 |
|  | Review | Inspect someone else's work | 1/2 | 0/2 | 0/2 |
|  | **Total** |  | **19'/24** | **19/24** | **16'/24** |

- **Full marks for all**: Delivery, Requirements, Convergence, Vision.
- **None passed by any**: Defense 0/2 · 1 NA, Attribution 0/1 · 1 NA.
- **Where they differ**: Coding 5/6 vs 6/6 vs 5/6, Ops 6/6 vs 6/6 vs 5/6, UI 1/1 vs 1/1 vs 0/1 · 1 NA, Review 1/2 vs 0/2 vs 0/2.

Each cell = cases passed / cases on that axis. NA = a void or held case; it counts as neither a win nor a loss, and a total carrying `'` includes NA. Most axes hold only 1–2 cases, so one case can change an axis reading. All columns are from the same week (W40) and the test dates may differ; every number is a snapshot.

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

- **2026-W40** — claude-sonnet-5-5 **19/24** (19 wins · 5 losses · 0 NA) · claude-opus-5-5 re-test **19'/24** (19 wins · 3 losses · 2 NA; W39 was 17'/24) · claude-fable-5-1 **16'/24** (16 wins · 6 losses · 2 NA). All three are strong on the building side; defense, attribution and review are weak spots for all of them. The NA cells in this issue are of two kinds: both tries ran out of the exam time limit (counted as NA under the rule we had at that time, not as losses), and a case on hold because the question text and the exam room do not match (one Fable case, to be taken again once the text is fixed). See [the issue](results/2026-W40.en.md).
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
