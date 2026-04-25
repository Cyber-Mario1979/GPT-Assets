# ASBP Branch / Pull Request / Merge Strategy

## Purpose

This strategy defines how code, documentation, and milestone work should move into `main` going forward.

The goal is to improve repository history, review discipline, public visibility, and rollback clarity without adding unnecessary bureaucracy to the deterministic build workflow.

---

## Core rule

`main` is the stable working branch.

Work that affects behavior, tests, architecture, roadmap execution, or milestone evidence should enter `main` through a pull request.

Tiny documentation corrections may still be committed directly when they do not affect project state, public meaning, code behavior, roadmap direction, or architecture rules.

---

## Recommended model

Use two PR levels:

1. **Slice PRs**
2. **Milestone closure PRs**

This is better than waiting until the end of a milestone for one large PR.

---

## 1. Slice PRs

Use a slice PR for normal development work.

A slice PR should be opened when the work represents a coherent implementation checkpoint or reviewable unit.

Examples:

- adding a focused behavior
- adding tests for a focused behavior
- refactoring a bounded module
- updating CLI behavior
- adding a new validation rule
- applying a public-surface documentation package
- completing a roadmap checkpoint

Recommended branch naming:

```text
slice/<checkpoint-id>-<short-description>
```

Examples:

```text
slice/m12-4-source-link-validation
slice/public-surface-cleanup
slice/task-status-transition-tests
```

Recommended PR title:

```text
<type>: <short purpose>
```

Examples:

```text
docs: clean public repository surface
tests: add invalid task status coverage
feat: add source-of-work relationship validation
refactor: isolate task ordering logic
```

A slice PR should include:

- what changed
- why it changed
- whether behavior changed
- what tests were run
- whether roadmap, architecture, or validation rules were affected

---

## 2. Milestone closure PRs

Use a milestone closure PR after implementation work for a milestone is complete and validated.

A milestone closure PR should not be a large hidden implementation bundle.

It should normally contain closure evidence and final documentation alignment, such as:

- final milestone closeout note
- tracker update
- UAT record
- validation evidence
- changelog note, if used
- documentation alignment required to close the milestone

Recommended branch naming:

```text
milestone/<milestone-id>-closeout
```

Examples:

```text
milestone/m12-closeout
milestone/m13-closeout
```

Recommended PR title:

```text
closeout: <milestone-id> milestone closure
```

Example:

```text
closeout: M12 milestone closure
```

Milestone closure PRs should confirm:

- milestone scope completed
- validation passed
- UAT completed, if applicable
- tracker updated
- no hidden implementation work is included unless explicitly stated
- exact next checkpoint is recorded

---

## When to use direct commits

Direct commits to `main` are allowed only for low-risk changes such as:

- typo fixes
- formatting-only documentation cleanup
- correcting a broken link
- updating a comment that does not change public meaning
- emergency cleanup that does not affect behavior or governance

Do not use direct commits for:

- behavior changes
- tests
- architecture changes
- roadmap/tracker changes
- milestone closure
- public-facing documentation packages
- refactors
- dependency or environment changes

When unsure, use a PR.

---

## Merge method

Preferred merge method:

```text
Squash and merge
```

Reason:

- keeps `main` history clean
- groups many small local commits into one meaningful repository event
- works well for slice-based and milestone-based development
- makes rollback and review easier

Use regular merge commits only when preserving the internal commit history is important.

Avoid rebase merging unless there is a specific reason.

---

## PR size rule

A PR should be small enough to review.

Prefer:

```text
one slice = one PR
one milestone closure = one PR
one public-surface package = one PR
```

Avoid:

```text
one milestone = one huge implementation PR
many unrelated changes = one PR
```

If a milestone contains several implementation slices, create several slice PRs during the milestone, then create one milestone closure PR at the end.

---

## Suggested lifecycle

For normal development:

```text
1. Confirm current checkpoint
2. Create slice branch
3. Implement narrow change
4. Run validation
5. Open slice PR
6. Self-review diff
7. Merge using squash
8. Continue next slice
```

For milestone closure:

```text
1. Confirm all milestone slices are merged
2. Run full validation
3. Complete UAT / closeout evidence if applicable
4. Create milestone closeout branch
5. Update tracker and closeout docs
6. Open milestone closure PR
7. Self-review
8. Merge using squash
9. Start next milestone from clean main
```

---

## CI policy

CI is recommended, but it should be introduced lightly.

Initial CI should only run:

```text
python -m pytest -q
```

Do not make CI or required approvals too strict until the PR workflow becomes stable.

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

## Operation pack rule

This strategy should be included in the assistant operation pack as the default repository workflow rule.

The assistant should treat PR strategy as workflow governance, not product architecture.

The assistant must not create roadmap addenda merely because a change uses a branch or pull request.

Branch and PR usage is a repository hygiene practice unless the change itself affects roadmap, architecture, validation rules, or code behavior.

---

## Assistant behavior rule

When the user says to apply a slice, public-surface package, or milestone closure:

1. Identify whether the change is:
   - slice work
   - public-surface work
   - milestone closeout work
   - emergency direct commit candidate

2. Recommend the correct branch type.

3. Keep the PR scope narrow.

4. Do not mix unrelated changes.

5. Do not escalate to governance unless the underlying change affects roadmap, architecture, validation rules, or behavior.

---

## Default recommendation

Going forward:

```text
Use slice PRs during milestone execution.
Use one milestone closure PR after each milestone is validated.
Use direct commits only for tiny, low-risk documentation corrections.
Prefer squash merge into main.
```
