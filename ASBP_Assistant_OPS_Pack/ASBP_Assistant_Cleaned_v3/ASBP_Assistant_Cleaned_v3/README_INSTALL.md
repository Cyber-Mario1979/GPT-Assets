# ASBP Assistant Cleaned Package v3

This package replaces the previous noisy Project assistant package and updates the branch / pull request / merge strategy.

## What changed in v3

- Replaced the old “one slice = one PR” default with a coherent PR-bundle strategy.
- Added `ASBP_BRANCH_PR_MERGE_STRATEGY.md` as an active Project Source.
- Updated `MASTER_PROMPT.txt` to reference branch/PR/merge workflow decisions.
- Updated `ASBP_OPERATING_RULES.md` to treat PR strategy as workflow hygiene, not roadmap or architecture.
- Updated `STARTER_PROMPT.md` so branch strategy is read only when branch/PR/merge guidance is needed.
- Kept learning documents removed from active operation.

## Install layout

### 1. ChatGPT Project instruction field

Copy the full content of:

```text
PROJECT_INSTRUCTION_FIELD/MASTER_PROMPT.txt
```

into the ChatGPT Project instruction field.

### 2. ChatGPT Project Sources

Upload these files to Project Sources:

```text
PROJECT_SOURCES/ASBP_OPERATING_RULES.md
PROJECT_SOURCES/ASBP_BRANCH_PR_MERGE_STRATEGY.md
PROJECT_SOURCES/STARTER_PROMPT.md
```

### 3. Remove old active Project Sources

Remove these from active Project Sources if present:

```text
PROJECT_INSTRUCTIONS.md
SESSION_WORKFLOW.md
LEARNING_PACK_STANDARD.md
M1_SELF_STUDY_PACK.md
```

The learning documents are no longer active operating references.

## Repo-side files that stay authoritative

Keep these in the repository, not Project Sources:

```text
ROADMAP_CANONICAL.md
ROADMAP_ADDENDUM_*.md
ARCHITECTURE_GUARDRAILS.md
PROGRESS_TRACKER.md
asbp/
tests/
```

## Main behavior model

The assistant now separates:

```text
Public GitHub surface = README, topics, issue templates, PR template, Code of Conduct
Execution control = roadmap, addenda, guardrails, progress tracker
Implementation truth = code and tests
Repository workflow = branch / PR / merge strategy
Assistant behavior = master prompt + operating rules + starter prompt
```

Public-surface cleanup and PR workflow decisions must not trigger governance panic.

## Shortcut commands included in MASTER_PROMPT

```text
SS
UPT
STATUS
NEXT
PLAN
PR
GO
SURFACE
HANDOFF
PAUSE
RESUME
HELP
```

## First use

In a new Project chat, type:

```text
SS
```

For the first chat after installing v3, you may use:

```text
SS

This project has been updated with ASBP Assistant Cleaned Package v3.

Use the current Project instruction field as the active master prompt.
Use ASBP_OPERATING_RULES.md, ASBP_BRANCH_PR_MERGE_STRATEGY.md, and STARTER_PROMPT.md from Project Sources.
Do not use removed legacy learning documents.
Do not treat this package cleanup as a roadmap, architecture, or codebase change.

Confirm only the current operating mode and exact next repo checkpoint.
```

The assistant should align state only and should not implement anything until you explicitly continue or say `GO`.
