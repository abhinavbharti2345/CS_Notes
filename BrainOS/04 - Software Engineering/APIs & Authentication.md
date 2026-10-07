---
type: concept
topic: Software Engineering
subtopic: APIs & Authentication
date: 2026-10-07
tags:
  - apis
  - rest
  - grpc
  - jwt
  - oauth2
  - authentication
---

# 🔐 APIs, REST, gRPC & Authentication

> The contract interfaces and security protocols through which clients, services, and external consumers communicate securely.

---

## 🎯 API Paradigms Comparison

| Feature | RESTful HTTP/JSON | gRPC (HTTP/2 + Protobuf) | GraphQL | WebSockets |
| :--- | :--- | :--- | :--- | :--- |
| **Protocol** | HTTP/1.1 or HTTP/2 | HTTP/2 | HTTP/1.1 or HTTP/2 | TCP WebSocket upgrade |
| **Data Format** | JSON (Text) | Protocol Buffers (Binary) | JSON (Text) | Text / Binary frames |
| **Streaming** | Request/Response | Unary, Server, Client, Bi-directional | Subscriptions | Full-Duplex Bi-directional |
| **Best For** | Public Web APIs, CRUD | Internal Microservices, High-Throughput | Complex Client queries, Mobile | Real-time chat, Live Tickers |

---

## 🛡️ Authentication & Authorization Models

```mermaid
flowchart TD
    subgraph JWT_FLOW ["JWT (JSON Web Token) Stateless Authentication"]
        direction TB
        C["<b>Client</b>"] -->|1. POST /login (email, pass)| S["<b>Auth Server</b>"]
        S -->|2. Validates & Signs Token with Secret/RS256| S
        S -->|3. Returns JWT (Header.Payload.Signature)| C
        C -->|4. Request with 'Authorization: Bearer <JWT>'| BE["<b>Resource Backend</b>"]
        BE -->|5. Verifies signature locally without DB hit| BE
        BE -->|6. Serves Protected Data| C
    end

    style JWT_FLOW stroke:#34D399,stroke-width:1.8px,color:#34D399

    classDef cNode stroke:#38BDF8,stroke-width:1.8px;
    classDef sNode stroke:#FB923C,stroke-width:1.8px;
    classDef beNode stroke:#34D399,stroke-width:1.8px;

    class C cNode;
    class S sNode;
    class BE beNode;
```

### 1. JWT Structure (`Header . Payload . Signature`)
- **Header:** Algorithm and token type (`{"alg": "HS256", "typ": "JWT"}`).
- **Payload:** Claims (`{"sub": "12345", "role": "ADMIN", "exp": 1716900000}`).
- **Signature:** Hash over `HMACSHA256(base64(header) + "." + base64(payload), secret)`.

### 2. OAuth2 & OpenID Connect (OIDC)
- **OAuth2:** Authorization framework allowing 3rd-party access without sharing passwords (Authorization Code Flow with PKCE).
- **OIDC:** Identity layer on top of OAuth2 delivering an `id_token` verifying user identity.

---

## 🔗 Related Topics
- [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering (Spring Security)]]
- [[BrainOS/05 - Systems/Distributed Systems|Distributed Systems (Rate Limiting & Gateways)]]
- [[00 - BrainOS Dashboard|Main Dashboard]]
