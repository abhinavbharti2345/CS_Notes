# Bit Tricks

> **Master Note:** [[Bit Manipulation]]  
> **Related Notes:** [[Bitwise Operators]] | [[XOR Patterns]] | [[Problems]]

---

## 1. Even / Odd Check

Checking parity using bitwise AND is faster than modulo arithmetic (`N % 2`).

```
N & 1
```

| Result | Meaning |
| :---: | :--- |
| `1` | **Odd** |
| `0` | **Even** |

### Why It Works
In binary representation, every bit position $i \ge 1$ represents an even value ($2^1 = 2, 2^2 = 4, 2^3 = 8, \dots$). Only bit 0 (the LSB) represents an odd value ($2^0 = 1$).
- If bit 0 is `1`, the number is odd.
- If bit 0 is `0`, the number is even.
- `N & 1` isolates bit 0 and masks out all higher bits.

---

## 2. Left Shift (`<<`)

Left shifting moves all bits to the left by $n$ positions, filling vacated bits on the right with `0`.

**Formula:**
$$A \ll n = A \times 2^n$$

| Expression | Calculation | Result |
| :--- | :--- | :---: |
| `10 << 1` | $10 \times 2^1$ | `20` |
| `10 << 2` | $10 \times 2^2$ | `40` |
| `10 << 3` | $10 \times 2^3$ | `80` |
| `10 << 4` | $10 \times 2^4$ | `160` |
| `10 << 5` | $10 \times 2^5$ | `320` |

> [!tip] Key Takeaway
> Each left shift by 1 effectively **multiplies the number by 2**.

---

## 3. Right Shift (`>>`)

Right shifting moves all bits to the right by $n$ positions, discarding the rightmost bits.

**Formula:**
$$A \gg n = \lfloor A / 2^n \rfloor \quad (\text{integer / floor division})$$

| Expression | Calculation | Result |
| :--- | :--- | :---: |
| `10 >> 1` | $\lfloor 10 / 2^1 \rfloor$ | `5` |
| `10 >> 2` | $\lfloor 10 / 2^2 \rfloor$ | `2` |
| `10 >> 3` | $\lfloor 10 / 2^3 \rfloor$ | `1` |
| `10 >> 4` | $\lfloor 10 / 2^4 \rfloor$ | `0` |

> [!tip] Key Takeaway
> Each right shift by 1 effectively **divides the number by 2** (floor division).

---

## 4. Bit Manipulation Operations

Let `i` = **bit position** (0-indexed from the right).

The fundamental building block for targeted bit manipulation is the single-bit mask:
```
1 << i
```
This produces a binary value where only the $i$-th bit is `1` and all other bits are `0`.

---

### Check Bit (Is bit $i$ set?)

To test whether the $i$-th bit is `1` or `0`:

```
N & (1 << i)
```

- **Non-zero (`> 0` / `!= 0`)** $\to$ Bit $i$ is **1** (set).
- **Zero (`== 0`)** $\to$ Bit $i$ is **0** (unset).

*Alternative:* `(N >> i) & 1` evaluates directly to `1` or `0`.

---

### Set Bit (Force bit $i$ to 1)

To turn bit $i$ ON without modifying any other bit:

```
N | (1 << i)
```

- If bit $i$ was `0`, it becomes `1`.
- If bit $i$ was already `1`, it remains `1`.

---

### Flip Bit (Toggle bit $i$)

To toggle bit $i$ ($0 \to 1$ or $1 \to 0$):

```
N ^ (1 << i)
```

- Since $0 \oplus 1 = 1$ and $1 \oplus 1 = 0$, XOR-ing with `1` inverts the target bit.
- All other bits XOR-ed with `0` remain unchanged ($A \oplus 0 = A$).

---

### Unset Bit (Force bit $i$ to 0)

To turn bit $i$ OFF without modifying any other bit:

```
N & ~(1 << i)
```

#### Why It Works:
- `(1 << i)` has only bit $i$ set.
- `~(1 << i)` creates a mask where **every bit is 1 except bit $i$**, which is 0.
- AND-ing `N` with this inverted mask forces bit $i$ to `0` while keeping all other bits identical ($A \& 1 = A$).

> [!note] Source Note
> The class handwritten notes discuss "check + flip" and show the mask `~(1 << i)` for unsetting. This material is preserved faithfully.

---

## Summary of Operations

| Operation | Formula | Mask Used |
| :--- | :--- | :--- |
| **Check $i$-th bit** | `N & (1 << i)` | `1 << i` |
| **Set $i$-th bit** | `N \| (1 << i)` | `1 << i` |
| **Flip $i$-th bit** | `N ^ (1 << i)` | `1 << i` |
| **Unset $i$-th bit** | `N & ~(1 << i)` | `~(1 << i)` |

---

## Navigation

- **Back to Master Note:** [[Bit Manipulation]]
- **Operators:** [[Bitwise Operators]]
- **XOR Techniques:** [[XOR Patterns]]
- **Applied Problems:** [[Problems]]
