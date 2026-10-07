---
type: concept
topic: Data Structures & Algorithms
subtopic: Linked Lists
date: 2026-10-07
tags:
  - dsa
  - linked-lists
  - pointers
  - memory
---

# 🔗 Linked Lists Master Note

> Linear collection of data elements whose order is not given by their physical placement in memory, but rather through reference pointers linking independent heap nodes.

---

## 🎯 Why It Matters
- **$O(1)$ Insertion and Deletion:** Unlike arrays, inserting or deleting at the head or after a known node requires zero element shifts ($O(1)$).
- **Core Systems Infrastructure:** Forms the foundation of memory allocators (free lists in OS kernels), hash map collision buckets, and LRU cache chains.
- **Pointer Fluency:** Teaches pristine pointer manipulation without memory corruption or lost references.

---

## 🧠 Core Patterns

```mermaid
flowchart TD
    subgraph P1 ["Pattern 1: Fast & Slow Pointers (Tortoise & Hare)"]
        direction LR
        S["slow (1 step)"] --> F["fast (2 steps)"]
    end

    subgraph P2 ["Pattern 2: In-Place Reversal (3-Pointer Loop)"]
        direction LR
        PR["prev"] --> CU["current"] --> NX["next"]
    end

    subgraph P3 ["Pattern 3: Dummy Head Sentinel"]
        direction LR
        DUM["<b>dummy (val: 0)</b>"] --> HD["head"]
    end

    style P1 fill:#0B0F14,stroke:#38BDF8,stroke-width:1.8px,color:#38BDF8
    style P2 fill:#0B0F14,stroke:#34D399,stroke-width:1.8px,color:#34D399
    style P3 fill:#0B0F14,stroke:#FB923C,stroke-width:1.8px,color:#FB923C

    classDef dsaNode stroke:#A78BFA,stroke-width:1.8px;
    class S,F,PR,CU,NX,DUM,HD dsaNode;
```

---

## 🛠️ Code Example: In-Place Reverse Linked List

```java
public class LinkedListReversal {
    static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
    }

    public static ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;

        while (curr != null) {
            ListNode next = curr.next; // 1. Save next
            curr.next = prev;          // 2. Reverse link
            prev = curr;               // 3. Move prev forward
            curr = next;               // 4. Move curr forward
        }
        return prev; // New head
    }
}
```

---

## 🔗 Related Notes
- In-depth study note: **[[CS/DSA/03. Linked Lists/01. Linked List Fundamentals|🧱 Detailed Linked List Fundamentals]]**
- Patterns study note: **[[CS/DSA/03. Linked Lists/02. Linked List Patterns|🧠 Linked List Patterns]]**
- DSA Master Hub: **[[BrainOS/02 - Foundations/DSA/DSA|DSA Master Hub]]**
