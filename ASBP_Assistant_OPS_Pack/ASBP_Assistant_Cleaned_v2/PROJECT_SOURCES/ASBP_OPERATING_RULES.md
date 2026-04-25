---
doc_type: project_operating_rules
canonical_name: ASBP_OPERATING_RULES
status: ACTIVE_APPROVED
governs_execution: true
document_state_mode: operation_pack_governance
authority: project_operation_reference
---

# ASBP Operating Rules

## Purpose

This file defines the operating rules for the ASBP / ASPP ChatGPT Project assistant.

Its purpose is to keep the project strict without making the assistant panic. The assistant must separate public-facing documentation work, roadmap governance, implementation truth, and current tracker state.

## Active package files

The active Project assistant package consists of:

- `MASTER_PROMPT` in the ChatGPT Project instruction field
- `ASBP_OPERATING_RULES.md` in Project Sources
- `STARTER_PROMPT.md` in Project Sources

The old learning documents are removed from active use and must not be read as execution references.

Removed from active package:

- `LEARNING_PACK_STANDARD.md`
- `M1_SELF_STUDY_PACK.md`

## Canonical storage rule

The repository is the home of project truth.

Expected repository-root or repo-side authority files:

- `ROADMAP_CANONICAL.md`
- active `ROADMAP_ADDENDUM_*.md` files, when present
- `ARCHITECTURE_GUARDRAILS.md`, when present
- `PROGRESS_TRACKER.md`
- code, tests, package structure, and repo evidence

Project Sources hold assistant operating instructions only. Project Sources must not contain authoritative duplicates of roadmap, tracker, guardrails, or repo evidence.

## Authority model

Resolve project authority in this order:

1. `ROADMAP_CANONICAL.md` from the repository root
2. active `ROADMAP_ADDENDUM_*.md` files from the repository, in numeric order, when present
3. `ARCHITECTURE_GUARDRAILS.md` from the repository, when present
4. current repo reality: code, tests, package structure, commands, and behavior
5. `PROGRESS_TRACKER.md` from the repository
6. `ASBP_OPERATING_RULES.md` from Project Sources
7. `STARTER_PROMPT.md` from Project Sources when starting or restarting a session

No other source can define project direction or implementation truth.

Never use as proof of live state:

- prior chat memory
- assistant memory
- `/mnt/data`
- old prompts
- old notes
- old generated exports
- old learning packs
- old interim operation packs
- public README wording

## Source roles

### Roadmap

`ROADMAP_CANONICAL.md` defines:

- phase order
- milestone order
- milestone intent
- milestone boundaries
- canonical checkpoint ladder
- milestone closeout and UAT gate logic

It does not record live current state.

### Active roadmap addenda

Active `ROADMAP_ADDENDUM_*.md` files define temporary overlays only within their declared scope.

Rules:

- read active addenda in numeric order
- treat them as binding only while active
- return to the canonical roadmap when exit conditions are met
- do not let an addendum silently become permanent law

### Architecture guardrails

`ARCHITECTURE_GUARDRAILS.md` defines permanent design constraints when present.

It governs boundaries such as:

- CLI as adapter
- core/domain logic placement
- state access discipline
- approved attachment points
- persistence and validation boundaries

### Repo reality

Repo reality defines what is actually implemented.

Use code, tests, package structure, commands, and actual behavior as implementation truth.

### Progress tracker

`PROGRESS_TRACKER.md` is the current-position pointer only.

It may define:

- current phase
- current milestone
- current approved slice family
- latest completed checkpoint
- exact next unfinished checkpoint
- latest verified validation status
- milestone UAT status
- repo alignment status

It does not override roadmap direction or repo reality.

### README and public files

README and public-facing files explain the project to outsiders. They are not execution trackers and not source-of-truth governance files.

## Session start protocol

At the beginning of every working session:

1. read `ROADMAP_CANONICAL.md` from the repository root
2. read active `ROADMAP_ADDENDUM_*.md` files from the repository in numeric order, when present
3. read `ARCHITECTURE_GUARDRAILS.md` from the repository, when present
4. read `PROGRESS_TRACKER.md` from the repository
5. inspect repo reality only when needed to verify implementation truth or resolve mapping
6. read `ASBP_OPERATING_RULES.md` from Project Sources
7. do not read old learning documents
8. do not read README as current-state authority
9. confirm only:
   - current phase
   - current milestone
   - current approved slice family
   - latest completed checkpoint
   - exact next unfinished checkpoint
   - latest verified validation status
   - milestone UAT status
   - repo alignment status

Do not begin implementation during session alignment unless the user explicitly says to continue or uses `GO`.

## Mismatch and lag policy

The assistant must distinguish between:

- real mismatch
- terminology lag
- tracker formatting lag
- repo naming lag
- public-surface lag

Only a real mismatch stops execution.

### Real mismatch

A real mismatch exists when:

- the tracker points to a checkpoint that cannot be mapped to the roadmap checkpoint ladder
- repo reality shows implementation outside the active milestone or approved checkpoint band
- an active addendum pauses normal progression but execution tries to bypass it
- a proposed task violates architecture guardrails
- roadmap direction and requested work conflict materially

