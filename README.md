# HaHaScore launch pack (DEPRECATED 2026-10-05)

> **STATUS: The numerical claims in this launch pack are DEPRECATED.**
>
> Earlier draft claimed "AUC 0.860 ± 0.018" for the Cascade Gate v7 model. That number was a single-fold leakage artifact.
>
> **Honest 5×3 repeated speaker-disjoint CV**:
> - Humor AUC: **0.6924 ± 0.0359**
> - Gold AUC:  **0.5453 ± 0.1313**
>
> The previous per-language normalization "+0.163" finding was refuted by the same protocol (true delta = −0.127, p = 0.0004, CI [−0.183, −0.078], n = 15). See `5x3_cv_results.json` and `COUNCIL_FINAL_DECISION.md` in the main repo.

## Files (kept for archive, do not redistribute with inflated claims)

| File | Status | Notes |
|---|---|---|
| `index.html` | needs `show-hn.md` / `youtube-description.txt` rewrite | Honest 5-fold number |
| `hahascore-demo.mp4` | keep as-is (visual demo only) | No fabricated claims in B-roll |
| `hahascore-vertical.mp4` | keep as-is | — |
| `hahascore-square.mp4` | keep as-is | — |
| `hahascore-thumbnail.jpg` | replace | Remove "AUC 0.860" if present in image |
| `youtube-description.txt` | REPLACED Oct 5 2026 | Now cites honest 5-fold |
| `show-hn.md` | REPLACED Oct 5 2026 | Now cites honest 5-fold |
| `x-thread.md` | REPLACED Oct 5 2026 | Now cites honest 5-fold |
| `linkedin.txt` | REPLACED Oct 5 2026 | Now cites honest 5-fold |

## Quickest path to ship (after fixes)

DO NOT publish this launch pack until the video thumbnail + index.html are also fixed. The earlier draft's claim "AUC 0.860" is now known to be a leakage artifact per `5x3_cv_results.json`. Publishing it now would contradict the falsification paper in the same org.

1. Manually edit `hahascore-thumbnail.jpg` to remove "AUC 0.860" text (or replace with "5-fold AUC 0.69")
2. Manually edit `index.html` to replace AUC references in body text
3. Re-record demo videos to show the honest 5-fold breakdown
5. Then upload to YouTube + distribute via fixed `show-hn.md` / `x-thread.md` / `linkedin.txt`

## Why this matters

The single most embarrassing failure mode for an AI research project is publishing a number you cannot reproduce. The 5×3 repeated CV protocol (15 measurements, paired bootstrap CI) is the methodology that catches this failure mode — and the protocol itself is the artifact. See `arxiv_submission/hahascore.tex` for the full paper draft.

**Do not cite the 0.860 number anywhere.** It is a leakage artifact, documented in the project's own falsification logs.