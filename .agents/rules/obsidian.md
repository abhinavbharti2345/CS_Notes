---
trigger: always_on
---

# Obsidian CS Knowledge Vault Rules

## Purpose

This vault is a **long-term Computer Science knowledge base and knowledge graph**.

Organize knowledge for **understanding, relationships, discoverability, and future reuse** — NOT primarily for exams, viva, courses, or memorization.

The vault should behave like a **connected personal CS textbook**.

---

## 1. Inspect Before Adding

Before creating or modifying anything:

1. Inspect the existing vault structure.
2. Search for related notes.
3. Find existing concepts that may already contain the information.
4. Identify relevant MOCs/README notes.
5. Identify prerequisites, dependencies, related concepts, and applications.

**Never blindly create a new note.**

Prefer updating/extending an existing note over creating duplicates.

---

## 2. Organize by Knowledge, Not Source

Organize around **concepts and domains**, not where the information came from.

Sources may include:

* Classes
* Courses
* Books
* Documentation
* Tutorials
* Videos
* Articles
* Projects
* Conversations
* Personal discoveries

A source is NOT automatically a folder.

For example, don't create:

```text
Class 1/Notes.md
Class 2/Notes.md
```

Instead integrate the concepts into the existing CS structure.

Preserve source information when useful using a small `Source` section or frontmatter.

---

## 3. Universal CS Structure

The vault should support any Computer Science domain, including:

```text
Computer Science/
├── Programming/
├── Data Structures & Algorithms/
├── Computer Architecture/
├── Operating Systems/
├── Networking/
├── Databases/
├── Distributed Systems/
├── Software Engineering/
├── System Design/
├── Web Development/
├── Backend/
├── Frontend/
├── DevOps/
├── Cloud/
├── Security/
├── Artificial Intelligence/
├── Machine Learning/
├── Theory/
├── Mathematics/
├── Tools & Technologies/
├── Projects/
└── Practical Knowledge/
```

This is a guideline, NOT a requirement to create every folder immediately.

Create structure organically. Do not create empty folders unnecessarily.

---

## 4. Automatically Determine Knowledge Type

For every new piece of information, determine what it represents.

Possible types include:

* Concept
* Principle
* Theory
* Algorithm
* Data structure
* Language feature
* API
* Library
* Framework
* Tool
* Protocol
* Architecture
* Design pattern
* System
* Workflow
* Project
* Implementation
* Debugging knowledge
* Problem/solution
* Best practice
* Trade-off
* Comparison
* Reference

These are examples, not rigid categories.

Choose the most natural representation.

---

## 5. Adaptive Note Structure

Do NOT force every note into one template.

Choose the structure based on the knowledge.

### Concept

```markdown
# Concept

## What is it?
## Why does it matter?
## How does it work?
## Example
## Related
```

### Algorithm

```markdown
# Algorithm

## Problem
## Idea
## How It Works
## Example
## Complexity
## Implementation
## Related
```

### Technology

```markdown
# Technology

## What is it?
## Architecture
## Core Concepts
## Usage
## Configuration
## Trade-offs
## Related
```

### Debugging / Problem

```markdown
# Problem

## Symptoms
## Cause
## Diagnosis
## Solution
## Why It Happened
## Related
```

### Project

```markdown
# Project

## Goal
## Architecture
## Technologies
## Implementation
## Design Decisions
## Problems
## Lessons
## Related Concepts
```

These are guidelines, not mandatory templates.

**Optimize the note for understanding the knowledge.**

---

## 6. One Canonical Note Per Concept

Avoid duplicate notes representing the same concept.

For example, don't create:

```text
TCP.md
TCP Protocol.md
TCP Networking.md
Transmission Control Protocol.md
```

if they represent the same knowledge.

Create one canonical note:

```text
TCP.md
```

Then link to it from everywhere else.

If duplicates already exist, merge/reconcile them and update their wikilinks.

---

## 7. Use Obsidian Wikilinks

Internal knowledge connections MUST use Obsidian wikilinks.

Use:

```markdown
[[TCP]]
[[HTTP]]
[[Operating Systems]]
[[Event Loop]]
```

When useful:

```markdown
[[TCP#Three-Way Handshake]]
```

Do not use ordinary Markdown links for internal vault concepts.

---

## 8. Build Meaningful Relationships

When adding a concept, determine its meaningful relationships.

Consider:

* Prerequisites
* Dependencies
* Parent concepts
* Child concepts
* Related concepts
* Alternatives
* Applications
* Technologies that implement it
* Systems that use it
* Concepts it enables

Example:

```markdown
## Prerequisites

- [[IP]]
- [[Computer Networks]]

## Related

- [[UDP]]
- [[HTTP]]

## Used By

- [[Web Applications]]
```

Do not add links artificially just to increase graph density.

---

## 9. Think in Graphs, Not Files

For every new piece of knowledge ask:

> What is this?
> Where does it belong?
> What does it depend on?
> What depends on it?
> What does it relate to?
> Where is it used?

For example:

```text
HTTP
├── uses → TCP
├── related → HTTPS
├── used by → REST APIs
└── implemented by → Web Servers
```

Represent meaningful relationships using wikilinks.

---

## 10. Maintain MOCs / README Notes

Major domains should have MOCs/README notes.

Example:

