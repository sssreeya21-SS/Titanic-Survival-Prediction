# 🚢 Titanic Survival Prediction Competition

> **Predict who survived the Titanic disaster using passenger data.**  
> Automated leaderboard updates on every submission via GitHub Actions.

---

## 🏆 Live Leaderboard

| Rank | Participant | Accuracy | Submitted At |
|------|-------------|----------|--------------|

> ⚡ The leaderboard above auto-updates within minutes of a valid pull request being merged.

---

## 📖 Problem Statement

The RMS Titanic sank on April 15, 1912. Of the 2,224 passengers and crew aboard, only 710 survived. Using passenger data (age, sex, class, fare, etc.), your task is to **build a model that predicts which passengers survived**.

This is a **binary classification** problem:
- `0` → Did not survive
- `1` → Survived

**Metric:** Accuracy (% of correct predictions)

---

## 📁 Repository Structure

```
titanic-competition/
├── data/
│   ├── train.csv              # Training data with labels
│   ├── test.csv               # Test data (no labels — submit predictions for this)
│   └── sample_submission.csv  # Submission format example
├── submissions/               # 📤 Drop your CSV here to participate
│   └── example_random.csv     # Example submission
├── notebooks/
│   └── starter_notebook.ipynb # Starter code to get you going
├── scripts/
│   ├── evaluate.py            # Scoring script (runs automatically)
│   └── update_leaderboard.py  # Leaderboard updater (runs automatically)
├── leaderboard/
│   └── scores.json            # Raw scores (auto-updated)
└── .github/
    └── workflows/
        └── evaluate.yml       # GitHub Actions workflow
```

---

## 🚀 How to Participate

### Step 1 — Fork this repository
Click **Fork** (top right) to create your own copy.

### Step 2 — Download the data
```
data/train.csv    ← Use this to train your model
data/test.csv     ← Generate predictions for these 200 passengers
```

### Step 3 — Build your model
Use any language/library you want. Check `notebooks/starter_notebook.ipynb` for a Python baseline.

### Step 4 — Create your submission file
Your submission must be a CSV with **exactly 2 columns**:
```csv
PassengerId,Survived
801,0
802,1
803,1
...
```
- Must contain **all 200 test passengers** (PassengerId 801–1000)
- `Survived` must be `0` or `1` only

### Step 5 — Submit via Pull Request
1. Name your file: `submissions/your_github_username.csv`
2. Open a Pull Request to this repo
3. Once merged, GitHub Actions will **auto-score your submission and update the leaderboard** ✅

---

## 📊 Data Description

### `train.csv` (800 rows)
| Column | Description |
|--------|-------------|
| PassengerId | Unique ID |
| Survived | **Target** — 0 = No, 1 = Yes |
| Pclass | Ticket class (1 = 1st, 2 = 2nd, 3 = 3rd) |
| Name | Passenger name |
| Sex | male / female |
| Age | Age in years |
| SibSp | # siblings/spouses aboard |
| Parch | # parents/children aboard |
| Ticket | Ticket number |
| Fare | Passenger fare |
| Cabin | Cabin number |
| Embarked | Port of embarkation (C = Cherbourg, Q = Queenstown, S = Southampton) |

### `test.csv` (200 rows)
Same columns as `train.csv` but **without `Survived`** — that's what you predict!

---

## 🧠 Tips & Hints

- **Sex** and **Pclass** are among the strongest predictors ("women and children first")
- Handle **missing Age** values (about 20% are null) — try median imputation
- **Fare** correlates with survival chance
- Try: Logistic Regression → Random Forest → XGBoost (increasing complexity)
- Feature engineering: extract title from Name, family size = SibSp + Parch + 1

---

## 📦 Quickstart (Python)

```bash
git clone https://github.com/YOUR_USERNAME/titanic-competition.git
cd titanic-competition
pip install pandas scikit-learn numpy
jupyter notebook notebooks/starter_notebook.ipynb
```

---

## 🛠 Rules

1. One submission CSV per GitHub username
2. Must predict all 200 test passengers
3. No peeking at `data/ground_truth.csv` (it's gitignored — only the CI runner sees it)
4. Have fun 🎉

---

## 📬 Questions?

Open an [Issue](../../issues) in this repository.
