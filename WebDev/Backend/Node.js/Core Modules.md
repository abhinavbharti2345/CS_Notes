---
topic: Node.js
type: concept
tags:
  - nodejs
  - modules
  - fs
  - http
date: 2026-09-04
---

# Core Modules

## 📦 What Are Core Modules?

Node.js comes bundled with a set of powerful **built-in modules** (called core modules) that are available without needing to install external packages via npm.

You import them into your JavaScript files using the `require()` function:

```javascript
const fs = require("fs");       // File System module
const http = require("http");   // HTTP Web Server module
const path = require("path");   // File paths normalization
const os = require("os");       // Operating System statistics
```

---

## 🗂️ 1. The `fs` Module (File System)

The `fs` module allows Node.js to read, write, update, and delete files on the server's hard drive.

### Asynchronous File Reading (Error-First Callback Pattern)
```javascript
const fs = require("fs");

fs.readFile("example.txt", "utf8", (err, data) => {
    // 1. Always check for errors first
    if (err) {
        console.error("Error reading file:", err.message);
        return;
    }

    // 2. Process data if successful
    console.log("File content:\n", data);
});
```

> [!important] The Error-First Callback Convention
> In Node.js core callbacks, the **first argument is always the error (`err`)**. If no error occurred, `err` will be `null` or `undefined`, and the second argument (`data`) contains the result.

---

## 🌐 2. The `http` Module (Web Servers)

Node.js includes a native `http` module that allows you to create a web server from scratch without third-party frameworks:

```javascript
const http = require("http");

const server = http.createServer((req, res) => {
    // Set HTTP Response Header
    res.writeHead(200, { "Content-Type": "text/plain" });

    // Send HTTP Response Body
    res.end("Hello from native Node.js HTTP Server!");
});

// Start server on port 3000
server.listen(3000, () => {
    console.log("Server listening on http://localhost:3000");
});
```

> [!note] Why We Use Express Later
> While the built-in `http` module works, managing complex routes, parsing JSON, and handling middleware manually becomes tedious. **Express.js** is a minimalist framework built on top of the `http` module to make web development much simpler.

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Introduction to Node.js]]
- [[Event Loop and Non-Blocking IO]]

### Next Step
- **Express.js Framework** — Learn how Express builds upon the `http` module to simplify routing and middleware.
- [[ShopKart Auth Project]] — See how these concepts apply to authentication.

## 🔗 Related Notes
- [[Node.js Runtime|📁 Node.js Runtime MOC]]
- [[Introduction to Node.js]]
- [[Event Loop and Non-Blocking IO]]
- [[Async JavaScript and JSON]]
