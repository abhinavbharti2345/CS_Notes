# Obsidian Vault Agent Instructions

This is an Obsidian vault.

Before modifying the vault, read the relevant rules in:

.agent/rules/

Important rules:
- Follow all applicable rules in .agent/rules/.
- Preserve existing Obsidian Markdown and YAML frontmatter.
- Use [[Wiki Links]] for internal links.
- Do not delete files unless explicitly instructed.
- Do not make large structural changes without approval.
- When creating or substantially modifying notes, check whether the dashboard/MOCs need updating.
- Keep the vault's existing organization and naming conventions.

## Rule files

Read these when relevant:

.agent/rules/vault.md
.agent/rules/notes.md
.agent/rules/dashboard.md
.agent/rules/graph.md


If a rule conflicts with an explicit user instruction, follow the user's instruction.


## Critical instruction

Always follow the user's CURRENT request literally.

Do not invent a project, product, task, or objective that the user did not mention.

If the user asks to READ, ANALYZE, REVIEW, SUMMARIZE, or EXPLAIN files:
- Read the requested files/folders.
- Do not modify anything.
- Do not create files.
- Do not create todos unless explicitly requested.
- Do not ask unnecessary clarification questions if the requested files are accessible.

## Read-only requests

When the user says:
- "read"
- "summarize"
- "tell me about"
- "analyze"
- "review"
- "brief me"

treat the task as READ-ONLY.

Do NOT:
- create files
- edit files
- rename files
- move files
- delete files
- update dashboards
- update MOCs
- modify metadata
- create tasks

unless the user explicitly asks for those actions.

## Obsidian

Use the existing vault structure.
Use [[Wiki Links]] when discussing existing notes, but do not modify notes merely to add links.