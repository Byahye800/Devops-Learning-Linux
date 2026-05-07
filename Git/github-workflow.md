# GitHub Workflow and Collaboration

## Module Objective

This module documents how Git and GitHub are used together in collaborative software engineering and DevOps workflows.

The goal is to understand how professional teams:

- collaborate safely
- manage feature development
- review code changes
- maintain repository quality
- synchronize local and remote repositories
- work using structured branch workflows

This module covers:

- GitHub workflow fundamentals
- cloning repositories
- pushing and pulling changes
- feature branch workflows
- pull requests
- upstream tracking
- merge strategies
- branch protection
- collaboration workflows
- professional engineering practices

---

# Understanding Git vs GitHub

## Git

Git is a distributed version control system.

Git tracks:

- file changes
- commit history
- branches
- merges
- repository history

Git operates locally on a developer machine.

---

## GitHub

GitHub is a cloud-based hosting platform built around Git repositories.

GitHub provides:

- remote repository hosting
- collaboration tools
- pull requests
- issue tracking
- CI/CD integrations
- access management
- branch protection
- code reviews

---

# Local Repository vs Remote Repository

| Repository Type | Purpose |
|---|---|
| Local Repository | Developer’s machine |
| Remote Repository | Shared GitHub repository |

---

# Basic GitHub Workflow

```text
Create Repository
        ↓
Clone Repository
        ↓
Create Feature Branch
        ↓
Make Changes
        ↓
Commit Changes
        ↓
Push Branch
        ↓
Open Pull Request
        ↓
Review and Merge
```

---

# Cloning a Repository

## Purpose

Copies a remote GitHub repository onto a local machine.

---

## Command

```bash
git clone repository-url
```

Example:

```bash
git clone git@github.com:user/project.git
```

---

# Why Cloning Matters

Cloning provides:

- full repository history
- branches
- commit logs
- remote connections

This creates the local working environment for development.

---

# Understanding Remote Repositories

A remote repository is a shared repository hosted externally.

Common remote names:

| Remote Name | Purpose |
|---|---|
| `origin` | Main remote repository |
| `upstream` | Original source repository |

---

# Viewing Remote Repositories

## Command

```bash
git remote -v
```

Example output:

```bash
origin  git@github.com:user/project.git (fetch)
origin  git@github.com:user/project.git (push)
```

---

# Understanding Upstream Tracking

An upstream branch links a local branch to a remote branch.

This allows simplified commands such as:

```bash
git push
git pull
```

without manually specifying remote names each time.

---

# Feature Branch Workflow

Professional teams rarely work directly on the `main` branch.

Instead, developers create feature branches.

---

# Why Feature Branches Matter

Feature branches help:

- isolate work
- reduce conflicts
- improve review workflows
- protect stable branches
- organize development

---

# Creating a Feature Branch

## Command

```bash
git checkout -b feature/new-feature
```

Example:

```bash
git checkout -b feature/login-page
```

---

# Workflow Example

```text
main
 ├── feature/login-page
 ├── feature/payment-system
 └── feature/api-refactor
```

Each branch contains isolated development work.

---

# Making Changes and Committing

After editing files:

## Check Status

```bash
git status -sb
```

---

## Stage Files

```bash
git add .
```

---

## Commit Changes

```bash
git commit -m "Add login page"
```

---

# Pushing Changes to GitHub

## Command

```bash
git push
```

Or during first push:

```bash
git push -u origin feature/login-page
```

---

# What `-u` Does

The `-u` flag creates upstream tracking between:

- local branch
- remote branch

This simplifies future pushes and pulls.

---

# Pull Requests (PRs)

A pull request is a formal request to merge changes into another branch.

Usually:

```text
feature branch → main branch
```

---

# Why Pull Requests Matter

Pull requests allow:

- code reviews
- discussion
- automated testing
- quality control
- approval workflows

They are a core part of professional engineering collaboration.

---

# Typical Pull Request Workflow

```text
Create Feature Branch
        ↓
Push Branch
        ↓
Open Pull Request
        ↓
Review Changes
        ↓
Approve or Request Changes
        ↓
Merge Into Main
```

