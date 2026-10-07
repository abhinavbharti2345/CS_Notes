---
type: concept
topic: Data Structures & Algorithms
subtopic: Two Pointers & Sliding Window
date: 2026-10-07
tags:
  - dsa
  - two-pointers
  - sliding-window
  - patterns
---

# 🔍 Two Pointers & Sliding Window Patterns

> Efficient $O(N)$ linear scanning techniques for search spaces, subarrays, and contiguous substring constraints.

---

## 🎯 Why It Matters
- **Drastic Complexity Reduction:** Converts brute-force $O(N^2)$ or $O(N^3)$ nested loops into a single linear $O(N)$ pass.
- **Real-World Streaming & Rate Limiting:** Sliding windows power network rate limiters, token buckets, moving-average stock tickers, and audio sample processing.

---

## 🧠 Core Patterns

### 1. Two Pointers (Opposite Direction / Inward)
- Used primarily on **sorted arrays** or palindromes.
- `left = 0`, `right = n - 1`. Move `left++` or `right--` based on comparison.
- **Key Problems:** Two Sum II, 3Sum, Container With Most Water, Trapping Rain Water.

### 2. Sliding Window (Fixed Size $K$)
- Calculate the metric for the first $K$ elements.
- Slide by 1: Subtract element leaving window (`nums[i - k]`), add element entering window (`nums[i]`).
- **Complexity:** $O(N)$ total operations.

### 3. Sliding Window (Dynamic / Variable Size)
- `left = 0, right = 0`.
- Expand `right` to include elements until the window becomes **invalid**.
- Shrink `left` to restore validity while updating maximum/minimum length.
- **Key Problems:** Longest Substring Without Repeating Characters, Minimum Window Substring.

---

## 🛠️ Practical Boilerplate: Dynamic Sliding Window

```java
import java.util.HashMap;
import java.util.Map;

public class SlidingWindowPattern {
    public static int lengthOfLongestSubstringKDistinct(String s, int k) {
        if (s == null || s.length() == 0 || k == 0) return 0;
        
        Map<Character, Integer> freqMap = new HashMap<>();
        int left = 0, maxLen = 0;

        for (int right = 0; right < s.length(); right++) {
            char rightChar = s.charAt(right);
            freqMap.put(rightChar, freqMap.getOrDefault(rightChar, 0) + 1);

            // Shrink window if constraint violated
            while (freqMap.size() > k) {
                char leftChar = s.charAt(left);
                freqMap.put(leftChar, freqMap.get(leftChar) - 1);
                if (freqMap.get(leftChar) == 0) {
                    freqMap.remove(leftChar);
                }
                left++;
            }

            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Arrays & Strings|Arrays & Strings]]
- [[BrainOS/02 - Foundations/DSA/Hashing & Prefix Sum|Hashing & Prefix Sum]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
