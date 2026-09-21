---
topic: Data Structures & Algorithms
type: moc
tags:
  - dsa
  - algorithms
  - data-structures
  - roadmap
date: 2026-09-05
---


# 🌳 Data Structures & Algorithms (DSA) Knowledge Base

> [!abstract] Master DSA Hub
> Welcome to the **Data Structures & Algorithms Knowledge Base**. This repository is structured for deep conceptual understanding, algorithmic pattern recognition, space-time complexity analysis, and coding interview preparation.

---

## 🗺️ DSA Master Roadmap

```mermaid
flowchart TD
    M0["00. Fundamentals<br/><i>Complexity Analysis & Math</i>"]
    M1["01. Strings & Arrays<br/><i>Two Pointers, Sliding Window, Prefix Sums</i>"]
    M2["02. Binary Search<br/><i>Monotonic search spaces & predicates</i>"]
    M3["03. Linked Lists<br/><i>Pointers, Reversal, Tortoise & Hare</i>"]
    M4["04. Bit Manipulation<br/><i>Masks, XOR, Bit Contribution</i>"]
    M5["05. Recursion & Backtracking<br/><i>DFS, Subsets, Pruning</i>"]
    M6["06. Stacks & Queues<br/><i>Monotonic Stack, Sliding Window Max</i>"]
    M7["07. Trees & BSTs<br/><i>Traversals, LCA, Height</i>"]
    M8["08. Heaps & Priority Queues<br/><i>Top-K, Min/Max-Heaps</i>"]
    M9["09. Graphs<br/><i>BFS, DFS, Dijkstra, DSU</i>"]
    M10["10. Dynamic Programming<br/><i>State transitions & memoization</i>"]

    M0 --> M1 --> M2 --> M3 --> M4 --> M5 --> M6 --> M7 --> M8 --> M9 --> M10

    classDef active fill:#1e293b,stroke:#10b981,stroke-width:2px,color:#fff;
    classDef planned fill:#1e293b,stroke:#3b82f6,stroke-width:1.5px,color:#fff;
    class M1,M2,M3,M4 active;
    class M0,M5,M6,M7,M8,M9,M10 planned;
```

---

## 📚 Active Modules

### 🔤 [[DSA/01. Strings/README|01. Strings]]
String operations, character manipulation, two-pointer simulation, and memory optimization:
- [[DSA/01. Strings/StringBuilder|🏗️ StringBuilder]] — Mutable character buffers, memory growth model, and DSA patterns.
- [[DSA/01. Strings/Add Binary & String Arithmetic|➕ Add Binary & String Arithmetic]] — Column-by-column math simulation, `StringBuilder` vs `String`, and carry propagation.
- [[DSA/DSA Problems/67. Add Binary|💡 67. Add Binary]] — Problem walkthrough, baseline vs. 100% `char[]` backward-fill optimization.

### 🔍 [[Binary Search|02. Binary Search]]
Searching monotonic patterns and halving search spaces:
- [[Binary Search]] — Monotonic property, $O(\log N)$ reduction, standard boundary template, example trace, and virtual reduction mental models.

### 🔗 [[DSA/03. Linked Lists/README|03. Linked Lists]]
Singly linked lists, non-contiguous node architecture, traversal, and core interview patterns:
- [[Linked List Fundamentals]] — Node class, pointer references, $O(1)$ vs $O(N)$ memory model, insertion/deletion mechanics, and 3-pointer mental model.
- [[Linked List Patterns]] — Fast & Slow pointers (Tortoise & Hare), in-place list reversal, and dummy head sentinel nodes.

### ⚡ [[Bit Manipulation|04. Bit Manipulation]]
Bit-level integer representation, operators, low-level tricks, and algorithmic XOR patterns:
- [[Bitwise Operators]] — AND (`&`), OR (`|`), XOR (`^`), NOT (`~`), truth tables, and algebraic identities
- [[Bit Tricks]] — Parity check (`N & 1`), Shift formulas (`<<`, `>>`), and bit masks (Check, Set, Flip, Unset)
- [[XOR Patterns]] — Identities ($A \oplus 0 = A$, $A \oplus A = 0$), duplicate cancellation, and bit-count observations
- [[Bit Manipulation Problems]] — Single Number, Two Missing Numbers (Partitioning), Minimum XOR Pair, and Sum of XOR of All Pairs (Bit Contribution)

---

## 🔗 Quick Links & Reference
- [[Dashboard|🧭 Main Command Center]]
- [[Quick Look|⚡ Quick Look & Cheatsheet (Frequently Forgotten Syntax)]]
- [[DSA/01. Strings/README|🔤 01. Strings Master Note]]
- [[Binary Search|🔍 Binary Search]]
- [[DSA/03. Linked Lists/README|🔗 03. Linked Lists Master Note]]
- [[Linked List Fundamentals|🧱 Linked List Fundamentals]]
- [[Linked List Patterns|🧠 Linked List Patterns]]
- [[Bit Manipulation|📁 Bit Manipulation Master Note]]
- [[Bit Manipulation Problems|💡 Bit Manipulation Problems]]


