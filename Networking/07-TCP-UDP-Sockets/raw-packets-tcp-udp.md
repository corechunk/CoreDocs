# 📦 Raw Packets: TCP Stream vs. UDP Datagram Semantics

This manual compares TCP stream semantics against UDP datagram semantics.

---

## 1. Architectural Comparison Matrix

| Feature Metric | Transmission Control Protocol (TCP) | User Datagram Protocol (UDP) |
|---|---|---|
| **Connection State** | Connection-oriented (Requires handshake) | Connectionless (Fire and forget) |
| **Reliability** | Guaranteed delivery (Retransmits lost packets) | Unreliable (No retransmissions or ACKs) |
| **Ordering** | Guaranteed in-order stream reconstruction | Unordered datagram delivery |
| **Framing Boundary** | Byte-stream (No packet boundary markers) | Message-based (Preserves datagram boundaries) |
| **Header Overhead** | Heavy 20-byte baseline header | Lightweight 8-byte baseline header |
| **Primary Use Cases** | Web pages, file transfers, SSH, databases | Video streaming, online gaming, DNS queries |
