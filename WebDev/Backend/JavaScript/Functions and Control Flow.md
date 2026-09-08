---
topic: JavaScript
type: concept
tags:
  - javascript
  - backend
  - functions
  - control-flow
date: 2026-09-04
---

# Functions and Control Flow

## 🧠 Functions in Backend JavaScript

A **function** is a reusable block of code designed to perform a specific task.

```javascript
// Function Definition
function greet(name) {    // 'name' is the PARAMETER (placeholder)
    console.log("Hello " + name);
}

// Function Invocation / Call
greet("John");            // "John" is the ARGUMENT (actual value passed)
```

```text
greet("John") ──> Execute instructions ──> "Hello John"
```

---

## 🔁 The `return` Keyword & Early Returns in Controllers

The `return` statement does two things:
1. Returns a result back to the caller.
2. **Immediately terminates** execution of the function.

```javascript
function add(a, b) {
    return a + b;
}

const result = add(10, 20); // result = 30
```

### 🚨 Critical Backend Pattern: Early Return
In backend API controllers, `return` prevents the server from executing subsequent code and attempting to send multiple HTTP responses for a single request:

```javascript
// Example Controller Route
app.post("/register", (req, res) => {
    const { password } = req.body;

    if (password.length < 6) {
        // Stop execution immediately and return 400 Bad Request
        return res.status(400).json({
            message: "Password must be at least 6 characters"
        });
    }

    // Code below only runs if password length is valid
    console.log("Password valid. Proceeding to hash...");
});
```

> [!warning] Common Mistake: Missing `return`
> If you omit `return` inside the `if` block:
> ```javascript
> if (password.length < 6) {
>     res.status(400).json({ message: "Password too short" });
>     // No return! The function continues running...
> }
> res.status(200).json({ message: "Success" }); // 💥 Crash: Cannot set headers after they are sent to the client
> ```

---

## 🏹 Arrow Functions `() => {}`

Arrow functions offer a concise syntax for writing functions and are used extensively in modern [[Introduction to Node.js|Node.js]] and Express route handlers.

### Syntax Comparison
```javascript
// Standard Function
function add(a, b) {
    return a + b;
}

// Arrow Function
const add = (a, b) => {
    return a + b;
};

// One-Line Implicit Return (Shorted)
const add = (a, b) => a + b;
```

### Arrow Functions as Route Handlers
```javascript
app.get("/api/health", (req, res) => {
    res.send("Server is healthy");
});
```

Breakdown:
```text
app.get(
    "/api/health",               <-- Route path
    (req, res) => {              <-- Arrow function callback executed on request
        res.send("Server is healthy");
    }
);
```

---

## 🎛️ Conditional Logic: `if / else` & Validation

Backend APIs constantly validate incoming user inputs:

```javascript
const password = "abc";

if (password.length < 6) {
    console.log("Password too short");
} else {
    console.log("Password valid");
}
```

### Multiple Branches with `else if`
```javascript
if (role === "admin") {
    console.log("Full access");
} else if (role === "seller") {
    console.log("Product management access");
} else {
    console.log("Customer access");
}
```

---

## 🔄 Array Iteration: `for...of` Loop

The `for...of` loop is a clean, readable syntax to iterate over array elements:

```javascript
const roles = ["customer", "seller", "admin"];

for (const role of roles) {
    console.log("Configuring role:", role);
}
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Variables and Data Types]]
- [[Objects and Destructuring]]

### Next Step
- [[Async JavaScript and JSON]] — Managing slow database queries using `async/await` and handling JSON payloads.

## 🔗 Related Notes
- [[JavaScript Foundations|📁 JavaScript Foundations MOC]]
- [[Objects and Destructuring]]
- [[Async JavaScript and JSON]]
- [[ShopKart Auth Project]]
