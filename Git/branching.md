# Git Branching

## Purpose

This document records my practical understanding of Git branching workflows as part of my DevOps learning portfolio.

The purpose of this section is to demonstrate:
- understanding of Git branches
- isolated development workflows
- safe feature development practices
- branch management operations
- merge workflows used in professional engineering environments

---

# What a Git Branch Is

A Git branch is an independent line of development inside a repository.

Branches allow engineers to work on changes safely without affecting the main project history.

Instead of modifying production-ready code directly, developers create separate branches to:
- develop features
- test ideas
- fix bugs
- experiment safely
- collaborate independently

---

# Why Branches Are Important

Branches are critical because they protect the stability of the main codebase.

Without branches:
- all developers would work directly on the main branch
- unfinished work could break production code
- collaboration would become risky

Branches allow:
- isolated development
- safer testing
- parallel workflows
- cleaner collaboration
- controlled merging

---

# The Main Branch

Most repositories contain a primary branch called:

```text
main
```

The `main` branch usually represents:
- stable code
- production-ready work
- approved project history

Professional teams typically avoid making experimental changes directly on `main`.

---

# Creating Branches

Branches can be created using:

```bash
git branch feature-login
```

This creates a new branch but does not switch into it.

To verify existing branches:

```bash
git branch
```

Example output:

```text
* main
  feature-login
```

The `*` symbol shows the currently active branch.

---

# Switching Branches

Switch to another branch using:

```bash
git switch feature-login
```

Older Git workflows commonly used:

```bash
git checkout feature-login
```

Modern Git versions prefer `git switch` because it is clearer and more focused.

---

# Creating and Switching in One Command

A branch can be created and switched into immediately using:

```bash
git switch -c feature-login
```

Older equivalent workflow:

```bash
git checkout -b feature-login
```

Both commands:
- create the branch
- immediately switch into it

---

# Branch Isolation

One important Git concept is branch isolation.

Changes made on one branch do not automatically appear on another branch until they are merged.

Example workflow:

```text
main branch
     ↓
create feature branch
     ↓
make isolated changes
     ↓
test safely
     ↓
merge back into main
```

This protects the stability of the main project.

---

# Viewing Branch History

Git can display branch history visually using:

```bash
git log --oneline --graph --all
```

This command helps visualize:
- commit relationships
- merge history
- branch structure
- repository evolution

Example simplified output:

```text
* commit-feature
|\
| * feature branch work
|/
* main branch commit
```

---

# Merging Branches

Branches are combined using:

```bash
git merge feature-login
```

This merges the selected branch into the currently active branch.

Typical workflow:

```bash
git switch main
git merge feature-login
```

This means:
1. switch to `main`
2. merge feature branch into `main`

---

# Fast-Forward Merges

A fast-forward merge happens when the target branch has not changed since the feature branch was created.

Example:

```text
main
  ↓
feature branch moves ahead
  ↓
main simply moves forward
```

No merge commit is required.

Fast-forward merges create a clean linear history.

---

# Merge Commits

If both branches contain different commits, Git may create a merge commit.

Example:

```text
main changed
feature branch changed
        ↓
Git combines histories
        ↓
merge commit created
```

Merge commits preserve branch history and show that independent development paths existed.

---

# Deleting Branches

After successful merging, old branches can be deleted.

Delete merged branch:

```bash
git branch -d feature-login
```

Force delete unmerged branch:

```bash
git branch -D feature-login
```

The `-D` option should be used carefully because it can permanently remove unmerged work.

---

# Real-World Feature Branch Workflow

A common professional workflow:

```text
main branch stays stable
        ↓
create feature branch
        ↓
develop feature
        ↓
commit changes
        ↓
test feature
        ↓
merge into main
        ↓
delete old feature branch
```

This workflow is heavily used in:
- DevOps
- software engineering
- CI/CD pipelines
- team collaboration
- pull request workflows

---

# Branch Naming Conventions

Professional repositories often use structured branch names.

Examples:

```text
feature/login-page
bugfix/navbar-error
hotfix/security-patch
docs/readme-update
```

Structured naming improves:
- readability
- organization
- collaboration
- workflow tracking

---

# Understanding HEAD

Git uses a special pointer called `HEAD`.

`HEAD` points to:
- the currently active branch
- or the currently checked-out commit

Example:

```text
HEAD → main
```

After switching branches:

```text
HEAD → feature-login
```

Understanding `HEAD` is important because Git operations act relative to the current checked-out branch.

---

# Practical Skills Demonstrated

Practical Git branching activities completed include:

- creating branches
- switching branches
- viewing branch history
- creating isolated feature workflows
- merging feature branches
- understanding fast-forward merges
- understanding merge commits
- deleting branches safely
- visualizing branch structure
- maintaining clean repository workflows

---

# Real-World Engineering Relevance

Branching is one of the most important Git workflows in professional engineering environments.

Branches allow teams to:
- work safely in parallel
- isolate unfinished work
- review code before merging
- test features independently
- reduce deployment risk

Branch-based workflows are heavily used in:
- GitHub collaboration
- pull request systems
- CI/CD pipelines
- Infrastructure as Code workflows
- DevOps automation projects

---

# Key Learning Outcome

I understand how Git branches allow isolated and safe development workflows.

I understand how to:
- create branches
- switch branches
- merge branches
- inspect branch history
- maintain stable main branch workflows

I also understand that Git branching is a critical collaboration and deployment safety mechanism used throughout modern software engineering and DevOps environments.
