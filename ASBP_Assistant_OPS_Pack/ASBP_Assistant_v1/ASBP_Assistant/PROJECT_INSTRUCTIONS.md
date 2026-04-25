---
doc_type: project_instructions
canonical_name: PROJECT_INSTRUCTIONS
status: ACTIVE_APPROVED
governs_execution: true
document_state_mode: operation_pack_governance
authority: project_operation_reference
---

# PROJECT_INSTRUCTIONS

## Purpose

This operation-pack file defines the operating rules for the ASBP ChatGPT Project.

The system is designed to:
- progress step-by-step
- avoid drift
- avoid duplicate sources of truth
- keep direction, implementation reality, and current state clearly separated
- preserve seamless continuity across chats, migrations, and Project workspaces
- prevent false mismatch alarms caused by terminology lag between roadmap, tracker, and repo wording
- ensure every claimed completion is validated before it is accepted
- preserve stable architectural boundaries for future AI and UI layers

---

## Canonical storage rule

`ROADMAP_CANONICAL.md` belongs in the **repo root** as the canonical direction file for the ASBP project.

It is expected to exist in the repository.

Project Sources should not hold an authoritative duplicate of the roadmap.
If an older Project-Sources copy still exists during migration, it must be treated as non-authoritative convenience only and removed when practical.

Reason:
- the roadmap is now a master governance document for the project
- the repository is already the home of implementation truth, tracker state, guardrails, addenda, code, tests, and repo evidence
- keeping the authoritative roadmap in the repo removes split-authority risk

---

## Authority Model

### Direction source of truth
- `ROADMAP_CANONICAL.md` from the repo root

Defines:
- phase order
- milestone order
- milestone intent
- milestone boundaries
- canonical checkpoint ladder inside each milestone
- allowed work inside each checkpoint or checkpoint band
- milestone closeout logic
- milestone UAT gate requirements from Milestone 4 onward

### Direction overlay source of truth
- active `ROADMAP_ADDENDUM_*.md` files from the repo

Defines:
- authorized corrective overlays
- temporary or transitional execution overlays
- milestone-specific detours that remain subordinate to the canonical roadmap
- exit conditions for returning to normal checkpoint progression

Rules:
- read active roadmap addenda in numeric order
- treat them as binding only within their declared scope
- once an addendum exit condition is satisfied, normal roadmap authority resumes unless another active addendum still applies

### Permanent design governance source
- `ARCHITECTURE_GUARDRAILS.md` from the repo when present

Defines:
- stable adapter/core boundary rules
- approved attachment-point discipline for future slices
- permanent architectural constraints that remain active after temporary addenda end

Rules:
- this file does not replace the roadmap
- it does not define milestone direction
- it does define permanent design boundaries once created
- future slices must respect it unless the user explicitly changes governance

### Implementation source of truth
- local repo / workspace
- current repo reality when checked against actual code

Defines:
- what is actually implemented
- what code, tests, commands, helpers, and contracts exist now
- what naming and wording are actually present in the repo today

### Current-state source of truth
- `PROGRESS_TRACKER.md` from the repo

Defines only:
- current phase
- current milestone
- current approved slice family
- latest completed checkpoint
- exact next unfinished checkpoint
- latest verified validation status
- milestone UAT status
- repo alignment status

### Tracker access policy
- `PROGRESS_TRACKER.md` is maintained outside Project Sources
- it is read from the repository via GitHub connector when session alignment is required
- it must not be duplicated inside Project Sources

### Non-authoritative sources
The following must never be treated as proof of project state:
- prior chat memory
- assistant memory
- `/mnt/data`
- old generated notes
- old prompts
- old learning packs
- old interim packs

---

## Core Interpretation Rule

The assistant must distinguish between:

1. **real mismatch**
2. **terminology lag**
3. **tracker formatting lag**
4. **repo naming lag**

These are not the same thing.

### Real mismatch
A real mismatch exists only when one or more of the following is true:
- the roadmap says execution should be in one milestone or checkpoint band, but repo reality clearly shows another
- the tracker points to a next checkpoint that does not fit the roadmap checkpoint ladder
- an active addendum says normal progression is paused, but execution tries to continue as if it were not paused
- architecture guardrails would be violated by the proposed next work

### Terminology lag
Terminology lag exists when:
- the roadmap uses the new canonical checkpoint-ladder naming
- the tracker or repo still uses older narrative wording
- both still refer to the same actual implementation sequence

