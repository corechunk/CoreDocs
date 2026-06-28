# 🔑 TLS Asymmetric Handshake & X.509 Certificates

This manual details asymmetric public/private key cryptography, key exchanges, and digital certificate validation.

---

## 1. Asymmetric Key Exchange Mechanics (ECDHE)

During a TLS handshake, client and server negotiate a shared secret over an insecure channel without transmitting the secret itself, using **Elliptic Curve Diffie-Hellman Ephemeral (ECDHE)** key exchange.

---

## 2. Digital Certificates (X.509) & Trust Chains

To prevent Man-in-the-Middle (MITM) attacks, servers present an X.509 digital certificate signed by a trusted Certificate Authority (CA). The client verifies the signature chain up to local root certificates pre-installed in the OS store.
