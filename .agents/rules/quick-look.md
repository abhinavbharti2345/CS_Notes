---
description: Rule for managing the Quick Look / Take a Look cheatsheet for frequently forgotten syntax and utilities
---

# Quick Look / Take a Look Cheatsheet Rule

## Purpose
The note located at `DSA/Quick Look.md` (wikilink: `[[Quick Look]]` or `[[DSA/Quick Look|Quick Look]]`) serves as the central, rapid-access cheatsheet for frequently forgotten syntax, standard library methods, constants, boilerplates, and edge-case pitfalls (primarily Java & DSA).

## Trigger Conditions
Automatically update or reference `DSA/Quick Look.md` whenever the user:
- Mentions they keep forgetting a piece of syntax, method, or idiom (e.g., `Arrays.sort`, `Integer.MAX_VALUE`, custom comparators, conversion syntax, etc.).
- Explicitly asks to "add this to quick look", "take a look", "cheatsheet", or "quick reference".
- Asks for a quick snippet or syntax reminder while solving DSA / coding problems.

## Actions to Take
1. **Locate & Inspect:** Check `DSA/Quick Look.md` for whether the snippet/concept already exists.
2. **Categorize Accurately:** Add new entries under the relevant section:
   - *Number & Math Essentials* (constants, bounds, modulo, overflow protection)
   - *Arrays & Matrices* (`Arrays.sort`, copy, fill, 2D sort)
   - *Strings & Characters* (`charAt`, `substring`, conversions, `StringBuilder`)
   - *Collections Framework* (`ArrayList`, `HashMap`, `HashSet`, `PriorityQueue`, `Deque`)
   - *Bit Manipulation Tricks* (masks, shifts, bitwise built-ins)
   - *Common Pitfalls & Gotchas* (reference equality vs value equality, comparator overflows, index boundaries)
3. **Format Clearly:** Provide clean, copy-paste ready code blocks with concise inline comments and warnings about common gotchas.
4. **Preserve Connections:** Keep wikilinks to relevant master notes (e.g., `[[Bit Manipulation]]`, `[[DSA/README]]`, `[[Dashboard]]`).
