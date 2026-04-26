# ASBP Assistant Cleaned Package v3 — Release Notes

## Summary

This version updates the operating pack to use a lighter, more practical branch / pull request / merge strategy.

The old “one slice = one PR” idea has been replaced with:

```text
direct commit only for tiny low-risk corrections
public-surface package = one PR
coherent capability bundle = one PR
milestone closure evidence = one PR
prefer squash merge into main
```

## Updated files

```text
PROJECT_INSTRUCTION_FIELD/MASTER_PROMPT.txt
PROJECT_SOURCES/ASBP_OPERATING_RULES.md
PROJECT_SOURCES/ASBP_BRANCH_PR_MERGE_STRATEGY.md
PROJECT_SOURCES/STARTER_PROMPT.md
README_INSTALL.md
```

## Removed from active operation

```text
LEARNING_PACK_STANDARD.md
M1_SELF_STUDY_PACK.md
```

## Key rule

Bundle by meaning, not by count.

A pull request should be a coherent review boundary, not a mechanical unit created for every tiny slice.
