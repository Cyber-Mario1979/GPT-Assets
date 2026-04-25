# ASBP Assistant Cleaned Package v2

This package replaces the previous noisy Project assistant package.

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

## Main behavior change

The assistant now separates:

```text
Public GitHub surface = README, topics, issue templates, PR template, Code of Conduct
Execution control = roadmap, addenda, guardrails, progress tracker
Implementation truth = code and tests
Assistant behavior = master prompt + operating rules + starter prompt
```

README/public-surface cleanup must not trigger governance panic.

## Shortcut commands included in MASTER_PROMPT

```text
SS
UPT
STATUS
NEXT
PLAN
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

The assistant should align state only and should not implement anything until you explicitly continue or say `GO`.
