# Git Stash and Rebase

## Purpose

This document records my practical understanding of Git stash and rebase workflows as part of my DevOps learning portfolio.

The purpose of this section is to demonstrate:
- understanding of temporary change management
- clean commit history workflows
- safe branch history manipulation
- professional repository maintenance practices
- advanced Git workflow concepts used in real engineering environments

---

# What Git Stash Is

Git stash temporarily saves uncommitted changes without creating a commit.

This allows engineers to:
- pause unfinished work
- switch branches safely
- handle urgent tasks
- keep the working directory clean

Git stash is useful when work is incomplete but a context switch is required.

---

# Why Git Stash Is Important

In real engineering environments:
- urgent bug fixes may appear suddenly
- developers may need to switch branches quickly
- unfinished work may not be ready for committing

Git stash prevents:
- unnecessary temporary commits
- losing unfinished work
- cluttered commit history

---

# Basic Git Stash Workflow

Typical stash workflow:

```text
working directory changes
        ↓
stash changes temporarily
        ↓
switch branches safely
        ↓
return later
        ↓
restore stashed work
```

---

# Creating a Stash

Save current uncommitted changes:

```bash
git stash
```

Git removes the changes from the working directory and stores them safely inside the repository stash stack.

---

# Viewing Existing Stashes

List stored stashes:

```bash
git stash list
```

Example output:

```text
stash@{0}: WIP on main
stash@{1}: WIP on feature-login
```

Git stores stashes in stack order.

---

# Restoring Stashed Changes

Restore latest stash:

```bash
git stash pop
```

This:
- restores the changes
- removes the stash from the stash list

Alternative restore without removing stash:

```bash
git stash apply
```

This keeps the stash available for reuse.

---

# Creating Named Stashes

Git allows descriptive stash messages.

Example:

```bash
git stash push -m "unfinished navbar changes"
```

Named stashes improve:
- readability
- organization
- workflow management

---

# Removing Stashes

Delete specific stash:

```bash
git stash drop stash@{0}
```

Delete all stashes:

```bash
git stash clear
```

These commands should be used carefully because deleted stashes may be difficult to recover.

---

# Real-World Stash Workflow Example

Example workflow:

```text
working on feature branch
        ↓
urgent production issue appears
        ↓
stash unfinished work
        ↓
switch to hotfix branch
        ↓
fix issue
        ↓
return to original branch
        ↓
restore stashed work
```

This workflow is common in professional engineering teams.

---

# What Git Rebase Is

Git rebase moves or reapplies commits onto another branch base.

Rebase is commonly used to:
- maintain cleaner history
- avoid unnecessary merge commits
- organize commit sequences
- keep feature branches updated

---

# Merge vs Rebase

Important distinction:

| Merge | Rebase |
|---|---|
| Preserves branch history | Rewrites commit history |
| Creates merge commits | Creates cleaner linear history |
| Safer for shared history | Best for local/private cleanup |
| Shows true branch structure | Simplifies history visualization |

---

# Basic Rebase Workflow

Example:

```bash
git switch feature-login
git rebase main
```

This reapplies feature branch commits onto the latest version of `main`.

---

# Rebase Visualization

Without rebase:

```text
main
  \
   feature branch
```

After rebase:

```text
main → feature commits continue linearly
```

This creates cleaner commit history.

---

# Interactive Rebase

Interactive rebase allows engineers to:
- squash commits
- reorder commits
- edit commit messages
- clean messy history

Example:

```bash
git rebase -i HEAD~3
```

This opens an interactive editor for the last three commits.

---

# Common Interactive Rebase Operations

| Operation | Purpose |
|---|---|
| `pick` | Keep commit normally |
| `squash` | Combine commit with previous commit |
| `reword` | Change commit message |
| `edit` | Pause to modify commit |
| `drop` | Remove commit |

Interactive rebase is commonly used before pushing feature branches publicly.

---

# Squashing Commits

Squashing combines multiple commits into a single cleaner commit.

Example:

```text
fix typo
another typo fix
small adjustment
        ↓
single clean commit
```

This improves:
- repository readability
- commit quality
- professional history presentation

---

# Rebasing Risks

Rebase rewrites commit history.

Because of this:
- rebasing shared public branches can be dangerous
- collaborators may experience history conflicts
- force pushing may become necessary

Best practice:
- rebase local/private branches
- avoid rebasing heavily shared branches

---

# Git Commit Amend

Git allows modification of the most recent commit using:

```bash
git commit --amend
```

This can:
- update commit message
- include forgotten staged files
- improve commit quality

Example:

```bash
git add forgotten-file.md
git commit --amend
```

---

# Rebase Conflict Handling

Rebase may also create conflicts.

Git pauses the rebase process and requires manual conflict resolution.

After resolving conflicts:

```bash
git add resolved-file.md
git rebase --continue
```

Abort rebase if necessary:

```bash
git rebase --abort
```

---

# Professional Commit History Practices

Professional repositories aim for:
- meaningful commits
- readable history
- organized feature development
- minimal unnecessary commits

Tools like:
- stash
- rebase
- squash
- amend

help maintain repository quality.

---

# Practical Skills Demonstrated

Practical stash and rebase activities completed include:

- stashing unfinished work
- restoring stashed changes
- listing stash history
- creating named stashes
- clearing stashes safely
- rebasing feature branches
- understanding linear history
- using interactive rebase
- squashing commits
- amending commits
- handling rebase conflicts
- maintaining clean repository history

---

# Real-World Engineering Relevance

Git stash and rebase workflows are heavily used in:
- DevOps engineering
- CI/CD workflows
- collaborative feature development
- pull request cleanup
- Infrastructure as Code repositories
- professional Git history maintenance

Maintaining clean and understandable repository history is important for:
- debugging
- auditing
- collaboration
- deployment tracking
- long-term maintainability

---

# Key Learning Outcome

I understand:
- how Git stash temporarily saves unfinished work
- how Git rebase rewrites branch history
- how interactive rebase cleans commit history
- how stash and rebase improve repository organization
- how professional engineers maintain clean Git workflows

I also understand the importance of using advanced Git workflows carefully to avoid damaging shared repository history.
