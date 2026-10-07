---
type: concept
topic: AI Infrastructure
subtopic: GPU Computing & CUDA
date: 2026-10-07
tags:
  - gpu
  - cuda
  - kernels
  - triton
  - hardware
---

# ⚡ GPU Hardware Architecture & CUDA Programming

> The massively parallel compute architecture of Graphics Processing Units (GPUs) and the CUDA programming model that executes thousands of mathematical operations concurrently across Streaming Multiprocessors.

---

## 🎯 CPU vs. GPU Architecture Comparison

```text
       CPU (Latency Optimized)                   GPU (Throughput Optimized)
┌──────────────────────────────────────┐  ┌──────────────────────────────────────┐
│  ┌─────────┐  ┌─────────┐  ┌──────┐  │  │  [Core][Core][Core][Core][Core][Core] │
│  │ Core 1  │  │ Core 2  │  │ DRAM │  │  │  [Core][Core][Core][Core][Core][Core] │
│  └─────────┘  └─────────┘  └──────┘  │  │  [Core][Core][Core][Core][Core][Core] │
│  ┌────────────────────────────────┐  │  │  [Core][Core][Core][Core][Core][Core] │
│  │   Massive L3 Cache & Branch    │  │  │  ┌────────────────────────────────┐  │
│  │      Prediction Hardware       │  │  │  │ Small L2 Cache | High HBM Band │  │
│  └────────────────────────────────┘  │  │  └────────────────────────────────┘  │
└──────────────────────────────────────┘  └──────────────────────────────────────┘
(4 - 64 Large Cores | Low Latency)         (10,000+ Small SIMD Cores | Massive Bandwidth)
```

---

## 🧠 GPU Memory Hierarchy (NVIDIA H100 / A100)

```text
Memory Level                 Typical Size        Bandwidth Latency
──────────────────────────────────────────────────────────────────
Registers (Per Thread)       ~64 - 255 KB / SM   ~30 TB/s (~1 cycle)
Shared Memory / L1 (SRAM)    ~228 KB / SM        ~15 TB/s (~15-30 cycles)
L2 Cache (On-Chip)           ~50 MB              ~5 TB/s (~200 cycles)
High Bandwidth Memory (HBM3) ~80 - 141 GB        ~3.35 TB/s (~400 cycles)
PCIe Gen5 Bus (Host RAM)     Host CPU Memory     ~64 GB/s (~1,000+ cycles)
──────────────────────────────────────────────────────────────────
```

> [!important] The Memory Bandwidth Bottleneck
> In LLM token generation, performance is almost always **Memory Bandwidth-Bound** (waiting for weights and KV-cache to transfer from HBM into SRAM), not compute-bound.

---

## 🛠️ Minimal Vector Addition in Triton (Pythonic CUDA)

```python
import triton
import triton.language as tl
import torch

@triton.jit
def vector_add_kernel(x_ptr, y_ptr, out_ptr, n_elements, BLOCK_SIZE: tl.constexpr):
    pid = tl.program_id(axis=0) # Block ID
    block_start = pid * BLOCK_SIZE
    offsets = block_start + tl.arange(0, BLOCK_SIZE)
    mask = offsets < n_elements

    x = tl.load(x_ptr + offsets, mask=mask)
    y = tl.load(y_ptr + offsets, mask=mask)
    output = x + y
    tl.store(out_ptr + offsets, output, mask=mask)

def triton_vector_add(x: torch.Tensor, y: torch.Tensor):
    output = torch.empty_like(x)
    n_elements = output.numel()
    grid = lambda meta: (triton.cdiv(n_elements, meta['BLOCK_SIZE']),)
    vector_add_kernel[grid](x, y, output, n_elements, BLOCK_SIZE=1024)
    return output
```

---

## 🔗 Related Topics
- [[BrainOS/03 - Core CS/Computer Architecture|Computer Architecture & Memory Hierarchy]]
- [[BrainOS/09 - AI Infrastructure/Model Serving & Inference|vLLM & Continuous Batching]]
- [[BrainOS/09 - AI Infrastructure/AI Infrastructure|AI Infrastructure Master Hub]]
