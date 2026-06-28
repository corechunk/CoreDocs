# 🕸️ Overlay Mesh Networks & STUN Hole-Punching

This manual details virtual private overlay networks (Tailscale, WireGuard) and NAT traversal protocols.

---

## 1. STUN NAT Hole-Punching (UDP)

Devices behind restrictive firewalls/NATs use Session Traversal Utilities for NAT (STUN) servers to discover their public reflective IP:Port mappings, exchanging UDP packets simultaneously to "punch" open direct peer-to-peer firewall pinholes.

---

## 2. DERP Relay Fallbacks

If strict Symmetric NATs block direct P2P socket establishment, traffic automatically falls back to encrypted relay servers (Designated Encrypted Relay Protocol / DERP), guaranteeing reliable connectivity.
