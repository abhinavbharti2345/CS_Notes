---
type: hub
topic: Systems
subtopic: System Design
date: 2026-10-07
tags:
  - system-design
  - architecture
  - scalability
  - high-availability
  - curriculum
---

# 🏗️ System Design Master Roadmap

> **Roadmap:** The methodology for architecting large-scale, reliable, maintainable software systems from initial requirements to distributed deployment.

---

## 🎯 Why Learn This?
- **End-to-End Holistic Thinking:** Connect databases, caches, queues, load balancers, and microservices into a unified production architecture.
- **Trade-off Analysis:** Master the art of justifying engineering decisions (e.g. SQL vs NoSQL, Sync vs Async, AP vs CP).
- **Senior Engineering Bar:** The primary differentiator for senior software engineers and technical leaders.

---

## 🔗 Prerequisites
- [[BrainOS/03 - Core CS/Computer Networks|Computer Networks]] & [[BrainOS/03 - Core CS/Databases|Databases]]
- [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering]]
- [[BrainOS/05 - Systems/Distributed Systems|Distributed Systems]]

---

## 🗺️ Learning Order & System Design Framework

```mermaid
flowchart TD
    S1["<b>1. Requirements & Scope:</b> Functional vs Non-Functional, Back-of-the-Envelope Math"] --> S2["<b>2. API & Data Model:</b> REST/gRPC Endpoints, Relational / NoSQL Schemas"]
    S2 --> S3["<b>3. High-Level Architecture:</b> Client → DNS → CDN → Load Balancer → Services → DB"]
    S3 --> S4["<b>4. Deep Dive Components:</b> Caching, Queuing, Partitioning, Sharding"]
    S4 --> S5["<b>5. Resilience & Edge Cases:</b> Circuit Breakers, Rate Limiters, Failover"]

    style S1 stroke:#FB923C,stroke-width:1.8px,color:#F8FAFC
    style S2 stroke:#FB923C,stroke-width:1.8px,color:#F8FAFC
    style S3 stroke:#FB923C,stroke-width:1.8px,color:#F8FAFC
    style S4 stroke:#F59E0B,stroke-width:1.8px,color:#F8FAFC
    style S5 stroke:#34D399,stroke-width:1.8px,color:#F8FAFC
```

### 1. Requirements & Capacity Estimation
- Functional Requirements (What the system does)
- Non-Functional Requirements (Availability, Latency, Consistency, Durability, SLA/SLO)
- Back-of-the-envelope calculations: QPS, Daily Active Users (DAU), Storage sizing over 5 years, Network bandwidth

### 2. Core Building Blocks
- **Load Balancing:** DNS Round Robin, L4 vs L7 (ALB, Nginx, Envoy), Algorithms (Round Robin, Least Connections, Consistent Hash)
- **Caching:** Cache-Aside, Write-Through, Invalidation (TTL, LRU eviction), Redis / Memcached
- **Databases:** PostgreSQL (Relational), Cassandra (High-write append), MongoDB (Documents), DynamoDB
- **Asynchronous Queues:** Apache Kafka, RabbitMQ, Amazon SQS
- **Rate Limiters:** Token Bucket, Leaky Bucket, Sliding Window Counter (Redis)

### 3. Classic System Architectures to Master
- **Beginner:** Scalable URL Shortener (TinyURL), Pastebin, Rate Limiter
- **Intermediate:** Instagram / Twitter Newsfeed, WhatsApp / Chat Engine, YouTube Video Streaming
- **Advanced:** Uber / Ride-Sharing (Geohashing, QuadTrees), Distributed Web Crawler, Real-Time Collaborative Document Editor (OT / CRDT)

---

## 🚀 Unlocks
- → [[BrainOS/06 - Infrastructure/Cloud & AWS|Cloud & Platform Engineering]]
- → [[BrainOS/09 - AI Infrastructure/AI Infrastructure|AI Infrastructure Systems]]
- → High-Level System Architecture Leadership

---

## 🧪 Suggested Project
- **High-Throughput Scalable URL Shortener (Level 5):** Build a distributed TinyURL service with Base62 encoding, Redis caching, and Token Bucket rate limiting handling 10,000 requests/sec.

---

## 📚 Detailed Notes in Vault
- [[BrainOS/05 - Systems/Caching & Message Queues|Caching & Message Queues]]
- [[BrainOS/05 - Systems/Scalability & Fault Tolerance|Scalability & Fault Tolerance]]
