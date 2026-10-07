---
type: hub
topic: Systems
subtopic: Distributed Systems
date: 2026-10-07
tags:
  - distributed-systems
  - consensus
  - cap-theorem
  - raft
  - sharding
  - curriculum
---

# 🌐 Distributed Systems Master Roadmap

> **Roadmap:** The study of autonomous computing nodes communicating over imperfect networks to execute tasks as a single resilient, coherent system.

---

## 🎯 Why Learn This?
- **The Limit of Single Machines:** Vertical scaling hits physical hardware boundaries; distributed systems enable horizontal scaling across thousands of nodes.
- **Zero-Downtime Resilience:** Learn how modern clusters survive node crashes, network partitions, and data center failures without losing data.
- **The Engine Behind AI & Cloud:** Ray, Kubernetes, Kafka, Cassandra, and distributed GPU training clusters are all distributed systems.

---

## 🔗 Prerequisites
- [[BrainOS/03 - Core CS/Operating Systems|Operating Systems]] (Threads, Concurrency, IPC)
- [[BrainOS/03 - Core CS/Computer Networks|Computer Networks]] (TCP/IP, Sockets, Packet latency)
- [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering]] (Stateless APIs, Databases)

---

## 🗺️ Learning Order & Topic Breakdown

![[distributed_systems_architecture.drawio.svg]]

### 1. Fundamental Theorems & Fallacies
- The 8 Fallacies of Distributed Computing (Network reliability, Latency, Bandwidth)
- CAP Theorem (Consistency vs Availability under Network Partitions)
- PACELC Theorem (Latency vs Consistency trade-offs during normal operation)

### 2. Time & Ordering in Distributed Systems
- Physical Clocks vs Clock Skew and Drift (NTP)
- Logical Clocks: Lamport Timestamps and Vector Clocks for causal event ordering

### 3. Distributed Consensus & Coordination
- The Byzantine Generals Problem and Crash Fault Tolerance (CFT)
- Raft Consensus Algorithm: Leader Election, Log Replication, Safety invariants
- Coordination engines: Apache ZooKeeper, etcd (Raft-backed key-value configuration)

### 4. Data Replication & Consistency Models
- Strong Consistency (Linearizability) vs Eventual Consistency
- Quorum Replication: Read/Write Quorums ($R + W > N$)
- Replication models: Single-Leader, Multi-Leader, Leaderless (Dynamo-style)

### 5. Partitioning & Data Placement
- Consistent Hashing with Virtual Nodes (Minimizing key remapping during node churn)
- Sharding strategies: Hash-based vs Range-based partitioning
- Distributed Transactions: Two-Phase Commit (2PC) vs Saga Pattern (Orchestration & Choreography)

### 6. Fault Tolerance & Failure Detection
- Heartbeats, Phi Accrual Failure Detectors, Gossip Protocols
- Idempotent API operations and Distributed Locks (Redlock, ZK locks)

---

## 🚀 Unlocks
- → [[BrainOS/05 - Systems/System Design|System Design]] (Large-scale architecture interviews & systems)
- → [[BrainOS/06 - Infrastructure/Docker & Kubernetes|Kubernetes & Cloud]] (Distributed container orchestration)
- → [[BrainOS/09 - AI Infrastructure/Quantization & Distributed Inference|Distributed AI Infrastructure]] (Tensor & Pipeline Parallelism)

---

## 🧪 Suggested Project
- **Distributed Real-Time Chat Engine (Level 6):** Build a distributed chat system using WebSockets, Redis Pub/Sub for node synchronization, and Kafka for persistent event delivery.

---

## 📚 Detailed Notes in Vault
- [[BrainOS/05 - Systems/Caching & Message Queues|Caching & Message Queues]]
- [[BrainOS/05 - Systems/Scalability & Fault Tolerance|Scalability & Fault Tolerance]]
