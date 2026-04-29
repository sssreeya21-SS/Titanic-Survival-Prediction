# 📤 How to Submit

## TL;DR
1. Build a model using `data/train.csv`
2. Predict survival for all 200 passengers in `data/test.csv`
3. Save as `submissions/your_github_username.csv`
4. Open a Pull Request

---

## Detailed Steps

### 1. Fork this repository
Click **Fork** at the top-right of this page.

### 2. Clone your fork
```bash
git clone https://github.com/YOUR_USERNAME/titanic-survival-competition.git
cd titanic-survival-competition
```

### 3. Build your model
See `notebooks/starter_notebook.ipynb` for a quick start.

### 4. Generate predictions
Your CSV must look exactly like this:
```csv
PassengerId,Survived
801,0
802,1
803,0
...
1000,1
```
Requirements:
- ✅ File name: `your_github_username.csv` (e.g., `johndoe.csv`)
- ✅ Exactly 200 rows (PassengerId 801 to 1000)
- ✅ `Survived` column: only `0` or `1`

### 5. Commit and push
```bash
cp your_submission.csv submissions/your_github_username.csv
git add submissions/your_github_username.csv
git commit -m "Add submission for your_github_username"
git push origin main
```

### 6. Open a Pull Request
- Go to your fork on GitHub
- Click **Compare & pull request**
- Title: `Submission: your_github_username`
- Click **Create pull request**

Once the PR is merged, the leaderboard updates automatically within ~1 minute! 🚀
