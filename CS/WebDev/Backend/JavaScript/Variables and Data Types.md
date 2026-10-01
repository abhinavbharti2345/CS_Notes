---
topic: JavaScript
type: concept
tags:
  - javascript
  - backend
  - fundamentals
date: 2026-09-04
---

# Variables and Data Types

## 🧠 What is a Variable?

A variable is simply a **named box in computer memory that holds a value**.

```text
  Variable Name: age
┌────────────────────┐
│         20         │  <-- Value stored in memory
└────────────────────┘
```

When you declare a variable, you allocate a location in memory:

```javascript
let name = "John";
console.log(name); // Output: John
```

---

## 🔒 Variable Declarations: `const` vs `let` vs `var`

In modern JavaScript and [[Introduction to Node.js|Node.js]] backend development, variable declarations use `const` and `let`.

```javascript
var   // ⚠️ Legacy JS (Function-scoped, prone to hoisting bugs; avoid in modern backends)
let   // ✅ Block-scoped; use when the value is expected to change
const // ✅ Block-scoped; use when the reference will never be reassigned
```

### 1. `let` (Mutable)
Use `let` when a value needs to be reassigned during runtime (e.g., counters, accumulated totals, state flags):

```javascript
let age = 20;
age = 21; // ✅ Allowed
```

### 2. `const` (Immutable Reference)
Use `const` by default. You cannot reassign a `const` variable to a new value:

```javascript
const serverPort = 5000;
// serverPort = 3000; // ❌ TypeError: Assignment to constant variable.
```

> [!important] Backend Convention
> In backend code, you will see **a massive amount of `const`**. We use `const` for imported libraries, database connections, model definitions, and route handlers:
> ```javascript
> const express = require("express");
> const mongoose = require("mongoose");
> const bcrypt = require("bcrypt");
> ```

---

## 📦 JavaScript Data Types

JavaScript categorizes values into primitive and complex types.

### 1. String (Text Data)
Represents text enclosed in single quotes `''`, double quotes `""`, or template literals ` `` `:

```javascript
const name = "John Doe";
const email = "john@gmail.com";
```

### 2. Number
Represents both integers and floating-point numbers:

```javascript
const age = 20;
const price = 499.99;
```

### 3. Boolean
Represents binary logical states: `true` or `false`:

```javascript
const isLoggedIn = true;
const isEmailVerified = false;
```

### 4. `null` (Intentional Emptiness)
Represents an intentional absence of any value. Used when a variable is deliberately empty:

```javascript
const currentUser = null; // Indicates no user is logged in
```

### 5. `undefined` (Unassigned)
Represents a variable that has been declared, but has not yet been assigned a value:

```javascript
let userProfile;
console.log(userProfile); // Output: undefined
```

> [!note] `null` vs `undefined`
> - `undefined` means: *"The variable exists, but JavaScript hasn't been given a value for it yet."*
> - `null` means: *"The developer explicitly set this value to indicate 'no data' or 'empty'."*

---

## 🛠️ Essential String Utility Methods for Backend

### 1. `.toLowerCase()`
Converts text to lowercase. Essential for normalizing user inputs (such as emails) before database queries:

```javascript
const rawEmail = "John.Doe@GMAIL.COM";
const normalizedEmail = rawEmail.toLowerCase();

console.log(normalizedEmail); // "john.doe@gmail.com"
```

### 2. `.split(separator)`
Splits a string into an array based on a delimiter:

```javascript
const csvTags = "tech,nodejs,backend";
const tagList = csvTags.split(",");

console.log(tagList); // ["tech", "nodejs", "backend"]
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- Basic understanding of programming concepts.

### Next Step
- [[Objects and Destructuring]] — Grouping related customer data and extracting fields from HTTP payloads.

## 🔗 Related Notes
- [[JavaScript Foundations|📁 JavaScript Foundations MOC]]
- [[Objects and Destructuring]]
- [[Functions and Control Flow]]
- [[Introduction to Node.js]]
