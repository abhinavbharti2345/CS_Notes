---
topic: JavaScript
type: concept
tags:
  - javascript
  - backend
  - objects
  - destructuring
date: 2026-09-04
---

# Objects and Destructuring

## 🚨 Why Objects are Critical for Backend

In backend engineering, nearly all data transferred over the network, processed by Express, or stored in MongoDB is structured as **Objects**.

An object allows us to group related attributes into a single entity using **key-value pairs**:

```javascript
const customer = {
    fullName: "John Doe",
    email: "john@gmail.com",
    password: "john123",
    phone: "9876543210"
};
```

```text
customer
   │
   ├── fullName ──> "John Doe"
   ├── email    ──> "john@gmail.com"
   ├── password ──> "john123"
   └── phone    ──> "9876543210"
```

---

## 🔍 Accessing Object Properties

### 1. Dot Notation (Standard)
```javascript
console.log(customer.fullName); // "John Doe"
console.log(customer.email);    // "john@gmail.com"
```

### 2. Bracket Notation (Dynamic Keys)
Use bracket notation when property names are stored inside variables or contain special characters:

```javascript
const field = "email";
console.log(customer[field]); // "john@gmail.com"
```

---

## 📦 Nested Objects & API Payloads

Objects can contain other objects or arrays. In Express route handlers, API responses are usually structured like this:

```javascript
const apiResponse = {
    statusCode: 200,
    success: true,
    data: {
        userId: "usr_1029",
        role: "admin",
        permissions: ["read", "write", "delete"]
    }
};

console.log(apiResponse.data.role); // "admin"
```

---

## 📚 Arrays and Arrays of Objects

An **array** is an ordered list of values indexed starting from `0`.

```javascript
const roles = ["customer", "seller", "admin"];
console.log(roles[0]); // "customer"
```

In databases (like MongoDB collections), query results return an **array of objects**:

```javascript
const customers = [
    { id: 1, name: "John", email: "john@gmail.com" },
    { id: 2, name: "Alice", email: "alice@gmail.com" }
];

console.log(customers[0].name); // "John"
```

---

## ✂️ Object Destructuring (Essential Backend Pattern)

**Destructuring** is a convenient syntax that unpacks properties from an object directly into distinct variables.

### The Problem without Destructuring:
```javascript
// Tedious, repetitive code:
const fullName = req.body.fullName;
const email = req.body.email;
const password = req.body.password;
const phone = req.body.phone;
```

### The Solution with Destructuring:
```javascript
const { fullName, email, password, phone } = req.body;
```

```text
       req.body (Incoming HTTP JSON Object)
     ┌───────────────────────────────────────┐
     │ fullName: "John Doe"                  │
     │ email:    "john@gmail.com"            │
     │ password: "john123"                   │
     │ phone:    "9876543210"                │
     └───────────────────────────────────────┘
                        │
       Destructuring: const { fullName, email, password, phone } = req.body;
                        │
                        ▼
  ┌─────────────────────────────────────────────────────────────┐
  │ fullName ──> "John Doe"                                     │
  │ email    ──> "john@gmail.com"                               │
  │ password ──> "john123"                                      │
  │ phone    ──> "9876543210"                                   │
  └─────────────────────────────────────────────────────────────┘
```

> [!important] Viva / TA Question
> **Q: What is `const { email, password } = req.body;` doing?**  
> **A:** It is JavaScript object destructuring. It extracts the `email` and `password` properties from the `req.body` object and creates local variables with the exact same names.

---

## 🔗 Prerequisites & Next Steps

### Prerequisites
- [[Variables and Data Types]] — Understanding `const`, `let`, and primitive types.

### Next Step
- [[Functions and Control Flow]] — Passing objects into functions, arrow functions, and early `return` patterns.

## 🔗 Related Notes
- [[JavaScript Foundations|📁 JavaScript Foundations MOC]]
- [[Variables and Data Types]]
- [[Async JavaScript and JSON]]
- [[ShopKart Auth Project]]
