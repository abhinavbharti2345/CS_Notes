---
topic: Data Structures & Algorithms
type: reference
tags:
  - dsa
  - java
  - cheatsheet
  - quick-look
  - reference
date: 2026-09-08
---

# ⚡ Quick Look: Java DSA Cheatsheet & "Take a Look" Reference

> [!tip] Purpose & How to Use
> A rapid, high-yield reference for easily forgotten syntax, standard library methods, constants, boilerplates, and edge-case gotchas during DSA problem solving in Java.
> 
> *Whenever you encounter tricky or frequently forgotten syntax, add it here under its corresponding section!*

---

## 🧭 Navigation & Connections
- 🏠 **Parent Hub:** [[DSA/README|DSA Master Roadmap]]
- 🧭 **Command Center:** [[Dashboard]]
- ⚡ **Related Topics:** [[Bit Manipulation]] | [[Bit Tricks]] | [[Bitwise Operators]]

---

## 🔢 1. Number & Math Essentials

### Constants & Limits
```java
// Integer bounds (32-bit signed: -2^31 to 2^31 - 1)
int maxInt = Integer.MAX_VALUE; //  2,147,483,647 (~2 * 10^9)
int minInt = Integer.MIN_VALUE; // -2,147,483,648

// Long bounds (64-bit signed: -2^63 to 2^63 - 1)
long maxLong = Long.MAX_VALUE;  //  9,223,372,036,854,775,807 (~9 * 10^18)
long minLong = Long.MIN_VALUE;

// All-ones masks (Two's complement: -1 has all bits set to 1)
int allOnesInt = -1;            // 32 ones: 11111111...1111 (0xFFFFFFFF)
long allOnesLong = -1L;         // 64 ones: 11111111...1111 (0xFFFFFFFFFFFFFFFFL)

// Double / Float Infinity
double posInf = Double.POSITIVE_INFINITY;
double negInf = Double.NEGATIVE_INFINITY;
```

### Common Math Methods
```java
Math.max(a, b);
Math.min(a, b);
Math.abs(a);
Math.pow(base, exp);       // returns double
Math.sqrt(val);            // returns double
Math.ceil(val);            // rounds up (returns double)
Math.floor(val);           // rounds down (returns double)

// Safe Midpoint Calculation (Avoids integer overflow)
int mid = low + (high - low) / 2;

// GCD (Euclidean Algorithm)
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}
```

---

## 📊 2. Arrays & Matrices

### Array Utilities (`java.util.Arrays`)
```java
import java.util.Arrays;

// Sorting primitives (ascending)
Arrays.sort(arr);

// Sorting subarray [fromIndex, toIndex)
Arrays.sort(arr, 0, k);

// Fill array
Arrays.fill(arr, -1);
Arrays.fill(arr, false);

// Copying arrays
int[] copy = Arrays.copyOf(arr, arr.length);
int[] sub = Arrays.copyOfRange(arr, startIdx, endIdx); // endIdx is exclusive

// 2D Array Comparison & Printing (Debugging)
System.out.println(Arrays.toString(arr));
System.out.println(Arrays.deepToString(matrix));

// Binary search on sorted array (returns index or negative insertion point)
int idx = Arrays.binarySearch(sortedArr, target);
```

### Sorting 2D Arrays & Custom Objects
```java
// Sort 2D array by first column (ascending)
Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

// Sort by first column asc, then second column desc (e.g., Russian Doll Envelopes)
Arrays.sort(envelopes, (a, b) -> {
    if (a[0] == b[0]) return Integer.compare(b[1], a[1]);
    return Integer.compare(a[0], b[0]);
});

// ⚠️ GOTCHA: Avoid `a[0] - b[0]` to prevent integer subtraction overflow! Use `Integer.compare(a[0], b[0])`.
```

---

## 🔤 3. Strings & Characters

### String Essentials
```java
String s = "leetcode";

int len = s.length();                 // note: method (), unlike arr.length
char c = s.charAt(i);
char[] chars = s.toCharArray();
String sub = s.substring(start, end); // [start, end)
int idx = s.indexOf("sub");           // -1 if not found
boolean starts = s.startsWith("pre");
boolean ends = s.endsWith("suf");

// Conversions
String strFromNum = String.valueOf(123);
int numFromStr = Integer.parseInt("123");
long longFromStr = Long.parseLong("12345678901");
```

### Character Utilities (`Character`)
```java
Character.isLetterOrDigit(c);
Character.isDigit(c);
Character.isLetter(c);
Character.toLowerCase(c);
Character.toUpperCase(c);

// Char to integer offset tricks
int digit = c - '0';       // '5' -> 5
int alphabetIdx = c - 'a'; // 'c' -> 2
char fromIdx = (char)('a' + 2); // 'c'
```

### `StringBuilder` (Mutable Strings)
```java
StringBuilder sb = new StringBuilder();
sb.append("hello");
sb.append(' ');
sb.append(123);

sb.charAt(0);
sb.setCharAt(0, 'H');
sb.deleteCharAt(sb.length() - 1); // delete last char (backtracking)
sb.reverse();
String result = sb.toString();

// Right-to-Left Arithmetic Template (Add Binary / Add Strings)
// (i >= 0 || j >= 0 || carry != 0) with sb.append(sum % base) + sb.reverse()
int bit1 = (i >= 0) ? a.charAt(i) - '0' : 0;
int bit2 = (j >= 0) ? b.charAt(j) - '0' : 0;
```

