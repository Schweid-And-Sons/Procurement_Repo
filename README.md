# How to Push Code to GitHub Using a Branch

This guide explains, step by step, how to make changes in a separate branch and push them to GitHub safely.

---

## Prerequisites

Before you begin, make sure you have:

- A GitHub account
- Git installed on your machine
- Access to the repository
- A terminal (Command Prompt, PowerShell, iTerm, etc.)

Check Git is installed:

```bash
git --version
```

---

## 1) Create and activate a virtual environment

Before starting anything, create and activate a virtual environment.

### macOS/Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows (PowerShell)

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### Windows (Command Prompt)

```bat
python -m venv .venv
.venv\Scripts\activate.bat
```

When the environment is active, your terminal usually shows `(.venv)` at the start.

---

## 2) Clone the repository (first time only)

If you do not already have the repo locally, clone it:

```bash
git clone https://github.com/Schweid-And-Sons/Procurement_Repo.git
cd Procurement_Repo
```

---

## 3) Make sure you are on the default branch

Usually this is `main` (sometimes `master`):

```bash
git checkout main
git pull origin main
```

> If your default branch is `master`, replace `main` with `master` in all commands.

---

## 4) Create a new branch for your work

Use a clear branch name related to your change:

```bash
git checkout -b feature/add-readme-guide
```

This creates the branch and switches you to it.

---

## 5) Make your code changes

Edit files as needed in your project.

Check what changed:

```bash
git status
```

---

## 6) Stage your changes

Add specific files:

```bash
git add README.md
```

Or stage everything changed:

```bash
git add .
```

---

## 7) Commit your changes

Write a clear commit message:

```bash
git commit -m "Add step-by-step guide for pushing code with branches"
```

---

## 8) Push the branch to GitHub

Push your new branch to remote:

```bash
git push -u origin feature/add-readme-guide
```

The `-u` sets the upstream so future pushes can be done with just:

```bash
git push
```

---

## 9) Open a Pull Request (PR)

1. Go to the repository on GitHub:
   `https://github.com/Schweid-And-Sons/Procurement_Repo`
2. GitHub will usually show a **Compare & pull request** button for your branch.
3. Click it, add a title/description, and create the PR.
4. Request reviewers if needed.

---

## 10) Keep your branch updated (optional but recommended)

If `main` has moved forward while you are working:

```bash
git checkout main
git pull origin main
git checkout feature/add-readme-guide
git merge main
```

Then push again:

```bash
git push
```

---

## 11) After merge: clean up branch

After PR is merged:

Delete local branch:

```bash
git branch -d feature/add-readme-guide
```

Delete remote branch:

```bash
git push origin --delete feature/add-readme-guide
```

---

## Quick Command Summary

```bash
python3 -m venv .venv
source .venv/bin/activate
git clone https://github.com/Schweid-And-Sons/Procurement_Repo.git
cd Procurement_Repo
git checkout main
git pull origin main
git checkout -b feature/add-readme-guide
# make changes
git add .
git commit -m "Describe your change"
git push -u origin feature/add-readme-guide
```

---

## Common Issues

### Permission denied (publickey)
Your SSH key may not be configured. Use HTTPS remote URL or set up SSH keys in GitHub settings.

### Rejected push (non-fast-forward)
Your branch is behind remote. Pull and merge/rebase, then push again.

### Wrong branch
Check current branch:

```bash
git branch
```

Switch to correct branch:

```bash
git checkout <branch-name>
```

---

## Best Practices

- Never commit directly to `main` for feature work.
- Use meaningful branch names (`feature/...`, `fix/...`, `chore/...`).
- Keep commits small and descriptive.
- Open PRs early for visibility.
