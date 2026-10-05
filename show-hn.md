# Title
Show HN: HaHaScore — sentence-level humor strength predictor (5-fold AUC 0.69 humor / 0.55 gold, 1.04M params, CPU)

# Body
Hi HN — I built a humor detector, then I caught myself faking the validation.

HaHaScore reads transcripts and audio together via a Cascade Gate: text confidence gates the audio stream, then a BiGRU scores per-segment humor strength. 1.04M parameters, runs on CPU, under 10 ms per utterance.

**The lesson from this project**: single-fold AUC on imbalanced speech-humor tasks (~1% positive rate, n ≤ 20 gold videos) systematically overstates performance by 0.15–0.20 AUC. Speaker identity and language channel leak through random K-fold splits.

After running a 5×3 repeated speaker-disjoint CV (15 measurements, paired bootstrap 95% CI), the honest 5-fold numbers are:

| Metric | Single-fold (claimed) | 5×3 repeated speaker-disjoint CV |
|---|---|---|
| Humor AUC | 0.823 | **0.6924 ± 0.0359** |
| Gold AUC | 0.613 | **0.5453 ± 0.1313** |

The single-fold numbers were folded into an earlier "Cascade Gate v7 AUC 0.860" headline that turned out to be a leakage artifact. The 5×3 CV is what the paper now reports.

I deleted the HF model deployment (0 downloads over 8 days anyway), kept the audit and falsification scripts in the repo, and drafted a methodology paper: *"Evaluating Speech-Humor Models Without Identity Leakage: A Self-Falsification Case Study."* The paper itself is **the artifact** — it documents the 5×3 repeated speaker-disjoint CV protocol that catches single-fold fold-luck at p < 0.001 (one such claim reversed from +0.163 to −0.127 across 15 measurements).

The model itself is at github.com/Das-rebel/HaHaScore. Open source (MIT), reproducible, currently archived pending re-validation on a larger labeled corpus.

The next 0.05 AUC doesn't come from compute. It comes from humans labeling ~100 more gold videos across more languages — the 12-video gold set this design was tuned against is too small to support any single-fold number. If you can spare a few hours on a clip, open a PR.