---

## 🗃️ 4. Collections Framework (`java.util.*`)

### `ArrayList` (Dynamic Array)
```java
List<Integer> list = new ArrayList<>();
list.add(10);
list.add(0, 5);              // insert at index 0
int val = list.get(i);
list.set(i, 99);             // update at index i
list.remove(list.size() - 1); // remove last element (O(1))
list.remove((Integer) 10);   // remove by object value
int size = list.size();
boolean empty = list.isEmpty();

// Convert List<Integer> to int[]
int[] arr = list.stream().mapToInt(i -> i).toArray();

// Initialize with values
List<Integer> init = new ArrayList<>(Arrays.asList(1, 2, 3));
```

### `HashMap` (Key-Value Lookups)
```java
Map<String, Integer> map = new HashMap<>();

map.put("key", 1);
int count = map.getOrDefault("key", 0);
map.put("key", map.getOrDefault("key", 0) + 1); // frequency counter idiom
map.putIfAbsent("key", 100);

boolean hasKey = map.containsKey("key");
map.remove("key");

// Iterating Map
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    String k = entry.getKey();
    int v = entry.getValue();
}
```

### `HashSet` (Unique Elements)
```java
Set<Integer> set = new HashSet<>();
set.add(10);
boolean contains = set.contains(10);
set.remove(10);
```

### `PriorityQueue` (Heaps)
```java
// Min-Heap (default)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

// Max-Heap
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
// or with lambda
PriorityQueue<Integer> maxHeap2 = new PriorityQueue<>((a, b) -> Integer.compare(b, a));

// Custom Object Heap (e.g., [val, freq]) sorted by frequency asc
PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> Integer.compare(a[1], b[1]));

pq.offer(val);  // add element
int top = pq.peek(); // inspect min/max
int rem = pq.poll(); // remove and return min/max
```

### `Deque` / `ArrayDeque` (Stack & Queue)
```java
// Prefer ArrayDeque over Stack (Stack is synchronized & legacy)
Deque<Integer> stack = new ArrayDeque<>();
stack.push(10);  // add to top
int top = stack.peek();
int val = stack.pop(); // remove from top

// Queue (FIFO)
Deque<Integer> queue = new ArrayDeque<>();
queue.offer(10); // add to back
int head = queue.peek();
int out = queue.poll(); // remove from front
```

---

## ⚡ 5. Bit Manipulation High-Yield Tricks
*(Full deep dive: [[Bit Manipulation]], [[Bit Tricks]], [[Bitwise Operators]])*

```java
// Check if odd / even
boolean isOdd = (n & 1) != 0;

// Check if power of 2
boolean isPowerOfTwo = n > 0 && (n & (n - 1)) == 0;

// Clear lowest set bit
n = n & (n - 1);

// Isolate lowest set bit
int lowestSetBit = n & (-n);

// Built-in bit utilities
int countOnes = Integer.bitCount(n); // e.g. Integer.bitCount(13) == 3 (13 = 1101)
long countLong = Long.bitCount(longVal);
int leadingZeros = Integer.numberOfLeadingZeros(n);
int highestOne = Integer.highestOneBit(n);

// Count Set Bits manually (Brian Kernighan: O(set bits))
int count = 0;
while (n != 0) {
    n = n & (n - 1); // clears lowest set bit
    count++;
}

// -------------------------------------------------------------
// -1L (All-Ones 64-bit Mask) & Fast Mask Generation:
// -1L in two's complement = 11111111...1111 (all 64 bits are 1)
// -------------------------------------------------------------
long maskTrailingZeros = -1L << B;  // 1111...11000...000 (B zeros at bottom)
long maskTrailingOnes  = ~(-1L << B); // 0000...00111...111 (B ones at bottom)
long maskRangeLtoR     = (-1L << L) & ~(-1L << (R + 1)); // 1s from bit L to R
```

---

## ⚠️ 6. Common Pitfalls & Gotchas

> [!warning] Top Java DSA Traps to Avoid
> 1. **String Equality:** NEVER use `==` for String content comparison. Always use `s1.equals(s2)`.
> 2. **Integer Object Comparison:** In `Integer a, b`, `==` compares references for values outside the cache `[-128, 127]`. Always use `a.equals(b)` or `int` primitives.
> 3. **Array vs List Length:** `arr.length` (field), `str.length()` (method), `list.size()` (method).
> 4. **Comparator Overflow:** Never do `(a, b) -> a - b` when numbers can be negative or large (e.g. `Integer.MIN_VALUE` or `10^9`). Use `Integer.compare(a, b)`.
> 5. **Modulo Arithmetic:** For negative numbers, `(a % mod + mod) % mod`.

---

## 📝 7. Quick Capture / Add to Quick Look
*Got a new syntax snippet or forgot something while coding? Add it here or ask the AI to append it!*
