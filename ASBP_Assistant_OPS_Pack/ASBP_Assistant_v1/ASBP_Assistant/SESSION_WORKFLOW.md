---
doc_type: session_workflow
canonical_name: SESSION_WORKFLOW
status: ACTIVE_APPROVED
governs_execution: true
document_state_mode: operation_pack_workflow
authority: session_behavior_reference
---

# SESSION_WORKFLOW

## Purpose

Define a strict, repeatable workflow for every ASBP working session.

Ensure:
- no drift
- no ambiguity
- deterministic execution
- clear separation between roadmap direction, repo reality, tracker state, and learning artifacts
- continuity across migrations and Project workspaces
- no false stop conditions caused by wording lag between roadmap, tracker, and repo naming
- milestone discipline from start to finish

---

## Canonical storage rule

`ROADMAP_CANONICAL.md` is stored in the **repo root**.

It is the canonical direction file for ASBP and is expected to exist in the repo.

Project Sources should not hold an authoritative duplicate of the roadmap. If a legacy Project-Sources copy remains during migration, it is non-authoritative convenience only.

The repo remains the home of:
- code and tests
- current implementation reality
- `PROGRESS_TRACKER.md`
- `ARCHITECTURE_GUARDRAILS.md`
- active `ROADMAP_ADDENDUM_*.md` files
- repo-side UAT and smoke-test evidence

---

## Authority Model

Always resolve project authority in this order:

1. `ROADMAP_CANONICAL.md` from the repo root
   Direction source of truth and canonical checkpoint ladder

2. active `ROADMAP_ADDENDUM_*.md` files from the repo
   Temporary execution overlays when explicitly active

3. `ARCHITECTURE_GUARDRAILS.md` from the repo
   Permanent design-governance source when present

4. local repo / current repo reality
   Implementation source of truth

5. `PROGRESS_TRACKER.md` from the repo
   Short current-position source of truth

6. `PROJECT_INSTRUCTIONS.md` from Project Sources
   Operating interpretation reference

7. `SESSION_WORKFLOW.md` from Project Sources
   Session behavior reference

8. `LEARNING_PACK_STANDARD.md` from Project Sources
   Learning-pack generation reference

9. `M1_SELF_STUDY_PACK.md` from Project Sources
   Default learning-pack style reference

No other source is allowed to define project direction or implementation reality.

Never use as proof of state:
- prior chat memory
- assistant memory
- `/mnt/data`
- old prompts
- old learning packs
- old interim packs
- old notes or exports

---

## Session Interpretation Rule

At session start, the assistant must distinguish between:

- real mismatch
- terminology lag
- tracker formatting lag
- repo naming lag

Only a **real mismatch** should stop execution.

### Real mismatch
A real mismatch exists when:
- the tracker’s current position cannot be mapped cleanly to the roadmap checkpoint ladder
- repo reality shows implementation outside the active milestone or approved checkpoint band
- an active addendum pauses normal progression but execution tries to bypass it
- a proposed next task violates architecture guardrails

### Terminology lag
Terminology lag exists when:
- the roadmap uses checkpoint-ladder naming
- the tracker or repo still uses older prose wording
- both still describe the same technical progression

Terminology lag alone is **not** a stop condition.

### Tracker formatting lag
Tracker formatting lag exists when:
- the tracker still uses narrative checkpoint wording
- but latest completed and next unfinished work can still be mapped cleanly to the roadmap ladder

Tracker formatting lag alone is **not** a stop condition.

### Repo naming lag
Repo naming lag exists when:
- code modules, comments, tests, smoke-test files, or helper names still use older wording
- but technical behavior remains aligned with the roadmap checkpoint sequence

Repo naming lag alone is **not** a stop condition.

---

## Chat and Session Definitions

### Chat
A chat is a conversation container / thread.

### Working session
A working session is an active ASBP execution run.

A new working session begins when:
- a new ASBP chat starts
- work is resumed after an explicit pause / stop / continue later event
- or a previous working run has clearly ended and a new one begins, even inside the same chat

Therefore:
- one chat may contain more than one working session
- a fresh chat always starts a new working session
- resuming inside the same chat may also begin a new working session if re-alignment is required