```markdown
# Networking

## Core Concepts

- [[OSI Model]]
- [[TCP]]
- [[UDP]]
- [[IP]]
- [[DNS]]

## Protocols

- [[HTTP]]
- [[HTTPS]]
- [[SSH]]

## Related Areas

- [[Operating Systems]]
- [[Distributed Systems]]
- [[Security]]
```

MOCs are **maps**, not copies of the actual knowledge.

When adding an important concept, update the relevant MOC.

---

## 11. Connect Across Domains

Do not allow domains to become isolated.

CS concepts naturally cross boundaries.

Examples:

```text
Operating Systems ↔ Networking
Networking ↔ Distributed Systems
Databases ↔ Backend
Backend ↔ System Design
Security ↔ Networking
AI ↔ Mathematics
```

When a real relationship exists, link the concepts.

---

## 12. Projects and Practical Knowledge

Projects should connect practical work to underlying CS concepts.

Example:

```text
Projects/ShopKart/
```

can link to:

```markdown
[[Node.js]]
[[Express.js]]
[[MongoDB]]
[[REST APIs]]
[[Authentication]]
```

The vault should also preserve useful practical knowledge such as:

* Debugging discoveries
* Design decisions
* Trade-offs
* Failure modes
* Configuration knowledge
* Performance observations
* Security considerations
* Lessons learned

Connect these back to reusable concepts whenever appropriate.

---

## 13. Temporary vs Permanent Knowledge

Not everything should become a permanent concept note.

Determine whether incoming information is:

### Permanent knowledge

Integrate into the CS knowledge graph.

### Temporary/contextual information

Keep separate when appropriate.

### Project-specific knowledge

Keep under the project, while linking reusable concepts to the main knowledge base.

Prioritize **quality and usefulness**, not maximum file count.

---

## 14. Preserve Source Material

When integrating provided material:

* Preserve important explanations.
* Preserve useful examples.
* Preserve terminology.
* Preserve warnings and mistakes.
* Preserve important reasoning.
* Preserve useful code.
* Preserve practical observations.

Do not silently replace source material with unrelated information.

Do not invent large explanations for concepts that are only briefly mentioned unless explicitly requested.

Small connective explanations are acceptable when necessary for coherence.

---

## 15. Beginner-Friendly, But Not Exam-Oriented

Write explanations so that concepts can be understood without assuming advanced knowledge.

Link prerequisites instead of repeatedly explaining them.

Do NOT optimize notes around:

* Exams
* Viva
* Marks
* Memorization
* Revision schedules
* Likely questions

unless explicitly requested.

This is a **long-term CS knowledge system**.

---

## 16. Tags and Metadata

Use tags sparingly.

Prefer:

```text
Folders + MOCs + Wikilinks
```

as the primary organization system.

Lightweight YAML frontmatter may be used when useful:

```yaml
---
type: concept
topic: Networking
---
```

Do not add unnecessary metadata.

---

## 17. Avoid Over-Organization

Do NOT create:

* unnecessary folders
* unnecessary MOCs
* unnecessary tags
* tiny notes for trivial facts
* duplicate concepts
* artificial links
* giant catch-all notes

The structure should be **simple enough to maintain and rich enough to represent relationships**.

---

## 18. New Material Workflow

Whenever new CS material is provided:

```text
NEW MATERIAL
     ↓
Inspect existing vault
     ↓
Find related concepts
     ↓
Does the concept already exist?
     │
   YES ──→ Update/extend existing note
     │
    NO
     ↓
Is it substantial enough for its own note?
     │
   YES ──→ Create canonical note
     │
    NO ──→ Add to appropriate existing note
     ↓
Determine meaningful relationships
     ↓
Add Obsidian wikilinks
     ↓
Update relevant MOCs
     ↓
Connect prerequisites / dependencies / applications
     ↓
Check duplicates and broken links
     ↓
Check graph coherence
```

The user should normally only need to provide the material.

Automatically determine where and how it belongs.

---

## 19. When to Create a New Note

Create a new note when the information:

* represents an independently useful concept,
* is likely to be referenced later,
* has meaningful relationships,
* contains enough substance to justify a note,
* or would make an existing note unwieldy if kept there.

Otherwise, add it to an existing note.

---

## 20. When to Merge

Merge notes when:

* They represent the same concept.
* One is a duplicate.
* Splitting them provides little value.
* The distinction is artificial.

After merging, update all references to the old note.

---

## 21. Final Consistency Check

After modifying the vault, verify:

### Structure

* Correct folder
* Consistent naming
* Relevant MOCs updated

### Content

* Important source information preserved
* No unnecessary invention
* No giant catch-all notes

### Links

* Meaningful wikilinks exist
* Important relationships are represented
* No broken wikilinks

### Graph

* Important concepts aren't orphaned
* Major domains connect where appropriate
* No artificial link spam

### Duplication

* No duplicate concepts
* Existing notes were reused where appropriate

---

## 22. Core Principle

Always think:

> **"What is this knowledge, where does it belong, what does it relate to, and how will it be useful later?"**

Not:

> **"What new file should I create?"**

The vault should continuously become a **coherent, interconnected map of Computer Science**.

When new CS material is provided without specific organization instructions, automatically apply these rules.

**Optimize for long-term understanding, conceptual relationships, discoverability, practical usefulness, and reuse — not exams, classes, or maximum organization complexity.**
