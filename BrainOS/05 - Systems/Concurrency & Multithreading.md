---
type: concept
topic: Systems
subtopic: Concurrency & Multithreading
date: 2026-10-07
tags:
  - concurrency
  - multithreading
  - java
  - lock-free
  - atomics
---

# ⚡ Concurrency & Multithreading in Java

> The engineering discipline of coordinating multiple concurrent execution threads sharing memory without data races, deadlocks, or performance bottlenecks.

---

## 🎯 Why It Matters
- **Saturating Multi-Core CPUs:** Modern servers have 64–128 CPU cores; single-threaded programs leave 98% of computing power idle.
- **High-Throughput IO Runtimes:** Netty, Tomcat, and Kafka brokers achieve millions of ops/sec through non-blocking event loops and tuned thread pools.
- **Avoiding Silent Data Corruption:** A single unguarded increment (`count++`) across threads causes silent data loss in production.

---

## 🧠 Core Memory & Synchronization Mechanics

### 1. The Java Memory Model (JMM) & `volatile`
- **CPU Caches & Memory Visibility:** Each CPU core caches memory in L1/L2. Changes made by Thread 1 may not be visible to Thread 2 without memory barriers.
- **`volatile` Keyword:** Guarantees **visibility** (reads and writes bypass CPU registers/cache directly to main memory) and establishes **Happens-Before** order by preventing instruction reordering.
- Note: `volatile` does **NOT** guarantee atomicity for compound operations like `count++`.

### 2. Lock-Free Programming & Atomic CAS (Compare-And-Swap)
- Uses hardware-level atomic CPU instructions (`cmpxchg` on x86).
- Optimistically attempts an update; if another thread updated it first, it retries in a loop without thread suspension/context switching.
- Backing primitive for `AtomicInteger`, `AtomicReference`, and `ConcurrentHashMap`.

### 3. Java `java.util.concurrent` (JUC) Ecosystem
- **`ReentrantLock` & `ReentrantReadWriteLock`:** Explicit locks supporting timed acquisition (`tryLock`) and fair scheduling.
- **`ExecutorService` & `ThreadPoolExecutor`:** Thread pool management (Core pool size, Max pool size, WorkQueue, Rejection Policy).
- **`CompletableFuture`:** Non-blocking asynchronous promise pipelines.
- **Virtual Threads (Project Loom / Java 21+):** Lightweight user-mode threads managed by the JVM runtime, enabling 1,000,000+ concurrent connections.

---

## 🛠️ Code Example: Thread-Safe Lock-Free Counter

```java
import java.util.concurrent.atomic.AtomicLong;

public class HighThroughputMetricsCounter {
    private final AtomicLong requestCount = new AtomicLong(0);

    public void increment() {
        requestCount.incrementAndGet(); // Lock-free atomic CAS
    }

    public long getCount() {
        return requestCount.get();
    }
}
```

---

## 🔗 Related Topics
- [[BrainOS/03 - Core CS/Operating Systems|Operating Systems (Process vs Thread)]]
- [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering]]
- [[BrainOS/05 - Systems/Distributed Systems|Distributed Systems]]
