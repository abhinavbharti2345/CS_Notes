---
description: Standards for creating aesthetic diagrams, flowcharts, and architectural charts in the vault using Draw.io and Mermaid.
---

# 🎨 Diagram & Flowchart Standards (Draw.io & Mermaid)

## 0. Visual Style Requirement

All vault diagrams must use a **Dark + Colorful + High-Contrast** style.

- Do not use white, pale blue, or light gray box/card backgrounds for diagram nodes.
- Use dark node fills such as `#111827`, `#13161C`, or `#0F172A`.
- Use bright, meaningful strokes and accents such as cyan, violet, emerald, amber, rose, and blue.
- Use white or near-white primary text on dark fills, with muted gray-blue secondary text.
- Keep diagram canvases transparent or dark; never use a white page/card behind the diagram.
- For Mermaid diagrams, rely on the enabled `diagrams.css` snippet and add explicit `classDef` colors only when a diagram needs semantic color categories.
- For Draw.io SVGs, set the page/background to dark and make every rounded rectangle/card dark-filled with colorful borders.

---

## 1. When to Use Draw.io vs Native Mermaid

- **Use Draw.io (`.drawio.svg`) for Large & Complex Flowcharts:**
  - Multi-stage architectures (e.g. OSI vs TCP/IP layer mappings, encapsulation/decapsulation pipelines).
  - Multi-tier workflows (e.g. Client $\leftrightarrow$ Express $\leftrightarrow$ JWT $\leftrightarrow$ Database auth flows).
  - Multi-step recursive execution traces, memory heaps, routing tables, and ML lifecycle pipelines.
  - Any flowchart with multiple decision branches, columns, or detailed annotations.

- **Keep Native Mermaid for Small & Compact Graphs:**
  - Small trees (2–5 nodes, exactly like in `01. Binary Tree Fundamentals.md`).
  - Simple 2–3 step linear state changes ($A \to B \to C$ or push/pop on a stack).
  - Compact bitmask operations and module roadmap indexes in `README.md`.

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
