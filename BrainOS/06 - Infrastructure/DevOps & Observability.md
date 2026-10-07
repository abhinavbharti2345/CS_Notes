---
type: concept
topic: Infrastructure
subtopic: DevOps & Observability
date: 2026-10-07
tags:
  - devops
  - observability
  - prometheus
  - grafana
  - opentelemetry
  - metrics
---

# 🔭 DevOps, Monitoring & Observability

> The operational telemetry discipline structured around the Three Pillars of Observability (Metrics, Logs, Traces) to understand system health, diagnose anomalies, and maintain SLAs.

---

## 🎯 The Three Pillars of Observability

```text
                     OBSERVABILITY
                          │
          ┌───────────────┼───────────────┐
          │               │               │
          ▼               ▼               ▼
       METRICS          LOGS           TRACES
    (Prometheus)      (Loki/ELK)    (OpenTelemetry)
   "Is it broken?"   "Why did it    "Where is the
                     break?"        bottleneck?"
```

| Pillar | Technology Stack | Format | Purpose |
| :--- | :--- | :--- | :--- |
| **Metrics** | Prometheus, Grafana, Datadog | Time-series numeric aggregations (Counter, Gauge, Histogram) | High-level alerting, CPU/memory saturation, request rates ($p50, p95, p99$) |
| **Logs** | Loki, Elasticsearch, Fluentbit | Structured JSON event lines with context | Detailed post-mortem error stack traces and forensic inspection |
| **Traces** | OpenTelemetry, Jaeger, Zipkin | Distributed Span IDs tracking requests across microservices | Pinpointing downstream RPC latency bottlenecks across service hops |

---

## 📊 The 4 Golden Signals (Google SRE)
1. **Latency:** Time taken to service a request (differentiate between successful requests and error latencies).
2. **Traffic:** Demand placed on the system (e.g., HTTP requests/sec, concurrent transactions).
3. **Errors:** Rate of requests that fail (e.g., HTTP 5xx responses, explicit exceptions).
4. **Saturation:** Measure of system utilization (e.g., memory usage %, thread pool queue depth, CPU load).

---

## 🔗 Related Topics
- [[BrainOS/06 - Infrastructure/Docker & Kubernetes|Docker & Kubernetes]]
- [[BrainOS/06 - Infrastructure/Cloud & AWS|Cloud & AWS]]
- [[BrainOS/09 - AI Infrastructure/AI Infrastructure|AI Infrastructure Monitoring]]
