---
description: Standards for creating aesthetic diagrams, flowcharts, and architectural charts in the vault using Draw.io and Mermaid.
---

# 🎨 Diagram & Flowchart Standards (Draw.io & Mermaid)

## 1. Primary Tool for Visual Flowcharts & Complex Concepts: Draw.io

For multi-step execution traces, call stack memory models, architectural diagrams, tree decompositions, and complex flowcharts, **use Draw.io vector SVG files (`.drawio.svg`)**:

- **Aesthetic Excellence:** Custom cards, rich dark-theme colors, clear typography, and clean multi-column layouts.
- **Interactive & Editable:** Seamlessly editable directly within Obsidian via the `drawio-obsidian` plugin.
- **Embedded XML Spec:** Always format as standalone SVG with embedded `<mxfile>` content so it renders instantly in Obsidian preview.

---

## 2. Mandatory `assets/` Folder Storage

**Never save `.drawio.svg` or image/asset files in the main notes folder.**

- Always place diagram files in an `assets/` subdirectory under the relevant module:
  ```text
  Module Folder/
  ├── Note Name.md
  ├── README.md
  └── assets/
      └── diagram_name.drawio.svg
  ```
- Embed diagrams in Markdown notes using clean Obsidian wikilink syntax:
  ```markdown
  > [!tip] 🎨 Visual Execution Model
  > ![[diagram_name.drawio.svg]]
  ```

---

## 3. Mermaid Diagram Best Practices (When Used)

When simple inline Mermaid diagrams are used:
- **Prefer Horizontal Orientation:** Use `flowchart LR` for sequential traces and state transitions to prevent tall, stretched vertical towers.
- **Avoid Complex Nested Subgraphs:** Do not mix opposite directional subgraphs (`direction TB` inside `direction LR`), which causes layout breakage.
- **No Intrusive HTML Tags:** Avoid wrapping node text in `<code>` or custom inline HTML that conflicts with Obsidian's global markdown styles.