---

## Session Start Protocol

At the beginning of every working session:

1. read `ROADMAP_CANONICAL.md` from the repo root
2. read active `ROADMAP_ADDENDUM_*.md` files from the repo in numeric order when present
3. read `ARCHITECTURE_GUARDRAILS.md` from the repo when present
4. read `PROGRESS_TRACKER.md` from the repo via GitHub connector
5. verify repo reality when needed against actual code/repo state
6. map tracker wording and repo wording into the roadmap checkpoint ladder when terminology lag exists
7. confirm:
   - current phase
   - current milestone
   - current approved slice family
   - latest completed checkpoint
   - exact next unfinished checkpoint
   - latest verified validation status
   - milestone UAT status
   - repo alignment status
8. if a real mismatch exists:
   - stop
   - state the mismatch clearly
   - resolve it before implementation work begins

Special rule:
- if `ROADMAP_ADDENDUM_02_M5_ARCHITECTURAL_HARDENING.md` is active, do not resume normal Milestone 5 feature expansion before checking its exit condition first

---

## Checkpoint Mapping Workflow

The roadmap checkpoint ladder is the forward execution authority.

The tracker and repo may temporarily use:
- broader milestone prose
- older checkpoint narration
- behavior-oriented wording
- file names or test names that predate checkpoint-ladder terminology

The assistant must map those to the active roadmap checkpoint ladder when possible.

### Mapping behavior
- map by actual technical behavior, not by superficial wording
- use repo reality to confirm what is really implemented
- use the tracker only as the current-position pointer
- use the roadmap as the canonical forward sequence

### If mapping is clean
- continue execution normally
- state the mapped checkpoint clearly
- do not call the situation a mismatch

### If mapping is ambiguous
- stop
- state that checkpoint mapping is ambiguous
- resolve roadmap/tracker normalization before continuing execution

---

## Execution Rules

- execute only the exact next unfinished checkpoint unless explicitly redirected by the user
- stay within the current milestone
- stay within the current approved roadmap checkpoint band
- do not invent ad hoc slices
- do not skip, combine, or jump ahead unless the user explicitly changes direction
- do not reopen completed milestones unless explicitly requested
- do not treat tracker alone as proof of implementation reality
- do not treat memory or prior chat as proof of implementation reality

---

## Repo Reality Rules

- local repo/workspace is the primary source of truth for code
- GitHub connector may be used for read-only repo inspection when needed
- `PROGRESS_TRACKER.md` is maintained outside Project Sources and is read from the repo when session alignment is required
- never rely on `/mnt/data` as proof of live repo state
- if repo reality conflicts with the roadmap checkpoint ladder or tracker mapping, stop and resolve the conflict first
- repo wording may lag behind roadmap terminology without creating a real mismatch

---

## Architecture Guardrail Rule

If `ARCHITECTURE_GUARDRAILS.md` is present:
- CLI remains an adapter only
- new domain behavior must attach through approved core module boundaries
- state/persistence access must go through approved state boundary helpers/modules
- if a proposed slice would bypass those boundaries, pause execution and open a planning checkpoint before coding

---

## Code Change Rules

All proposed changes must be:
- minimal
- targeted
- explicit
- paste-ready for manual local application

Rules:
- do not refactor unrelated code
- do not rewrite full files unless explicitly required
- do not propose speculative cleanup outside the approved checkpoint
- do not claim completion before validation is confirmed

---

## Output Mode Workflow

### Use code blocks for
- next-chat start prompts
- manual patching content
- exact replacement text
- short command blocks

### Use downloadable files for
- `apply.py` or other executable scripts
- zip packs
- generated artifacts intended to live as files

### Never use
- diff patch files
- diff-only patch outputs

---

## Validation Protocol

A checkpoint is not complete until:

1. full test suite passes:
   `python -m pytest -q`

2. exact manual validation passes when applicable

Validation confirms technical correctness.
Validation does not replace milestone UAT.

---

## Milestone UAT Rule

From Milestone 4 onward, milestone completion requires:

1. implementation complete
2. validation complete
3. milestone UAT checkpoint complete
4. milestone closeout complete

