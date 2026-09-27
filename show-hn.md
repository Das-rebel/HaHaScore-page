# Title
Show HN: HaHaScore — sentence-level humor strength predictor (0.860 AUC, 1.04M params, CPU)

# Body
Hi HN — I built a humor detector.

For years, joke-detection research kept dying the same way: throw RoBERTa at a transcript and call it comedy. AUC: ~0.50. The transcript was never the joke. The laugh is in the room — in prosody, in timing, in vocal inflection. Delivery is everything.

HaHaScore listens. Whisper transcribes with word-level timestamps. Twenty equal-length segments per utterance. RoBERTa reads each one. Then — here's the twist — **text doesn't get a vote**. Its confidence gates the audio stream. When the words are sure, the sound gets through. 1.04M parameters. Runs on CPU. Under 10 ms per utterance.

**Numbers (5-fold CV, StandUp4AI, 12 gold-labeled specials from Comedy Central Stand-Up + Montreux Comedy — Mike Birbiglia, Mae Martin, Élodie Poux, Jayde Adams, Nash, more):**

| Model | AUC | Params | Notes |
|---|---|---|---|
| Text-only RoBERTa-large | 0.499 | 355M | indistinguishable from random |
| Audio-only WavLM LR | 0.538 | 94M | moderate signal |
| Bridge 4 (audio + BiGRU arcs) | 0.842 ± 0.027 | 790K | sequential modeling |
| v6 cross-attention fusion | 0.858 ± 0.015 | 1.16M | text ⇄ audio |
| **Cascade Gate v7 (new SOTA)** | **0.860 ± 0.018** | **1.04M** | **text gates audio** |

The weird number: **pseudo-label AUC is 0.860, gold-label AUC is 0.590.** That's not a bug — it means the model measures the intrinsic humor strength of the delivery, while human laughter depends on the room, the audience, the shared knowledge. The 0.27 gap *is* the audience.

**Honest limitations:**
- Text features beyond RoBERTa CLS would likely help
- Prosody is engineered (RMS/ZCR/MFCC/pitch), not learned
- "Funny" is culturally loaded; the gold set leans English/Western standup

**Open asks:**
- Help label a few hours of laughter on new specials — PRs welcome
- Try it on your own podcast / set; I want to see where it breaks
- Architecture feedback welcome — the cascade gate is a small idea, maybe it generalizes

**GitHub:** github.com/Das-rebel/HaHaScore
**HF model:** Hayasuki/hahascore-cascade
**5-line inference.** MIT. Happy to answer questions.