Terminology lag alone is **not** a mismatch.

### Tracker formatting lag
Tracker formatting lag exists when:
- the tracker still expresses progress in older prose style
- but the actual current checkpoint can still be mapped cleanly to the roadmap ladder

Tracker formatting lag alone is **not** a mismatch.

### Repo naming lag
Repo naming lag exists when:
- code, comments, helper names, smoke-test files, or test names do not yet use the new checkpoint labels
- but the implemented behavior is still technically aligned to the roadmap checkpoint sequence

Repo naming lag alone is **not** a mismatch.

### Required behavior
If the assistant finds terminology lag, tracker formatting lag, or repo naming lag without a real direction conflict:
- do not stop work as if a mismatch exists
- do not falsely claim inconsistency
- explicitly state that the issue is wording lag, not execution drift
- continue using the roadmap checkpoint ladder as the forward execution authority
- use repo reality to verify technical truth
- use the tracker as the current-position pointer
- propose tracker/document normalization only when explicitly requested

---

## Governance Read Order

At session alignment time, resolve authority in this order:

1. `ROADMAP_CANONICAL.md` from the repo root
2. active `ROADMAP_ADDENDUM_*.md` files from the repo in numeric order
3. `ARCHITECTURE_GUARDRAILS.md` from the repo when present
4. local repo / current repo reality
5. `PROGRESS_TRACKER.md` from the repo
6. `PROJECT_INSTRUCTIONS.md` from Project Sources
7. `SESSION_WORKFLOW.md` from Project Sources
8. `LEARNING_PACK_STANDARD.md` from Project Sources
9. `M1_SELF_STUDY_PACK.md` from Project Sources as style reference only

Interpretation:
- roadmap defines direction and canonical checkpoint ladder
- active addenda overlay direction within authorized scope
- architecture guardrails define permanent design boundaries when present
- repo reality defines implementation truth
- tracker defines current position only

---

## File Roles

### ROADMAP_CANONICAL.md
- stored in the repo root
- fixed unless project direction is intentionally changed
- defines structure, milestone boundaries, and canonical checkpoint ladders
- does not record session history
- does not claim live current position
- must be updated before executing any new slice that does not clearly fit a declared milestone checkpoint or checkpoint band
- if a legacy Project-Sources copy still exists during migration, it is non-authoritative and should not be read as direction proof

### ROADMAP_ADDENDUM_*.md
- stored in the repo
- subordinate roadmap overlays
- used only when corrective or transitional direction is needed
- may pause normal checkpoint progression within a milestone
- must include scope and exit condition
- must not silently become permanent design law

### ARCHITECTURE_GUARDRAILS.md
- stored in the repo
- fixed governance/reference file once introduced
- defines permanent adapter/core boundary rules
- protects future AI/UI attachment readiness
- does not define milestone order or current-state progress
- must be treated as one of the governance documents during design and refactor decisions

### PROGRESS_TRACKER.md
- stored in the repo
- short current-state tracker only
- not a session diary
- updated only when explicitly requested
- must not become a historical narrative log
- may temporarily lag in wording relative to the roadmap as long as the actual checkpoint mapping remains clear

### PROJECT_INSTRUCTIONS.md
- stored in Project Sources
- fixed operation-pack reference file
- defines operating rules, file responsibilities, interpretation rules, and generator behavior
- supports the master prompt but does not replace it

### MASTER_PROMPT.txt
- stored in Project Sources
- runtime control prompt for the ChatGPT Project instruction field
- short, high-priority, execution-oriented
- controls session-start behavior and execution discipline
- must remain consistent with this file

### SESSION_WORKFLOW.md
- stored in Project Sources
- fixed operation-pack workflow reference
- describes session behavior in more detail
- remains subordinate to roadmap authority, active addenda, architecture guardrails, repo reality, and tracker policy
- should not contradict this file on startup interpretation

### LEARNING_PACK_STANDARD.md
- stored in Project Sources
- fixed operation-pack learning standard reference
- defines when learning packs may be generated
- defines interim vs final pack rules
- defines required pack structure
- does not become a source of project state

### M1_SELF_STUDY_PACK.md
- stored in Project Sources
- fixed approved default style reference
- used as the baseline learning-pack model unless the user explicitly declares a different approved style baseline
- is a style reference, not a source of project state

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
- a fresh chat always starts a new session
- resuming later inside the same chat may also start a new session if re-alignment is required

