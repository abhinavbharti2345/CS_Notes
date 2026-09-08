---
topic: Backend Development
type: moc
tags:
  - backend
  - nodejs
  - webdev
  - roadmap
date: 2026-09-04
---

# 🌐 Backend Development Knowledge Base

Welcome to the **Backend Development Knowledge Base**. This repository contains interconnected study notes designed to take you from core JavaScript foundations to production-ready backend architectures with [[Introduction to Node.js|Node.js]], Express, MongoDB, and Authentication.

---

## 🗺️ Master 13-Part Learning Path

```text
PART 0 — [[JavaScript Foundations|JavaScript Foundations]] (Variables, Objects, Functions, Async, JSON)
        ↓
PART 1 — [[Introduction to Node.js|Node.js Runtime]] & [[V8 Engine|V8 Engine]]
        ↓
PART 2 — npm, Packages & package.json (Upcoming)
        ↓
PART 3 — Express.js Framework (Upcoming)
        ↓
PART 4 — HTTP & RESTful APIs (Upcoming)
        ↓
PART 5 — MongoDB & Mongoose ODM (Upcoming)
        ↓
PART 6 — Password Hashing with bcrypt (Upcoming)
        ↓
PART 7 — JWT (JSON Web Tokens) (Upcoming)
        ↓
PART 8 — Cookies & HttpOnly Security (Upcoming)
        ↓
PART 9 — Authentication Middleware (Upcoming)
        ↓
PART 10 — MVC Architecture (Upcoming)
        ↓
PART 11 — [[ShopKart Auth Project|Build ShopKart Authentication]]
        ↓
PART 12 — Postman API Testing (Upcoming)
        ↓
PART 13 — Viva & Interview Preparation
```

---

## 📚 Core Modules

### 1. [[JavaScript Foundations|01. JavaScript Foundations]]
The essential JavaScript concepts required for backend engineering:
- [[Variables and Data Types]] — `const` vs `let`, primitives, `null` vs `undefined`, string methods
- [[Objects and Destructuring]] — Key-value pairs, nested payloads, destructuring `req.body`
- [[Functions and Control Flow]] — Declarations, parameters vs arguments, arrow functions, early `return`, `if/else`
- [[Async JavaScript and JSON]] — `async/await`, Promises, non-blocking DB calls, JSON data format

### 2. [[Node.js Runtime|02. Node.js Runtime & Architecture]]
How JavaScript executes outside the browser on servers:
- [[Introduction to Node.js]] — JavaScript runtime environment & browser vs server capabilities
- [[V8 Engine]] — Google's C++ engine, JIT compilation, machine code
- [[Event Loop and Non-Blocking IO]] — Single-threaded concurrency & waiter analogy
- [[Core Modules]] — Built-in modules (`fs`, `http`, `path`, `os`)

### 3. Practical Lab Implementation
- [[ShopKart Auth Project]] — The complete authentication request lifecycle & TA viva guide.

---

## 🔄 Knowledge Flow Graph

```text
[[Variables and Data Types]]
        │
        ▼
[[Objects and Destructuring]] ──┐
        │                       │
        ▼                       ▼
[[Functions and Control Flow]] ─┼─> [[ShopKart Auth Project]]
        │                       │           ▲
        ▼                       │           │
[[Async JavaScript and JSON]] ──┘           │
        │                                   │
        ▼                                   │
[[Introduction to Node.js]]                 │
        │                                   │
        ├──> [[V8 Engine]]                  │
        │                                   │
        ├──> [[Event Loop and Non-Blocking IO]]
        │                                   │
        └──> [[Core Modules]] ──────────────┘
```

---

## 🔗 Quick Links
- [[Dashboard|🧭 Main Command Center]]
- [[WebDev/Backend/JavaScript/README|📁 JavaScript Foundations MOC]]
- [[WebDev/Backend/Node.js/README|📁 Node.js Runtime MOC]]
- [[ShopKart Auth Project|🧪 ShopKart Auth Lab & Viva]]
