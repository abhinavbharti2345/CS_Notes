---
topic: Node.js
type: moc
tags:
  - nodejs
  - backend
  - runtime
date: 2026-09-04
---

# 🟢 Node.js Runtime & Architecture

> [!important] Overview
> Node.js is an open-source, cross-platform JavaScript runtime environment that allows you to execute JavaScript on servers and computers outside the web browser.

---

## 📖 Learning Path

1. **[[Introduction to Node.js]]**
   - What is Node.js and why does it exist?
   - Browser JavaScript vs Server JavaScript (Fish with gills analogy)
   - Running scripts via Node CLI (`node script.js`)

2. **[[V8 Engine]]**
   - Google Chrome's V8 C++ execution engine
   - Just-In-Time (JIT) compilation from JS to machine code
   - How Node.js embeds V8 and adds system-level APIs

3. **[[Event Loop and Non-Blocking IO]]**
   - Single-threaded execution model
   - Synchronous vs Asynchronous waiter analogy
   - Why code written later can run before earlier asynchronous operations

4. **[[Core Modules]]**
   - Node.js built-in modules (`fs`, `http`, `path`, `os`)
   - Non-blocking file operations with `fs.readFile`
   - Introduction to building HTTP servers

---

## 🔗 Connections

### Prerequisites
- [[JavaScript Foundations|JavaScript Foundations]] (Variables, Objects, Functions, `async/await`, JSON)

### What This Prepares You For
- **Express.js Framework**: Building web servers and REST APIs.
- **MongoDB & Mongoose**: Asynchronous database modeling.
- **Authentication**: Implementing secure auth flows in [[ShopKart Auth Project]].

---

## 🔗 Related Notes
- [[WebDev/Backend/README|🌐 Backend Master MOC]]
- [[WebDev/Backend/JavaScript/README|🟨 JavaScript Foundations MOC]]
- [[ShopKart Auth Project|🧪 ShopKart Auth Lab]]
- [[Dashboard|🧭 Main Command Center]]