---

## Session Start Rules

At the start of a working session:

1. read `ROADMAP_CANONICAL.md` from the repo root
2. read active `ROADMAP_ADDENDUM_*.md` files from the repo in numeric order when present
3. read `ARCHITECTURE_GUARDRAILS.md` from the repo when present
4. read `PROGRESS_TRACKER.md` from the repo via GitHub connector
5. verify repo reality when needed against actual code/repo state
6. map tracker wording and repo wording to the roadmap checkpoint ladder if terminology lag exists
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
   - resolve mismatch first
   - do not proceed with implementation work

Special rule:
- if `ROADMAP_ADDENDUM_02_M5_ARCHITECTURAL_HARDENING.md` is active, do not resume normal Milestone 5 feature expansion before checking its exit condition first

---

## Checkpoint Mapping Policy

The roadmap checkpoint ladder is the forward execution authority.

The tracker and repo may temporarily use:
- broader milestone prose
- older checkpoint narration
- behavior-oriented wording
- file/test names that predate the ladder terminology

The assistant must map those into the active roadmap ladder when possible.

Examples:
- a tracker line such as “first deterministic task-to-work-package association write surface” may map to a canonical checkpoint inside `M5.6A`
- a tracker line such as “inverse work-package list visibility surface” may map to a canonical checkpoint inside `M5.4C` or another defined read/list checkpoint band depending on the approved roadmap wording
- this mapping must be based on actual technical behavior, not guesswork

If clean mapping is not possible:
- stop
- state that checkpoint mapping is ambiguous
- request or prepare roadmap/tracker normalization before further execution

---

## Execution Rules

- work only on the exact next checkpoint unless the user explicitly changes direction
- stay inside the current milestone
- stay inside the current approved roadmap checkpoint band
- do not invent ad hoc slices
- do not infer implementation reality from tracker alone
- do not infer implementation reality from memory or prior chat
- local repo/workspace is the primary source of truth for code
- GitHub connector may be used for read-only repo inspection when needed
- never rely on `/mnt/data` as proof of live repo state
- if a proposed task does not clearly fit the approved roadmap checkpoint ladder, stop and update the roadmap first
- if an active roadmap addendum is present, obey it within its declared scope until its exit condition is satisfied
- if `ARCHITECTURE_GUARDRAILS.md` is present, future design and refactor decisions must attach through its approved boundaries unless the user explicitly changes governance

---

## Milestone Discipline

- never skip checkpoints
- never reopen completed milestones unless the user explicitly asks to do so
- never jump into another milestone because it feels adjacent
- never begin Milestone 5 work while Milestone 4 is still open
- from Milestone 4 onward, no milestone may be closed without passing its milestone UAT gate
- from Milestone 4 onward, the next milestone may not begin until:
  1. implementation is complete
  2. validation passes
  3. milestone UAT passes
  4. milestone closeout is complete

---

## Code Change Rules

All proposed code changes must be:
- explicit
- minimal
- targeted
- paste-ready for manual local application

Rules:
- no unrelated refactors
- no speculative cleanup outside the approved checkpoint
- no full-file rewrites unless explicitly required
- no completion claims until validation is confirmed

---

## Output Mode Policy

### Use code blocks for
- next-chat start prompts
- manual patching content
- exact replacement text
- short command blocks
- any paste-ready text the user will apply manually

### Use downloadable files for
- `apply.py` or any executable script
- zip packs
- full artifacts intended to be kept as files
- generated files that are impractical as direct manual paste

### Do not use
- diff patch files
- diff-only patch outputs
- any patch format that requires apply/patch tooling from a diff

Reason:
- diff patch files are not part of the approved ASBP operating workflow

---

## Validation Rules

A checkpoint is NOT complete until:

1. full test suite passes:
   `python -m pytest -q`

2. exact manual verification passes, if applicable

Validation confirms technical correctness.
Validation alone does not replace milestone UAT.

---

## Tracker Policy

`PROGRESS_TRACKER.md` must remain short and current-state only.

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
- a step-by-step narrative
- a reconstructed session history
- a substitute for roadmap direction

Allowed short active notes may include:
- whether a roadmap addendum is currently active
- whether `ARCHITECTURE_GUARDRAILS.md` is now active governance
- whether normal slicing is paused by an active overlay
- whether terminology mapping is still transitional

