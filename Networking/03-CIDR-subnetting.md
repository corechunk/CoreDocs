# 🔢 CIDR Subnetting & Network Address Calculations

This guide details Classless Inter-Domain Routing (CIDR) notation, subnet masks, and mathematical IP range calculations.

---

## 1. CIDR Notation & Subnet Masks

CIDR notation appends a suffix `/N` to an IP address (e.g., `192.168.1.0/24`), indicating that the first $N$ bits represent the **Network Identifier**, while the remaining $32 - N$ bits represent individual **Host Identifiers**.

| CIDR Notation | Subnet Mask Binary Equivalent | Subnet Mask Dotted Decimal | Total Usable Hosts ($2^{32-N} - 2$) |
|---|---|---|---|
| `/24` | `11111111.11111111.11111111.00000000` | `255.255.255.0` | 254 hosts |
| `/16` | `11111111.11111111.00000000.00000000` | `255.255.0.0` | 65,534 hosts |
| `/8` | `11111111.00000000.00000000.00000000` | `255.0.0.0` | 16,777,214 hosts |

---

## 2. Mathematical Calculation Example (`192.168.1.100/24`)

1. **Network Address:** Set all host bits to 0 -> `192.168.1.0` (Identifies the subnet network).
2. **Broadcast Address:** Set all host bits to 1 -> `192.168.1.255` (Targeted for local broadcasts).
3. **Usable Host Range:** `192.168.1.1` through `192.168.1.254`.
