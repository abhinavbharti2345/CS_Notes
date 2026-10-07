---
type: concept
topic: Data Structures & Algorithms
subtopic: Dynamic Programming
date: 2026-10-07
tags:
  - dsa
  - dynamic-programming
  - optimization
  - memoization
---

# ⚡ Dynamic Programming (DP) Mastery

> An algorithmic technique that solves complex optimization problems by breaking them down into overlapping subproblems and optimal substructures, storing solutions to avoid redundant recomputation.

---

## 🎯 Why It Matters
- **Exponential to Polynomial Speedup:** Transforms $O(2^N)$ brute-force recursive decision trees into $O(N)$ or $O(N^2)$ polynomial-time DP tables.
- **Underpins Core Systems Optimization:** Viterbi algorithm in speech processing, Needleman-Wunsch in DNA sequencing, Diff algorithms in Git, and database query cost estimators all rely on dynamic programming.

---

## 🧠 Core Patterns & Archetypes

| Pattern Archetype | State Definition | Classic Problems |
| :--- | :--- | :--- |
| **1. 1D State Transitions** | `dp[i]` = optimal solution considering first $i$ elements | Climbing Stairs, House Robber, Coin Change, LIS ($O(N \log N)$) |
| **2. 2D Grid / Matrix** | `dp[i][j]` = cost to reach cell $(i, j)$ | Unique Paths, Minimum Path Sum, Maximal Square |
| **3. 0/1 & Unbounded Knapsack** | `dp[i][w]` = max value using first $i$ items with capacity $w$ | Partition Equal Subset Sum, Target Sum, Coin Change II |
| **4. Longest Common Subsequence (LCS)** | `dp[i][j]` = match between `s1[0..i]` and `s2[0..j]` | Edit Distance, Longest Palindromic Subsequence, LCS |
| **5. Interval DP** | `dp[i][j]` = cost of optimal bracket/range partition `[i..j]` | Matrix Chain Multiplication, Burst Balloons |

---

## 🛠️ Code Example: 0/1 Knapsack (Space-Optimized 1D Array)

```java
public class Knapsack01 {
    public static int knapSack(int capacity, int[] weights, int[] values, int n) {
        int[] dp = new int[capacity + 1];

        for (int i = 0; i < n; i++) {
            // Traverse capacity backwards to prevent using the same item multiple times
            for (int w = capacity; w >= weights[i]; w--) {
                dp[w] = Math.max(dp[w], values[i] + dp[w - weights[i]]);
            }
        }
        return dp[capacity];
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Greedy & Backtracking|Greedy & Backtracking]]
- [[BrainOS/02 - Foundations/DSA/Trees & BST|Trees & Recursion]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
