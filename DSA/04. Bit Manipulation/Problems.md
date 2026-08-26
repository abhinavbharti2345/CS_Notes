# Bit Manipulation Problems

> **Master Note:** [[Bit Manipulation]]  
> **Related Notes:** [[XOR Patterns]] | [[Bit Tricks]] | [[Bitwise Operators]]

---

## 1. Single Number

### Problem
Given an array `A[]` where every number occurs **twice** except **one** element that occurs **once**, find that single unique element.

### Example
```
A = [4, 5, 5, 4, 1, 6, 6]        →   Answer = 1
A = [7, 5, 5, 1, 7, 6, 1, 6, 4]  →   Answer = 4
```

### Key Observation
From [[XOR Patterns]]:
- $A \oplus A = 0$ (identical pairs cancel out to zero)
- $A \oplus 0 = A$ (XOR with zero preserves the value)

Because XOR is commutative and associative, we can rearrange the entire array XOR sequence:
```
  4 ^ 5 ^ 5 ^ 4 ^ 1 ^ 6 ^ 6
= (4 ^ 4) ^ (5 ^ 5) ^ (6 ^ 6) ^ 1
= 0 ^ 0 ^ 0 ^ 1
= 1
```

### Approach
Iterate through the array and accumulate the XOR of every element into a running variable `ans` initialized to `0`. All paired elements cancel out, leaving only the unique number.

### Algorithm
```java
int singleNumber(int[] A) {
    int ans = 0;
    for (int x : A) {
        ans ^= x;
    }
    return ans;
}
```

### Complexity
- **Time Complexity:** $O(N)$ — single pass over the array
- **Space Complexity:** $O(1)$ — constant auxiliary space

