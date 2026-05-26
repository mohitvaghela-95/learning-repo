# Git Cheat Sheet

A short, practical Git reference for everyday development and pull request workflows.

---

## Mental Model

| Git concept | Change delivery equivalent |
|---|---|
| Repository | Controlled project/application codebase |
| Branch | Isolated change workstream |
| Commit | Versioned implementation checkpoint |
| Pull request | Review and approval workflow |
| Merge | Promotion into the controlled baseline |
| Tag/release | Versioned release package |

---

## Installation and Setup

### Check if Git is installed

```bash
git --version
```

If Git is installed, this returns the installed version.

### Install Git

#### macOS

Using Homebrew:

```bash
brew install git
```

Or install Xcode Command Line Tools:

```bash
xcode-select --install
```

#### Windows

Install Git for Windows, then use **Git Bash** or your terminal.

After installation, check:

```bash
git --version
```

#### Linux / Ubuntu

```bash
sudo apt update
sudo apt install git
```

### Set your Git identity

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

This identity is attached to your commits.

### Check your Git configuration

```bash
git config --list
```

### Set default branch name to main

```bash
git config --global init.defaultBranch main
```

### Clone an existing GitHub repository

Using HTTPS:

```bash
git clone https://github.com/org/repo.git
```

Using SSH:

```bash
git clone git@github.com:org/repo.git
```

### Initialise Git in an existing folder

```bash
git init
```

### Add a remote repository

```bash
git remote add origin https://github.com/org/repo.git
```

Check remotes:

```bash
git remote -v
```

### Optional: Generate an SSH key

```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```

Start the SSH agent:

```bash
eval "$(ssh-agent -s)"
```

Add your key:

```bash
ssh-add ~/.ssh/id_ed25519
```

Show your public key so you can add it to GitHub:

```bash
cat ~/.ssh/id_ed25519.pub
```

Test SSH connection:

```bash
ssh -T git@github.com
```

---

## Most Common Workflow

```bash
# 1. Start from the latest stable branch
git switch main
git pull

# 2. Create a branch for your change
git switch -c feature/my-change

# 3. Make changes, then review them
git status
git diff

# 4. Stage and commit
git add .
git commit -m "Describe the change"

# 5. Push branch to GitHub
git push -u origin feature/my-change
```

Then open a **pull request** in GitHub.

---

## Essential Commands

| Task | Command |
|---|---|
| Check current state | `git status` |
| See unstaged changes | `git diff` |
| See commit history | `git log --oneline` |
| Get latest changes | `git pull` |
| Create and switch branch | `git switch -c <branch-name>` |
| Switch branch | `git switch <branch-name>` |
| Stage all changes | `git add .` |
| Commit changes | `git commit -m "Message"` |
| Push new branch | `git push -u origin <branch-name>` |
| Push existing branch | `git push` |
| Fetch remote updates | `git fetch` |

---

## Branches

```bash
# List branches
git branch

# Create and switch to a new branch
git switch -c feature/CHG12345-customer-revenue-fix

# Switch to an existing branch
git switch main

# Delete a merged local branch
git branch -d feature/my-change
```

Recommended naming:

```text
feature/short-description
bugfix/short-description
hotfix/short-description
docs/short-description
chore/short-description
```

With enterprise references:

```text
feature/CHG12345-customer-revenue-fix
bugfix/JIRA-456-late-arriving-facts
hotfix/INC789-failed-daily-load
```

---

## Commits

A commit should be a small, logical checkpoint.

```bash
git add .
git commit -m "Fix revenue aggregation for late-arriving facts"
```

Good commit messages:

```text
Add validation for late-arriving transactions
Fix null handling in revenue model
Update Airflow retry policy for daily ingestion
```

Avoid:

```text
changes
fix stuff
updates
```

---

## Pull Requests

Typical PR flow:

```bash
git switch main
git pull
git switch -c feature/my-change

# make changes

git add .
git commit -m "Implement my change"
git push -u origin feature/my-change
```

A good PR should explain:

- What changed
- Why it changed
- How it was tested
- Any deployment, backfill, or rollback notes
- Related ticket/change reference

---

## Keeping Your Branch Updated

Merge latest `main` into your branch:

```bash
git switch main
git pull
git switch <your-branch>
git merge main
```

Alternative using rebase:

```bash
git switch <your-branch>
git fetch
git rebase origin/main
```

Use `merge` if unsure. Use `rebase` only if your team prefers linear history.

---

## Merge Conflicts

When Git cannot combine changes automatically:

```bash
git status
```

Open the conflicted files and look for:

```text
<<<<<<< HEAD
Your version
=======
Incoming version
>>>>>>> branch-name
```

Edit the file so it contains the correct final version, then:

```bash
git add <file-name>
git commit
```

If rebasing:

```bash
git add <file-name>
git rebase --continue
```

Abort if needed:

```bash
git merge --abort
git rebase --abort
```

---

## Undo and Fix Mistakes

| Situation | Command |
|---|---|
| Unstage a file | `git restore --staged <file>` |
| Discard local changes to a file | `git restore <file>` |
| Fix last commit | `git commit --amend` |
| Safely undo a public commit | `git revert <commit-hash>` |
| Temporarily park work | `git stash` |
| Bring stashed work back | `git stash pop` |

Use carefully:

```bash
git reset --hard <commit-hash>
git clean -fd
git push --force
```

Safer force push:

```bash
git push --force-with-lease
```

---

## Stash

Use stash when you need to temporarily move unfinished work aside.

```bash
# Save current work
git stash push -m "WIP customer revenue changes"

# List stashes
git stash list

# Restore latest stash and remove it from stash list
git stash pop
```

---

## Tags and Releases

Tags are commonly used to mark release versions.

```bash
# Create tag
git tag v1.0.0

# Push tag
git push origin v1.0.0

# List tags
git tag
```

---

## .gitignore Essentials

Use `.gitignore` to prevent Git from tracking files that should stay local.

Common data engineering examples:

```gitignore
# Secrets
.env
*.key
*.pem

# Python
__pycache__/
.venv/
venv/

# Logs
*.log

# Data extracts
*.csv
*.json
*.parquet
*.avro

# dbt
target/
dbt_packages/
logs/

# Notebooks
.ipynb_checkpoints/
```

---

## Data Engineering Example

```bash
git switch main
git pull

git switch -c feature/CHG12345-fix-customer-revenue

# update dbt model / Spark job / Airflow DAG

git status
git diff
git add .
git commit -m "Fix customer revenue aggregation logic"
git push -u origin feature/CHG12345-fix-customer-revenue
```

Then open a pull request for review.

---

## Enterprise Change Mapping

| Enterprise activity | Git/GitHub action |
|---|---|
| Create change ticket | Create branch and link ticket in PR |
| Implement change | Commit work on feature branch |
| Peer review | Open pull request |
| Technical approval | PR approval |
| Automated validation | CI checks |
| Promote to baseline | Merge PR into `main` |
| Release package | Tag or GitHub release |
| Rollback | Revert commit or redeploy previous tag |

---

## Golden Rules

1. Check `git status` often.
2. Pull latest `main` before starting work.
3. Work on a branch, not directly on `main`.
4. Keep commits small and meaningful.
5. Do not commit secrets or large data files.
6. Use pull requests for review and traceability.
7. Prefer `git revert` for shared/public changes.
8. Be careful with `reset --hard`, `clean`, and force pushes.
