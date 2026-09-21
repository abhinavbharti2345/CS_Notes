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

> [!abstract] Master Backend MOC
> Welcome to the **Backend Development Knowledge Base**. This repository contains interconnected architecture notes designed to take you from core JavaScript runtime mechanics to production-ready backend architectures with [[Introduction to Node.js|Node.js]], Express, MongoDB, and Authentication.

---

## 🗺️ Master 13-Part Learning Roadmap

```mermaid
flowchart TD
    P0["🟨 PART 0: JavaScript Foundations<br/><i>Variables, Objects, Functions, Async, JSON</i>"]
    P1["🟢 PART 1: Node.js Runtime & V8 Engine<br/><i>Single thread, Libuv, JIT compilation</i>"]
    P2["📦 PART 2: npm & Package Architecture"]
    P3["🚂 PART 3: Express.js Framework & Middleware"]
    P4["🌐 PART 4: HTTP & RESTful API Design"]
    P5["🍃 PART 5: MongoDB & Mongoose ODM"]
    P6["🔐 PART 6: Cryptographic Hashing with bcrypt"]
    P7["🎟️ PART 7: JWT (JSON Web Tokens)"]
    P8["🍪 PART 8: Cookies & HttpOnly Security"]
    P9["🛡️ PART 9: Auth Middleware & RBAC"]
    P10["🏛️ PART 10: MVC & Scalable Project Structure"]
    P11["🛒 PART 11: Production Auth Project (ShopKart)"]
    P12["📮 PART 12: API Integration Testing"]
    P13["🧠 PART 13: System Architecture Deep Dives"]

    P0 --> P1 --> P2 --> P3 --> P4 --> P5 --> P6 --> P7 --> P8 --> P9 --> P10 --> P11 --> P12 --> P13

    classDef active fill:#10b98118,stroke:#10b981,stroke-width:2px;
    classDef planned fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.5px;
    class P0,P1,P11 active;
    class P2,P3,P4,P5,P6,P7,P8,P9,P10,P12,P13 planned;
```

---

## 📚 Core Modules

### 1. [[WebDev/Backend/JavaScript/README|01. JavaScript Foundations]]
The essential JavaScript concepts required for backend engineering:
- [[Variables and Data Types]] — `const` vs `let`, primitives, `null` vs `undefined`, string methods
- [[Objects and Destructuring]] — Key-value pairs, nested payloads, destructuring `req.body`
- [[Functions and Control Flow]] — Declarations, parameters vs arguments, arrow functions, early `return`, `if/else`
- [[Async JavaScript and JSON]] — `async/await`, Promises, non-blocking DB calls, JSON data format

### 2. [[WebDev/Backend/Node.js/README|02. Node.js Runtime & Architecture]]
How JavaScript executes outside the browser on servers:
- [[Introduction to Node.js]] — JavaScript runtime environment & browser vs server capabilities
- [[V8 Engine]] — Google's C++ engine, JIT compilation, machine code
- [[Event Loop and Non-Blocking IO]] — Single-threaded concurrency & worker pool
- [[Core Modules]] — Built-in modules (`fs`, `http`, `path`, `os`)

### 3. Practical Implementation
- [[ShopKart Auth Project]] — The complete authentication request lifecycle, bcrypt hashing, and HttpOnly session cookies.

---

## 🔄 Knowledge Flow Graph

```mermaid
flowchart TD
    V["Variables and Data Types"] --> O["Objects and Destructuring"]
    O --> F["Functions and Control Flow"]
    F --> A["Async JavaScript and JSON"]
    
    A --> N["Introduction to Node.js"]
    N --> V8["V8 Engine"]
    N --> EL["Event Loop and Non-Blocking IO"]
    N --> CM["Core Modules"]

    O -.-> SK["🛒 ShopKart Auth Project"]
    F -.-> SK
    A -.-> SK
    EL -.-> SK
    CM -.-> SK

    classDef js fill:#f59e0b18,stroke:#f59e0b,stroke-width:1.8px;
    classDef node fill:#10b98118,stroke:#10b981,stroke-width:1.8px;
    classDef proj fill:#8b5cf618,stroke:#8b5cf6,stroke-width:2px;
    class V,O,F,A js;
    class N,V8,EL,CM node;
    class SK proj;
```

---

## 🔗 Quick Links
- [[Dashboard|🧭 Main Command Center]]
- [[WebDev/Backend/JavaScript/README|📁 JavaScript Foundations MOC]]
- [[WebDev/Backend/Node.js/README|📁 Node.js Runtime MOC]]
- [[ShopKart Auth Project|🛒 ShopKart Auth Project]]

