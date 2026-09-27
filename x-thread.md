1/ Every comedian knows the bomb. ML has been dying the same way for years — reading transcripts and calling it comedy. AUC: ~0.50.

The transcript was never the joke. The laugh is in the room.

2/ I built a model that listens.

HaHaScore: sentence-level humor strength predictor.
- 1.04M params
- CPU
- under 10 ms
- AUC 0.860 (pseudo) / 0.590 (gold)

github.com/Das-rebel/HaHaScore

[attach video]

3/ The trick isn't bigger models. It's that text alone is random — RoBERTa, 355M params, AUC 0.499. The signal is in the audio. In *delivery*.

4/ So I made text a confidence prior that *gates* the audio stream. When the words are sure, the sound gets through. When they aren't, the model listens for the laugh anyway.

1.04M params beats 355M by *architectural humility*.

5/ Tested on the gold set — Comedy Central Stand-Up + Montreux Comedy. 12 specials. EN/ES/FR. Mike Birbiglia, Mae Martin, Élodie Poux, Jayde Adams, Nash.

Real laughter blocks at real timestamps. The model scored 0.860 on the bits themselves; the room laughed 0.590. That gap *is* the audience.

6/ Humor ≠ laughter. The model measures the intrinsic strength of the delivery. Behavioral laughter depends on the room, the audience, shared knowledge.

That's not a flaw. That's the field's feature.

7/ MIT license. 5-line inference. HF model + arxiv paper in the repo.

The next 0.02 doesn't come from compute. It comes from humans labeling the gold.

If you can spare a few hours on a clip, open a PR.

github.com/Das-rebel/HaHaScore
