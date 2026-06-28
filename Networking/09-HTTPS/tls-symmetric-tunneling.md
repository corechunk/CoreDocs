# ⚡ TLS Symmetric Tunneling Ciphers (AES-GCM & ChaCha20)

This manual details high-speed symmetric encryption ciphers used for bulk data transmission inside established TLS tunnels.

---

## 1. Why Symmetric Ciphers are Used for Data

Asymmetric RSA/ECDHE calculations are computationally expensive. Once the TLS handshake negotiates a shared master key, traffic switches to hardware-accelerated **Symmetric Encryption** (where identical keys encrypt and decrypt data).

---

## 2. Modern Authenticated Encryption (AEAD)

Modern TLS 1.3 exclusively permits **Authenticated Encryption with Associated Data (AEAD)** ciphers:
- **AES-256-GCM:** Hardware-accelerated on modern x86/ARM CPUs via dedicated AES-NI instructions.
- **ChaCha20-Poly1305:** High-speed software cipher optimized for mobile devices without hardware AES acceleration.
