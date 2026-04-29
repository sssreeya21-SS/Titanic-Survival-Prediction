# 🛠 Owner Setup Guide

Follow these steps **once** to get your competition running. Takes ~10 minutes.

---

## Step 1 — Create the GitHub Repository

1. Go to https://github.com/new
2. Set name: `titanic-survival-competition`
3. Set to **Public**
4. Do **NOT** initialize with README (you'll push your own)
5. Click **Create repository**

---

## Step 2 — Push all files to GitHub

```bash
cd titanic-competition          # this folder

git init
git add .
git commit -m "🚀 Initial competition setup"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/titanic-survival-competition.git
git push -u origin main
```

> ⚠️ Make sure `data/ground_truth.csv` is in `.gitignore` (it already is).  
> It must **never** be pushed to GitHub publicly.

---

## Step 3 — Add the Ground Truth as a GitHub Secret

The ground truth CSV is stored as a base64-encoded GitHub Secret so the CI can use it without exposing it publicly.

**On your local machine:**
```bash
# Encode ground_truth.csv to base64
base64 -w 0 data/ground_truth.csv
# On macOS: base64 -i data/ground_truth.csv
```

Copy the output (it's one long string).

**In GitHub:**
1. Go to your repo → **Settings** → **Secrets and variables** → **Actions**
2. Click **New repository secret**
3. Name: `GROUND_TRUTH_B64`
4. Value: paste the base64 string
5. Click **Add secret**

---

## Step 4 — Test the Workflow

1. Go to your repo → **Actions** tab
2. Click **Auto-Score Submissions & Update Leaderboard**
3. Click **Run workflow** → **Run workflow**

It should:
- ✅ Restore ground truth
- ✅ Score 0 submissions (none yet)
- ✅ Update README with empty leaderboard
- ✅ Commit back to repo

---

## Step 5 — Enable Pull Request submissions (optional but recommended)

To let participants submit via Pull Requests:

1. Go to **Settings** → **Branches**
2. Add a branch protection rule for `main`
3. Require **pull request reviews before merging** (set to 0 required reviews if you want auto-merge)

OR simply let people submit PRs and you manually merge them — the CI fires automatically on every merge.

---

## Step 6 — Share the repo!

Tell participants to:
1. Fork the repo
2. Download `data/train.csv` and `data/test.csv`
3. Build a model
4. Save predictions as `submissions/their_github_username.csv`
5. Open a PR

The leaderboard will update automatically when you merge their PR. 🎉

---

## How the Automation Works

```
PR merged → GitHub Actions triggers → evaluate.py runs →
scores all submissions → updates leaderboard/scores.json →
update_leaderboard.py rewrites README table → commits back
```

Every time a new submission is merged, the leaderboard in the README updates within ~1 minute.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Workflow fails with "Ground truth not found" | Check that `GROUND_TRUTH_B64` secret is set correctly |
| Workflow has no write permission | Ensure `permissions: contents: write` is in the YAML (already set) |
| Leaderboard not updating in README | Check that the README section markers haven't been modified |
| Submission rejected | Check that filename = `username.csv` and has exactly 200 rows with PassengerId 801–1000 |