---

# Code Reviews

Code reviews are used to:

- identify bugs
- improve code quality
- share engineering knowledge
- enforce standards
- reduce security risks

Professional teams rely heavily on peer review workflows.

---

# Merge Strategies

GitHub supports multiple merge strategies.

---

## Standard Merge Commit

Preserves full branch history.

Example:

```text
feature branch commit history retained
```

---

## Squash Merge

Combines all feature branch commits into one commit.

Benefits:

- cleaner history
- easier readability
- simplified logs

---

## Rebase and Merge

Replays commits onto the target branch without creating merge commits.

Benefits:

- linear history
- cleaner commit timeline

Risks:

- history rewriting complexity

---

# Merge Conflicts

Conflicts occur when multiple changes affect the same section of a file.

Git cannot automatically determine which version should be kept.

---

# Conflict Workflow

```text
Pull Changes
        ↓
Conflict Detected
        ↓
Edit Conflict Markers
        ↓
Stage Resolved Files
        ↓
Commit Resolution
```

---

# Branch Protection

Professional repositories often protect important branches such as:

```text
main
production
release
```

---

# Why Branch Protection Matters

Branch protection helps prevent:

- accidental force pushes
- direct commits to production branches
- unreviewed code merges
- unstable deployments

---

# Common Branch Protection Rules

Examples include:

- require pull requests
- require approvals
- require status checks
- block force pushes
- require signed commits

---

# Pulling Changes from GitHub

## Command

```bash
git pull
```

---

# What Git Pull Does

`git pull` performs:

```text
git fetch
        +
git merge
```

This synchronizes the local repository with remote changes.

---

# Fetch vs Pull

| Command | Purpose |
|---|---|
| `git fetch` | Download remote changes only |
| `git pull` | Download and merge changes |

---

# Forking Repositories

Forking creates a personal copy of another repository.

Used commonly in:

- open-source contributions
- external collaboration
- experimentation

---

# Fork Workflow

```text
Fork Repository
        ↓
Clone Fork
        ↓
Create Branch
        ↓
Push Changes
        ↓
Open Pull Request to Original Repository
```

---

# GitHub Issues

GitHub Issues are used for:

- bug tracking
- feature requests
- task management
- engineering discussions

---

# Labels and Milestones

Professional teams organize work using:

| Tool | Purpose |
|---|---|
| Labels | Categorize issues |
| Milestones | Group work into targets |
| Projects | Track workflow progress |

---

# Relationship Between GitHub and CI/CD

GitHub commonly integrates with CI/CD systems.

Examples:

- GitHub Actions
- Jenkins
- GitLab CI
- CircleCI

---

# Why CI/CD Integration Matters

Automated pipelines can:

- run tests
- validate code
- scan for vulnerabilities
- deploy applications
- enforce quality gates

---

# DevOps Perspective

GitHub workflows are a critical part of DevOps engineering.

Modern teams rely on:

- collaboration automation
- pull request workflows
- branch protection
- CI/CD integration
- repository governance

---

# Commands Practiced

```bash
git clone repository-url
git remote -v
git checkout -b feature/branch-name
git status -sb
git add .
git commit -m "message"
git push
git push -u origin branch-name
git pull
git fetch
```

---

# Evidence to Capture

Recommended screenshots or terminal evidence:

- cloning a repository
- creating feature branches
- pushing to GitHub
- pull request examples
- merge conflict resolution
- branch protection settings
- GitHub repository structure
- clean Git status verification

---

# Final Verification

```bash
git status -sb
```

Expected clean output:

```bash
## main...origin/main
```

---

# Module Summary

This module demonstrates professional GitHub collaboration and workflow management practices.

Key concepts covered:

- Git vs GitHub
- cloning repositories
- feature branch workflows
- pull requests
- upstream tracking
- merge strategies
- conflict handling
- branch protection
- GitHub collaboration workflows
- CI/CD integration

Modern engineering teams rely heavily on structured GitHub workflows to maintain scalable, collaborative, and reliable software development environments.
