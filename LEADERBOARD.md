# NanoPitch Student Leaderboard

Ranked by **Realtime RPA (clean condition)** — Raw Pitch Accuracy of the streaming Viterbi decoder on clean audio.

> **Higher is better** for RPA and VAD Accuracy.  **Lower is better** for Median Cent Error.

*Last updated: 2026-04-08*

## Results

| Rank | Student | RPA Clean ↑ | RPA 0 dB ↑ | RPA -5 dB ↑ | VAD Acc ↑ | Median Err ↓ | Note |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Charis Test | — | — | — | — | — | Baseline run with default hyperparameters (gru_size=96, cond_size=64, lr=1e-3). |

---

## Metrics glossary

| Metric | Description |
|--------|-------------|
| RPA | Raw Pitch Accuracy — % of voiced frames within 50 cents of ground truth |
| VAD Acc | Voice Activity Detection accuracy — % of frames correctly classified as voiced/unvoiced |
| Median Err | Median pitch error in cents across all voiced frames (100 cents = 1 semitone) |

Evaluation uses the **realtime Viterbi decoder**, which matches the browser deployment (no lookahead).
