---
name: new-epic-author
description: Create a new HPE GreenLake epic markdown file using the canonical template. Use when a Product Manager wants to author a new epic in this repository (capabilities or services-intake) so the PR-merge workflow can sync it to Aha! and Jira automatically.
---

# Skill: New Epic Author

You are guiding a Product Manager through creating a new epic markdown file in
this repository. The file is reviewed via PR; on merge, the `sync-aha-epics`
GitHub Actions workflow creates the corresponding Aha! epic in the workspace's
`R-1 Parking lot` release and sets its status to `Approved`. For capabilities
workspaces, an Aha automation rule then forwards it to Jira.

## When to use this skill

Use whenever the user says any of:
- "I want to create a new epic"
- "Author a new epic for <workspace>"
- "Start a PRD/epic in <capability or service-intake folder>"
- "/new-epic"

## Inputs to gather (one round, all at once)

1. **Workspace folder**. Must exist under
   `requirements/capabilities/<folder>` or
   `requirements/services-intake/<folder>`. If the PM is unsure, list the
   available folders by reading the workspace.
2. **Epic title**. Short, capitalized; used as the H1 and as the file slug.
3. **One-line problem statement** — what is the user pain or business gap.

Do not invent these. Ask if any are missing.

## Steps

1. Compute the file slug: lowercase the title, replace non-alphanumerics with
   hyphens, collapse repeats, trim hyphens.
2. Compute the path:
   `requirements/<capabilities|services-intake>/<folder>/epics/<slug>.md`.
   If the file exists, append `-2`, `-3`, ... until a free name is found.
3. Read the canonical template from
   [.github/EPIC_TEMPLATE.md](../../.github/EPIC_TEMPLATE.md) and use it
   verbatim as the file body. Do not reformat or reword section headers.
4. Replace only:
   - The H1 placeholder line with `# <Epic title>`.
   - The placeholder under `**Problem Statement:**` with a one-paragraph draft
     derived from the PM's one-line input.
5. Leave all other sections (Context, Goal, Workflows, Functional
   Requirements, Acceptance Criteria, Dependencies) as the template prompts.
6. Create the file with `create_file`.
7. Tell the PM:
   - Open a feature branch and a PR targeting `main`.
   - The PR check `Validate Epic Template` requires these section markers
     (case-sensitive, exact text):
     - `**Problem Statement:**`
     - `**Goal:**`
     - `**Functional Requirements:**`
     - `**Acceptance Criteria:**`
   - On merge, the Aha epic is created and approved automatically.

## Hard rules

- **Never** modify section markers — they must match `**Section:**` exactly so
  the validator passes and Aha consumes the body verbatim.
- **Never** fill in sections beyond the Problem Statement draft.
- **Never** create a new workspace folder. If the requested folder is not in
  the existing list, ask the PM to confirm or pick an existing one.
- **Never** include placeholder text like `TBD` or `<fill me in>` in the
  Problem Statement — write a concise draft from the PM's input or ask for a
  better summary.
