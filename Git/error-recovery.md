# Git Error Recovery

## Module Objective

This module documents practical Git recovery techniques used to safely recover from mistakes during real-world development and DevOps workflows.

The goal is to understand:

- how Git tracks changes
- how to safely undo mistakes
- when to use reset vs revert
- how to recover lost work
- how to avoid damaging shared repository history

---

# Why Git Error Recovery Matters

Mistakes happen constantly in software engineering.

Common examples include:

- editing the wrong file
- committing too early
- staging sensitive files accidentally
- deleting important work
- pushing broken code
- merging incorrectly
- rebasing improperly

Professional engineers are not judged by never making mistakes.

They are judged by:

- how safely they recover
- how calmly they troubleshoot
- how well they protect repository history
- how well they prevent data loss

---

# Understanding Git States

Git mainly works with three areas:

| Area | Purpose |
|---|---|
| Working Directory | Files currently being edited |
| Staging Area | Files prepared for commit |
| Repository History | Saved Git commits |

Understanding these areas is critical for recovery operations.

---

# Visual Workflow

```text
Working Directory
        ↓
git add
        ↓
Staging Area
        ↓
git commit
        ↓
Repository History
```

Most recovery commands affect one or more of these layers.

---

# Core Recovery Commands

| Command | Purpose |
|---|---|
| `git status -sb` | Check repository state |
| `git diff` | View unstaged changes |
| `git diff --staged` | View staged changes |
| `git restore` | Discard local changes |
| `git restore --staged` | Remove file from staging |
| `git reset --soft` | Undo commit but keep staging |
| `git reset --mixed` | Undo commit and unstage |
| `git reset --hard` | Completely remove changes |
| `git revert` | Safely reverse shared commits |
| `git reflog` | Recover lost commit references |

---

# Scenario 1 — Recovering Unstaged Changes

## Problem

A file was edited incorrectly but was never staged.

---

## Step 1 — Check Status

```bash
git status -sb
```

Example:

```bash
## main
 M README.md
```

The `M` means the file was modified.

---

## Step 2 — View Changes

```bash
git diff
```

This shows exactly what changed before removing anything.

---

## Step 3 — Discard Changes

```bash
git restore README.md
```

---

## What This Does

- removes local edits
- restores the file to the last committed version
- affects only the working directory

---

## Important Warning

This permanently removes uncommitted edits.

Always inspect changes first with:

```bash
git diff
```

---

# Scenario 2 — Unstaging a File

## Problem

A file was added to staging accidentally.

---

## Step 1 — View Staged Files

```bash
git status -sb
```

Example:

```bash
A README.md
```

---

## Step 2 — Remove From Staging

```bash
git restore --staged README.md
```

---

## What This Does

- removes the file from staging
- keeps the actual file edits
- does NOT delete work

---

# Scenario 3 — Undo Last Commit but Keep Changes

## Problem

The commit happened too early or had a bad message.

---

## Command

```bash
git reset --soft HEAD~1
```

---

## What This Does

| Action | Result |
|---|---|
| Removes commit | Yes |
| Keeps file changes | Yes |
| Keeps files staged | Yes |

---

## Best Use Case

- fixing commit messages
- reorganizing commits
- recommitting cleanly

---

## Example Workflow

```bash
git reset --soft HEAD~1
git commit -m "Better commit message"
```

---

# Scenario 4 — Undo Commit and Unstage Changes

## Problem

The commit should be removed and files reviewed again.

---

## Command

```bash
git reset --mixed HEAD~1
```

---

## What This Does

| Action | Result |
|---|---|
| Removes commit | Yes |
| Keeps file changes | Yes |
| Removes staging | Yes |

---

## Best Use Case

- commit structure cleanup
- reviewing files before recommitting
- separating commits properly

---

# Scenario 5 — Completely Remove Commit and Changes

## Problem

The commit and all related changes should be deleted entirely.

---

## Command

```bash
git reset --hard HEAD~1
```

---

## What This Does

| Action | Result |
|---|---|
| Removes commit | Yes |
| Removes file changes | Yes |
| Removes staging | Yes |

---

## Critical Warning

This is destructive.

Improper use can permanently delete work.

---

## Professional Safety Practice

Before destructive operations:

```bash
git branch backup-before-reset
```

This creates a recovery point.

---

# Scenario 6 — Safely Reversing Shared Commits

## Problem

A bad commit was already pushed to GitHub.

Using reset here can damage shared history.

---

## Safe Solution

```bash
git revert commit-hash
```

Example:

```bash
git revert a1b2c3d
```

---

## What This Does

Git creates a NEW commit that reverses the previous changes.

History remains intact.

---

# Reset vs Revert

| Command | Rewrites History | Safe for Shared Repos |
|---|---|---|
| `git reset` | Yes | No |
| `git revert` | No | Yes |

---

# Simple Rule

| Situation | Use |
|---|---|
| Local cleanup before push | `reset` |
| Already pushed/shared commits | `revert` |

---

# Scenario 7 — Recovering Lost Work with Reflog

## Problem

A commit disappeared after:

- reset
- rebase
- checkout
- accidental HEAD movement

---

## Recovery Command

```bash
git reflog
```

---

## What Reflog Shows

Reflog tracks where HEAD previously pointed.

Even commits no longer visible in `git log` can often still be recovered.

---

## Example Output

```bash
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
d4e5f6g HEAD@{1}: commit: Add feature
```

---

## Recovering the Commit

```bash
git checkout d4e5f6g
```

Or safely create a branch:

```bash
git checkout -b recovery-branch d4e5f6g
```

---

# Professional Recovery Workflow

Before recovery operations:

## 1. Inspect Repository State

```bash
git status -sb
```

---

## 2. Review Unstaged Changes

```bash
git diff
```

---

## 3. Review Staged Changes

```bash
git diff --staged
```

---

## 4. Create Backup Branch if Needed

```bash
git branch backup-before-recovery
```

---

## 5. Choose Safest Recovery Method

Always choose the least destructive solution first.

---

# Important Engineering Mindset

Professional engineers:

- inspect before deleting
- avoid panic commands
- protect shared history
- create recovery points
- verify before force operations

Git recovery is about controlled troubleshooting.

---

# Commands Practiced

```bash
git status -sb
git diff
git diff --staged
git restore README.md
git restore --staged README.md
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
git revert commit-hash
git reflog
git checkout -b recovery-branch commit-hash
```

---

# Evidence to Capture

Recommended screenshots or terminal evidence:

- modified file before recovery
- git status output
- git diff output
- unstaging workflow
- reset examples
- revert example
- reflog recovery example
- final clean working tree

---

# Final Verification

After all recovery testing:

```bash
git status -sb
```

Expected clean output:

```bash
## main...origin/main
```

---

# Module Summary

This module demonstrates professional Git recovery workflows and safe troubleshooting practices.

Key skills covered:

- discarding unwanted edits
- unstaging files
- undoing commits safely
- understanding reset modes
- safely reverting shared history
- recovering lost work with reflog
- protecting repository history
- creating backup recovery points

Git recovery is a critical engineering skill because mistakes are inevitable in real-world development environments.
