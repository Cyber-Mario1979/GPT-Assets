Start ASBP migrated session.

Read in this order:
1) `ROADMAP_CANONICAL.md` from the repository root
2) active `ROADMAP_ADDENDUM_*.md` files from the repository, in numeric order, when present
3) `ARCHITECTURE_GUARDRAILS.md` from the repository, when present
4) `PROGRESS_TRACKER.md` from the repository
5) current repo reality only when needed
6) `PROJECT_INSTRUCTIONS.md` from Project Sources
7) `SESSION_WORKFLOW.md` from Project Sources
8) `LEARNING_PACK_STANDARD.md` from Project Sources
9) `M1_SELF_STUDY_PACK.md` from Project Sources as style reference only

Treat the operation-pack files as execution-governance references, not as proof of implementation reality.

Canonical storage rule:
- the roadmap is now in the repo root
- the tracker and guardrails are in the repo
- the operation-pack files remain in Project Sources
- do not expect the roadmap in Project Sources anymore

Then confirm only:
- current phase
- current milestone
- current approved slice family
- latest completed checkpoint
- exact next unfinished checkpoint
- latest verified validation status
- milestone UAT status
- repo alignment status

Rules:
- roadmap = direction + canonical checkpoint ladder
- active addenda = authorized overlay only while active
- architecture guardrails = permanent design governance
- repo reality = implementation truth
- tracker = current-position pointer only
- do not infer state from memory or prior chat
- do not use `/mnt/data` as proof of live repo state
- terminology lag, tracker formatting lag, or repo naming lag alone are not mismatches
- if there is a real conflict, stop and state the mismatch first
- after alignment, work only on the exact next checkpoint unless explicitly redirected
- minor local implementation decisions inside a checkpoint must be discussed immediately before implementation when they materially affect behavior, defaults, flexibility, regional assumptions, or contract shape