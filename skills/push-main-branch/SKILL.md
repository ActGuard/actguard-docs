---
name: push-main-branch
description: Safely prepare and push repository changes to the main branch with explicit verification steps, clean commits, and conflict handling. Use when a user asks to push to main, publish current work, sync local changes to origin/main, or finalize a completed task by committing and pushing.
---

# Push Main Branch

## Overview

Execute a deterministic, low-risk workflow for pushing changes to `main`. Verify working tree state, run relevant checks, create clear commits, rebase/pull when needed, then push and report exact outcomes.

## Workflow

1. Verify repository state.
2. Confirm branch and remote alignment.
3. Validate changes before commit.
4. Create a focused commit.
5. Sync with remote `main`.
6. Push and verify remote result.

## Step 1: Verify State

Run:

```bash
git status --short --branch
git remote -v
```

If the working tree has unrelated unexpected changes, stop and ask how to proceed.

## Step 2: Confirm Main Branch

Run:

```bash
git branch --show-current
```

If not on `main`, switch only if the user asked for direct push to `main`:

```bash
git checkout main
```

## Step 3: Validate Before Commit

Run project checks relevant to the repo before committing. For documentation repositories, at minimum validate config and link targets when changed.

Example:

```bash
jq -e . docs.json
```

## Step 4: Commit Cleanly

Stage only intended files and create a specific message.

```bash
git add <files>
git commit -m "Short imperative summary"
```

If there are no staged changes, do not create an empty commit unless explicitly requested.

## Step 5: Sync With Remote Main

Prefer rebasing to keep history linear:

```bash
git fetch origin
git pull --rebase origin main
```

If conflicts occur, stop and resolve deliberately; do not force push.

## Step 6: Push and Verify

```bash
git push origin main
git log --oneline -n 3
```

Report:
- Branch pushed
- Commit hash(es)
- Whether checks passed
- Any skipped validations and why

## Resources (optional)
No extra resources are required for this skill.
