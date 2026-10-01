---
topic: Node.js
type: concept
tags:
  - nodejs
  - v8
  - compiler
  - runtime
date: 2026-09-04
---

# V8 Engine

## 🧠 What is a JavaScript Engine?

When you write JavaScript code:

```javascript
let x = 10;
let y = 20;

console.log(x + y);
```

Your computer's CPU does not understand high-level JavaScript text. Something must translate that JavaScript source code into binary machine instructions (`0`s and `1`s) that the CPU can execute.

That translator is a **JavaScript Engine**.

```text
JavaScript Source Code
          ↓
  JavaScript Engine (V8)
          ↓
  Machine Instructions
          ↓
         CPU
```

---

## 🚀 What is V8?

**V8** is Google's open-source, high-performance C++ JavaScript and WebAssembly engine.

It was originally built for the Google Chrome web browser to execute client-side JavaScript at lightning speed using **Just-In-Time (JIT) compilation**.

```text
Google Chrome ──> embeds V8 ──> Executes client-side JavaScript in browser
```

---

## 🤔 How Does Node.js Use V8?

Node.js creator Ryan Dahl took Google's V8 engine out of Chrome, embedded it inside a standalone C++ application, and added system-level bindings (`fs`, `http`, `path`, `os`).

```text
                 Google V8 Engine
                        ↓
               Executes JavaScript
                        ↓
        ┌───────────────┴───────────────┐
        ↓                               ↓
  Google Chrome                      Node.js
        ↓                               ↓
  Browser APIs                     Node.js APIs
(DOM, window, document)        (fs, http, path, os)
```

- **V8** = Compiles and executes pure JavaScript code.
- **Node.js** = V8 + Node's C++ bindings that give JavaScript access to the Operating System.

---

## 👐 Why Node Gives JavaScript "Hands"

Normally, JavaScript running in a browser tab cannot touch the host computer's hard disk:

```javascript
// Browser JS cannot do this (blocked for security)!
deleteAllFilesFromMyComputer();
```

Node.js provides C++ bindings through built-in modules so your JavaScript can read, write, and manage files on disk:

```javascript
const fs = require("fs");

fs.readFile("data.txt", "utf8", (err, data) => {
    if (err) {
        console.error(err);
        return;
    }
    console.log("File content:", data);
});
```

### Execution Flow:
```text
Your JavaScript Code
        ↓
    V8 Engine (Compiles JS to Machine Code)
        ↓
 Node.js Runtime (Bridges calls to C++ libraries)
        ↓
    fs Module (Interacts with OS system calls)
        ↓
 Operating System / File System
        ↓
    data.txt
```

> [!tip] Summary
> **V8** is Google's engine that compiles and executes JavaScript code. **[[Introduction to Node.js|Node.js]]** embeds V8 and pairs it with operating system APIs (`fs`, `http`, `path`, `os`) so JavaScript can run as a backend server.

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Introduction to Node.js]]

### Next Step
- [[Event Loop and Non-Blocking IO]] — Learn how Node.js manages asynchronous tasks and concurrency on a single thread.

## 🔗 Related Notes
- [[Node.js Runtime|📁 Node.js Runtime MOC]]
- [[Introduction to Node.js]]
- [[Event Loop and Non-Blocking IO]]
- [[Core Modules]]
