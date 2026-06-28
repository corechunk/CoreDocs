# 🔌 Transport Physics & Socket Sub-Hub

Welcome to the low-level Transport Layer sub-hub. This hub details POSIX socket descriptors, TCP 3-way handshakes, TCP Sliding Window flow control, and endianness byte conversions.

---

## 🗺️ Direct Socket Physics Index

- 🔌 [**socket-allocation.md**](./socket-allocation.md) — POSIX file descriptors (`int fd`), `socket()`, `bind()`, `listen()`, and `accept()` execution loops.
- 🤝 [**tcp-handshake-state-machine.md**](./tcp-handshake-state-machine.md) — SYN/ACK 3-way handshake, connection teardowns, `TIME_WAIT`, and `RST` reset packets.
- 🪟 [**tcp-sliding-window-flow-control.md**](./tcp-sliding-window-flow-control.md) — TCP Sliding Window algorithm, Receive Window (`rwnd`), Congestion Window (`cwnd`), and Slow Start.
- 🔄 [**endianness-conversion.md**](./endianness-conversion.md) — Big-Endian network byte order vs Little-Endian host systems (`htons`, `htonl`, `ntohs`, `ntohl`).
- 📦 [**raw-packets-tcp-udp.md**](./raw-packets-tcp-udp.md) — Reliable TCP stream semantics vs connectionless UDP datagrams & raw socket sniffing.
