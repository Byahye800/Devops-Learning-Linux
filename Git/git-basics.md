# Git Basics

## Purpose

This document records my practical understanding of Git fundamentals as part of my DevOps learning portfolio.

The purpose of this section is to demonstrate:
- understanding of core Git concepts
- practical Git workflow usage
- repository management skills
- change tracking principles
- professional version control practices used in real engineering environments

---

# What Git Is

Git is a distributed version control system used to track changes in files over time.

It allows engineers to:
- record project history
- collaborate safely
- restore previous versions
- inspect changes
- work on isolated branches
- manage code and infrastructure reliably

Git is heavily used in:
- DevOps
- Cloud Engineering
- Software Engineering
- CI/CD pipelines
- Infrastructure as Code (IaC)
- automation workflows

---

# Core Concept: Git Tracks Snapshots

Git does not simply save individual file differences.

Git records snapshots of a project at specific points in time.

Each commit represents a saved state of the repository.

Simple workflow concept:

```text
Files change
     ↓
Changes are staged
     ↓
A commit is created
     ↓
Git records a repository snapshot
```

Each commit has its own unique identifier called a SHA-1 hash.

---

# Git Internal Structure

Git stores repository data inside the `.git` directory.

This hidden directory contains:
- commit history
- branches
- repository configuration
- object database
- references
- staging information

Important internal Git components:

| Component | Purpose |
|---|---|
| `objects/` | Stores Git objects and history |
| `refs/` | Stores branch and tag references |
| `HEAD` | Points to current branch/commit |
| `index` | Represents the staging area |
| `config` | Repository configuration settings |

---

# The Three Main Areas of Git

Git works with three primary areas:

```text
Working Directory → Staging Area → Repository
```

| Area | Meaning |
|---|---|
| Working Directory | The files currently being edited |
| Staging Area | Selected changes prepared for commit |
| Repository | Saved Git history after committing |

---

# Basic Git Workflow

The standard Git workflow is:

```bash
git status
git add <file>
git commit -m "message"
```

## Workflow Explanation

### `git status`

Displays:
- modified files
- staged changes
- untracked files
- branch information

### `git add`

Moves selected changes into the staging area.

Examples:

```bash
git add file.txt
git add .
```

### `git commit`

Creates a permanent snapshot of staged changes.

Example:

```bash
git commit -m "Add Git basics documentation"
```

---

# Repository Initialization

A new Git repository is created using:

```bash
git init
```

This command creates the hidden `.git` directory and initializes version control tracking.

---

# Essential Git Commands Practised

| Command | Purpose |
|---|---|
| `git init` | Create a new Git repository |
| `git status` | Check repository state |
| `git add <file>` | Stage a file |
| `git add .` | Stage all current changes |
| `git commit -m "message"` | Save staged changes |
| `git log` | View commit history |
| `git log --oneline` | Compact history view |
| `git log --oneline --graph --all` | Visual branch history |
| `git show <commit>` | Inspect a specific commit |
| `git diff` | View unstaged changes |
| `git diff --staged` | View staged changes |
| `git restore <file>` | Undo unstaged file changes |
| `git restore --staged <file>` | Unstage a file |
| `git mv old new` | Rename or move tracked files |
| `git rm <file>` | Remove tracked files |
| `git blame <file>` | Show who modified lines in a file |

---

# Git Configuration

Git requires user identity configuration so commits can record the correct author.

Example configuration:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

To verify configuration:

```bash
git config --list
```

This is important because professional commit history should accurately identify contributors.

---

# SSH Authentication Setup

SSH authentication allows secure communication with remote Git repositories such as GitHub.

Generate SSH key:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

Test SSH authentication:

```bash
ssh -T git@github.com
```

SSH authentication is commonly used because it is more secure and efficient than repeatedly entering passwords.

---

# Remote Repository Operations

Git repositories can connect to remote repositories such as GitHub.

Example remote setup:

```bash
git remote add origin <repository-url>
```

Push commits to GitHub:

```bash
git push -u origin main
```

Retrieve remote changes:

```bash
git pull
```

---

# File Operations

Git tracks:
- file creation
- modifications
- renames
- deletions

Examples:

```bash
git mv old-file.md new-file.md
git rm unwanted-file.md
git restore changed-file.md
```

Using Git-aware file operations preserves clean repository history and improves change tracking.

---

# Viewing Repository History

Useful history inspection commands:

```bash
git log
git log --oneline
git log --oneline --graph --all
git show <commit>
```

These commands help engineers:
- inspect repository evolution
- debug issues
- review commits
- understand project changes over time

---

# Viewing Differences

Git can compare changes before and after staging.

View unstaged changes:

```bash
git diff
```

View staged changes:

```bash
git diff --staged
```

Reviewing differences before committing is an important professional workflow habit.

---

# Understanding Git Status Indicators

Common Git status categories:

| Status | Meaning |
|---|---|
| Untracked | File exists but Git is not tracking it |
| Modified | Tracked file has changed |
| Staged | Changes prepared for commit |
| Committed | Changes saved into repository history |

---

# Practical Skills Demonstrated

Practical Git activities completed include:

- initializing repositories
- configuring Git identity
- staging changes
- creating commits
- viewing repository history
- inspecting staged and unstaged differences
- safely renaming README files
- working with GitHub remotes
- verifying branch synchronization
- using SSH authentication
- configuring pre-commit automation
- maintaining clean commit history

---

# Real-World Engineering Relevance

Git is a critical engineering tool because it provides:
- version control
- collaboration safety
- rollback capability
- audit history
- controlled deployment workflows

In DevOps environments, Git commonly manages:
- infrastructure code
- CI/CD pipelines
- automation scripts
- Kubernetes manifests
- Terraform configurations
- deployment workflows
- documentation

---

# Key Learning Outcome

I understand the professional Git workflow:

```text
edit files → inspect changes → stage changes → review changes → commit → push
```

I also understand that Git is not simply a backup tool, but a professional change management system used to protect project history, engineering collaboration, and deployment reliability.
