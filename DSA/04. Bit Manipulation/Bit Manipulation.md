---
topic: Data Structures & Algorithms
subtopic: Bit Manipulation
type: moc
tags:
  - dsa
  - bit-manipulation
  - algorithms
  - binary
date: 2026-09-05
---

# ⚡ Bit Manipulation

> [!important] Core Concept
> At the hardware and memory level, every integer is stored internally as a sequence of binary digits or **bits** (`0` or `1`). Understanding bit-level representation enables writing highly optimized algorithms ($O(1)$ time, $O(1)$ auxiliary space), solving parity and cancellation problems, and working directly with bit masks and flags.

---

## 📖 Module Learning Path

1. **[[Bitwise Operators]]**
   - Fundamental operators: AND (`&`), OR (`|`), XOR (`^`), NOT (`~`)
   - Truth tables and operator algebraic properties (Commutative, Associative)
   - Decimal arithmetic examples (`20 & 45`, `20 | 45`, `20 ^ 45`)

2. **[[Bit Tricks]]**
   - Parity check (`N & 1` for Even/Odd)
   - Left Shift (`<<`) and Right Shift (`>>`) arithmetic formulas
   - Single-bit mask operations: Check Bit, Set Bit, Flip Bit, Unset Bit

3. **[[XOR Patterns]]**
   - Core XOR identities ($A \oplus 0 = A$, $A \oplus A = 0$)
   - Duplicate cancellation and associative rearrangement
   - Bit-count frequency observation across 32 bit positions

4. **[[Bit Manipulation Problems]]**
   - **Single Number:** $O(N)$ time, $O(1)$ space using XOR cancellation
   - **Two Missing Numbers:** Sorting vs Math vs XOR Partitioning
   - **Minimum XOR Pair:** Sorting and adjacent scanning
   - **Sum of XOR of All Pairs:** Bit contribution technique across 32 bit positions

---

## 1. Binary Representation & Positions

### Binary Representation (8-bit Example)

| Decimal | Binary (8-bit) | Formula |
| :---: | :---: | :--- |
| **20** | `0001 0100` | $16 + 4$ |
| **45** | `0010 1101` | $32 + 8 + 4 + 1$ |
| **255** | `1111 1111` | $2^8 - 1 = 255$ |

### Bit Positions & Indexing
- Bit positions are **0-indexed from the right** (Least Significant Bit or LSB).
- The bit at index $i$ carries a weight of $2^i$.
- For example, in $20 = 10100_2$:
  - Bit 0 (weight $2^0 = 1$): `0`
  - Bit 1 (weight $2^1 = 2$): `0`
  - Bit 2 (weight $2^2 = 4$): `1`
  - Bit 3 (weight $2^3 = 8$): `0`
  - Bit 4 (weight $2^4 = 16$): `1`
  - Total decimal value = $16 + 4 = 20$.

---

## 2. ⚡ Quick Revision Cheat Sheet

### Operators & Identities

| Symbol | Operation | Core Identity |
| :---: | :--- | :--- |
| `&` | AND | $A \& 0 = 0, \quad A \& A = A$ |
| <code>&#124;</code> | OR | $A \mid 0 = A, \quad A \mid A = A$ |
| `^` | XOR | $A \oplus 0 = A, \quad A \oplus A = 0$ |
| `~` | NOT | Inverts every bit (bitwise complement) |

- **Commutative:** $A \& B = B \& A, \quad A \| B = B \| A, \quad A \oplus B = B \oplus A$
- **Associative:** $(A \oplus B) \oplus C = A \oplus (B \oplus C)$

### Bit Formulas (Position $i$, 0-indexed from right)

```text
Parity:      N & 1             → 1 = Odd,  0 = Even
Left Shift:  A << n            = A × 2ⁿ     (multiply by 2ⁿ)
Right Shift: A >> n            = ⌊A / 2ⁿ⌋   (floor division by 2ⁿ)

Check Bit:   N & (1 << i)      → Non-zero if bit i is 1, 0 if bit i is 0
Set Bit:     N | (1 << i)      → Force bit i to 1
Flip Bit:    N ^ (1 << i)      → Toggle bit i (0 ↔ 1)
Unset Bit:   N & ~(1 << i)     → Force bit i to 0

All-1s Mask: -1L               → 1111...1111 (all 64 bits set in two's complement)
B Zeros End: -1L << B          → 1111...0000 (B trailing zeros)
B Ones End:  ~(-1L << B)       → 0000...1111 (B trailing ones)

Count 1s:    Integer.bitCount(N) → O(1) hardware count (e.g. 13 = 1101 -> 3)
Count 1s:    N = N & (N - 1)     → Brian Kernighan algorithm O(set bits)
```

### Complexity Summary

| Problem | Time Complexity | Space Complexity | Primary Technique |
| :--- | :---: | :---: | :--- |
| **Single Number** | $O(N)$ | $O(1)$ | XOR Accumulation |
| **Two Missing — Sorting** | $O(N \log N)$ | $O(1)$ | Array Sorting |
| **Two Missing — Math** | $O(N)$ | $O(1)$ | Linear & Square Sum |
| **Two Missing — XOR (Optimal)** | $O(N)$ | $O(1)$ | Set-Bit Partitioning |
| **Minimum XOR Pair** | $O(N \log N)$ | $O(1)$ | Sort + Adjacent Check |
| **Sum of XOR of All Pairs** | $O(N)$ | $O(1)$ | Bit Contribution |

---

## 🔗 Related Notes
- [[DSA/README|🌳 DSA Master MOC]]
- [[Quick Look|⚡ Quick Look (Java / DSA Cheatsheet)]]
- [[Bitwise Operators]]
- [[Bit Tricks]]
- [[XOR Patterns]]
- [[Bit Manipulation Problems]]
- [[Dashboard|🧭 Main Command Center]]
