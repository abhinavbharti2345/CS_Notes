---
type: concept
topic: Software Engineering
subtopic: Design Patterns
date: 2026-10-07
tags:
  - design-patterns
  - oop
  - architecture
  - gang-of-four
---

# 🎨 Software Design Patterns (Gang of Four)

> Reusable, battle-tested solutions to recurring software engineering design problems across object creation, composition, and behavioral interaction.

---

## 🎯 The Three Categories of Design Patterns

| Category | Purpose | Key Patterns |
| :--- | :--- | :--- |
| **1. Creational** | Mechanisms for object creation that decouple client code from instantiation logic. | **Factory Method**, **Builder**, **Singleton**, Abstract Factory |
| **2. Structural** | Ways to compose classes and objects into larger, flexible structures. | **Adapter**, **Decorator**, **Proxy**, Facade, Composite |
| **3. Behavioral** | Algorithms and assignment of responsibilities between cooperating objects. | **Strategy**, **Observer**, **Template Method**, Chain of Responsibility |

---

## 🧠 Most Crucial Patterns in Backend Engineering

### 1. Strategy Pattern (Interchangeable Business Algorithms)
- Encapsulates a family of algorithms into separate classes implementing a shared interface.
- Example: Dynamic payment gateway selection (`StripePaymentStrategy`, `PayPalPaymentStrategy`).

### 2. Builder Pattern (Complex Object Construction)
- Separates object construction from its representation, supporting fluent API chaining.
- Example: Lombok's `@Builder` annotation for multi-field DTOs.

### 3. Proxy Pattern (Lazy Loading & Cross-Cutting Concerns)
- Provides a surrogate placeholder controlling access to another object.
- Example: Spring's `@Transactional` and `@Cacheable` rely on dynamic CGLIB/JDK proxies!

### 4. Observer Pattern (Event-Driven Publish/Subscribe)
- One-to-many dependency where state changes notify all registered observers.
- Example: Spring Application Events (`ApplicationEventPublisher`, `@EventListener`).

---

## 🔗 Related Topics
- [[BrainOS/04 - Software Engineering/Software Architecture|Clean Architecture & SOLID]]
- [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering]]
- [[BrainOS/00 - BrainOS Dashboard|Main Dashboard]]
