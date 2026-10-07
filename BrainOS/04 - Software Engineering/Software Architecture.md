---
type: concept
topic: Software Engineering
subtopic: Software Architecture
date: 2026-10-07
tags:
  - architecture
  - solid
  - clean-code
  - hexagonal
---

# 🏛️ Software Architecture & SOLID Principles

> The high-level organizational structure, component boundaries, and design heuristics that keep codebases extensible, testable, and maintainable over decades.

---

## 🎯 The SOLID Principles

| Principle | Meaning | Real-World Application |
| :--- | :--- | :--- |
| **S — Single Responsibility** | A class should have only one reason to change. | Separate Email Sending logic from User Registration service. |
| **O — Open/Closed** | Open for extension, closed for modification. | Add new payment providers via Strategy interface without editing checkout code. |
| **L — Liskov Substitution** | Subtypes must be substitutable for base types without breaking code. | Never throw `UnsupportedOperationException` in interface implementations. |
| **I — Interface Segregation** | Prefer small, client-specific interfaces over fat ones. | Split `PaymentGateway` from `RefundableGateway` and `RecurringGateway`. |
| **D — Dependency Inversion** | Depend on abstractions (interfaces), not concrete implementations. | Inject `NotificationService` interface instead of `SendGridClient` class. |

---

## 🧠 Hexagonal (Ports & Adapters) & Clean Architecture

```mermaid
flowchart TD
    subgraph CLEAN ["Clean Architecture Dependency Direction (Inward)"]
        direction TB
        FW["<b>Frameworks & Drivers</b><br/>(Spring Boot, PostgreSQL, Web Controllers, Kafka)"]
        AD["<b>Interface Adapters</b><br/>(Repositories, Controllers, Presenters)"]
        UC["<b>Application Use Cases</b><br/>(CreateOrderUseCase, TransferFundsUseCase)"]
        ENT["<b>Domain Entities</b><br/>(Core Business Logic & Rules)"]

        FW --> AD --> UC --> ENT
    end

    style CLEAN stroke:#34D399,stroke-width:1.8px,color:#34D399

    classDef fwNode stroke:#64748B,stroke-width:1.8px;
    classDef adNode stroke:#38BDF8,stroke-width:1.8px;
    classDef ucNode stroke:#22D3EE,stroke-width:1.8px;
    classDef entNode stroke:#34D399,stroke-width:2px;

    class FW fwNode;
    class AD adNode;
    class UC ucNode;
    class ENT entNode;
```

> [!important] The Dependency Rule
> Source code dependencies must **only point inward**. The Domain Entity layer knows nothing about Spring Boot, SQL, HTTP, or external cloud providers.

---

## 🔗 Related Topics
- [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering]]
- [[BrainOS/04 - Software Engineering/Design Patterns|Design Patterns]]
- [[BrainOS/05 - Systems/Distributed Systems|Distributed Systems]]
