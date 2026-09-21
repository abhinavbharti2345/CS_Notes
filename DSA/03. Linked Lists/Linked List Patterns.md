---
topic: Data Structures & Algorithms
subtopic: Linked Lists
type: concept
tags:
  - dsa
  - linked-lists
  - patterns
  - fast-slow-pointers
  - reversal
  - dummy-node
date: 2026-09-17
---

# 🧠 Linked List Core Patterns

> **Module Master Note:** [[DSA/03. Linked Lists/README|03. Linked Lists]]  
> **Prerequisites:** [[Linked List Fundamentals]]  
> **Related Notes:** [[Quick Look]] | [[DSA/README|DSA Master Roadmap]]

---

## 🎯 Overview of Core Patterns

Mastering linked lists is about recognizing a small set of pointer-manipulation idioms rather than memorizing individual solutions:

| Pattern | Key Idiom | Primary Applications |
| :--- | :--- | :--- |
| **1. Basic Traversal** | `curr = curr.next` | Printing, searching, counting, finding min/max |
| **2. Fast & Slow Pointers** | `slow = slow.next; fast = fast.next.next;` | Finding list middle, cycle detection, palindrome check |
| **3. In-Place Reversal** | `next = curr.next; curr.next = prev; prev = curr; curr = next;` | Reversing lists, reverse sub-segments, reversing in K-groups |
| **4. Dummy Node (Sentinel)** | `Node dummy = new Node(0); dummy.next = head;` | Head deletions, list merges, partition problems |

---

## 1. Pattern 1: Basic Traversal & Linear Aggregation

The cornerstone template for single-pass processing:

```java
Node current = head;

while (current != null) {
    // Process current node (e.g., search, count, accumulate)
    current = current.next;
}
```

### Common Variants:
- **Search:** `if (current.data == target) return true;`
- **Count Nodes:** `int count = 0; while (curr != null) { count++; curr = curr.next; }`
- **Find Tail:** `while (current.next != null) { current = current.next; }` *(Note: checks `current.next != null` to stop ON the last node instead of stepping past it into `null`)*.

---

## 2. Pattern 2: Fast & Slow Pointers (Floyd's Tortoise & Hare) 🐢🐇

Instead of moving one pointer one step at a time, two pointers advance at different speeds:
- `slow` moves **1 step** per iteration: `slow = slow.next;`
- `fast` moves **2 steps** per iteration: `fast = fast.next.next;`

```text
slow
 ↓
[10] ──→ [20] ──→ [30] ──→ [40] ──→ [50] ──→ null
                   ↑
                  fast
```

### Use Case A: Finding the Middle Node (In a Single Pass)
Without knowing the length in advance:
- When `fast` reaches the end (`fast == null` or `fast.next == null`), `slow` will be exactly at the middle.

```java
Node slow = head;
Node fast = head;

while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
}
// slow now points to the middle node
```

### Use Case B: Cycle Detection (Floyd's Cycle Finding Algorithm)
- If a cycle exists, `fast` will eventually wrap around and collide with `slow` (`slow == fast`).
- If no cycle exists, `fast` reaches `null`.

```java
Node slow = head;
Node fast = head;

while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
    
    if (slow == fast) {
        return true; // Cycle detected!
    }
}
return false; // No cycle
```

### Use Case C: Checking Palindrome Linked List
1. Find the middle using Fast & Slow pointers.
2. Reverse the second half of the list (Pattern 3).
3. Compare the first half and reversed second half node-by-node.

---

## 3. Pattern 3: In-Place List Reversal 🔄

Transforming $1 \longrightarrow 2 \longrightarrow 3 \longrightarrow 4 \longrightarrow \text{null}$ into $4 \longrightarrow 3 \longrightarrow 2 \longrightarrow 1 \longrightarrow \text{null}$ with $O(1)$ extra space.

### The Algorithm:
We maintain three sliding pointers:
- `prev`: The head of the already-reversed portion (starts at `null`).
- `current`: The node currently being rewired (starts at `head`).
- `next`: Temporary reference to save the remaining forward list.

```java
Node prev = null;
Node current = head;

while (current != null) {
    Node next = current.next; // 1. Save next node
    current.next = prev;      // 2. Reverse current node's link
    prev = current;           // 3. Move prev forward
    current = next;           // 4. Move current forward
}

head = prev; // prev is the new head of the reversed list
```

### Step-by-Step Visual Trace:

#### Initial State:
```text
prev = null
current = [ 1 ] ──→ [ 2 ] ──→ [ 3 ] ──→ [ 4 ] ──→ null
```

#### Step 1:
```text
Save: next = [ 2 ]
Rewire: [ 1 ] ──→ null
Advance: prev = [ 1 ], current = [ 2 ]
```

#### Step 2:
```text
Save: next = [ 3 ]
Rewire: [ 2 ] ──→ [ 1 ] ──→ null
Advance: prev = [ 2 ], current = [ 3 ]
```

#### Step 3:
```text
Save: next = [ 4 ]
Rewire: [ 3 ] ──→ [ 2 ] ──→ [ 1 ] ──→ null
Advance: prev = [ 3 ], current = [ 4 ]
```

#### Step 4:
```text
Save: next = null
Rewire: [ 4 ] ──→ [ 3 ] ──→ [ 2 ] ──→ [ 1 ] ──→ null
Advance: prev = [ 4 ], current = null (Loop ends)
New head = prev ([ 4 ])
```

---

## 4. Pattern 4: Dummy Head Node (Sentinel) 🛡️

### The Problem it Solves:
When modifying a linked list, operations at the very front (`head`) often require messy special-case `if (head == ...)` checks (e.g., removing the first node, inserting before `head`, merging lists).

### The Solution:
Create a fake "dummy" node that sits right before `head`:

```java
Node dummy = new Node(0);
dummy.next = head;
```

```text
dummy ──→ [10] ──→ [20] ──→ [30] ──→ null
  ↑
head reference preserved
```

### Key Advantages:
1. The real head (`head`) always has a preceding node (`dummy`), eliminating null-checks for the head.
2. At the end of the algorithm, the updated list is always accessible via `dummy.next`.

```java
// Example: Removing all nodes matching a target value
Node dummy = new Node(0);
dummy.next = head;
Node curr = dummy;

while (curr.next != null) {
    if (curr.next.data == val) {
        curr.next = curr.next.next; // Safely bypasses even if target was original head!
    } else {
        curr = curr.next;
    }
}

return dummy.next; // New head of modified list
```

---

## ⚠️ Common Pointer Traps & Pitfalls

1. **`NullPointerException` on chained access:**
   - Writing `current.next.next` without checking `current.next != null` first causes runtime crashes if `current` is the tail node.
   - Always verify `fast != null && fast.next != null` in fast-pointer loops.

2. **Losing reference chains:**
   - Overwriting `current.next` before caching the remaining list or before pointing the new node forward breaks the list irreversibly.

3. **Accidental Infinite Cycles:**
   - Forgetting to terminate the tail with `null` after reversing or reordering nodes produces infinite loops in subsequent traversals.

---

## 🔗 Related Notes & Practice
- [[Linked List Fundamentals|🧱 Linked List Fundamentals]]
- [[DSA/03. Linked Lists/README|🔗 03. Linked Lists Master Note]]
- [[Quick Look|⚡ Quick Look Cheatsheet]]
- [[DSA/README|🌳 DSA Roadmap]]
