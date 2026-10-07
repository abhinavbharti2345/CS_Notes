---
type: concept
topic: AI Infrastructure
subtopic: Quantization & Distributed Inference
date: 2026-10-07
tags:
  - quantization
  - tensor-parallelism
  - awq
  - fp8
  - distributed-inference
---

# 📉 Quantization & Multi-GPU Distributed Inference

> Compression techniques to reduce precision representation (FP16 $\rightarrow$ INT4/FP8) and distributed model partitioning strategies across NVLink-connected GPUs.

---

## 🎯 Quantization Techniques (AWQ, GPTQ, FP8)

| Format | Bits Per Weight | Memory Savings | Quality Loss | Best Use Case |
| :--- | :--- | :--- | :--- | :--- |
| **FP16 / BF16** | 16 bits (2 bytes) | Baseline | 0% (Full precision) | Model Training & High-precision baseline |
| **FP8 (E4M3/E5M2)** | 8 bits (1 byte) | 50% Reduction | Negligible ($< 0.5\%$) | NVIDIA Hopper (H100/H200) production serving |
| **AWQ (Activation-aware)** | 4 bits (0.5 bytes) | 75% Reduction | Low ($< 1\%$) | Low-latency edge & single-GPU 70B model serving |
| **GPTQ** | 4 bits (0.5 bytes) | 75% Reduction | Low | Offline post-training weight compression |

---

## 🌐 Multi-GPU Parallelism Models

```mermaid
flowchart TD
    subgraph PARALLEL_MODELS ["Distributed GPU Parallelism Strategies"]
        direction TB
        subgraph TP ["1. Tensor Parallelism (TP - Megatron-LM)"]
            direction LR
            W1["<b>GPU 0:</b> $W_1$ Col Slice"] <-->|All-Reduce (NVLink)| W2["<b>GPU 1:</b> $W_2$ Row Slice"]
        end

        subgraph PP ["2. Pipeline Parallelism (PP)"]
            direction LR
            L1["<b>GPU 0:</b> Layers 1-16"] -->|Activations| L2["<b>GPU 1:</b> Layers 17-32"]
        end

        subgraph DP ["3. Data Parallelism (DP)"]
            direction LR
            D1["<b>GPU 0:</b> Model Copy (Batch 1)"] --- D2["<b>GPU 1:</b> Model Copy (Batch 2)"]
        end
    end

    style PARALLEL_MODELS fill:#0B0F14,stroke:#FACC15,stroke-width:2px,color:#FACC15
    style TP fill:#0B0F14,stroke:#38BDF8,stroke-width:1.5px,color:#38BDF8
    style PP fill:#0B0F14,stroke:#A78BFA,stroke-width:1.5px,color:#A78BFA
    style DP fill:#0B0F14,stroke:#34D399,stroke-width:1.5px,color:#34D399

    classDef tpSt stroke:#38BDF8,stroke-width:1.8px;
    classDef ppSt stroke:#A78BFA,stroke-width:1.8px;
    classDef dpSt stroke:#34D399,stroke-width:1.8px;
    class W1,W2 tpSt;
    class L1,L2 ppSt;
    class D1,D2 dpSt;
```

### 1. Tensor Parallelism (TP)
- Splits individual weight matrices ($W$) across GPUs within a single server over ultra-high-speed **NVLink (900 GB/s)**.
- Each attention head/MLP layer is computed in parallel, followed by a fast `All-Reduce` communication step.

### 2. Pipeline Parallelism (PP)
- Splits model layers sequentially across nodes (e.g. Layers 1–16 on Node 1, Layers 17–32 on Node 2).
- Communicates activations over InfiniBand (slower, requires micro-batch pipelining to avoid bubble idle time).

---

## 🔗 Related Topics
- [[BrainOS/09 - AI Infrastructure/GPU Computing & CUDA|GPU Computing & CUDA]]
- [[BrainOS/09 - AI Infrastructure/Model Serving & Inference|vLLM Model Serving]]
- [[BrainOS/09 - AI Infrastructure/AI Infrastructure|AI Infrastructure Master Hub]]
