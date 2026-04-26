# ASBP Branch / Pull Request / Merge Strategy

## Purpose

This strategy defines how code, documentation, public-surface work, and milestone closeout evidence should move into `main`.

The goal is to improve review clarity, repository history, rollback clarity, and public visibility without creating unnecessary PR noise.

This is workflow governance only. It does not change roadmap order, checkpoint authority, architecture guardrails, validation policy, or implementation truth.

---

## Core rule

`main` is the stable working branch.

Use pull requests for coherent review boundaries, not for every tiny slice automatically.

A PR should represent one meaningful review unit.

Do not use PRs as performance theater.

Do not use direct commits for changes that should be reviewed.

---

## PR levels

Use these four levels.

### 1. Direct commit

Use direct commits only for tiny, low-risk corrections.

Allowed examples:

- typo fix
- broken link
- formatting-only documentation cleanup
- comment wording that does not change public meaning
- harmless metadata correction

Do not direct-commit:

- behavior changes
- tests
- refactors
- architecture-sensitive changes
- roadmap or tracker changes
- milestone closure
- public-surface packages
- dependency or environment changes

When unsure, use a PR.

---

### 2. Public-surface PR

Use one public-surface PR for repository-facing documentation and GitHub surface changes.

Examples:

- README evergreen cleanup
- CONTRIBUTING cleanup
- CODE_OF_CONDUCT addition
- issue templates
- PR template
- GitHub-facing docs package

Recommended branch naming:

```text
docs/public-surface-cleanup
```

Recommended PR title:

```text
docs: clean public repository surface
```

Rules:

- do not alter code
- do not alter tests
- do not alter roadmap authority
- do not alter architecture guardrails
- do not create roadmap addenda merely because public-facing files changed

---

### 3. Capability bundle PR

Use one capability bundle PR for a small group of adjacent, related roadmap checkpoints that form one coherent feature boundary.

This replaces the earlier “one slice = one PR” default.

A capability bundle may include multiple adjacent checkpoints only when they are tightly related and easier to review together.

Bundle by meaning, not by number.

Good bundle examples:

```text
M12.4 + M12.5
controlled authoring modes + standards/language/evidence guardrails

M12.6 + M12.7
document lifecycle + workflow-state integration
```

Bad bundle examples:

```text
M12.4 + M13.1
unrelated milestone areas

M12.5 + random README rewrite + dependency change
mixed unrelated work
```

Recommended branch naming:

```text
feature/<milestone-id>-<capability-name>
```

Examples:

```text
feature/m12-authoring-guardrails
feature/m12-document-lifecycle
feature/m13-export-contracts
```

Recommended PR title:

```text
engine: <capability summary>
```

Examples:

```text
engine: define controlled document authoring guardrails
engine: add document lifecycle workflow integration
```

Rules:

- keep the bundle small enough to review
- keep adjacent checkpoints explicit in the PR body
- do not hide unrelated work inside the bundle
- do not use bundling to skip checkpoint reasoning
- preserve deterministic validation and checkpoint mapping

---

### 4. Milestone closure PR

Use one milestone closure PR after milestone implementation work is complete and validated.

This PR should normally contain closure evidence and final documentation alignment only.

Typical contents:

- tracker update
- validation evidence
- UAT record, when applicable
- milestone closeout note
- final documentation alignment required for closeout

Recommended branch naming:

```text
closeout/<milestone-id>
```

Examples:

```text
closeout/m12
closeout/m13
```

Recommended PR title:

```text
closeout: <milestone-id> milestone closure
```

Example:

```text
closeout: M12 milestone closure
```

Rules:

- no hidden implementation bundle
- no unrelated refactor
- no new feature unless explicitly stated and justified
- confirm validation and UAT status
- record exact next checkpoint after closure

---

## Merge method

Preferred merge method:

```text
Squash and merge
```

Reason:

- keeps `main` history clean
- groups local commits into one meaningful repository event
- works well for public-surface PRs, capability bundle PRs, and milestone closure PRs
- improves rollback and review clarity

Use regular merge commits only when preserving internal commit history is important.

Avoid rebase merging unless there is a specific reason.

---

## PR size rule

A PR should be small enough to review.

Prefer:

```text
one public-surface package = one PR
one coherent capability bundle = one PR
one milestone closure = one PR
```

Avoid:

```text
one tiny slice = one PR by default
one whole milestone = one huge implementation PR
many unrelated changes = one PR
```

---

## Branch naming summary

```text
docs/public-surface-cleanup
feature/<milestone-id>-<capability-name>
fix/<short-bug-name>
tests/<coverage-area>
refactor/<bounded-area>
closeout/<milestone-id>
```

Examples:

```text
feature/m12-authoring-guardrails
feature/m12-document-lifecycle
tests/task-status-transitions
refactor/task-ordering-helpers
closeout/m12
```

---

## Suggested lifecycle

For public-surface work:

```text
1. Prepare approved public-surface files
2. Create docs/public-surface-cleanup branch
3. Apply files
4. Open one public-surface PR
5. Self-review
6. Squash merge
```

For capability work:

```text
1. Confirm exact active checkpoint and adjacent related checkpoint boundary
2. Decide whether the work should be one checkpoint PR or one capability bundle PR
3. Create feature branch
4. Implement narrow related work only
5. Run validation
6. Open capability bundle PR
7. Self-review
8. Squash merge
```

For milestone closure:

```text
1. Confirm all milestone implementation work is complete
2. Run full validation
3. Complete UAT / closeout evidence if applicable
4. Create closeout branch
5. Update tracker and closeout docs
6. Open milestone closure PR
7. Self-review
8. Squash merge
9. Start next milestone from clean main
```

---

## CI policy

CI is recommended, but introduce it lightly.

Initial CI should only run:

```text
python -m pytest -q
```

Initial policy:

- no mandatory external approval
- self-review is acceptable
- local test run required for code changes
- documentation-only PRs may skip tests if clearly stated

Later policy:

- enable CI on pull requests
- optionally require passing tests before merging
- avoid heavy branch protection until the workflow feels natural

---

## Assistant behavior rule

When the user asks to apply work:

1. Identify the work type:
   - tiny direct commit candidate
   - public-surface package
   - single-checkpoint work
   - capability bundle
   - milestone closure
   - emergency fix

2. Recommend:
   - branch name
   - PR boundary
   - PR title
   - validation expectation
   - merge method

3. Keep the PR scope narrow.

4. Do not mix unrelated changes.

5. Do not escalate to roadmap governance unless the underlying change affects roadmap order, architecture boundaries, validation rules, or behavior.

---

## Default recommendation

Going forward:

```text
Use direct commits only for tiny low-risk corrections.
Use one PR for a public-surface package.
Use one PR for a coherent capability bundle.
Use one PR for milestone closure evidence.
Prefer squash merge into main.
```
