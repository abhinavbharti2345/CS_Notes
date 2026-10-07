---
type: concept
topic: Data Structures & Algorithms
subtopic: Hashing & Prefix Sum
date: 2026-10-07
tags:
  - dsa
  - hashing
  - prefix-sum
  - patterns
---

# ⚡ Hashing & Prefix Sum Patterns

> Algorithmic paradigms leveraging $O(1)$ amortized dictionary lookups and precomputed cumulative sums for constant-time range queries.

---

## 🎯 Why It Matters
- **Instant Range Queries:** Prefix sums reduce arbitrary subarray sum queries from $O(N)$ to $O(1)$.
- **Subarray Sum Equals K:** Combining prefix sums with a hash map solves continuous target-sum questions in a single $O(N)$ pass.
- **Hash Table Internals:** Core understanding of hashing, collision resolution (chaining vs open addressing), load factors, and cryptographic hash functions.

---

## 🧠 Core Concepts

### 1. Prefix Sum Formula
Given an array `nums`:
$$\text{prefix}[i] = \sum_{j=0}^{i} \text{nums}[j]$$
Any range sum between indices $L$ and $R$ is:
$$\text{Sum}(L, R) = \text{prefix}[R] - \text{prefix}[L - 1]$$

### 2. The Prefix Sum + HashMap Idiom
To find if a subarray with sum $K$ ends at index $i$:
$$\text{Current Prefix Sum} - \text{Target } K = \text{Needed Earlier Prefix Sum}$$
Store seen prefix sums and their frequency in a `HashMap`.

---

## 🛠️ Code Example: Subarray Sum Equals K

```java
import java.util.HashMap;
import java.util.Map;

public class SubarraySumEqualsK {
    public static int subarraySum(int[] nums, int k) {
        int count = 0;
        int currentPrefixSum = 0;
        
        // Map: PrefixSum -> Frequency
        Map<Integer, Integer> prefixMap = new HashMap<>();
        prefixMap.put(0, 1); // Base case: prefix sum of 0 has occurred once

        for (int num : nums) {
            currentPrefixSum += num;

            // Check if (currentPrefixSum - k) exists in history
            if (prefixMap.containsKey(currentPrefixSum - k)) {
                count += prefixMap.get(currentPrefixSum - k);
            }

            prefixMap.put(currentPrefixSum, prefixMap.getOrDefault(currentPrefixSum, 0) + 1);
        }
        return count;
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Arrays & Strings|Arrays & Strings]]
- [[BrainOS/02 - Foundations/DSA/Two Pointers & Sliding Window|Two Pointers & Sliding Window]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
