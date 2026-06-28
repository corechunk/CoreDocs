# 🏷️ Layer 2 Data Link Physics: MAC Addresses & ARP

This manual details physical Local Area Network (LAN) communication, Ethernet frames, 48-bit MAC addresses, and Address Resolution Protocol (ARP) operations.

---

## 1. MAC Addresses (Media Access Control)

Every Network Interface Card (NIC)—whether Ethernet or Wi-Fi—is burned with a unique 48-bit (6-byte) physical hardware address formatted in hexadecimal (e.g., `00:1A:2B:3C:4D:5E`).
- **First 3 Bytes (`00:1A:2B`):** Organizationally Unique Identifier (OUI) assigned to hardware manufacturers (Intel, Realtek, Apple).
- **Last 3 Bytes (`3C:4D:5E`):** Unique device serial number.

---

## 2. Address Resolution Protocol (ARP) Operation

IP addresses are logical and change per network. To deliver an Ethernet frame to a host on the same local network, the OS must translate target IP addresses into physical MAC addresses using **ARP**.

### 2.1 The ARP Lookup Workflow (`Who has 192.168.1.50?`)

1. **ARP Cache Probe:** The operating system inspects its local kernel ARP table (`arp -a`). If the MAC address is missing, it constructs an ARP Request.
2. **Ethernet Broadcast:** The sender broadcasts an ARP request packet to destination MAC `FF:FF:FF:FF:FF:FF` across the local LAN switch.
3. **Unicast Reply:** The target device (`192.168.1.50`) recognizes its IP and sends an ARP Reply containing its physical MAC address directly back to the requester.
4. **Cache Insertion:** The sender updates its kernel ARP table for subsequent zero-latency frame transmission.
