---
type: concept
topic: Data Structures & Algorithms
subtopic: Binary Search
date: 2026-10-07
tags:
  - dsa
  - binary-search
  - algorithms
  - divide-and-conquer
---

# 🎯 Binary Search on Monotonic Space

> A divide-and-conquer search algorithm that eliminates half the search space at each iteration, operating in $O(\log N)$ logarithmic time.

---

## 🎯 Why It Matters
- **Logarithmic Scalability:** Searches across 4 billion items in just 32 operations.
- **Search on Answer Space:** Extends far beyond sorted arrays to find optimal thresholds, minimum capacities, and maximum allocation limits in continuous or discrete monotonic functions.
- **Database B-Tree Page Lookups:** B-Tree internal nodes use binary search across sorted keys to select disk child pointers.

---

## 🧠 Core Patterns

### 1. Classical Binary Search (Exact Value / Lower Bound)
```java
public static int lowerBound(int[] nums, int target) {
    int low = 0, high = nums.length - 1;
    int ans = nums.length;

    while (low <= high) {
        int mid = low + (high - low) / 2; // Prevents integer overflow
        if (nums[mid] >= target) {
            ans = mid;
            high = mid - 1; // Look for earlier occurrence on left
        } else {
            low = mid + 1;
        }
    }
    return ans;
}
```

### 2. Binary Search on Answer Space (Predicate Monotonicity)
- Pattern: Identify a monotonic predicate function: `isValid(mid) -> boolean`.
- If `isValid(mid) == true`, search left (`high = mid - 1`) or right (`low = mid + 1`) depending on optimization direction.
- **Key Problems:** Koko Eating Bananas, Capacity to Ship Packages, Split Array Largest Sum, Aggressive Cows.

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Trees & BST|Trees & BSTs]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