Only then may the next milestone begin.

Do not move into the next milestone before the current milestone UAT gate has passed.

---

## Tracker Workflow

`PROGRESS_TRACKER.md` remains short and current-state only.

It may include:
- current phase
- current milestone
- current approved slice family
- latest completed checkpoint
- exact next unfinished checkpoint
- latest verified validation status
- milestone UAT status
- repo alignment status
- short active notes only when needed

It must not become:
- a diary
- a session log
- a reconstructed work history
- a substitute for roadmap direction

Recommended controlled values:

### Milestone UAT status
- `NOT_STARTED_MILESTONE_OPEN`
- `PENDING_CLOSEOUT_WINDOW`
- `IN_PROGRESS`
- `PASSED`
- `FAILED`

### Repo alignment status
- `ALIGNED_VERIFIED`
- `ALIGNED_WITH_TERMINOLOGY_LAG`
- `CHECKPOINT_MAPPING_PENDING`
- `MISMATCH_FOUND`

---

## Learning Pack Workflow

### Final milestone self-study pack
Generate only on explicit user request after:
1. milestone implementation complete
2. validation complete
3. milestone UAT complete
4. milestone closeout complete

### Interim study pack
Generate only on explicit user request when needed for:
- token-pressure carry-forward
- project congestion
- migration to another chat
- migration to another project
- structured continuity before milestone closeout

### Interim-to-final behavior
If an interim study pack already exists for the same milestone:
- do not blindly regenerate the final pack from zero
- treat the final pack as an updated version built from the interim pack plus the later verified milestone closeout state

### Style reference
- follow `LEARNING_PACK_STANDARD.md`
- use `M1_SELF_STUDY_PACK.md` as the default style reference
- do not switch style baselines unless the user explicitly says so

### Learning-pack authority boundary
Learning packs are educational continuity artifacts only.
They may use:
- roadmap direction
- active addenda when relevant
- architecture guardrails when relevant
- repo reality
- tracker anchor state

They must not:
- override roadmap direction
- override repo reality
- become a source of project state

---

## Session-End Actions

When requested:

- do not modify `PROGRESS_TRACKER.md` implicitly
- update it only when explicitly requested by the user
- keep it short and current-state only
- do not turn it into diary history

### Planning checkpoints
Planning checkpoints, checkpoint mapping normalization, and transitional alignment steps do not require automatic tracker updates unless explicitly requested.

---

## Generators

### Generate progress tracker
- read the current `PROGRESS_TRACKER.md`
- apply only verified updates
- return a short current-state tracker
- do not reconstruct diary history
- do not add session storytelling
- if wording lags behind the roadmap ladder, normalize only when explicitly requested

### Update progress tracker
- read the current `PROGRESS_TRACKER.md`
- return only the minimal current-state update needed
- do not reconstruct unchanged sections
- if no verified tracker-worthy change exists, return no update block

### Generate next-chat start prompt
- use:
  - `ROADMAP_CANONICAL.md` from Project Sources
  - active `ROADMAP_ADDENDUM_*.md` files from the repo when present
  - `ARCHITECTURE_GUARDRAILS.md` from the repo when present
  - `PROGRESS_TRACKER.md` from the repo
  - repo reality when needed
- treat roadmap checkpoint naming as canonical even if tracker/repo wording lags
- use this only for a fresh chat
- do not use tracker alone as direction authority

### Continue current chat
- do not generate a next-chat prompt for a simple resume inside the same chat
- instead perform session re-alignment when a new working session begins inside that same chat

### Generate learning pack
- generate only on explicit user request
- follow `LEARNING_PACK_STANDARD.md`
- use roadmap direction + active roadmap addenda when relevant + architecture guardrails when relevant + repo reality + tracker anchor
- use `M1_SELF_STUDY_PACK.md` as the default style reference
- update from an existing interim pack when applicable

---

## Workflow Discipline

This workflow prioritizes:
- determinism over convenience
- roadmap direction over tracker convenience
- checkpoint-ladder clarity over vague slice narration
- repo reality over memory
- validation before completion claims
- milestone discipline over opportunistic drift
- seamless continuity without false mismatch alarms
