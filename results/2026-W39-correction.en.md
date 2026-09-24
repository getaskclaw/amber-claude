# 2026-W39 correction: A-1fd3683a is NA due to test-harness infrastructure

> 中文：[中文](2026-W39-correction.md)

A case is one task counted in the score. NA means neither a win nor a loss; it is not zero. bundle_sha is the case-content hash fingerprint.

## What changes

The W39 report for `claude-opus-5-5 @ Anthropic` marked the case below as contested (held for safety refusal). It used that record to describe a “probabilistic safety boundary”. The corrected score label is **invalid / NA (test-harness infrastructure)**.

| Public alias | bundle_sha | Old label | Corrected label |
|---|---|---|---|
| A-1fd3683a | `6a980035b42f` | contested, safety refusal, NA | invalid, void due to test-harness infrastructure, NA; neither a win nor a loss |

The reason for NA is that **the original answer was not saved and cannot be scored; the zero-traffic gate also misclassified the attempt and stopped the test**. This is an answer-capture and test-harness infrastructure problem. It cannot add a model pass or loss, and it does not deny that a refusal was observed.

Diagnostic note: the retained account records a refusal observation with `stop_reason: refusal`; that refusal's answer text was not saved. There was 1 later probe on the same day, which returned `end_turn`. The saved re-probe is a diagnostic attachment only. It cannot replace the original answer or enter capability scores. These observations do not show that “several checks proved there was no refusal”.

**The owner has signed off on withdrawing** the “probabilistic safety boundary” interpretation and deployment advice based on this case. This limits the claim to what the evidence supports. It does not infer from one re-probe that the model never refuses, now passes, or is confirmed to fail.

## Same pass count, clear status

The valid pass count stays at 17 in this 24-case set. In full: **17 wins · 6 losses · 1 case void due to infrastructure**. Short labels still use `17'/24`. The NA case stays in the case set, but is not a win or a loss.

Shared legend: `'` marks held or void cases — **contested (held for safety refusal) or invalid (infrastructure-related (test harness or scoring environment) cases: held, void or awaiting re-scoring); neither counts as a win or a loss**. A-1fd3683a has the score label invalid, no longer safety refusal. The refusal observation remains only in the diagnostic note above. Case marks: ✓ pass; ✗ fail; ⊘ contested; ◍ invalid; — not tested.

The Delivery axis still uses only valid cases: 2 scored cases, with 1 NA case left out. Its value does not change. Only the reason for leaving out the case changes from contested to invalid. Do not fill it with zero.

Corrected charts (created in this same release):

![Corrected board: 17 wins, 6 losses and 1 case void due to infrastructure](assets/2026-W39-board-correction.en.png?v=corrections-20260924-r2)

![Unchanged ten-axis values; Delivery excludes 1 invalid / NA case](assets/2026-W39-radar-correction.en.png?v=corrections-20260924-r2)

## Keep the report, correct the current entry points

The [old W39 report](2026-W39.en.md) stays, with a correction link at the top. This notice replaces its claims about this case in the summary, matrix, legend, Findings and deployment advice. Other case scores do not change.

The current README, hub footnotes, site legends in both languages and chart text were updated in the same release. The board chart moves 1 case from contested to invalid without changing wins or losses. The profile chart uses the new reason too.
