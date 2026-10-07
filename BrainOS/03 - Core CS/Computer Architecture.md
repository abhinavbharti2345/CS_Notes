---
type: concept
topic: Core Computer Science
subtopic: Computer Architecture
date: 2026-10-07
tags:
  - architecture
  - hardware
  - cpu
  - cache
  - memory-hierarchy
---

# 💻 Computer Architecture & Hardware Hierarchy

> The structural design and functional organization of CPUs, memory subsystems, and buses that define hardware execution capabilities.

---

## 🎯 Why It Matters
- **Mechanical Sympathy:** Writing software with hardware architecture in mind (Cache Line alignment, False Sharing, Branch Prediction) unlocks 10x–100x performance gains.
- **Bridging CPU to GPU:** Understanding CPU caches (latency-optimized) vs GPU architecture (throughput-optimized massively parallel SIMD cores) is essential for AI Infrastructure.

---

## 🧠 The Memory Latency Hierarchy

```text
Level                   Typical Size         Access Latency
────────────────────────────────────────────────────────────
Registers               ~1 KB                < 1 ns (1 cycle)
L1 Cache (Per Core)     32 - 64 KB           ~ 1 ns (4 cycles)
L2 Cache (Per Core)     512 KB - 1 MB        ~ 4 ns (14 cycles)
L3 Cache (Shared)       16 - 64 MB           ~ 15 ns (50 cycles)
Main Memory (DDR5 RAM)  16 - 128 GB          ~ 60 - 80 ns (200 cycles)
NVMe SSD Storage        512 GB - 4 TB        ~ 20,000 ns (20 µs)
Rotational Disk (HDD)   2 - 20 TB            ~ 10,000,000 ns (10 ms)
────────────────────────────────────────────────────────────
```

### Core Architecture Principles
1. **Cache Lines (64 Bytes):** CPU fetches RAM in 64-byte chunks. Accessing contiguous elements hits L1 cache instantly; accessing scattered pointers causes cache misses.
2. **Branch Prediction & Pipelining:** Modern CPUs execute speculative instructions ahead of conditional branches. Branch mispredictions flush the pipeline.
3. **SIMD (Single Instruction, Multiple Data):** Vector extensions (AVX-512, NEON) execute identical operations across multiple numbers simultaneously.

---

## 🔗 Related Topics
- [[BrainOS/03 - Core CS/Operating Systems|Operating Systems & Paging]]
- [[BrainOS/09 - AI Infrastructure/GPU Computing & CUDA|GPU Computing & CUDA]]
- [[BrainOS/00 - BrainOS Dashboard|Main Dashboard]]