### Bit-Count Alternative
As observed in [[XOR Patterns#4. Bit-Count XOR Observation|Bit-Count XOR Observation]], counting the frequency of set bits across all numbers at each bit position (0 to 31) reveals that any bit with an **odd count** belongs to the unique number.

### Pattern / When to Use
Use XOR cancellation whenever elements appear in pairs (or even frequencies) and exactly one element has an odd frequency.

---

## 2. Two Missing Numbers

### Problem
Given an array `A[]` of length $N$ containing distinct integers from the range $[1, N+2]$. Exactly two numbers from that range are missing. Find the two missing numbers.

### Example
```
A = [5, 1, 3, 6]   →   Range [1, 6]   →   Missing: {2, 4}
A = [3, 2, 4]       →   Range [1, 5]   →   Missing: {1, 5}
```

---

### Approach 1 — Sorting

Sort the array, then iterate from $1$ to $N+2$ comparing each expected number against the current pointer in the sorted array.

```
A = [5, 1, 3, 6]
Sorted:   [1, 3, 5, 6]
Expected: [1, 2, 3, 4, 5, 6]
Missing:       2     4
```

- **Time Complexity:** $O(N \log N)$
- **Space Complexity:** $O(1)$ (in-place sort)

---

### Approach 2 — Sum and Square Sum

Let the two missing numbers be $x$ and $y$.

#### Step 1 — Linear Sum:
Total expected sum of numbers from $1$ to $N+2$:
$$S = \frac{(N+2)(N+3)}{2}$$

$$x + y = S - \sum_{i=0}^{N-1} A[i]$$

#### Step 2 — Sum of Squares:
Total expected sum of squares of numbers from $1$ to $N+2$:
$$T = \frac{(N+2)(N+3)(2(N+2)+1)}{6}$$

$$x^2 + y^2 = T - \sum_{i=0}^{N-1} A[i]^2$$

#### Step 3 — Solve System of Equations:
Using $(x - y)^2 = 2(x^2 + y^2) - (x + y)^2$, find $(x - y)$, and then compute $x$ and $y$.

- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(1)$
- *Caveat:* Potential integer overflow with large values during square calculations.

---

### Approach 3 — XOR Partitioning (Optimal)

#### Key Steps:
1. **XOR Everything:** XOR all elements of $A$ and all integers from $1$ to $N+2$.
   - All present elements appear twice and cancel out.
   - Result: `xorAll` = $x \oplus y$.
2. **Find a Differing Bit:** Since $x \ne y$, $x \oplus y \ne 0$. There must be at least one set bit (`1`) in `xorAll`. Let its position be `pos`.
   - At bit position `pos`, one missing number has a `1` and the other has a `0`.
3. **Partition & XOR:** Divide all numbers (both array elements and range $[1, N+2]$) into two groups based on whether bit `pos` is `0` or `1`, and XOR each group separately:
   - Group 0 (bit `pos` == 0) $\to$ XOR yields $x$.
   - Group 1 (bit `pos` == 1) $\to$ XOR yields $y$.

#### Class Worked Example:
```
A = [5, 1, 3, 6]   →   Range [1, 6]   →   Missing: {2, 4}

xorAll = (5 ^ 1 ^ 3 ^ 6) ^ (1 ^ 2 ^ 3 ^ 4 ^ 5 ^ 6)
       = 2 ^ 4 = 6 = 110₂

pos = 1  (bit 1 is set)

Group with bit 1 = 0:
  Numbers: {1, 4, 5, 1, 4, 5} → XOR = 4

Group with bit 1 = 1:
  Numbers: {3, 6, 2, 3, 6}    → XOR = 2

Missing numbers = {2, 4}  ✓
```

### Algorithm
```java
int[] twoMissingNumbers(int[] A, int N) {
    // Step 1: XOR everything together
    int xorAll = 0;
    for (int v : A) xorAll ^= v;
    for (int i = 1; i <= N + 2; i++) xorAll ^= i;

    // Step 2: Find a set bit position
    int pos = 0;
    while (((xorAll >> pos) & 1) == 0) pos++;

    // Step 3: Partition and XOR separately
    int x = 0, y = 0;
    for (int v : A) {
        if (((v >> pos) & 1) == 0) x ^= v;
        else y ^= v;
    }
    for (int i = 1; i <= N + 2; i++) {
        if (((i >> pos) & 1) == 0) x ^= i;
        else y ^= i;
    }
    return new int[]{x, y};
}
```

### Complexity
- **Time Complexity:** $O(N)$
- **Space Complexity:** $O(1)$

### Pattern / When to Use
Use XOR Partitioning whenever two distinct elements need to be separated from a collection of paired elements.

---

## 3. Minimum XOR Pair

### Problem
Given an integer array `A[]` of $N$ integers, find the **minimum XOR value** among all pairs $(i, j)$ where $i \ne j$.

### Example
```
A = [0, 2, 5, 7]

0 ^ 2 = 2   0 ^ 5 = 5   0 ^ 7 = 7
2 ^ 5 = 7   2 ^ 7 = 5   5 ^ 7 = 2

Answer = 2
```

```
A = [3, 10, 12, 4, 7, 14]   →   Answer = 2  (= 0010₂)
```

### Key Observation
XOR represents bitwise difference. Two numbers that are **close in value** share more leading (most significant) bits in common, which results in a smaller XOR value.
- After sorting the array in ascending order, the minimum XOR pair is **guaranteed to be adjacent** ($A[i]$ and $A[i+1]$).
- It is never necessary to check non-adjacent pairs after sorting.

### Approach
1. Sort array `A[]` in ascending order.
2. Initialize `ans = A[0] ^ A[1]`.
3. Iterate through adjacent pairs $i$ from $1$ to $N-2$, updating `ans = min(ans, A[i] ^ A[i+1])`.
4. Return `ans`.

### Algorithm
```java
int minXorPair(int[] A) {
    Arrays.sort(A);
    int ans = A[0] ^ A[1];
    for (int i = 1; i < A.length - 1; i++) {
        ans = Math.min(ans, A[i] ^ A[i + 1]);
    }
    return ans;
}
```

### Complexity
- **Time Complexity:** $O(N \log N)$ — dominated by sorting
- **Space Complexity:** $O(1)$ (or $O(\log N)$ depending on sort implementation)

> [!note] Source Note
> The class handwritten notes appear to write "max" in the final line of the algorithm, which contradicts the problem statement (minimum XOR). This looks like a transcription error. The clearly intended operation is **minimum**; the algorithm above uses `Math.min` accordingly.

### Pattern / When to Use
Whenever minimizing XOR across all pairs, sort the numbers first to bring numbers with matching high-order prefixes together.

---

## 4. Sum of XOR of All Pairs

### Problem
Given an array `A[]` of $N$ integers, find the **sum of XOR of all pairs** $(i, j)$ where $i < j$.
Return the answer **modulo $10^9 + 7$**.

### Example
```
A = [3, 4, 2]

3 ^ 4 = 7
3 ^ 2 = 1
4 ^ 2 = 6

Sum = 7 + 1 + 6 = 14
```

### Key Observation
Calculating all pairs directly requires $O(N^2)$ time. To optimize to $O(N)$, analyse each **bit position independently** (Contribution Technique).

For any fixed bit position $b$ ($0 \le b < 32$):
- Let `count0` = number of elements in $A$ with bit $b = 0$.
- Let `count1` = number of elements in $A$ with bit $b = 1$.

A pair of numbers $(A[i], A[j])$ produces a `1` at bit $b$ in $(A[i] \oplus A[j])$ **if and only if** one number has bit $b = 0$ and the other has bit $b = 1$.

- **Number of pairs with 1 at bit $b$:**
  $$\text{Pairs} = \text{count0} \times \text{count1}$$

- **Total contribution of bit $b$ to the sum:**
  $$\text{Contribution}_b = \text{count0} \times \text{count1} \times 2^b$$

Summing contributions across all 32 bits gives the total sum of XOR for all pairs.

### Class Worked Example
```
A = [2, 3, 5, 7, 11, 13]

Bit contributions (derived in class):
- Bit 0 to 5 contributions: 64 + 36 + 16 + 5 = 121

Answer = 121
```

### Algorithm
```java
int sumXorPairs(int[] A, int N) {
    long ans = 0;
    long MOD = 1_000_000_007L;

    for (int b = 0; b < 32; b++) {
        long x = 0, y = 0;   // x = count of 0s, y = count of 1s

        for (int i = 0; i < N; i++) {
            if ((A[i] & (1 << b)) == 0) x++;
            else y++;
        }

        ans = (ans + (x * y) % MOD * (1L << b) % MOD) % MOD;
    }

    return (int) ans;
}
```

### Complexity
- **Time Complexity:** $O(N)$ — outer loop runs exactly 32 times ($32 \times N = O(N)$)
- **Space Complexity:** $O(1)$ — only counters and accumulators

### Pattern / When to Use
Use the **Bit Contribution Technique** whenever you need to compute aggregate bitwise expressions (sum of XOR/AND/OR of all pairs or subsets) across arrays.

---

## 5. Complexity Summary Table

| Problem | Approach | Time Complexity | Space Complexity |
| :--- | :--- | :---: | :---: |
| **Single Number** | XOR Accumulation | $O(N)$ | $O(1)$ |
| **Two Missing Numbers** | Sorting Scan | $O(N \log N)$ | $O(1)$ |
| **Two Missing Numbers** | Sum & Square Sum | $O(N)$ | $O(1)$ |
| **Two Missing Numbers** | XOR Partitioning (Optimal) | $O(N)$ | $O(1)$ |
| **Minimum XOR Pair** | Sort + Adjacent Check | $O(N \log N)$ | $O(1)$ |
| **Sum of XOR of All Pairs** | Bit Contribution (32 bits) | $O(N)$ | $O(1)$ |

---

## Navigation

- **Back to Master Note:** [[Bit Manipulation]]
- **XOR Patterns:** [[XOR Patterns]]
- **Bit Techniques:** [[Bit Tricks]]
- **Operators:** [[Bitwise Operators]]
