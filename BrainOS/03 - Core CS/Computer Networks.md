---
type: hub
topic: Core CS
subtopic: Computer Networks
date: 2026-10-07
tags:
  - networking
  - tcp-ip
  - osi-model
  - http
  - sockets
  - curriculum
---

# 🌐 Computer Networks Master Roadmap

> **Roadmap:** The communication backbone of the Internet. Master layered protocol stacks, packet flow, transport reliability, and application protocols before designing distributed systems and cloud networks.

---

## 🎯 Why Learn This?
- **Connect Isolated Machines:** Understand how packets travel across physical links, routers, and switches to connect distributed nodes.
- **Diagnose Network Latency:** Know why packet drops occur, how TCP congestion windows adapt, and where latency originates (DNS, TLS handshake, RTT).
- **Architect Resilient Backend APIs:** Design robust REST/gRPC endpoints with keep-alives, connection pooling, and proper timeouts.

---

## 🔗 Prerequisites
- [[BrainOS/02 - Foundations/Programming/Java|Programming Foundations]] (Sockets, I/O Streams)
- [[BrainOS/03 - Core CS/Operating Systems|Operating Systems]] (File descriptors, I/O multiplexing, concurrency)

---

## 🗺️ Learning Order & Topic Breakdown

![[osi_vs_tcp_ip_architecture.drawio.svg]]

### 1. Network Models & Architecture
- Layered Abstractions: OSI 7-Layer vs TCP/IP 5-Layer model
- Packet Switching vs Circuit Switching
- Network Performance metrics: Latency, Bandwidth, Throughput, Jitter, RTT

### 2. Data Flow & Encapsulation
- PDU transitions: Application Data → Segment → Packet → Frame → Bits
- Ethernet, MAC addressing, Address Resolution Protocol (ARP)
- Maximum Transmission Unit (MTU), MSS, and IP Packet Fragmentation

### 3. Network Layer & Addressing
- IPv4 structure, Classless Inter-Domain Routing (CIDR), Subnet Masks
- Public vs Private IP ranges, Network Address Translation (NAT)
- Routing Algorithms: Distance Vector (Bellman-Ford / RIP), Link State (Dijkstra / OSPF), BGP

### 4. Transport Layer (TCP vs UDP)
- UDP: Connectionless, lightweight datagrams (DNS, Video streaming, QUIC)
- TCP: Connection-oriented reliability, sequence numbers, checksums
- TCP Three-Way Handshake (`SYN`, `SYN-ACK`, `ACK`) and Four-Way Teardown (`FIN`)
- Flow Control (Sliding Window) and Congestion Control (Slow Start, Congestion Avoidance, AIMD)

### 5. Application Layer Protocols
- DNS: Hierarchical resolution (Root, TLD, Authoritative), DNS record types (A, CNAME, MX)
- HTTP/1.1 vs HTTP/2 (Multiplexing, Header Compression) vs HTTP/3 (QUIC over UDP)
- TLS / HTTPS Handshake, Public Key Infrastructure (PKI), Certificates

### 6. Edge & Scale Infrastructure
- Reverse Proxies (Nginx, Envoy) vs Forward Proxies
- Load Balancers: Layer 4 (TCP/UDP) vs Layer 7 (HTTP/Path routing)
- Content Delivery Networks (CDNs) and Anycast routing

---

## 🚀 Unlocks
- → [[BrainOS/04 - Software Engineering/Backend Engineering|Backend Engineering]] (REST APIs, WebSockets, gRPC)
- → [[BrainOS/05 - Systems/Distributed Systems|Distributed Systems]] (RPCs, partition tolerance, consensus heartbeats)
- → [[BrainOS/06 - Infrastructure/Cloud & AWS|Cloud & VPC Networking]] (Subnets, Security Groups, ALBs)
- → [[BrainOS/05 - Systems/System Design|System Design Architecture]] (Load balancing, CDN caching)

---

## 🧪 Suggested Project
- **Raw Socket Protocol Analyzer:** Build a Java CLI tool that captures raw network packets, parses Ethernet frames, and dissects IP/TCP headers.

---

## 📚 Detailed Notes in Vault
- [[CS/Computer Networking/00. Networking Nexus|CS > Computer Networking Hub]]
- [[CS/Computer Networking/01. Architecture & Fundamentals/README|Architecture & Fundamentals]]
- [[CS/Computer Networking/02. Data Flow & Encapsulation/README|Data Flow & Encapsulation]]
- [[CS/Computer Networking/03. IP Addressing & Subnetting/01. IP Addressing Fundamentals|IP Addressing & Subnetting]]
- [[CS/Computer Networking/04. Routing & Network Layer/README|Routing & Network Layer]]
