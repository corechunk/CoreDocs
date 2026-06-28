# 🪟 TCP Sliding Window Algorithm & Flow Control

This manual details TCP flow control, sliding window mechanics, Receive Windows (`rwnd`), and Congestion Windows (`cwnd`).

---

## 1. The Sliding Window Algorithm Mechanics

Without flow control, a high-speed server could overwhelm a low-memory mobile receiver. TCP uses a dynamic **Sliding Window** advertised in every TCP header segment.

```text
[ Sent & ACKed ] [ Sent, UnACKed ] [ Usable Window ] [ Not Usable Yet ]
                 └─────────────── Sliding Window ───────────────┘
```

The receiver advertises its available kernel buffer space as the **Receive Window (`rwnd`)**. The sender is prohibited from transmitting more unacknowledged data bytes than `rwnd`.

---

## 2. Congestion Control (Slow Start & `cwnd`)

To prevent network router buffer overflows, TCP dynamically adjusts a **Congestion Window (`cwnd`)**:
- **Slow Start:** Probes network capacity by doubling `cwnd` every Round Trip Time (RTT).
- **Congestion Avoidance:** Linearly increases `cwnd` upon detecting packet loss or duplicate ACKs.