### Controlled status values

Recommended milestone UAT status values:
- `NOT_STARTED_MILESTONE_OPEN`
- `PENDING_CLOSEOUT_WINDOW`
- `IN_PROGRESS`
- `PASSED`
- `FAILED`

Recommended repo alignment status values:
- `ALIGNED_VERIFIED`
- `ALIGNED_WITH_TERMINOLOGY_LAG`
- `CHECKPOINT_MAPPING_PENDING`
- `MISMATCH_FOUND`

---

## Learning Pack Policy

### Final milestone self-study pack
A final milestone self-study pack may be generated only on explicit user request after:
1. milestone implementation is complete
2. validation is complete
3. milestone UAT is complete
4. milestone closeout is complete

This is a post-closeout educational artifact.
It is not a gate for moving to the next milestone.

### Interim study pack
An interim study pack may be generated on explicit user request before milestone closeout when needed for:
- token-pressure carry-forward
- project congestion
- migration to another project
- migration to another chat
- structured continuity before a milestone is fully closed

### Interim-to-final rule
If an interim study pack already exists for the same milestone, the later final milestone pack must be treated as an updated version, not as a blind regeneration from scratch.

### Style reference
- `M1_SELF_STUDY_PACK.md` is the approved default style reference baseline
- `LEARNING_PACK_STANDARD.md` defines the required generation structure
- use M1 style as the default model unless the user explicitly declares a new style reference

### Milestone 4 special rule
Milestone 4 learning-pack generation is special-cased because its implementation history may be distributed across more than one chat or project context.
A final M4 pack should not be generated casually.
Use:
- interim pack generation when needed for migration/continuity
- explicit user scoping before attempting a final M4 pack

### Learning-pack authority
Learning packs:
- may use roadmap direction
- may use active roadmap addenda when relevant
- may use architecture guardrails when relevant
- may use repo reality
- may use tracker state as an anchor
- must never override roadmap direction or repo reality
- must never become a source of project state

---

## Generator Rules

### Generate next-chat start prompt
- use:
  - `ROADMAP_CANONICAL.md` from the repo root
  - active `ROADMAP_ADDENDUM_*.md` files from the repo when present
  - `ARCHITECTURE_GUARDRAILS.md` from the repo when present
  - `PROGRESS_TRACKER.md` from the repo
  - repo reality when needed
- treat roadmap ladder naming as canonical even when repo/tracker wording lags
- use this only when starting a fresh chat
- do not use tracker alone as direction authority

### Continue current chat
- do not generate a next-chat prompt for simple resume inside the same chat
- instead perform session re-alignment when a new working session begins inside that same chat

### Generate progress tracker
- read the current `PROGRESS_TRACKER.md`
- return a short current-state tracker only
- apply only verified updates
- do not reconstruct diary history
- do not add session storytelling
- when wording lag exists, normalize the tracker minimally and only when explicitly requested

### Update progress tracker
- read the current `PROGRESS_TRACKER.md`
- return only the minimal current-state update needed
- do not reconstruct unchanged sections
- if no tracker-worthy verified change exists, return no update block

### Generate learning pack
- generate only on explicit user request
- follow `LEARNING_PACK_STANDARD.md`
- use roadmap direction + active roadmap addenda when relevant + architecture guardrails when relevant + repo reality + tracker anchor
- use `M1_SELF_STUDY_PACK.md` as the default style reference
- when an interim pack exists, update from it instead of regenerating blindly
- for Milestone 4, require explicit user scoping before attempting a final milestone pack

---

## Inconsistency Rule

If any inconsistency exists between:
- `ROADMAP_CANONICAL.md` from Project Sources
- active `ROADMAP_ADDENDUM_*.md` files from the repo
- `ARCHITECTURE_GUARDRAILS.md` from the repo when present
- `PROGRESS_TRACKER.md` from the repo
- repo reality

then the assistant must:
1. distinguish real mismatch from terminology lag
2. stop only if a real mismatch exists
3. state the mismatch clearly
4. resolve it before continuing

---

## Design Principles

This system prioritizes:
- determinism over flexibility
- clarity over verbosity
- roadmap direction over tracker convenience
- active overlay direction over drift when an addendum is active
- architecture guardrails over convenience once they are established
- repo reality over memory
- validation before completion claims
- continuity without false mismatch alarms
- current-state tracking without diary-style growth
