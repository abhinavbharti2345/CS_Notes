---
type: concept
topic: Data Structures & Algorithms
subtopic: Stack & Queue
date: 2026-10-07
tags:
  - dsa
  - stack
  - queue
  - monotonic-stack
---

# 📚 Stack & Queue Fundamentals

> Linear abstract data types enforcing Last-In-First-Out (LIFO) and First-In-First-Out (FIFO) access disciplines, powering execution runtimes and asynchronous message buffers.

---

## 🎯 Why It Matters
- **Stack:** Powers function call execution frames, recursive backtracks, expression parsers, and browser back buttons.
- **Monotonic Stack:** Solves "Next Greater Element" and "Largest Rectangle in Histogram" in optimal linear $O(N)$ time.
- **Queue / Deque:** Powers Breadth-First Search (BFS), thread pool task scheduling, circular buffers, and sliding window maximums.

---

## 🧠 Core Patterns

### 1. Monotonic Stack (Next Greater Element)
- Maintain elements in strictly increasing or decreasing order.
- When a new element violates the order, pop from stack and record the newly found answer.
- Each element is pushed and popped at most once $\rightarrow O(N)$ time.

### 2. Monotonic Deque (Sliding Window Maximum)
- Maintain indices in a `Double-Ended Queue (Deque)` where values are strictly decreasing.
- Remove elements outside the window ($i - K$) from the front.
- Pop smaller elements from the back before adding the current element.

---

## 🛠️ Code Example: Next Greater Element I

```java
import java.util.ArrayDeque;
import java.util.Deque;
import java.util.HashMap;
import java.util.Map;

public class NextGreaterElement {
    public static int[] nextGreaterElements(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        Deque<Integer> stack = new ArrayDeque<>(); // stores indices

        for (int i = 0; i < n; i++) {
            while (!stack.isEmpty() && nums[i] > nums[stack.peek()]) {
                int prevIndex = stack.pop();
                result[prevIndex] = nums[i];
            }
            stack.push(i);
        }

        while (!stack.isEmpty()) {
            result[stack.pop()] = -1;
        }
        return result;
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Trees & BST|Trees & BST (Tree Traversals)]]
- [[BrainOS/02 - Foundations/DSA/Graphs|Graphs (BFS Traversal)]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
