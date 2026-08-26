# Bit Manipulation

> **Folder:** `DSA/04. Bit Manipulation`  
> **Source:** Class revision PDFs (Bit Manipulation + XOR Problems)

---

## Topics

- [[Bitwise Operators]]
- [[Bit Tricks]]
- [[XOR Patterns]]
- [[Problems]]

---

## 1. Introduction & Binary Representation

At the hardware and memory level, every integer is stored internally as a sequence of binary digits or **bits** (either `0` or `1`).

Understanding bit-level representation enables writing highly optimized algorithms ($O(1)$ time, $O(1)$ auxiliary space), solving parity and cancellation problems, and working directly with bit masks and flags.

### Binary Representation (8-bit Example)

| Decimal | Binary (8-bit) |
| :--- | :--- |
| 20 | `0001 0100` |
| 45 | `0010 1101` |
| 255 | `1111 1111` |

**8-bit maximum unsigned value:**
$$11111111_2 = 2^8 - 1 = 255$$

---

## 2. Bit Positions & Indexing

In standard binary representations:
- Bit positions are **0-indexed from the right** (Least Significant Bit or LSB).
- The bit at index $i$ carries a weight of $2^i$.
- For example, in $20 = 10100_2$:
  - Bit 0 (weight $2^0 = 1$): `0`
  - Bit 1 (weight $2^1 = 2$): `0`
  - Bit 2 (weight $2^2 = 4$): `1`
  - Bit 3 (weight $2^3 = 8$): `0`
  - Bit 4 (weight $2^4 = 16$): `1`
  - Total decimal value = $16 + 4 = 20$.

To manipulate or inspect specific bit positions, see [[Bit Tricks]].

---

## 3. Section Overview

The material is structured into dedicated modular notes:

1. **[[Bitwise Operators]]**
   - Fundamental operators: AND (`&`), OR (`|`), XOR (`^`), NOT (`~`)
   - Truth tables and operator algebraic properties (Commutative, Associative)
   - Arithmetic class examples (`20 & 45`, `20 | 45`, `20 ^ 45`)

2. **[[Bit Tricks]]**
   - Parity check (`N & 1` for Even/Odd)
   - Left Shift (`<<`) and Right Shift (`>>`) formulas
   - Targeted bit operations: Check Bit, Set Bit, Flip Bit, Unset Bit using bit masks

3. **[[XOR Patterns]]**
   - Core XOR identities ($A \oplus 0 = A$, $A \oplus A = 0$)
   - Cancellation and rearrangement properties
   - Pattern recognition guide for coding interviews
   - Bit-count observation and theoretical foundation

4. **[[Problems]]**
   - **Single Number:** $O(N)$ time, $O(1)$ space using XOR cancellation
   - **Two Missing Numbers:** Sorting vs Sum/Square Sum vs XOR Partitioning
   - **Minimum XOR Pair:** Sorting and adjacent scanning
   - **Sum of XOR of All Pairs:** Bit contribution technique across 32 bit positions

---

## 4. ⚡ Quick Revision Cheat Sheet

### Operators & Properties

| Symbol | Operation | Core Identity |
| :---: | :--- | :--- |
| `&` | AND | $A \& 0 = 0, \quad A \& A = A$ |
| `\|` | OR | $A \| 0 = A, \quad A \| A = A$ |
| `^` | XOR | $A \oplus 0 = A, \quad A \oplus A = 0$ |
| `~` | NOT | Inverts every bit (bitwise complement) |

- **Commutative:** $A \& B = B \& A, \quad A \| B = B \| A, \quad A \oplus B = B \oplus A$
- **Associative:** $(A \oplus B) \oplus C = A \oplus (B \oplus C)$ (holds for `&`, `|`, and `^`)

### Bit Formulas (Position $i$, 0-indexed from right)

```
Parity:      N & 1             → 1 = Odd,  0 = Even
Left Shift:  A << n            = A × 2ⁿ     (multiply by 2ⁿ)
Right Shift: A >> n            = ⌊A / 2ⁿ⌋   (floor division by 2ⁿ)

Check Bit:   N & (1 << i)      → Non-zero if bit i is 1, 0 if bit i is 0
Set Bit:     N | (1 << i)      → Force bit i to 1
Flip Bit:    N ^ (1 << i)      → Toggle bit i (0 ↔ 1)
Unset Bit:   N & ~(1 << i)     → Force bit i to 0
```

### XOR Pattern Quick Map

```
Single Number        → XOR all elements (pairs cancel: A ^ A = 0)

Two Missing Numbers  → 1. XOR (array + full range [1..N+2]) → gives x ^ y
                       2. Find any set bit position pos in x ^ y
                       3. Partition all numbers by bit pos and XOR separately → gives x and y

Minimum XOR Pair     → Sort array → scan adjacent pairs (A[i] ^ A[i+1]) → take minimum

Sum of XOR of Pairs  → For each bit b (0 to 31):
                          contribution = count0 × count1 × 2^b
                       Sum contributions over all 32 bits
```

### Complexity Summary

| Problem | TC | SC | Primary Technique |
| :--- | :---: | :---: | :--- |
| **Single Number** | $O(N)$ | $O(1)$ | XOR Accumulation |
| **Two Missing — Sorting** | $O(N \log N)$ | $O(1)$ | Array Sorting |
| **Two Missing — Sum / Math** | $O(N)$ | $O(1)$ | Linear & Square Sum |
| **Two Missing — XOR (Optimal)** | $O(N)$ | $O(1)$ | Set-Bit Partitioning |
| **Minimum XOR Pair** | $O(N \log N)$ | $O(1)$ | Sort + Adjacent Check |
| **Sum of XOR of All Pairs** | $O(N)$ | $O(1)$ | Bit Contribution |

---

## Related Topics

- [[Dashboard]]
