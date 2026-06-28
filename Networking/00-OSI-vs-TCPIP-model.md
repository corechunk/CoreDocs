# 🌉 The OSI 7-Layer vs. TCP/IP 4-Layer Model Bridge

This guide bridges academic network theory with practical software engineering by comparing the traditional 7-layer OSI model against the practical 4-layer TCP/IP execution stack.

---

## 1. Architectural Comparison Matrix

| OSI 7-Layer Model | TCP/IP 4-Layer Stack | Primary Function & Hardware/Software Execution Realm | Example Protocols & Units |
|---|---|---|---|
| **Layer 7: Application** | **Application Layer** | High-level user applications and data formats. (Software Realm) | HTTP, HTTPS, SSH, DNS, FTP |
| **Layer 6: Presentation** | *(Merged into Application)* | Data encoding, compression, and TLS/SSL encryption. | TLS, ASCII, JSON, UTF-8 |
| **Layer 5: Session** | *(Merged into Application)* | Managing persistent session connections between applications. | POSIX Sockets, RPC, NetBIOS |
| **Layer 4: Transport** | **Transport Layer** | Host-to-host process communication and reliable data delivery. | TCP, UDP (Segment / Datagram) |
| **Layer 3: Network** | **Internet Layer** | Packet routing across logical global networks. | IPv4, IPv6, ICMP (Packet) |
| **Layer 2: Data Link** | **Link Layer** | Local hardware network frame delivery across physical media. | Ethernet, Wi-Fi 802.11, ARP (Frame) |
| **Layer 1: Physical** | *(Merged into Link)* | Raw binary bit transmission over physical signals. (Hardware Realm) | Copper Cable, Fiber, Radio Waves (Bits) |

---

## 2. Encapsulation & Decapsulation Physics

When sending data across a network, higher-layer data is wrapped in lower-layer headers during **Encapsulation**. When receiving data, headers are stripped off during **Decapsulation**.

```text
[ Data ]                                       <-- Application Layer (Payload)
[ TCP Header | Data ]                          <-- Transport Layer (Segment)
[ IP Header | TCP Header | Data ]              <-- Internet Layer (Packet)
[ Frame Header | IP Header | TCP | Data | FCS ] <-- Link Layer (Frame)
```
