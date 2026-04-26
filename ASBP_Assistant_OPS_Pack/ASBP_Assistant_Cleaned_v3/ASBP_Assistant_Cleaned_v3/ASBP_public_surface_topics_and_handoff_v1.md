# AI_SYSTEM_BUILDER Public-Surface Final Handoff

## Repository topics

Use these GitHub repository topics:

```text
python
cli
workflow-engine
system-modeling
deterministic-engine
state-management
task-management
project-management
automation
pytest
pydantic
argparse
software-architecture
domain-modeling
developer-tools
test-driven-development
open-source
```

Do not add these yet:

```text
ai-agent
chatgpt
gpt
cqv
gmp
pharma
```

Reason: the repository is currently best represented as a deterministic Python workflow/system-modeling engine. AI/runtime and CQV context exist, but they should not define the public discovery surface until the implementation surface clearly supports that identity.

---

## Final Project handoff prompt

Use this prompt inside the active ChatGPT Project after the public-surface files are approved.

```text
SS

Public-surface handoff.

The following repository public-facing surface artifacts were prepared outside the Project and are approved for controlled implementation:

1. README.md
   - Convert README into an evergreen public project overview.
   - Remove live milestone/status table.
   - Remove manual test-count badge.
   - Remove current “What comes next” roadmap/status section.
   - Keep current-state authority delegated to PROGRESS_TRACKER.md.
   - Keep roadmap authority delegated to ROADMAP_CANONICAL.md.
   - Keep architecture authority delegated to ARCHITECTURE_GUARDRAILS.md.

2. CONTRIBUTING.md
   - Clean Markdown structure.
   - Clarify contribution flow.
   - Clarify public-surface vs behavior/architecture/roadmap changes.
   - Clarify PR and validation expectations.

3. CODE_OF_CONDUCT.md
   - Add as a new public-surface community readiness file.

4. GitHub issue templates
   - Add .github/ISSUE_TEMPLATE/bug_report.md
   - Add .github/ISSUE_TEMPLATE/documentation.md
   - Add .github/ISSUE_TEMPLATE/design_question.md

5. GitHub pull request template
   - Add .github/PULL_REQUEST_TEMPLATE.md

6. Repository topics
   - Apply the approved public discovery topics separately through GitHub repository settings.

Treat this work as public-surface maintenance only.

Do not reinterpret these changes as:
- roadmap changes
- architecture changes
- code behavior changes
- validation rule changes
- milestone scope changes
- implementation checkpoint changes

Do not create a roadmap addendum.

Apply this work through one public-surface PR.

Recommended branch:
docs/public-surface-cleanup

Expected PR title:
docs: clean public repository surface

Do not alter:
- asbp/
- tests/
- ROADMAP_CANONICAL.md
- ARCHITECTURE_GUARDRAILS.md

Only update PROGRESS_TRACKER.md if the project workflow requires a minimal note after implementation. If updated, the note must state that this was public-surface maintenance only and caused no roadmap, architecture, behavior, or validation-rule change.

Use the normal authority model:
- code and tests are implementation truth
- PROGRESS_TRACKER.md is current-state authority
- ROADMAP_CANONICAL.md is roadmap authority
- ARCHITECTURE_GUARDRAILS.md is architecture authority
- README.md is public-facing overview only
- ASBP_BRANCH_PR_MERGE_STRATEGY.md is workflow hygiene only

Task:
Create a controlled implementation plan for applying the approved public-surface changes through one documentation PR.

Expected PR scope:
- README.md
- CONTRIBUTING.md
- CODE_OF_CONDUCT.md
- .github/ISSUE_TEMPLATE/bug_report.md
- .github/ISSUE_TEMPLATE/documentation.md
- .github/ISSUE_TEMPLATE/design_question.md
- .github/PULL_REQUEST_TEMPLATE.md

After implementation, confirm:
- files changed
- no code changed
- no tests changed
- no roadmap changed
- no architecture guardrails changed
- whether PROGRESS_TRACKER.md received a minimal maintenance note
```

---

## Implementation package checklist

Files prepared outside the Project:

```text
README_evergreen_public_surface_v1.md
CONTRIBUTING_public_surface_v1.md
CODE_OF_CONDUCT_public_surface_v1.md
issue_templates_public_surface_v1.zip
pr_template_public_surface_v1.zip
```

Inside the Project, apply them as one controlled documentation PR.
