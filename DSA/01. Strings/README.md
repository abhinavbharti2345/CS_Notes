---
topic: Data Structures & Algorithms
subtopic: Strings
type: moc
tags:
  - dsa
  - strings
  - algorithms
  - stringbuilder
date: 2026-09-08
---

# 🔤 Strings & String Manipulation

Welcome to the **Strings** module. Strings are one of the most foundational data structures in programming interviews, testing character arithmetic, two-pointer techniques, sliding windows, string builder memory models, and pattern matching.

---

## 🗺️ Module Learning Path

1. **[[DSA/01. Strings/StringBuilder|🏗️ StringBuilder (Architecture, Methods & DSA Patterns)]]**
   - In-depth look at mutable strings, memory buffer allocation, capacity growth ($2 \times \text{cap} + 2$), and performance.
   - Core API operations: `append()`, `insert()`, `deleteCharAt()`, `reverse()`, `setLength(0)`.
   - DSA patterns: Backtracking path rollback, right-to-left reversal, buffer reuse, and reference equality traps.

2. **[[DSA/01. Strings/Add Binary & String Arithmetic|➕ String Arithmetic & Add Binary]]**
   - Simulating column-by-column math from right to left (`i = A.length - 1`, `j = B.length - 1`).
   - Why `StringBuilder.append()` + `reverse()` beats `String` concatenation ($O(N)$ vs $O(N^2)$).
   - Base conversion and carry propagation (Binary Base 2 and Decimal Base 10).

---

## ⚡ Essential String Idioms (Java)
*(Full quick look: [[Quick Look]])*

```java
// Char to digit / digit to char
int digit = c - '0';
char c = (char) ('0' + digit);

// In-place reversal & mutation
StringBuilder sb = new StringBuilder();
sb.append(val);
sb.reverse().toString();

// Character tests
Character.isLetterOrDigit(c);
Character.toLowerCase(c);
```

---

## 🔗 Related Notes
- [[DSA/README|🌳 DSA Master Roadmap]]
- [[Quick Look|⚡ Quick Look & Cheatsheet]]
- [[Bit Manipulation|⚡ Bit Manipulation Master Note]]
- [[Dashboard|🧭 Main Command Center]]
