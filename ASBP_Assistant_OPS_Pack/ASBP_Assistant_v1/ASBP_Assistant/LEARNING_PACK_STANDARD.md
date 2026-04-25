# LEARNING_PACK_STANDARD

## Purpose

Define the canonical generation standard for ASBP self-study / learning packs.

This file controls:
- when a learning pack may be generated
- what sources are allowed
- how interim and final packs differ
- what structure the pack must follow
- how style must be aligned with the approved baseline

Learning packs are educational artifacts.
They are not execution checkpoints.
They are not sources of project state.

---

## Authority Boundary

Learning packs may use:
1. `ROADMAP_CANONICAL.md` for milestone direction and boundaries
2. repo reality for verified implementation truth
3. `PROGRESS_TRACKER.md` as a short state anchor
4. an existing interim pack for continuity when applicable
5. `M1_SELF_STUDY_PACK.md` as the default approved style reference

Learning packs must never:
- override roadmap direction
- override repo reality
- override tracker state
- become a source of project state
- silently invent milestone scope

---

## Eligibility Rules

### Final milestone self-study pack
A final milestone self-study pack may be generated only on explicit user request after:
1. milestone implementation is complete
2. validation is complete
3. milestone UAT is complete
4. milestone closeout is complete

This is a post-closeout educational artifact.

### Interim study pack
An interim study pack may be generated on explicit user request before milestone closeout when needed for:
- token-pressure carry-forward
- project congestion
- migration to another project
- migration to another chat
- structured continuity before milestone closeout
- preserving learning context before a handoff

### Interim-to-final rule
If an interim pack already exists for the same milestone:
- the later final pack must be treated as an updated version
- do not regenerate blindly from zero
- preserve useful structure from the interim pack
- replace stale assumptions with later verified milestone reality

---

## Milestone 4 Special Rule

Milestone 4 may span multiple chats, migrations, or project contexts.

Therefore:
- interim study packs are allowed when needed
- a final M4 learning pack must not be generated casually
- final M4 pack generation requires explicit user scoping first
- the user may choose whether M4 is handled as one full milestone pack or as a scoped sub-pack approach

---

## Naming Convention

### Final pack
`M#_SELF_STUDY_PACK.md`

Examples:
- `M1_SELF_STUDY_PACK.md`
- `M5_SELF_STUDY_PACK.md`

### Interim pack
`M#_INTERIM_STUDY_PACK.md`

Examples:
- `M4_INTERIM_STUDY_PACK.md`
- `M7_INTERIM_STUDY_PACK.md`

### Updated final from interim
Use the standard final milestone file name unless the user explicitly asks for versioning.

Optional versioning if needed:
- `M4_SELF_STUDY_PACK_v1.md`
- `M4_SELF_STUDY_PACK_v2.md`

---

## Output Mode

Learning packs are full artifacts and must be returned as downloadable files.

Do not return a full learning pack as:
- a diff patch
- a diff-only output
- a long raw response intended for manual assembly

If the user asks for smaller reusable text components related to learning packs, those may be returned in code blocks only when they are clearly paste-ready fragments rather than full artifact files.

---

## Default Style Reference

### Approved baseline
- `M1_SELF_STUDY_PACK.md`

Use M1 as the default style reference unless the user explicitly declares a new approved style baseline.

This means:
- copy the learning philosophy
- copy the section logic
- copy the density and tone balance
- copy the active-learning shape

Do not:
- copy milestone-specific content from M1
- force irrelevant M1 technical topics into other milestones
- imitate wording blindly when milestone content demands a different explanation

---

## Required Pack Structure

Every milestone learning pack should follow this high-level order unless the user explicitly requests a variation:

1. **What this pack is**
2. **How to use this pack**
3. **Mastery Map**
4. **Self-Study Journey**
5. **Core Vocabulary**
6. **Milestone Story / clean narrative**
7. **Deep Reference Booklet**
8. **Active Recall + Drills**
9. **Final Mastery Checklist**

This order is the canonical default structure.

---

## Section Intent

### 1) What this pack is
Explain:
- what the pack is for
- what mastery looks like
- how the pack should help the user learn actively rather than passively read

### 2) How to use this pack
Explain:
- learning mode
- revision mode
- recommended reading order
- how to use recall before rereading code

### 3) Mastery Map
Define the layers or dimensions of understanding required for the milestone.

The mastery map should tell the user exactly what they should be able to explain by the end.

### 4) Self-Study Journey
Walk through the milestone learning path from big picture to detail.

It should help the user understand:
- what the milestone built
- why it exists
- how the control flow works
- what design choices matter
- what refactors or structural changes matter

### 5) Core Vocabulary
Define milestone vocabulary in plain English.

The goal is to eliminate fake familiarity and force real understanding of terms.

### 6) Milestone Story / clean narrative
Provide one coherent narrative of the milestone.

This section should let the user explain the milestone to another person without depending on fragmented notes.

### 7) Deep Reference Booklet
This is the detailed technical core.

It may include:
- file inventory
- walkthroughs
- source explanations
- architecture diagrams
- relationship tables
- behavior matrices
- rationale summaries
- pitfalls and alternatives
- annotated code explanations when appropriate

This section should be as deep as necessary, but still structured for learning, not just dumping information.

### 8) Active Recall + Drills
Include:
- section recall prompts
- mini-drills
- explain-this-line prompts
- reconstruction prompts
- compare/contrast prompts
- failure diagnosis prompts when relevant

### 9) Final Mastery Checklist
Close with a checklist the user can use to decide whether they truly understand the milestone.

---

## Content Rules

- use only verified milestone scope
- stay inside the milestone boundary
- do not pull content from future milestones unless clearly labeled as preview only
- do not fabricate implementation details
- do not rely on memory when repo reality is required
- do not let educational flow distort technical truth
- keep explanations concrete, layered, and teachable
- prioritize understanding over verbosity

---

## Source Use Rules

When generating a learning pack:
1. read the roadmap for milestone intent and boundaries
2. inspect repo reality for actual implementation truth
3. read the tracker for current state anchor only
4. use an interim pack if updating from one
5. use M1 as style reference unless the user explicitly changes the style baseline

If any contradiction exists between educational notes and repo reality:
- repo reality wins
- roadmap direction still governs intended milestone boundary

---

## Acceptance Criteria

A learning pack is acceptable only if:
- it matches verified milestone reality
- it respects milestone boundaries
- it follows the approved section logic unless the user requested a different structure
- it teaches actively rather than describing passively
- it can serve as a real self-study artifact, not just a summary
- it does not become a substitute for tracker or roadmap state

---

## Deferred Flexibility

The user may later choose to introduce:
- alternate style baselines
- milestone-family specific pack shapes
- scoped sub-pack structures for unusually large milestones
- versioned study pack evolution

Unless explicitly changed later, this file remains the default canonical learning-pack standard.
