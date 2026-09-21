---
topic: Data Structures & Algorithms
subtopic: Searching
type: concept
tags:
  - dsa
  - algorithms
  - binary-search
  - searching
date: 2026-09-10
---

# 🔍 Binary Search

> **Master Roadmap:** [[DSA/README|DSA Master Roadmap]]  
> **Quick Reference:** [[Quick Look|⚡ Quick Look Cheatsheet]]

---

## 💡 1. Core Idea

Binary search works when we have something that is **sorted** or has a **monotonic pattern**.

Instead of checking every element sequentially:
```text
1 2 3 4 5 6 7 8 9
```
We check the middle element:
```text
        5
```
Then eliminate half of the remaining search space based on the comparison:
- **If $\text{target} < 5$:** Search space becomes `1 2 3 4`
- **If $\text{target} > 5$:** Search space becomes `6 7 8 9`

### Time Complexity Reduction
```text
N elements
    ↓
   N/2
    ↓
   N/4
    ↓
   N/8
    ↓
   ...
    ↓
    1
```

- **Time Complexity:** $O(\log N)$

---

## 📋 2. Basic Template

For a sorted array `A`:

```java
int low = 0;
int high = A.length - 1;

while (low <= high) {
    int mid = low + (high - low) / 2;

    if (A[mid] == target) {
        return mid;
    }
    else if (A[mid] < target) {
        low = mid + 1;
    }
    else {
        high = mid - 1;
    }
}

return -1;
```

### 🧠 The Three Cases to Remember

| Case | Meaning | Action |
| :--- | :--- | :--- |
| `A[mid] == target` | Element found | Return `mid` |
| `A[mid] < target` | Target lies to the **RIGHT** | `low = mid + 1` |
| `A[mid] > target` | Target lies to the **LEFT** | `high = mid - 1` |

---

## 🎯 3. Walkthrough Example

Given:
- **Array:** `A = [2, 5, 8, 12, 16, 23, 38, 45, 56]`
- **Target:** `23`

### Step 1: Initial State
- `low = 0`, `high = 8`
- $\text{mid} = \frac{0 + 8}{2} = 4$
- `A[mid] = A[4] = 16`
- **Comparison:** $16 < 23$ (`A[mid] < target` $\rightarrow$ target is on the right)
- **Boundary update:** `low = mid + 1 = 4 + 1 = 5`

```text
[2, 5, 8, 12, 16, | 23, 38, 45, 56]
                   ^               ^
                  low=5          high=8
```

### Step 2: Second Iteration
- `low = 5`, `high = 8`
- $\text{mid} = \frac{5 + 8}{2} = 6$
- `A[mid] = A[6] = 38`
- **Comparison:** $38 > 23$ (`A[mid] > target` $\rightarrow$ target is on the left)
- **Boundary update:** `high = mid - 1 = 6 - 1 = 5`

```text
[23, 38, 45, 56]
 ^   ^
low high
(low = 5, high = 5)
```

### Step 3: Third Iteration
- `low = 5`, `high = 5`
- $\text{mid} = \frac{5 + 5}{2} = 5$
- `A[mid] = A[5] = 23`
- **Comparison:** $23 == 23$ (`A[mid] == target`)
- 🎯 **Found at index 5!**

---

## ❓ 4. Key Questions & Nuances

### Why do we change `low` or `high` instead of changing `mid`?
`low` and `high` define our **current active search area**. We do not manually adjust `mid`; rather, `mid` is always computed dynamically from the boundaries `low` and `high`.

### Why not simply do `mid++`?
Binary search is designed to throw away **half of the search space** in each step, not step forward by one index.

If `low = 0`, `high = 1000`, `mid = 500`, and $\text{target} > A[500]$:
- ❌ **Doing `mid++` $\rightarrow 501$:** You would end up checking almost every remaining element sequentially ($O(N)$ behavior).
- ✅ **Doing `low = mid + 1` $\rightarrow 501$:** Recalculates $\text{mid} = \frac{501 + 1000}{2} = 750$, jumping straight to the middle of the remaining half ($O(\log N)$ behavior).

---

## 🧠 5. Mental Model

```text
low ───────────── mid ───────────── high
         ↓
    eliminate one side
         ↓
  change low / high
         ↓
   recalculate mid
```

### Virtual Array Reduction
We do not physically copy or allocate a new array. Instead, `low` and `high` define the smaller window of interest after each step:

```text
Check middle ──→ Eliminate half ──→ Shrink window bounds ──→ Recalculate middle ──→ Repeat
```
