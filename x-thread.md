1/ Every comedian knows the bomb. ML has been dying the same way for years — reading transcripts and calling it comedy. AUC: ~0.50.

The transcript was never the joke. The laugh is in the room.

2/ I built a model that listens.

HaHaScore: sentence-level humor strength predictor.
- 1.04M params
- CPU
- under 10 ms
- 5×3 repeated speaker-disjoint CV: humor AUC 0.69, gold AUC 0.55

github.com/Das-rebel/HaHaScore

[attach video]

3/ The honest number is 0.69 / 0.55 — not 0.86. A single-fold CV at n=12 gold videos inflated performance by 0.15–0.20 AUC.

5×3 repeated CV caught a +0.163 fold-luck at p < 0.001 (true delta was −0.127).

4/ The trick isn't bigger models. It's that text alone is random — RoBERTa, 355M params, AUC 0.499. The signal is in the audio. In *delivery*.

5/ So I made text a confidence prior that *gates* the audio stream. When the words are sure, the sound gets through. When they aren't, the model listens for the laugh anyway.

1.04M params beats 355M by *architectural humility*. On the 5-fold honest number.

6/ The methodology is now the artifact. 5×3 repeated speaker-disjoint CV with bootstrap CIs.

Every speech-humor paper should report it. Most don't.

7/ MIT license. Repo has the falsification scripts + paper draft.

If you can spare a few hours labeling a gold clip, the next 0.05 doesn't come from compute. It comes from humans.

github.com/Das-rebel/HaHaScore