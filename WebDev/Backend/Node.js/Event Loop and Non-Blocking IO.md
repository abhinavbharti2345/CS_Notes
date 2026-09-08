---
topic: Node.js
type: concept
tags:
  - nodejs
  - event-loop
  - async
  - concurrency
date: 2026-09-04
---

# Event Loop and Non-Blocking I/O

## 🧵 Single-Threaded Concurrency

Node.js executes your JavaScript on a **single main thread**.

Despite running on one thread, Node.js can handle thousands of simultaneous client connections, database queries, and file operations without locking up.

It achieves this via **Non-Blocking I/O** (Input/Output) driven by the **Event Loop**.

---

## 🍽️ The Restaurant Waiter Analogy

> [!example] Blocking vs Non-Blocking Waiter
> 
> ### 1. Blocking (Synchronous) Waiter
> - The waiter takes the order from Table 1.
> - Walks into the kitchen and **stands there waiting** while the chef cooks the meal.
> - No other tables can place orders or get water while that meal cooks.
> - **Result:** Extremely slow and inefficient.
> 
> ---
> 
> ### 2. Non-Blocking (Asynchronous) Node.js Waiter
> - The waiter takes the order from Table 1 and hands the ticket to the kitchen.
> - **Immediately walks to Table 2, Table 3, and Table 4** to take more orders while the kitchen cooks in parallel.
> - When the chef finishes Table 1's meal, a bell rings (the **Callback / Event**).
> - The waiter pauses for a moment to deliver Table 1's food, then continues serving others.
> - **Result:** A single waiter serves hundreds of customers without delay.

---

## ⏱️ Why Later Code Runs Before Earlier Code

Because asynchronous operations (such as reading a file or querying a database) are offloaded to background threads or OS subsystems, JavaScript does not wait for them:

```javascript
const fs = require("fs");

console.log("1. Starting file read...");

fs.readFile("notes.txt", "utf8", (err, data) => {
    if (err) throw err;
    console.log("3. File read finished! Content:", data);
});

console.log("2. Code execution continues immediately...");
```

### Console Output:
```text
1. Starting file read...
2. Code execution continues immediately...
3. File read finished! Content: Hello World
```

### Why this happens:
1. `console.log("1...")` runs synchronously on the main thread.
2. `fs.readFile()` sends the file read request to the operating system and immediately yields control back.
3. `console.log("2...")` runs immediately without waiting for the disk.
4. When the operating system finishes reading `notes.txt`, the **Event Loop** places the callback into the event queue, executing step `3`.

---

## 🔄 The Event Loop Mental Model

```text
  Call Stack (Main Thread)               Operating System / Thread Pool
┌───────────────────────────┐           ┌──────────────────────────────┐
│  Executes synchronous JS  │ ──Offload─>  Reads files, queries DB,    │
│  line by line             │           │  handles network requests    │
└───────────────────────────┘           └──────────────┬───────────────┘
              ▲                                        │
              │                                        │ When finished,
              │ Pulls callbacks when Stack is empty    │ pushes callback
              │                                        ▼
      ┌───────────────┐                 ┌──────────────────────────────┐
      │  EVENT LOOP   │ <───────────────┤   Callback / Event Queue     │
      └───────────────┘                 └──────────────────────────────┘
```

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Introduction to Node.js]]
- [[Async JavaScript and JSON]]

### Next Step
- [[Core Modules]] — Explore Node's built-in modules (`fs`, `http`, `path`, `os`).

## 🔗 Related Notes
- [[Node.js Runtime|📁 Node.js Runtime MOC]]
- [[Introduction to Node.js]]
- [[V8 Engine]]
- [[Core Modules]]
- [[Async JavaScript and JSON]]
