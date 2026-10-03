# amber-claude

> ⚠️ **Correction (2026-10-02, second)**: one defense-axis case, A-d511f9e8, is now NA on every lane (the exam room did not grade the file the candidate delivered, and the grader asks for something the task text does not say). The denominator and the **number of passed cases do not change**; every lane's total now carries `'`. In this repo's issue tables, read that cell as NA. Everything else stays as published; the [correction notice](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.en.md) governs.

We give Anthropic's Claude models the same **private**, real-work exam (a question bank called **AMBER**, 24 tasks). Only results are public, never the questions.
中文: [README.md](README.md)

> **In one line**: three Claude models each took the same 24 real-work tasks (writing code, running ops, spotting flaws in someone else's work, and more). Tasks passed: **claude-sonnet-5-5 19'/24 · claude-opus-5-5 19'/24 · claude-fable-5-1 16'/24**. They pass most of the hands-on tasks (coding, ops, delivery) and lose most of their points on three judgment tasks: defense, attribution and review.
>
> A `'` after a score means some tasks are not scored for now (NA): neither a pass nor a fail; reasons below. claude-opus-5-5 is a re-test; its first test in W39 was 17'/24. Read the two side by side; they do not show it got stronger or weaker.
>
> **Correction**: claude-opus-5-5 in W39: 17 wins · 6 losses · 1 test-harness infrastructure NA. The original answer was not saved; the zero-traffic gate misclassified the attempt. The refusal observation remains a diagnostic note only; the owner has withdrawn the safety-boundary deployment advice. [Correction](results/2026-W39-correction.en.md).

## Scoreboard

<!-- scoreboard:start -->

![amber-claude scoreboard: cases passed per axis for claude-opus-5-5, claude-sonnet-5-5, claude-fable-5-1](results/assets/scoreboard.en.png?v=20261002c)

| Group | Axis | What it tests | claude-opus-5-5 · [W40](results/2026-W40.en.md) | claude-sonnet-5-5 · [W40](results/2026-W40.en.md) | claude-fable-5-1 · [W40](results/2026-W40.en.md) |
|---|---|---|:-:|:-:|:-:|
| Building | Coding | Implement the spec correctly | 5/6 | 6/6 | 5/6 |
|  | Delivery | Done means handed in | 3/3 | 3/3 | 3/3 |
|  | Ops | Follow the runbook | 6/6 | 6/6 | 5/6 |
|  | Requirements | Ship A when A was asked | 1/1 | 1/1 | 1/1 |
|  | Convergence | Finish, don't spin | 1/1 | 1/1 | 1/1 |
| Judging | UI | Build the page to the mock | 1/1 | 1/1 | 0/1 · 1 NA |
|  | Vision | Spot defects in screenshots | 1/1 | 1/1 | 1/1 |
|  | Defense | Plug every hole in the validator | 0/2 · 2 NA | 0/2 · 1 NA | 0/2 · 2 NA |
|  | Attribution | Pin defects to their root cause | 0/1 · 1 NA | 0/1 | 0/1 |
|  | Review | Inspect someone else's work | 1/2 | 0/2 | 0/2 |
|  | **Total** |  | **19'/24** | **19'/24** | **16'/24** |

- **Full marks for all**: Delivery, Requirements, Convergence, Vision.
- **None passed by any**: Defense, Attribution (not one pass on these axes; NA does not count as a fail).
- **Where they differ** (numbers follow the table columns, left to right): Coding 5/6 vs 6/6 vs 5/6, Ops 6/6 vs 6/6 vs 5/6, UI 1/1 vs 1/1 vs 0/1 · 1 NA, Review 1/2 vs 0/2 vs 0/2.

Each cell = cases passed / cases on that axis (a case is one scored task). NA = the case was voided or put on hold; it counts as neither a pass nor a fail, and a total carrying `'` contains at least one NA. Most axes hold only 1–2 cases, so one case moves the reading: do not over-read small gaps. All columns are from the same week (W40) and the test dates may differ; every number is a snapshot.

<!-- scoreboard:end -->

## What this is

- **AMBER** is a private real-work question bank: models do what an engineer does (build a feature, run an ops runbook, review someone else's delivery, find defects in screenshots, cope with requirements that change mid-task, and more), then get scored against preset checks. Spec and tooling: [getaskclaw/amber](https://github.com/getaskclaw/amber); the questions themselves stay private.
- **One report per period**, `results/YYYY-Www.md`: same questions, same harness (the program that runs the exam and scores it), every model sits the full library. Each report gives suite size and hashes (a hash is the fingerprint that proves questions were not swapped), pass or fail and score per case (our own scoring; the algorithm stays private), token usage and cost (subscription lanes have no price sheet, so no dollar cost), time taken, environment details, and written verdicts based on the evidence.
- Questions, graders, full answer logs and intermediate artifacts are **never published** (see "Publication rules").

A few terms:

- **Case**: one scored task. **NA**: the case was voided or put on hold; it counts as neither a pass nor a fail.
- **Lane**: one vendor's shop or API for a model name. The same model name on different lanes may be a different endpoint, so cross-repo comparisons always carry the date and band.
- **Effort band**: the thinking-effort setting we give the model.

## Sibling repos

[amber-gpt](https://github.com/getaskclaw/amber-gpt) · [amber-kimi](https://github.com/getaskclaw/amber-kimi) · [amber-commandcode](https://github.com/getaskclaw/amber-commandcode) · [amber-nous](https://github.com/getaskclaw/amber-nous) · [amber-deepseek](https://github.com/getaskclaw/amber-deepseek) · [amber-doubao](https://github.com/getaskclaw/amber-doubao) · [amber-stepfun](https://github.com/getaskclaw/amber-stepfun) · [amber-ollama](https://github.com/getaskclaw/amber-ollama) · [amber-crof](https://github.com/getaskclaw/amber-crof) · [amber-opencode](https://github.com/getaskclaw/amber-opencode) · [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy) · [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato) · [amber-devin](https://github.com/getaskclaw/amber-devin)

## Results by issue

- **2026-W40** — claude-sonnet-5-5 **19'/24** (19 wins · 4 losses · 1 NA) · claude-opus-5-5 re-test **19'/24** (19 wins · 2 losses · 3 NA; W39 was 17'/24) · claude-fable-5-1 **16'/24** (16 wins · 5 losses · 3 NA). All three are strong on the hands-on tasks; defense, attribution and review are weak spots for all of them. The NA cells in this issue have three causes:
  1. Defense case A-d511f9e8 is on hold on every lane (the exam room's grading had problems; see the [correction](https://github.com/getaskclaw/amber/blob/main/docs/corrections-2026-10-02-a-d511f9e8.en.md)); each of the three models has this one NA;
  2. Both tries ran out of the exam time limit, counted as NA under the rule we had at that time, not as losses (2 Opus cases, 1 Fable case);
  3. The question text and the exam room do not match, so the case is on hold (1 Fable case, to be taken again once the text is fixed).

  See [the issue](results/2026-W40.en.md).
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
