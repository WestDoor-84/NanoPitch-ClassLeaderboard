# Submitting to the NanoPitch Leaderboard

Follow these steps to submit your trained model and appear on the leaderboard.

## 1. Train your model

```bash
cd training
python train.py --data-dir ../data --output-dir ./runs/my_run \
  --epochs 50 --batch-size 32
```

Your best checkpoint will be saved at `./runs/my_run/checkpoints/best.pth`.

## 2. Create your submission directory

Create a folder under `submissions/` named after yourself (no spaces):

```
submissions/
└── your_name/
    ├── weights.pth       ← your best.pth (rename it)
    └── submission.yaml   ← required metadata
```

### submission.yaml format

```yaml
name: "Your Full Name"
note: "Brief description of what you changed — e.g. increased gru_size to 128 and tuned LR schedule."
```

Both fields are required. `note` appears on the leaderboard and in the PR comment, so make it useful.

## 3. Open a pull request

> **Do not fork this repo.** Because it is a template repository, forking puts you in GitHub's fork network and PRs may target the wrong upstream. Use the steps below instead.

1. If you haven't already, click **"Use this template" → "Create a new repository"** on the GitHub repo page to create your own copy.
2. Clone your copy, add your `submissions/your_name/` directory, and push.
3. Open a PR from your repo against `main` on this repo.

The bot will automatically:
- Evaluate your checkpoint against the test set.
- Post your scores as a PR comment within a few minutes.

## 4. Wait for review

Once the PR is merged your scores are committed to `results/` and `LEADERBOARD.md` is rebuilt.

---

## Tips

- Only the **realtime Viterbi** score (no lookahead) counts for ranking — it matches what the browser actually does.
- Larger models aren't always better. A GRU size of 256+ can degrade due to insufficient training data.
- The biggest win is usually in the `augment_mel_batch()` stub in `train.py` — implement proper noise mixing!
- You can submit multiple times; each PR replaces your previous entry on the leaderboard.
