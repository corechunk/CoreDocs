# 🔄 Endianness Byte Conversions (Host vs. Network Byte Order)

This guide details byte ordering architectures and POSIX endianness conversion functions.

---

## 1. Host vs. Network Byte Order

- **Little-Endian (Host Byte Order - x86/ARM):** Stores least-significant bytes at lower memory addresses.
- **Big-Endian (Network Byte Order):** Stores most-significant bytes at lower memory addresses. Standardized as the universal binary transmission format across all internet routers.

---

## 2. POSIX Conversion Function Reference

When populating socket address structs (`sockaddr_in`), multi-byte integers (like ports and IPs) must be converted using POSIX macros:

| Conversion Function | Direction | Target Data Type |
|---|---|---|
| `htons(uint16_t val)` | Host to Network Short | 16-bit Port Numbers |
| `htonl(uint32_t val)` | Host to Network Long | 32-bit IPv4 Addresses |
| `ntohs(uint16_t val)` | Network to Host Short | 16-bit Port Numbers |
| `ntohl(uint32_t val)` | Network to Host Long | 32-bit IPv4 Addresses |
