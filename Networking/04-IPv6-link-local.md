# 🌍 IPv6 Link-Local Addressing & SLAAC

This guide details IPv6 architecture, 128-bit address representations, link-local addresses, and Stateless Address Autoconfiguration (SLAAC).

---

## 1. 128-Bit Hexadecimal Address Structure

IPv6 expands global address space to $2^{128}$ addresses, written as eight groups of four hexadecimal digits separated by colons (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`).
- **Compression Rules:** Leading zeroes in a group can be omitted (`:0000:` -> `:0:`). A double colon (`::`) replaces consecutive groups of zeroes once per address.

---

## 2. Link-Local Automatic Addressing (`fe80::/10`)

IPv6 interface hardware generates an automatic **Link-Local** address immediately upon powering on, pre-fixed with `fe80::`. Link-local addresses are restricted to local network segments and are never routed across internet routers.

---

## 3. Stateless Address Autoconfiguration (SLAAC)

SLAAC enables IPv6 hosts to automatically configure their global unicast addresses without needing a centralized DHCP server. The host sends a Router Solicitation request, receives a Router Advertisement containing the network prefix, and appends its local interface identifier to form a valid global IP.
