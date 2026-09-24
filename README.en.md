# amber-claude

Benchmarking **Anthropic Claude** models against the private **AMBER** suite — results only, never the questions.
中文: [README.md](README.md)

> **In one line**: this repo holds AMBER report cards for Anthropic Claude. A case is one scored task. claude-opus-5-5 in W39: 17 wins · 6 losses · 1 test-harness infrastructure NA. The original answer was not saved; the zero-traffic gate misclassified the attempt. The refusal observation remains a diagnostic note only; the owner has withdrawn the safety-boundary deployment advice. [Correction](results/2026-W39-correction.en.md).

## What this is

- One `results/YYYY-Www.md` per period: same questions, same harness (the program that runs the exam and scores it), full-library runs; same-named models compared across vendors.
- Each report pins: suite size and hashes (a hash is the fingerprint that proves questions were not swapped), per-case d2 scores (our own scoring; the algorithm stays private) and pass/fail, terminal states, token usage and cost (real prices on pay-as-you-go lanes; subscription lanes have no price sheet, so no dollar cost), latency, environment fingerprints, and qualitative verdicts written under evidence discipline.
- Questions, oracles (the graders), transcripts (full answer logs), and intermediate artifacts are **never published** (see "Publication rules").
- AMBER is an agentic, real-work suite (build / ops / review / vision / requirement-drift — the requirements change mid-task). Spec and tooling: [getaskclaw/amber](https://github.com/getaskclaw/amber); the question bodies stay private.
- A "lane" is one vendor's shop/API for a model name; "effort band" is the thinking-effort setting we give the model. The same model name on different lanes may be a different endpoint, so cross-repo references always carry date and band declarations.

## Sibling repos

[amber-gpt](https://github.com/getaskclaw/amber-gpt) · [amber-kimi](https://github.com/getaskclaw/amber-kimi) · [amber-commandcode](https://github.com/getaskclaw/amber-commandcode) · [amber-nous](https://github.com/getaskclaw/amber-nous) · [amber-deepseek](https://github.com/getaskclaw/amber-deepseek) · [amber-doubao](https://github.com/getaskclaw/amber-doubao) · [amber-stepfun](https://github.com/getaskclaw/amber-stepfun) · [amber-ollama](https://github.com/getaskclaw/amber-ollama) · [amber-crof](https://github.com/getaskclaw/amber-crof) · [amber-opencode](https://github.com/getaskclaw/amber-opencode) · [amber-workbuddy](https://github.com/getaskclaw/amber-workbuddy) · [amber-goldenpotato](https://github.com/getaskclaw/amber-goldenpotato) · [amber-devin](https://github.com/getaskclaw/amber-devin)

## Latest results

- **2026-W39** — claude-opus-5-5 **17'/24**: 17 wins · 6 losses · 1 case void due to infrastructure. ' = contested (held for safety refusal) or invalid (infrastructure-related (test harness or scoring environment) cases: held, void or awaiting re-scoring); neither counts as a win or a loss. Every lane with NA carries an apostrophe, including frozen display rows; a hold does not settle the cause. [Correction](results/2026-W39-correction.en.md) · [original report](results/2026-W39.en.md).

![Ten-axis completion profile: claude-opus-5-5 vs k3](results/assets/2026-W39-radar-correction.en.png?v=corrections-20260924-r2)

## Publication rules (hard lines)

1. Publish only: scores and aggregates, token usage and cost, speed, qualitative verdicts.
2. Never publish: question content, oracles/graders, transcripts, candidate workspaces, or any intermediate artifact that could reconstruct a question.
3. Every issue pins: model ID, effort band, date (UTC), harness version, per-case content hash (bundle_sha), cross-checked against the public hash index in [amber](https://github.com/getaskclaw/amber).
4. Case numbers and suite structure are private: public results use stable aliases (A-xxxxxxxx, hash-derived) plus bundle hashes only; internal case IDs, variant names, and question descriptions never appear.
5. Tone: this is community measurement, not an attack on vendors. Data talks; wording stays restrained.

## One methodological note

Same model, same provider, two runs can still score differently — sampling settings, load, and server-side versions all drift. Every claim here carries a date and a band, and we re-test regularly. A single day's number is a snapshot, not a law.
