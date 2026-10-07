---
type: concept
topic: Data Structures & Algorithms
subtopic: Heaps & Priority Queues
date: 2026-10-07
tags:
  - dsa
  - heap
  - priority-queue
  - algorithms
---

# 🏔️ Heaps & Priority Queues

> Complete binary trees stored in contiguous arrays that maintain the Heap Property, enabling $O(1)$ peak retrieval and $O(\log N)$ dynamic updates.

---

## 🎯 Why It Matters
- **Top-K Element Streaming:** Finding the $K$-th largest/smallest item in continuous data streams without sorting the entire dataset ($O(N \log K)$ vs $O(N \log N)$).
- **Core Engine of Dijkstra & A\*:** Priority Queues select the lowest-cost edge/node dynamically.
- **Operating System Task Schedulers:** Completely Fair Scheduler (CFS) and real-time process queues use priority structures to allocate CPU slices.

---

## 🧠 Core Array-Backed Binary Heap Mechanics
For an element at array index $i$:
- $\text{Left Child} = 2i + 1$
- $\text{Right Child} = 2i + 2$
- $\text{Parent} = \lfloor (i - 1) / 2 \rfloor$

---

## 🛠️ Code Example: Top K Frequent Elements

```java
import java.util.HashMap;
import java.util.Map;
import java.util.PriorityQueue;

public class TopKFrequent {
    public static int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> countMap = new HashMap<>();
        for (int num : nums) {
            countMap.put(num, countMap.getOrDefault(num, 0) + 1);
        }

        // Min-Heap ordered by frequency
        PriorityQueue<Integer> minHeap = new PriorityQueue<>((a, b) -> countMap.get(a) - countMap.get(b));

        for (int key : countMap.keySet()) {
            minHeap.offer(key);
            if (minHeap.size() > k) {
                minHeap.poll(); // Evict lowest frequency element
            }
        }

        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = minHeap.poll();
        }
        return result;
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/02 - Foundations/DSA/Trees & BST|Trees & BSTs]]
- [[BrainOS/02 - Foundations/DSA/Graphs|Graphs (Dijkstra's Algorithm)]]
- [[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]
