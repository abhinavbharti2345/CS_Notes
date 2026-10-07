---
type: concept
topic: Data Structures & Algorithms
subtopic: Greedy & Backtracking
date: 2026-10-07
tags:
  - dsa
  - greedy
  - backtracking
  - recursion
---

# ⚔️ Greedy & Backtracking Paradigms

> Two foundational problem-solving approaches: locally optimal decision-making without reconsideration (Greedy) versus systematic state exploration with pruning and state reversal (Backtracking).

---

## 🎯 Why It Matters
- **Greedy:** Optimal for problems exhibiting the greedy-choice property (Interval Scheduling, Huffman Coding, Kruskal MST, Task Scheduling).
- **Backtracking:** Exhaustively solves NP-complete constraint satisfaction problems (Sudoku Solver, N-Queens, Subsets, Permutations, Word Search) while pruning dead ends early.

---

## 🧠 Core Patterns

### 1. Greedy Interval Scheduling
- Sort intervals by **End Time**.
- Select the first interval, then greedily pick the next non-overlapping interval with the earliest finish time.

### 2. Backtracking Template (Choose ➔ Explore ➔ Un-choose)
```java
void backtrack(State state, List<Candidate> candidates) {
    if (isGoal(state)) {
        recordSolution(state);
        return;
    }
    for (Candidate choice : candidates) {
        if (isValid(choice, state)) {
            makeChoice(state, choice);    // 1. Choose
            backtrack(state, candidates); // 2. Explore
            undoChoice(state, choice);    // 3. Un-choose (Backtrack)
        }
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Dynamic Programming|Dynamic Programming]]
- [[BrainOS/02 - Foundations/DSA/Graphs|Graphs & Topological Sort]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
