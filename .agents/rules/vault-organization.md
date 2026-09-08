---
description: Enforces organizational rules for the Obsidian vault, ensuring the Dashboard stays in sync and new notes are properly connected.
---

==================================================
OBSIDIAN VAULT ORGANIZATION & DASHBOARD RULE
==================================================

The Obsidian vault has a central `Dashboard.md` that acts as the main navigation hub and knowledge-map entry point.

The Dashboard must remain synchronized with meaningful changes to the vault.

--------------------------------------------------
1. NEW FILES
--------------------------------------------------

Whenever you create a new Markdown note or other meaningful knowledge file:

1. Determine which subject/category it belongs to.
2. Place it in the appropriate existing folder.
3. Check whether the Dashboard should expose the new note.
4. If the new note represents a meaningful topic, subject, hub, resource, or important study area, add an appropriate Wikilink to the Dashboard.
5. Do not add every tiny temporary/helper file to the Dashboard.
6. Do not create fake or broken Wikilinks.

Example:

If creating:

DSA/04. Bit Manipulation/XOR Patterns.md

and it is a meaningful note, ensure the appropriate Bit Manipulation section of the Dashboard can navigate to it.

--------------------------------------------------
2. NEW FOLDERS / TOPICS
--------------------------------------------------

When creating a new meaningful subject or topic folder:

1. Follow the existing vault naming conventions.
2. Determine where it belongs in the existing hierarchy.
3. Update the relevant parent/index note if one exists.
4. Update Dashboard.md if the new area is significant enough to be a top-level or important navigation category.
5. Do not clutter Dashboard.md with every minor subfolder.

--------------------------------------------------
3. NEW NOTES MUST BE CONNECTED
--------------------------------------------------

A new meaningful note should not become an isolated orphan.

When appropriate:

- link the new note to its parent/topic note;
- link related concepts using `[[Wikilinks]]`;
- add links from relevant hub/index notes;
- add a `[[Dashboard]]` backlink when appropriate for major hub/navigation notes.

Do not manufacture relationships merely to increase backlink count.

Links must represent genuine conceptual or navigational relationships.

--------------------------------------------------
4. DASHBOARD MAINTENANCE
--------------------------------------------------

Whenever a meaningful structural change is made to the vault, inspect:

Dashboard.md

and determine whether it needs updating.

Update it when:

- a new major subject is added;
- a new important DSA topic is added;
- a new major project/area is added;
- an important resource section is added;
- an existing important note is renamed or moved;
- an important section is removed;
- the hierarchy of the vault changes.

Do NOT rewrite the entire Dashboard for every small change.

Make the smallest necessary update.

--------------------------------------------------
5. RENAMING OR MOVING FILES
--------------------------------------------------

If a file or folder is renamed or moved:

1. Search the vault for references to the old path/name.
2. Update affected Wikilinks where necessary.
3. Update Dashboard.md if the moved/renamed item appears there.
4. Check relevant parent/index notes.
5. Ensure no broken links are introduced.

Never leave the Dashboard pointing to an old filename.

--------------------------------------------------
6. DELETING FILES
--------------------------------------------------

Before deleting a meaningful note:

1. Search for references to it.
2. Remove or update obsolete Dashboard links.
3. Update relevant parent/index notes.
4. Check for backlinks that would become invalid.

Do not delete files unless the current task explicitly requires deletion.

--------------------------------------------------
7. DUPLICATE PREVENTION
--------------------------------------------------

Before creating a new note:

1. Search the vault for existing notes covering the same topic.
2. If an appropriate note already exists, update or extend it instead of creating a duplicate.
3. Follow existing naming conventions.

Do not create multiple notes with nearly identical purposes.

--------------------------------------------------
8. DASHBOARD AS A HUB
--------------------------------------------------

Treat Dashboard.md as the central navigation hub.

Its structure should remain approximately:

Dashboard
├── Major Subjects
├── DSA
│   └── DSA Topics
├── Programming / Development
├── AI & ML
├── Daily Notes
└── Resources

However, always use the ACTUAL current vault structure rather than assuming this exact hierarchy.

The Dashboard must never contain links to files that do not exist.

--------------------------------------------------
9. HUB NOTES
--------------------------------------------------

Important folders/topics should have appropriate hub or index notes where useful.

For example:

Dashboard
↓
DSA
↓
04. Bit Manipulation
↓
Bit Manipulation
↓
Bitwise Operators / Bit Tricks / XOR Patterns / Problems

Use the existing vault structure rather than creating unnecessary hub notes.

--------------------------------------------------
10. SOURCE / RAW MATERIAL
--------------------------------------------------

Files placed inside source/reference areas such as PDFs, raw class material, or imported resources do not automatically need to appear individually on Dashboard.md.

Only expose them when they are meaningful resources for navigation.

If source material is converted into study notes, connect the resulting notes to the appropriate subject/topic.

--------------------------------------------------
11. PRESERVE EXISTING STRUCTURE
--------------------------------------------------

Do NOT:

- reorganize the entire vault unnecessarily;
- rename files without a reason;
- create unnecessary folders;
- delete useful notes;
- add fake links;
- add unnecessary Dashboard entries;
- create excessive atomic notes;
- modify unrelated areas of the vault.

Prefer minimal, targeted changes.

--------------------------------------------------
12. FINAL VERIFICATION
--------------------------------------------------

After any structural change:

1. Verify newly created Wikilinks.
2. Verify Dashboard links.
3. Check for obvious broken references.
4. Confirm the new note is connected to its relevant parent/topic.
5. Confirm Dashboard.md accurately represents the important current structure.
6. Avoid modifying unrelated files.

The goal is to keep the vault continuously organized and connected without requiring manual Dashboard maintenance.

--------------------------------------------------
13. PRIORITY
--------------------------------------------------

This rule should be treated as a persistent organizational rule for future vault operations.

Whenever another task conflicts with this rule, preserve the user's explicit current task requirements while maintaining the vault's organization wherever possible.

The Dashboard should evolve naturally as the vault grows.

Do not blindly update it after every file operation.

Use judgment based on whether the change is meaningful to navigation or knowledge structure.
