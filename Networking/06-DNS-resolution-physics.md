# 🔍 DNS Resolution Physics: How Domain Names Become IPs

This manual details the Domain Name System (DNS) recursive resolution chain, DNS record types, and operating system caching layers.

---

## 1. The Recursive DNS Resolution Chain

When typing `https://example.com` into a browser, the system resolves human-readable strings into 32-bit IPv4 or 128-bit IPv6 addresses through a 4-step hierarchy:

```text
[ Client OS Cache / hosts ] ──(Cache Miss)──> [ Recursive DNS Resolver (ISP/1.1.1.1) ]
                                                       │
                                                       ├── 1. Query Root Server (.) ────> Returns TLD (.com)
                                                       ├── 2. Query TLD Server (.com) ──> Returns Authoritative
                                                       └── 3. Query Authoritative Server ─> Returns IP Address
```

---

## 2. Essential DNS Record Types

| Record Type | Full Name | Functional Role & Return Value |
|---|---|---|
| **`A`** | IPv4 Address Record | Maps hostname directly to a 32-bit IPv4 address (`93.184.216.34`). |
| **`AAAA`** | IPv6 Address Record | Maps hostname directly to a 128-bit IPv6 address (`2606:2800:220:1:248:1893:25c8:1946`). |
| **`CNAME`** | Canonical Name Record | Alias mapping one domain name to another canonical domain name. |
| **`MX`** | Mail Exchange Record | Specifies incoming mail server hostnames for email delivery. |
| **`NS`** | Name Server Record | Delegates a DNS zone to use specific authoritative name servers. |
| **`TXT`** | Text Record | Arbitrary human/machine readable text (Used for SPF, DKIM verification). |
