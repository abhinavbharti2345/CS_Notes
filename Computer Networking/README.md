---
topic: Computer Networks
type: moc
tags:
  - networking
  - moc
  - roadmap
date: 2026-09-18
---

# 🌐 Computer Networks MOC (Map of Content)

> [!abstract] 📚 Domain Overview
> A computer network is an interconnected collection of autonomous computing devices capable of exchanging data and sharing resources. This Map of Content tracks the four-stage foundational roadmap from foundational physics and edge architecture to advanced binary subnetting and packet routing.

---

## 🗺️ Curriculum Roadmap

```mermaid
flowchart TD
    S1["🌍 <b>Stage 1: Fundamentals & Architecture</b><br><i>Edge vs Core, Switching, LAN/MAN/WAN, Devices, OSI/TCP-IP</i>"]
    S2["📦 <b>Stage 2: Data Flow & Encapsulation</b><br><i>Protocols, Headers, PDUs (Frame/Packet/Segment), MTU, MAC</i>"]
    S3["🔢 <b>Stage 3: IP Addressing & Subnetting I</b><br><i>IPv4 32-bit, Binary Math, Network vs Host ID, CIDR Masks</i>"]
    S4["🧮 <b>Stage 4: Subnetting II & Operations</b><br><i>VLSM, Usable Ranges, Broadcast, NAT, Default Gateways</i>"]

    S1 --> S2 --> S3 --> S4

    classDef s1 fill:#0ea5e918,stroke:#0ea5e9,stroke-width:1.8px;
    classDef s2 fill:#6366f118,stroke:#6366f1,stroke-width:1.8px;
    classDef s3 fill:#8b5cf618,stroke:#8b5cf6,stroke-width:1.8px;
    classDef s4 fill:#10b98118,stroke:#10b981,stroke-width:1.8px;

    class S1 s1;
    class S2 s2;
    class S3 s3;
    class S4 s4;
```

---

## 📚 Roadmap Stages & Core Notes

### 🌍 Stage 1 — What is a Network & Internet Architecture
- [[Introduction to Computer Networks|🌐 01. Introduction to Computer Networks (Definition, Scale, LAN/MAN/WAN, Internet Model)]]
- [[Packets and Packet Switching|📦 02. Packets and Packet Switching (Data vs Packet, Headers, Multiplexing, Store-and-Forward)]]
- [[Switching Techniques - Packet vs Circuit|🔄 03. Switching Techniques - Packet vs Circuit (Dedicated vs Shared, Bursty Traffic, Statistical Multiplexing)]]
- [[Network Performance - Delay, Latency, Throughput|⏱️ 04. Network Performance - Delay, Latency, Throughput (Nodal Delays, Bandwidth, Throughput, Bottleneck Law)]]
- [[Network Hardware - Hub, Switch, Router, Modem|🔌 05. Network Hardware - Hub, Switch, Router, Modem (Layer 1-3 Devices, MAC Table, Collision Domains)]]
- [[OSI vs TCP-IP Model|🧱 06. Layered Models - OSI vs TCP-IP (5-Layer vs 7-Layer, PDU Hierarchy, Encapsulation Flow)]]
- `[[Network Edge and Core]]` — Hosts, Access Networks, Physical Media vs Packet-Switched Core

---

### 📦 Stage 2 — How Data Travels (Encapsulation & Data Link Layer)
- [[Network Protocols and Standards|📜 07. Network Protocols and Standards (Syntax, Semantics, Timing, Stack of Agreements, RFCs)]]
- [[Encapsulation and Decapsulation|📦 08. Encapsulation and Decapsulation (Nested Envelopes, Headers vs Payloads, Hop-by-Hop Device Processing)]]
- [[Data Units - Segment, Packet, Frame, Bits|📦 09. Protocol Data Units (Segment, Packet, Frame, Bits & TCP vs UDP Trade-offs)]]
- [[Ethernet and MAC Addressing|🪪 10. Ethernet and MAC Addressing (48-bit Hex, OUI, MAC vs IP, Hop-by-Hop Link Delivery)]]
- [[MTU and Fragmentation|📏 11. MTU and IP Fragmentation (1500-Byte Limit, Flags DF/MF, Offset, IPv4 vs IPv6 Rules)]]

---

### 🏠 Stage 3 — IP Addressing & Subnetting I
- [[IP Addressing Fundamentals|🏠 12. IP Addressing Fundamentals (IPv4 32-bit Structure, Binary Math, 8-Bit Magic Table, Octets)]]
- [[Network ID and Host ID|🏘️ 13. Network ID vs Host ID (Street & House Analogy, Ambiguity Dilemma, Role of Subnet Mask)]]
- [[Subnet Masks and CIDR Notation|🥸 14. Subnet Masks & CIDR Notation (/8 to /32 Reference Table, Slash Notation, Bitwise AND)]]
- `[[Special IP Addresses]]` — Public vs Private (RFC 1918), Loopback (`127.0.0.1`), APIPA, Broadcast

---

### 🧮 Stage 4 — Subnetting II & Routing
- `[[Subnetting and Host Range Calculation]]` — Network address, broadcast address, first/last usable IP
- `[[Variable Length Subnet Masking (VLSM)]]` — Efficient address allocation without waste
- `[[Default Gateway and ARP]]` — How packets leave the local LAN (Address Resolution Protocol)
- `[[Network Address Translation (NAT)]]` — Private-to-public IP translation, PAT, port mapping
- `[[IPv6 Fundamentals]]` — 128-bit addressing, hex notation, motivation, coexistence with IPv4

---

## 🔗 Cross-Domain CS Connections

| Related CS Domain | Connection Point |
| :--- | :--- |
| **[[Operating Systems]]** | Sockets, network system calls (`socket()`, `bind()`, `connect()`), I/O multiplexing (`epoll`), kernel network buffers. |
| **[[WebDev/Backend/README\|Backend Development]]** | HTTP/HTTPS, WebSockets, REST APIs, TCP handshake latency, load balancing. |
| **[[Distributed Systems]]** | Network partitions (CAP theorem), consensus over unreliable networks, RPC mechanisms. |
| **Security** | Firewalls, packet filtering, ARP spoofing, Man-in-the-Middle (MitM), TLS/SSL encryption. |
