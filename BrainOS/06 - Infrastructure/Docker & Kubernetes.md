---
type: hub
topic: Infrastructure
subtopic: Docker & Kubernetes
date: 2026-10-07
tags:
  - docker
  - kubernetes
  - containers
  - microservices
  - curriculum
---

# 🐳 Docker & Kubernetes Master Roadmap

> **Roadmap:** Containerization packaging and declarative distributed cluster orchestration ensuring reproducible deployments across any cloud or local environment.

---

## 🎯 Why Learn This?
- **Eliminate "Works on My Machine":** Package application code, runtimes, system dependencies, and configs into immutable container images.
- **Automated Self-Healing:** Kubernetes automatically restarts crashed pods, rolls out updates with zero downtime, and scales replicas based on CPU/memory metrics.
- **The Universal Cloud OS:** Kubernetes is the industry-standard substrate for microservices, data pipelines, and AI training workloads.

---

## 🔗 Prerequisites
- [[BrainOS/03 - Core CS/Operating Systems|Operating Systems & Linux]] (Namespaces, cgroups, file systems)
- [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering]] (Dockerizing web services)
- [[BrainOS/06 - Infrastructure/Cloud & AWS|Cloud Fundamentals]]

---

## 🗺️ Learning Order & Topic Breakdown

```mermaid
%%{init: {'theme': 'base', 'themeVariables': { 'darkMode': true, 'background': '#0B0F14', 'mainBkg': '#111827', 'primaryColor': '#111827', 'primaryTextColor': '#F8FAFC', 'primaryBorderColor': '#38BDF8', 'lineColor': '#64748B', 'secondaryColor': '#0B0F14', 'tertiaryColor': '#0B0F14', 'clusterBkg': '#0B0F14', 'clusterBorder': '#38BDF8' }}}%%
flowchart TD
    DK1["<b>1. Container Basics:</b> Dockerfile, Multi-Stage Builds, Images, Layers"] --> DK2["<b>2. Multi-Container Orchestration:</b> Docker Compose, Bridge Networks, Volumes"]
    DK2 --> DK3["<b>3. Kubernetes Fundamentals:</b> Pods, Deployments, ReplicaSets, Services"]
    DK3 --> DK4["<b>4. Storage & Config:</b> ConfigMaps, Secrets, PersistentVolumes (PV/PVC)"]
    DK4 --> DK5["<b>5. Ingress & Routing:</b> Nginx Ingress Controller, TLS, Path Routing"]
    DK5 --> DK6["<b>6. Advanced Scaling & GitOps:</b> HPA, Helm Charts, ArgoCD Deployments"]

    style DK1 fill:#111827,stroke:#22D3EE,stroke-width:1.8px,color:#F8FAFC
    style DK2 fill:#111827,stroke:#22D3EE,stroke-width:1.8px,color:#F8FAFC
    style DK3 fill:#111827,stroke:#38BDF8,stroke-width:1.8px,color:#F8FAFC
    style DK4 fill:#111827,stroke:#38BDF8,stroke-width:1.8px,color:#F8FAFC
    style DK5 fill:#111827,stroke:#34D399,stroke-width:1.8px,color:#F8FAFC
    style DK6 fill:#111827,stroke:#FB923C,stroke-width:1.8px,color:#F8FAFC
```

### 1. Docker & Container Internals
- Linux cgroups (Resource limits) and namespaces (PID, Mount, Network isolation)
- Dockerfile optimization: Layer caching, Multi-stage builds, Minimal distroless/alpine bases
- Container networking, volume mounts, and container lifecycle commands

### 2. Multi-Container Systems (Docker Compose)
- Defining local microservice stacks (App + PostgreSQL + Redis) in `docker-compose.yml`
- Environment variables, health checks, and service dependency ordering (`depends_on`)

### 3. Kubernetes Core Architecture
- Control Plane (API Server, etcd, Scheduler, Controller Manager) vs Worker Nodes (Kubelet, Kube-Proxy, Container Runtime)
- Workloads: Pods (Atomic scheduling unit), ReplicaSets, Deployments
- Rolling updates, rollbacks, and readiness/liveness health probes

### 4. Kubernetes Networking & Services
- ClusterIP (Internal cluster communication), NodePort, and LoadBalancer
- Ingress Controllers (Nginx Ingress, Traefik, AWS ALB Ingress)
- CoreDNS service discovery and Kubernetes Network Policies

### 5. Configuration, Storage & Packaging
- ConfigMaps (Non-sensitive configuration) and Secrets (Encrypted credentials)
- PersistentVolumes (PV) and PersistentVolumeClaims (PVC)
- Helm: Templating manifests, values files, chart dependencies, and releases

### 6. Production Operations & GitOps
- Horizontal Pod Autoscaler (HPA) based on CPU/memory and custom Prometheus metrics
- GitOps continuous delivery with ArgoCD / Flux

---

## 🚀 Unlocks
- → [[BrainOS/06 - Infrastructure/DevOps & Observability|DevOps & Production Observability]]
- → [[BrainOS/09 - AI Infrastructure/Model Serving & Inference|vLLM Model Serving on Kubernetes]]
- → Enterprise Microservices Operations

---

## 🧪 Suggested Project
- **Cloud-Native Microservices Cluster (Level 7):** Deploy a multi-service application with Redis, PostgreSQL, and Ingress on a local Minikube / AWS EKS cluster managed with Helm charts.

---

## 📚 Detailed Notes in Vault
- [[BrainOS/04 - Software Engineering/Testing & CI-CD|Testing & CI-CD]]
- [[BrainOS/06 - Infrastructure/Cloud & AWS|Cloud & AWS]]
