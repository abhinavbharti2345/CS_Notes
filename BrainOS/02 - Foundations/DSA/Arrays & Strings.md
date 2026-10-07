---
type: concept
topic: Data Structures & Algorithms
subtopic: Arrays & Strings
date: 2026-10-07
tags:
  - dsa
  - arrays
  - strings
  - memory
---

# 📦 Arrays & Strings Fundamentals

> The foundational contiguous memory data structures enabling $O(1)$ random indexing and high-throughput cache locality.

---

## 🎯 Why It Matters
- **CPU Cache Friendliness:** Because array elements sit side-by-side in physical RAM, CPU pre-fetchers load contiguous cache lines (64 bytes) instantly, making array scans dramatically faster than pointer-based lists.
- **Underpinning of Everything:** Hash tables, heaps, string builders, vectors, and neural network weight matrices are all backed by flat contiguous arrays.

---

## 🧠 Core Concepts

### 1. Memory Layout & Offset Calculation
- Address of element at index $i$:
  $$\text{Address}(\text{arr}[i]) = \text{Base Address} + (i \times \text{Element Size})$$
- Consequence: Random access by index is $O(1)$.
- Cost of middle insertion/deletion: $O(N)$ due to shifting elements.

### 2. Strings & Immutability
- In Java, `String` is immutable and stored in the String Pool.
- String concatenation in loops (`s += char`) creates $O(N^2)$ garbage objects; always use `StringBuilder` for $O(N)$ accumulation.

---

## 🗺️ Learning Order & Key Patterns
1. Basic 1D array traversal, reversal, and in-place transformations.
2. 2D Matrix rotations, spiral traversal, and diagonal traversal.
3. String manipulation, anagram checks, palindrome validation.
4. Boyer-Moore Majority Voting Algorithm ($O(N)$ time, $O(1)$ space).
5. Kadane's Algorithm for Maximum Subarray Sum ($O(N)$ time).

---

## 🛠️ Practical Code: Kadane's Maximum Subarray Sum

```java
public class KadanesAlgorithm {
    public static int maxSubArray(int[] nums) {
        int maxGlobal = nums[0];
        int maxCurrent = nums[0];

        for (int i = 1; i < nums.length; i++) {
            maxCurrent = Math.max(nums[i], maxCurrent + nums[i]);
            maxGlobal = Math.max(maxGlobal, maxCurrent);
        }
        return maxGlobal;
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Two Pointers & Sliding Window|Two Pointers & Sliding Window]]
- [[BrainOS/02 - Foundations/DSA/Hashing & Prefix Sum|Hashing & Prefix Sum]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
