---
type: concept
topic: AI Infrastructure
subtopic: Model Serving & Inference
date: 2026-10-07
tags:
  - inference
  - vllm
  - pagedattention
  - continuous-batching
  - tensorrt
---

# 🚀 Model Serving & High-Throughput Inference (vLLM)

> Modern high-throughput LLM inference architectures designed to eliminate memory fragmentation and maximize GPU utilization through PagedAttention and Continuous Iteration-Level Batching.

---

## 🎯 The Two Key Breakthroughs of vLLM

### 1. PagedAttention (Virtual Memory for KV-Cache)
- **The Problem:** Traditional inference pre-allocated contiguous memory blocks for the maximum context window (e.g. 8K tokens) per request, resulting in 60%–80% memory waste due to internal/external fragmentation.
- **The Solution:** Inspired by **Virtual Memory Paging in Operating Systems**, PagedAttention splits KV-Cache into fixed-size physical blocks (e.g. 16 tokens) mapped dynamically via a logical Block Table.

```mermaid
flowchart TD
    subgraph PAGED_ATTN ["PagedAttention: Logical vs Physical KV Memory"]
        direction LR
        subgraph LOGICAL ["Logical KV Tokens"]
            direction TB
            L1["Tokens 0 - 15 (Block 0)"]
            L2["Tokens 16 - 31 (Block 1)"]
            L3["Tokens 32 - 47 (Block 2)"]
        end

        subgraph TABLE ["Block Table Mapping"]
            direction TB
            T1["Block 0 ➔ Phys #7"]
            T2["Block 1 ➔ Phys #2"]
            T3["Block 2 ➔ Phys #9"]
        end

        subgraph PHYSICAL ["Physical GPU VRAM Pool"]
            direction TB
            P7["<b>Physical Block #7</b>"]
            P2["<b>Physical Block #2</b>"]
            P9["<b>Physical Block #9</b>"]
        end

        L1 & L2 & L3 --> TABLE
        TABLE --> P7 & P2 & P9
    end

    style PAGED_ATTN stroke:#FACC15,stroke-width:2px,color:#FACC15
    style LOGICAL stroke:#38BDF8,stroke-width:1.5px,color:#38BDF8
    style TABLE stroke:#E879F9,stroke-width:1.5px,color:#E879F9
    style PHYSICAL stroke:#FACC15,stroke-width:1.5px,color:#FACC15

    classDef logNode stroke:#38BDF8,stroke-width:1.8px;
    classDef tabNode stroke:#E879F9,stroke-width:1.8px;
    classDef physNode stroke:#FACC15,stroke-width:2px;

    class L1,L2,L3 logNode;
    class T1,T2,T3 tabNode;
    class P7,P2,P9 physNode;
```

### 2. Continuous (Iteration-Level) Batching
- Traditional static batching waited for the slowest sequence in a batch to finish before accepting new requests (massive idle time).
- Continuous batching operates at the token-iteration level: as soon as a sequence generates `<EOS>`, it is evicted and a new pending request enters the next iteration instantly.

---

## 📊 Core Serving Metrics
- **Time to First Token (TTFT):** Measures prefill speed and queue latency (critical for interactive user responsiveness).
- **Time Per Output Token (TPOT) / Inter-Token Latency (ITL):** Measures auto-regressive generation speed (e.g., 20ms/token $\approx$ 50 tokens/sec).
- **Tokens Per Second Per Dollar:** The true operational efficiency benchmark of model serving platforms.

---

## 🔗 Related Topics
- [[BrainOS/03 - Core CS/Operating Systems|Operating Systems (Paging & Virtual Memory)]]
- [[BrainOS/09 - AI Infrastructure/Quantization & Distributed Inference|Quantization & Scaling]]
- [[BrainOS/09 - AI Infrastructure/AI Infrastructure|AI Infrastructure Master Hub]]
