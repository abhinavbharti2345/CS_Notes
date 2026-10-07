---
type: concept
topic: LLM & GenAI
subtopic: RAG & Vector Databases
date: 2026-10-07
tags:
  - rag
  - vector-databases
  - embeddings
  - qdrant
  - search
---

# 📚 Retrieval-Augmented Generation (RAG) & Vector Databases

> The architecture that grounds LLM responses with proprietary, up-to-date external knowledge by retrieving relevant context from vector indices before generation, eliminating hallucinations.

---

## 🎯 Why It Matters
- **Eliminating Hallucinations:** LLM parametric memory is fixed at training cutoff and prone to hallucinating facts. RAG injects verified source documents directly into the prompt context.
- **Cost & Efficiency:** Updating domain knowledge via vector embeddings costs fractions of a cent, whereas full model retraining or fine-tuning costs thousands of dollars.
- **Enterprise Access Control:** Vector retrieval allows document-level metadata filtering matching user role permissions (RBAC).

---

## 🏗️ Advanced Production RAG Pipeline

```mermaid
flowchart TD
    subgraph INGESTION ["1. Document Ingestion Pipeline"]
        direction LR
        DOC["<b>Raw PDFs / Docs</b>"] --> CHUNK["<b>Recursive Chunking</b><br/>(512 tokens + 10% overlap)"]
        CHUNK --> EMBED["<b>Embedding Model</b><br/>(e.g., text-embedding-3-small)"]
        EMBED --> VDB[("<b>Vector Database (Qdrant)</b><br/>(HNSW Index + Metadata)")]
    end

    subgraph RETRIEVAL ["2. Query & Generation Pipeline"]
        direction TB
        Q["<b>User Query</b>"] --> HYBRID["<b>Hybrid Search</b><br/>(Dense Vector + Sparse BM25)"]
        VDB --> HYBRID
        HYBRID --> RERANK["<b>Cross-Encoder Re-ranker</b><br/>(Cohere / BGE-Reranker)"]
        RERANK --> CONTEXT["<b>Top-K Context Chunks</b>"]
        CONTEXT & Q --> LLM["<b>LLM Generation with Citations</b>"]
    end

    style INGESTION stroke:#38BDF8,stroke-width:1.8px,color:#38BDF8
    style RETRIEVAL stroke:#E879F9,stroke-width:1.8px,color:#E879F9

    classDef ingestNode stroke:#38BDF8,stroke-width:1.8px;
    classDef vdbNode stroke:#A78BFA,stroke-width:2px;
    classDef queryNode stroke:#22D3EE,stroke-width:1.8px;
    classDef rankNode stroke:#34D399,stroke-width:1.8px;
    classDef llmNode stroke:#E879F9,stroke-width:2px;

    class DOC,CHUNK,EMBED ingestNode;
    class VDB vdbNode;
    class Q,CONTEXT queryNode;
    class HYBRID,RERANK rankNode;
    class LLM llmNode;
```

---

## 🧠 Core Vector Database Mechanics
- **Hierarchical Navigable Small World (HNSW):** Multi-layer graph index enabling sub-linear $O(\log N)$ approximate nearest neighbor (ANN) vector search.
- **Cosine Distance vs Dot Product vs Euclidean ($L_2$):**
  $$\text{Cosine Similarity}(u, v) = \frac{u \cdot v}{\|u\|_2 \|v\|_2}$$
- **Hybrid Search with Reciprocal Rank Fusion (RRF):** Merges dense semantic embeddings (captures conceptual meaning) with sparse BM25 keyword search (captures exact product IDs, acronyms, and names).

---

## 🔗 Related Topics
- [[BrainOS/08 - LLM & GenAI/LLM Engineering|LLM Engineering]]
- [[BrainOS/08 - LLM & GenAI/AI Agents|AI Agents]]
- [[BrainOS/08 - LLM & GenAI/Fine Tuning & Evaluation|Evaluation & RAGAS]]
- [[BrainOS/00 - BrainOS Dashboard|Main Dashboard]]
