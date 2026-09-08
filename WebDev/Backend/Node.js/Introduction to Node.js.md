---
topic: Node.js
type: concept
tags:
  - nodejs
  - backend
  - runtime
  - v8
date: 2026-09-04
---

# Introduction to Node.js

## 🌟 What Is Node.js, Really?

JavaScript was originally born to run exclusively **inside a web browser** (Netscape, Chrome, Firefox) to make web pages interactive (DOM manipulation, form validation, animations).

The browser provides browser-specific globals and APIs:

```text
JavaScript
   ↓
Browser Environment
   ↓
DOM (document)
Window (window)
localStorage
fetch API
```

Because browsers must safeguard client devices, browser JavaScript is isolated in a security sandbox and is strictly prevented from touching the operating system's hard drive or opening raw server ports.

> [!important] Key Definition
> **Node.js is an open-source, cross-platform JavaScript runtime environment that allows JavaScript to run outside the browser.**

```text
Before Node.js:               With Node.js:
 JavaScript                     JavaScript
     ↓                              ↓
  Browser                        Node.js
                                    ↓
                           Your Computer / Server
```

With Node.js, JavaScript is no longer confined to frontend browsers. We use it to build:
- Backend Web Servers & REST APIs
- Microservices & Real-Time Applications (WebSockets)
- Command Line Interface (CLI) tools
- File processing & automation scripts
- Development build tools

And that is why the **[[ShopKart Auth Project|ShopKart backend]] can be built entirely in JavaScript**.

---

## 🚫 Common Misconception: Node.js is NOT a Programming Language

| Layer | Component | Purpose |
| :--- | :--- | :--- |
| **Language** | **JavaScript** | The syntax, keywords, data structures, and logic. |
| **Engine** | **[[V8 Engine\|V8]]** | Google's C++ engine that parses and compiles JS into machine code. |
| **Runtime** | **Node.js** | The environment and standard libraries (`fs`, `http`, `os`) wrapping V8. |

```text
JavaScript (Language)
    │
    │ is compiled & executed by
    ▼
V8 (JavaScript Engine)
    │
    │ packaged into an environment with OS bindings
    ▼
Node.js (Runtime Environment)
```

---

## ⚙️ V8 vs Node.js (V8 ≠ Node.js)

Understanding the distinction is fundamental:

- **[[V8 Engine|V8]]** answers: *"How do I parse, compile, and execute JavaScript instructions?"*
- **Node.js** answers: *"How can JavaScript interact with the outside world and operating system?"*

```text
Your JavaScript Code
      ↓
    Node.js (Provides runtime APIs: fs, http, path, os)
      ↓
   V8 Engine (Compiles JS to machine code)
      ↓
  CPU / Operating System Executes Instructions
```

---

## ⚖️ Browser JavaScript vs Node.js

Both environments execute standard JavaScript, but they expose completely different system APIs:

```text
                     JavaScript (Language)
                               │
            ┌──────────────────┴──────────────────┐
            ▼                                     ▼
     Browser Runtime                       Node.js Runtime
  ├── document (DOM)                    ├── fs (File System)
  ├── window                            ├── http (Web Server)
  ├── localStorage                      ├── process (Process & Env)
  └── fetch API                         └── path (OS File Paths)
```

> [!quote] The Fish with Gills Analogy
> Browser JavaScript is like a **fish** — it can only survive in the water of the browser (accessing `window`, `document`, DOM).  
> 
> **Node.js gives that fish a pair of lungs/gills to breathe air on land:** It is the exact same JavaScript language, but now it can live on a server, manage files, open network ports, and communicate with databases like MongoDB.

---

## 🚀 Why Was Node.js Such a Game Changer?

Traditionally, web development required learning two separate language ecosystems:

```text
Traditional Stack:                     Full-Stack JavaScript (Node.js):
Frontend ──> JavaScript                Frontend ──> JavaScript
Backend  ──> Java / Python / PHP       Backend  ──> JavaScript + Node.js
```

Node.js unified full-stack software development under a **single language (JavaScript)**, allowing developers to share code, models, and mental overhead across client and server.

---

## 💻 Running JavaScript with Node.js

To run JavaScript directly on your computer:

1. Create a file named `hello.js`:
   ```javascript
   console.log("Hello from Node!");
   ```
2. Open your terminal in that folder and run:
   ```bash
   node hello.js
   ```
3. Output:
   ```text
   Hello from Node!
   ```

You just ran JavaScript **without a browser**.

---

## ⚡ Why Node.js is Ideal for Servers (I/O & Waiting)

Most backend server operations do **not** involve heavy mathematical calculations; they involve **waiting**:
- Waiting for MongoDB queries to finish.
- Waiting for files to read from disk.
- Waiting for third-party HTTP requests.
- Waiting for incoming network packets.

Instead of idling or spawning expensive new threads per user, Node.js uses **Non-Blocking I/O** coordinated by the **[[Event Loop and Non-Blocking IO|Event Loop]]**:

```text
Node Server (Handling 1,000 requests)
  │
  ├── Request A ──> Start File Read ──> (Waiting in background)
  │
  ├── Request B ──> Start DB Query  ──> (Waiting in background)
  │
  ├── Request C ──> Compute Response ──> Sent immediately ✅
  │
  └── Request A File Read Finishes ──> Send response to Client A ✅
```

> [!important] Crucial Correction: Is Node.js "Single-Threaded"?
> The **JavaScript execution model** is single-threaded (one call stack executing JS line-by-line). However, **Node.js under the hood** uses multi-threaded background worker pools and OS asynchronous subsystems for file and network I/O operations.

---

## 🛒 Connection to the ShopKart Project

In our upcoming **[[ShopKart Auth Project]]**, Node.js serves as the underlying engine powering the authentication pipeline:

```text
Client (Postman / Browser)
   │ HTTP POST /customers/login
   ▼
Express.js (Routing & Middleware)
   │
   ▼
Node.js Runtime (Execution & Event Loop)
   │
   ├── 1. Read email & password from req.body
   ├── 2. Query MongoDB asynchronously
   ├── 3. Compare passwords using bcrypt
   ├── 4. Sign JWT Authentication Token
   ├── 5. Set HttpOnly Cookie
   └── 6. Return response to Client
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[JavaScript Foundations|🟨 JavaScript Foundations MOC]] (Variables, Objects, Functions, `async/await`, JSON)

### Next Step
- [[V8 Engine]] — How Google's V8 compiles JS into high-speed machine instructions.
- [[Event Loop and Non-Blocking IO]] — Deep dive into Node's concurrency and non-blocking model.

## 🔗 Related Notes
- [[WebDev/Backend/Node.js/README|🟢 Node.js Runtime MOC]]
- [[V8 Engine]]
- [[Event Loop and Non-Blocking IO]]
- [[Core Modules]]
- [[ShopKart Auth Project]]