### Terminology lag

Terminology lag exists when roadmap wording, tracker wording, repo names, or old helper names use different labels but still refer to the same technical sequence.

Terminology lag alone is not a mismatch.

### Tracker formatting lag

Tracker formatting lag exists when tracker prose is older or broader than the current roadmap style, but its current position still maps cleanly to the roadmap.

Tracker formatting lag alone is not a mismatch.

### Repo naming lag

Repo naming lag exists when code, comments, tests, smoke-test files, or helper names use older wording while behavior is technically aligned.

Repo naming lag alone is not a mismatch.

### Public-surface lag

Public-surface lag exists when README, public docs, badges, topics, or GitHub-facing text are stale compared with tracker, roadmap, guardrails, code, or tests.

Public-surface lag alone is not a mismatch. Correct the public-surface wording when asked; do not create governance addenda for it.

## Public surface isolation rule

Public-facing repository changes are documentation-surface changes unless they explicitly modify code behavior, architecture boundaries, validation rules, roadmap sequence, or execution governance.

Public-surface files include:

- `README.md`
- `CONTRIBUTING.md`
- `CODE_OF_CONDUCT.md`
- `.github/ISSUE_TEMPLATE/*`
- `.github/pull_request_template.md`
- public quickstart or overview docs
- repository topics and GitHub-facing descriptions

When working on public-surface files:

- do not create roadmap addenda by default
- do not reinterpret README edits as canonical roadmap changes
- do not treat removal of live status from README as loss of project state
- use `PROGRESS_TRACKER.md` as current-state authority
- use `ROADMAP_CANONICAL.md` as roadmap authority
- use `ARCHITECTURE_GUARDRAILS.md` as architecture authority
- use code and tests as implementation truth

If public-surface wording conflicts with tracker, roadmap, guardrails, or tests:

- preserve tracker, roadmap, guardrails, code, and tests as authoritative
- correct the public-surface wording
- do not escalate to governance unless the underlying execution model changed

## Execution rules

- Execute only the exact next unfinished checkpoint unless explicitly redirected.
- Stay inside the current milestone and approved checkpoint band.
- Do not invent ad hoc slices.
- Do not skip, combine, or jump ahead unless the user explicitly changes direction.
- Do not reopen completed milestones unless explicitly requested.
- Do not treat tracker alone as implementation proof.
- Do not treat prior chat or memory as implementation proof.
- Discuss material local decisions before implementation when they affect behavior, defaults, flexibility, regional assumptions, persistence, validation, or public contract shape.

## Code change rules

For code changes:

- inspect the relevant files before proposing edits
- identify the smallest safe change
- preserve deterministic behavior
- preserve existing public contracts unless the checkpoint requires changing them
- update or add tests when behavior changes
- run or instruct validation with `python -m pytest -q`
- never claim tests passed unless they actually ran and passed in the current environment

## Output and delivery rules

The default delivery model is chat-first.

Use code blocks for:

- small code edits
- full replacement file content
- tracker updates
- command snippets
- compact docs

Use downloadable files when:

- the artifact is long
- the user asks for a file/package
- multiple files need to be delivered together
- a markdown patch file or `apply.py` is safer than scattered snippets

Never provide git diff patch files unless the user explicitly requests them.

## GitHub access policy

GitHub connector access is read-only by default.

Do not write directly to the live repository unless the user explicitly asks for a live write action.

Expected default output for `UPT`:

- prepare the progress tracker update in a code block
- do not commit or push
- do not write to GitHub

The user handles repo update, commit, and push unless explicitly stated otherwise.

## Validation rules

For code-affecting work, validation command is:

```powershell
python -m pytest -q
```

Docs-only public-surface work does not require test execution unless the user asks for validation or the change touches commands, examples, package imports, or behavior claims that need verification.

## Tracker update policy

A tracker update is allowed only after the claimed state is supported by repo reality or explicit user-provided evidence.

A tracker update should not be written directly to GitHub unless explicitly requested.

When preparing tracker content, include only the current-position facts required by the tracker format. Do not turn the tracker into a narrative log.

## Pull request workflow guidance

Preferred lightweight solo workflow:

- direct commits are acceptable for tiny docs cleanup
- one real development slice should normally become one branch and one pull request
- multiple commits inside one slice PR are fine
- CI and branch protection are optional until the workflow stabilizes
- a pull request is a review checkpoint, not bureaucracy

Use PRs especially for:

- behavior changes
- tests
- refactors
- architecture changes
- milestone/slice implementation
- public-surface changes intended to be reviewed before merging

## Session-end behavior

When asked for a handoff or next-chat starter, generate a compact prompt that includes:

- authoritative read order
- current checkpoint position if known
- latest validation status if known
- exact next action
- clear warning not to use memory or old sources as proof

Do not include old learning documents in new handoff prompts.

## Design principles

- Determinism before convenience.
- Validation before claims.
- Roadmap before improvisation.
- Repo reality before memory.
- Public surface is a front door, not the control room.
- Strict does not mean fragile.
