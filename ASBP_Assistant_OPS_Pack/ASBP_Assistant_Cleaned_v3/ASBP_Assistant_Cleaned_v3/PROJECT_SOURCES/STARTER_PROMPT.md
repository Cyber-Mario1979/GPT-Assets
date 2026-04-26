# STARTER_PROMPT

Start ASBP / ASPP working session.

Read in this order:

1. `ROADMAP_CANONICAL.md` from the repository root
2. active `ROADMAP_ADDENDUM_*.md` files from the repository, in numeric order, when present
3. `ARCHITECTURE_GUARDRAILS.md` from the repository, when present
4. `PROGRESS_TRACKER.md` from the repository
5. current repo reality only when needed to verify implementation truth or resolve checkpoint mapping
6. `ASBP_OPERATING_RULES.md` from Project Sources
7. `ASBP_BRANCH_PR_MERGE_STRATEGY.md` from Project Sources only when branch/PR/merge guidance is needed

Do not read old learning documents.
Do not use README as current-state authority.
Do not use memory, prior chats, `/mnt/data`, old generated notes, or old Project-Sources duplicates as proof of live state.

Canonical storage rule:

- roadmap lives in the repo root
- tracker lives in the repo
- guardrails live in the repo when present
- active roadmap addenda live in the repo when present
- operating rules, branch/PR/merge strategy, and this starter prompt live in Project Sources
- learning documents are removed from active operation

Interpretation rules:

- roadmap = direction and canonical checkpoint ladder
- active addenda = authorized temporary overlay only while active
- guardrails = permanent architecture governance
- repo reality = implementation truth
- tracker = current-position pointer only
- branch/PR/merge strategy = workflow hygiene only
- README/public GitHub files = public surface only
- terminology lag, tracker formatting lag, repo naming lag, public-surface lag, or PR workflow-format lag alone are not mismatches
- if a real conflict exists, stop and state it before implementation

After alignment, confirm only:

- current phase
- current milestone
- current approved slice family
- latest completed checkpoint
- exact next unfinished checkpoint
- latest verified validation status
- milestone UAT status
- repo alignment status

Do not implement during this startup response unless the user explicitly says `GO` or gives a direct implementation instruction after alignment.
