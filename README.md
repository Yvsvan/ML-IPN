# ML-IPN — Kaggle Competition Workspace

Collaborative repository for IPN Kaggle competitions. Each competition lives in its own folder under `competitions/`.

---

## Repo Structure

```
ML-IPN/
├── competitions/        # One subfolder per Kaggle competition
│   └── <comp-name>/
│       ├── data/        # Raw data (gitignored — download via Kaggle API)
│       ├── notebooks/   # Exploration and experiments
│       ├── src/         # Reusable scripts and pipelines
│       └── README.md    # Competition-specific notes
├── shared/              # Utilities shared across competitions
└── README.md
```

---

## Setup

### 1. Clone the repo

```bash
git clone <repo-url>
cd ML-IPN
```

### 2. Install dependencies

Each competition folder may have its own `requirements.txt`. Install with:

```bash
pip install -r competitions/<comp-name>/requirements.txt
```

### 3. Download competition data

Use the [Kaggle API](https://github.com/Kaggle/kaggle-api):

```bash
kaggle competitions download -c <comp-name> -p competitions/<comp-name>/data/
```

---

## Git Workflow

### Pull latest changes before starting work

Always sync before you begin to avoid conflicts:

```bash
git checkout main
git pull origin main
```

### Create a branch for your work

Never commit directly to `main`. Create a feature branch:

```bash
git checkout -b <your-name>/<short-description>
# e.g. git checkout -b ivan/lgbm-baseline
```

### Stage and commit your changes

Check what you changed, then commit with a clear message:

```bash
git status                        # see changed files
git diff                          # review changes
git add <file1> <file2>           # stage specific files
# or: git add .                   # stage everything (use carefully)

git commit -m "short description of what and why"
```

**Good commit messages:**
- `add LightGBM baseline for tabular comp`
- `fix feature encoding bug in preprocessing pipeline`
- `tune XGBoost hyperparameters — CV improves from 0.82 to 0.85`

### Push your branch

```bash
git push origin <your-branch-name>
# e.g. git push origin ivan/lgbm-baseline
```

Then open a Pull Request on GitHub for review before merging to `main`.

### Merge and clean up

After the PR is merged:

```bash
git checkout main
git pull origin main
git branch -d <your-branch-name>   # delete local branch
```

---

## Conventions

- **Don't commit data files.** The `data/` folders are gitignored. Share data via the Kaggle API or a shared drive.
- **Don't commit notebooks with large outputs.** Clear cell outputs before committing: `Kernel → Restart & Clear Output`.
- **One competition, one folder.** Keep experiments isolated.
- **Document your experiments.** Note CV scores, key decisions, and ideas in the competition `README.md`.

---

## Quick Reference

| Task | Command |
|---|---|
| Sync with remote | `git pull origin main` |
| New branch | `git checkout -b name/description` |
| Stage all changes | `git add .` |
| Commit | `git commit -m "message"` |
| Push branch | `git push origin <branch>` |
| See log | `git log --oneline` |
| Discard local changes | `git checkout -- <file>` |
