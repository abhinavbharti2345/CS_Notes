---
topic: Data Structures & Algorithms
subtopic: Stacks & Queues
type: moc
tags:
  - dsa
  - stack
  - queue
  - data-structures
  - roadmap
date: 2026-09-24
---

# 🥞 Stacks & Queues Module

> [!abstract] Module Overview
> Welcome to the **Stacks & Queues** module. Stacks (LIFO) and Queues (FIFO) are foundational restricted-access linear data structures critical for simulation, expression parsing, recursion management, tree/graph traversals, and monotonic sliding windows.

---

## 🗺️ Module Learning Path

```mermaid
flowchart TD
    SQ["🥞 Stacks & Queues"] --> S1["🧱 Stacks 1: Foundations"]
    SQ --> S2["🧠 Stacks 2: Monotonic Stack"]
    SQ --> Q["🔄 Queues & Deques"]

    subgraph S1_Flow ["Stacks 1 — Foundations"]
        direction TB
        F1["1. [[01. Stack Fundamentals]]<br/><i>LIFO, 5 Operations, Plate Analogy</i>"]
        F2["2. [[02. Stack Implementation from Scratch]]<br/><i>Array & Linked List implementations</i>"]
        F3["3. Double Character Trouble<br/><i>Adjacent duplicate removal pattern</i>"]
        F4["4. Min Stack<br/><i>O(1) getMin auxiliary tracking</i>"]
        F1 --> F2 --> F3 --> F4
    end

    subgraph S2_Flow ["Stacks 2 — Monotonic Stack"]
        direction TB
        M1["5. Nearest Smaller / Greater on Left (NSL/NGL)"]
        M2["6. Nearest Smaller / Greater on Right (NSR/NGR)"]
        M3["7. Subarray Contribution: A[i] as Minimum"]
        M4["8. Sum of (Max - Min) across all Subarrays"]
        M1 --> M2 --> M3 --> M4
    end

    S1 --> S1_Flow
    S2 --> S2_Flow

    classDef core fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.5px;
    classDef section fill:#f59e0b18,stroke:#f59e0b,stroke-width:1.8px;
    classDef step fill:#10b98118,stroke:#10b981,stroke-width:1.5px;
    class SQ core;
    class S1,S2,Q section;
    class F1,F2,F3,F4,M1,M2,M3,M4 step;
```

---

## 📚 Syllabus & Notes Breakdown

### 🧱 Stacks 1 — Foundations
1. **[[01. Stack Fundamentals|🥞 01. Stack Fundamentals]]**
   - Core Concept: **LIFO (Last In, First Out)** & Plate Analogy
   - The 5 Essential Operations: `push(x)`, `pop()`, `peek()`, `isEmpty()`, `size()`
   - Java Standard Library (`Stack<T>` vs `ArrayDeque<T>`)
2. **[[02. Stack Implementation from Scratch|🛠️ 02. Stack Implementation from Scratch]]**
   - **Array Implementation:** `arr[]` + `top` pointer, Overflow / Underflow checks
   - **Linked List Implementation:** `head` as `top`, dynamic memory, $O(1)$ operations
   - **Deep Comparison:** Memory overhead, cache locality, and runtime trade-offs
3. **Double Character Trouble**
   - Eliminating adjacent duplicate characters via Stack simulation
4. **Min Stack**
   - Constant-time $O(1)$ minimum element retrieval (`2x - min` vs auxiliary stack)

---

### 🧠 Stacks 2 — Monotonic Stack Patterns
5. **Nearest Smaller & Greater Element on Left (NSL / NGL)**
   - Maintaining monotonic increasing/decreasing order from left to right
6. **Nearest Smaller & Greater Element on Right (NSR / NGR)**
   - Monotonic stack traversal from right to left (Next Greater Element)
7. **Count of Subarrays where $A[i]$ is Minimum**
   - Contribution technique using boundary spans `(i - left) * (right - i)`
8. **Sum of $(Max - Min)$ for All Subarrays**
   - Combining monotonic stack boundaries to solve range sum differences in $O(N)$

---

## 🔗 Related Notes & Navigation
- [[CS/DSA/README|🌳 DSA Master Roadmap]]
- [[Quick Look|⚡ Quick Look Cheatsheet]]
- [[01. Stack Fundamentals|🥞 01. Stack Fundamentals]]
- [[02. Stack Implementation from Scratch|🛠️ 02. Stack Implementation from Scratch]]
- [[Home|🧭 Main Command Center]]
