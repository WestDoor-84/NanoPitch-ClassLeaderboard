# NanoPitch Student Leaderboard

*Last updated: 2026-04-16*

All metrics use the **realtime Viterbi decoder** (no lookahead), matching the browser deployment.

---

## 1. RPA Leaderboards

### RPA — Clean Audio ↑

Raw Pitch Accuracy on clean (no-noise) test clips. Higher is better.

| Rank | Student | RPA Clean ↑ | RPA +0 dB | RPA -5 dB | VAD Acc | Median Err | Note |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Charis NoiseAugBaseline | 96.6% | 88.8% | 87.8% | 97.3% | 12.1¢ | Baseline run with default hyperparameters, and the baseline noise augmentation (gru_size=96, cond_size=64, lr=1e-3). |
| 2 | Dillon Positive Weight | 95.4% | 89.1% | 91.3% | 97.7% | 10.6¢ | Applied recommended augmentation w/ 25% chance of clean output and applied 0.6x weight to stop the model from over-favoring voiced predictions. |
| 3 | Charis Test | 94.8% | 87.3% | 88.0% | 98.3% | 6.5¢ | Baseline run with default hyperparameters (gru_size=96, cond_size=64, lr=1e-3). |
| 4 | Charis - Noise Augmentation v2 | 90.1% | 86.3% | 88.4% | 95.8% | 18.0¢ | Baseline run with default hyperparameters, with the basic noise augmentation and clean signal 10% of the time (gru_size=96, cond_size=64, lr=1e-3). |

### RPA — Macro Average (all SNR conditions) ↑

Mean RPA across all 6 SNR conditions (clean, −5 dB, 0 dB, +5 dB, +10 dB, +20 dB). Higher is better.

| Rank | Student | RPA Macro Avg ↑ | RPA Clean | RPA +0 dB | RPA -5 dB | Note |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Dillon Positive Weight | 92.2% | 95.4% | 89.1% | 91.3% | Applied recommended augmentation w/ 25% chance of clean output and applied 0.6x weight to stop the model from over-favoring voiced predictions. |
| 2 | Charis NoiseAugBaseline | 91.9% | 96.6% | 88.8% | 87.8% | Baseline run with default hyperparameters, and the baseline noise augmentation (gru_size=96, cond_size=64, lr=1e-3). |
| 3 | Charis Test | 90.2% | 94.8% | 87.3% | 88.0% | Baseline run with default hyperparameters (gru_size=96, cond_size=64, lr=1e-3). |
| 4 | Charis - Noise Augmentation v2 | 88.0% | 90.1% | 86.3% | 88.4% | Baseline run with default hyperparameters, with the basic noise augmentation and clean signal 10% of the time (gru_size=96, cond_size=64, lr=1e-3). |

---

## 2. Gross Error Rate Leaderboards

### Gross Error Rate — Clean Audio ↓

Fraction of voiced frames with pitch error > 50 cents on clean audio. Lower is better.

| Rank | Student | Gross Err Clean ↓ | GER +0 dB | GER -5 dB | Note |
| --- | --- | --- | --- | --- | --- |
| 1 | Charis NoiseAugBaseline | 3.4% | 11.2% | 12.2% | Baseline run with default hyperparameters, and the baseline noise augmentation (gru_size=96, cond_size=64, lr=1e-3). |
| 2 | Dillon Positive Weight | 4.6% | 10.9% | 8.7% | Applied recommended augmentation w/ 25% chance of clean output and applied 0.6x weight to stop the model from over-favoring voiced predictions. |
| 3 | Charis Test | 5.2% | 12.7% | 12.0% | Baseline run with default hyperparameters (gru_size=96, cond_size=64, lr=1e-3). |
| 4 | Charis - Noise Augmentation v2 | 9.9% | 13.7% | 11.6% | Baseline run with default hyperparameters, with the basic noise augmentation and clean signal 10% of the time (gru_size=96, cond_size=64, lr=1e-3). |

### Gross Error Rate — Macro Average (all SNR conditions) ↓

Mean gross error rate across all 6 SNR conditions. Lower is better.

| Rank | Student | Gross Err Macro Avg ↓ | GER Clean | GER +0 dB | GER -5 dB | Note |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Dillon Positive Weight | 7.8% | 4.6% | 10.9% | 8.7% | Applied recommended augmentation w/ 25% chance of clean output and applied 0.6x weight to stop the model from over-favoring voiced predictions. |
| 2 | Charis NoiseAugBaseline | 8.1% | 3.4% | 11.2% | 12.2% | Baseline run with default hyperparameters, and the baseline noise augmentation (gru_size=96, cond_size=64, lr=1e-3). |
| 3 | Charis Test | 9.8% | 5.2% | 12.7% | 12.0% | Baseline run with default hyperparameters (gru_size=96, cond_size=64, lr=1e-3). |
| 4 | Charis - Noise Augmentation v2 | 12.0% | 9.9% | 13.7% | 11.6% | Baseline run with default hyperparameters, with the basic noise augmentation and clean signal 10% of the time (gru_size=96, cond_size=64, lr=1e-3). |

---

## Metrics glossary

| Metric | Description |
|--------|-------------|
| RPA | Raw Pitch Accuracy — % of voiced frames within 50 cents of ground truth (higher = better) |
| Gross Error Rate (GER) | % of voiced frames with pitch error > 50 cents (lower = better) |
| VAD Acc | Voice Activity Detection accuracy — % of frames correctly classified as voiced/unvoiced |
| Median Err | Median pitch error in cents across voiced frames (100 cents = 1 semitone) |
| Macro Avg | Mean of the metric across all 6 SNR conditions: clean, −5 dB, 0 dB, +5 dB, +10 dB, +20 dB |
