# 🌐 Networking & Protocol Architecture Hub

Welcome to the central architectural hub for computer networking, routing physics, socket programming, application protocols, and advanced decentralized/anonymity networks.

---

## 🗺️ Direct Topic & Sub-Hub Index

### 🌐 Network Layer & Protocol Fundamentals
- 🌉 [**00-OSI-vs-TCPIP-model.md**](./00-OSI-vs-TCPIP-model.md) — 7-Layer OSI theoretical model mapped to the 4-Layer TCP/IP software execution stack.
- 🏷️ [**01-mac-address-and-arp.md**](./01-mac-address-and-arp.md) — Layer 2 Ethernet frames, 48-bit MAC addresses, and Address Resolution Protocol (ARP) tables.
- 📡 [**02-IPv4-fundamentals.md**](./02-IPv4-fundamentals.md) — 32-bit IPv4 addressing structure, IP packet headers, Time-to-Live (TTL), and packet fragmentation.
- 🔢 [**03-CIDR-subnetting.md**](./03-CIDR-subnetting.md) — Subnet masks (`/24`, `/16`, `/8`), IP network IDs, usable host ranges, and broadcast address calculations.
- 🌍 [**04-IPv6-link-local.md**](./04-IPv6-link-local.md) — 128-bit IPv6 structures, link-local automatic addresses (`fe80::`), and SLAAC neighbor discovery.
- 🔀 [**05-NAT-PAT-translation.md**](./05-NAT-PAT-translation.md) — Network Address Translation (NAT) and Port Address Translation (PAT) router lookup tables.
- 🔍 [**06-DNS-resolution-physics.md**](./06-DNS-resolution-physics.md) — Recursive DNS lookup chains, A/AAAA records, root/TLD servers, and operating system DNS caching.

---

### 🔌 Transport Physics & Application Protocols
- 🔌 [**07-TCP-UDP-Sockets**](./07-TCP-UDP-Sockets/README.md) — POSIX socket allocation (`socket`, `bind`, `listen`, `accept`), SYN/ACK state machines, TCP Sliding Window flow control, and network endianness (`htons`/`htonl`).
- 📄 [**08-HTTP**](./08-HTTP/README.md) — HTTP/1.1 protocol specification, raw request/response header parsing, and state machine buffer handlers.
- 🔒 [**09-HTTPS**](./09-HTTPS/README.md) — TLS/SSL cryptographic handshakes, asymmetric key exchange (ECDHE), symmetric stream ciphers (AES-GCM), and OpenSSL engine integration.

---

### 🕸️ Advanced Decentralized & Anonymity Networks
- 👥 [**10-Advanced-P2P-Architectures**](./10-Advanced-P2P-Architectures/README.md) — Peer-to-Peer file sharing wire protocols (BitTorrent piece hashing), Kademlia Distributed Hash Tables (DHT), and STUN hole-punching overlay mesh VPNs.
- 🧅 [**11-Tor-Onion-Routing**](./11-Tor-Onion-Routing/README.md) — Tor anonymity network architecture, 3-hop circuit construction (Guard, Middle, Exit nodes), layered multi-layer TLS encryption, and Onion hidden services (`.onion`).
