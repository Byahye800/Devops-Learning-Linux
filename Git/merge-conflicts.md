# Git Merge Conflicts

## Purpose

This document records my practical understanding of Git merge conflicts and conflict resolution workflows as part of my DevOps learning portfolio.

The purpose of this section is to demonstrate:
- understanding of merge conflicts
- conflict identification skills
- manual conflict resolution workflows
- safe merge recovery practices
- collaborative Git troubleshooting techniques used in professional engineering environments

---

# What a Merge Conflict Is

A merge conflict happens when Git cannot automatically determine how to combine changes from different branches.

This usually occurs when:
- the same file was modified on multiple branches
- the same lines were edited differently
- one branch deleted code while another modified it

Git stops the merge process and requires manual human decision-making.

---

# Why Merge Conflicts Happen

Git normally merges changes automatically.

However, conflicts occur when Git detects ambiguous changes.

Example scenario:

```text
main branch edits line 10
feature branch also edits line 10
        ↓
Git cannot determine which version is correct
        ↓
merge conflict occurs
```

Git prevents automatic merging to avoid accidentally overwriting important work.

---

# Common Causes of Merge Conflicts

Typical causes include:
- multiple developers editing the same file
- long-lived feature branches
- outdated local branches
- simultaneous documentation edits
- conflicting configuration changes
- large refactors across branches

Merge conflicts are normal in real-world engineering workflows.

---

# Example Conflict Workflow

Typical merge conflict workflow:

```text
create feature branch
        ↓
edit files on feature branch
        ↓
main branch also changes same file
        ↓
attempt merge
        ↓
Git detects conflict
        ↓
manual conflict resolution required
```

---

# Creating a Merge Conflict Example

Example workflow:

```bash
git switch -c feature-update
```

Modify a file on the feature branch and commit changes.

Switch back to main branch:

```bash
git switch main
```

Modify the same file differently and commit changes.

Attempt merge:

```bash
git merge feature-update
```

Git may then report a merge conflict.

---

# Understanding Conflict Markers

When a conflict occurs, Git inserts special conflict markers into the affected file.

Example:

```text
<<<<<<< HEAD
Current branch content
=======
Incoming branch content
>>>>>>> feature-update
```

---

# Conflict Marker Breakdown

| Marker | Meaning |
|---|---|
| `<<<<<<< HEAD` | Current branch version |
| `=======` | Separator between versions |
| `>>>>>>> feature-update` | Incoming branch version |

These markers help engineers decide which content to keep.

---

# Resolving Merge Conflicts

Conflict resolution normally involves:

1. opening the conflicted file
2. reviewing both versions
3. deciding what content to keep
4. removing conflict markers
5. saving the corrected file

After resolution:

```bash
git add conflicted-file.md
```

Then finalize the merge:

```bash
git commit
```

---

# Example Conflict Resolution

Example conflicted file:

```text
<<<<<<< HEAD
Production database configuration
=======
Development database configuration
>>>>>>> feature-update
```

Possible resolved version:

```text
Production database configuration
Development database configuration
```

or alternatively selecting only one version.

The engineer decides the correct final result.

---

# Checking Conflict Status

Git status helps identify conflicted files.

Example:

```bash
git status
```

Git may display:

```text
both modified: app-config.yml
```

This indicates manual resolution is required before the merge can complete.

---

# Aborting a Merge

If necessary, a merge can be cancelled using:

```bash
git merge --abort
```

This restores the repository to its previous pre-merge state.

This is useful when:
- the merge became too complex
- incorrect branches were merged
- additional review is needed

---

# Best Practices to Reduce Merge Conflicts

Professional practices to reduce conflicts include:
- pulling changes frequently
- keeping branches short-lived
- communicating with team members
- making smaller focused commits
- avoiding large overlapping edits
- merging regularly into feature branches

These practices reduce integration complexity.

---

# Real-World Team Collaboration

In collaborative environments:
- multiple engineers may work simultaneously
- conflicts are expected occasionally
- communication becomes important
- pull request reviews help identify issues early

Merge conflict resolution is therefore an essential engineering skill.

---

# Conflict Resolution Workflow Summary

Professional conflict resolution workflow:

```text
attempt merge
        ↓
Git detects conflict
        ↓
inspect conflicted files
        ↓
manually resolve content
        ↓
remove conflict markers
        ↓
stage resolved files
        ↓
complete merge commit
```

---

# Merge Conflicts vs Merge Commits

Important distinction:

| Concept | Meaning |
|---|---|
| Merge Commit | Combines branch histories successfully |
| Merge Conflict | Git cannot automatically combine changes |

A merge commit is normal successful repository history.

A merge conflict requires manual intervention before merging can continue.

---

# Practical Skills Demonstrated

Practical merge conflict activities completed include:

- creating feature branches
- modifying conflicting files
- identifying merge conflicts
- understanding conflict markers
- manually resolving conflicts
- staging resolved files
- completing merge workflows
- aborting problematic merges
- inspecting Git status during conflicts
- maintaining safe repository recovery practices

---

# Real-World Engineering Relevance

Merge conflict management is a critical collaboration skill in:
- DevOps engineering
- software engineering
- Infrastructure as Code workflows
- CI/CD pipelines
- GitHub pull request systems
- team-based development environments

Professional engineers must understand how to safely resolve conflicts without damaging repository history or overwriting important changes.

---

# Key Learning Outcome

I understand:
- what Git merge conflicts are
- why conflicts occur
- how Git conflict markers work
- how to manually resolve conflicts
- how to safely complete or abort merges

I also understand that merge conflict resolution is a critical collaboration and repository safety skill used throughout professional software engineering and DevOps workflows.
