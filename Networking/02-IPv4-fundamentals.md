# 📡 IPv4 Fundamentals & Packet Structure

This manual details the 32-bit Internet Protocol Version 4 (IPv4) address structure, packet header layouts, and fragmentation mechanics.

---

## 1. 32-Bit Dotted-Decimal Addressing

IPv4 addresses consist of 32 binary bits divided into four 8-bit octets separated by dots (e.g., `192.168.1.1`). Total global address space is limited to $2^{32} \approx 4.3 \text{ billion}$ unique addresses.

---

## 2. IPv4 Packet Header Layout

Every IPv4 packet travelling across the internet wraps data with a 20-byte base header.

```text
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|Version|  IHL  |Type of Service|          Total Length         |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|         Identification        |Flags|      Fragment Offset    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|  Time to Live |    Protocol   |        Header Checksum        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       Source IP Address                       |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Destination IP Address                     |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

### Key Field Descriptions
- **Time to Live (TTL):** An 8-bit hop counter decremented by 1 at every router hop. Prevents lost packets from looping infinitely across the internet (drops with ICMP Time Exceeded when TTL = 0).
- **Protocol:** Identifies encapsulated payload protocol (6 for TCP, 17 for UDP, 1 for ICMP).
- **Identification & Flags:** Governs IP packet fragmentation when packets exceed Maximum Transmission Unit (MTU) sizes (typically 1500 bytes).
