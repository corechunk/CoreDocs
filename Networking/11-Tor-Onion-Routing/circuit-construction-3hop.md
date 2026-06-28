# 🔀 Tor 3-Hop Circuit Construction & Layered Encryption

This manual details the cryptographic mechanics of the Tor (The Onion Router) anonymity network.

---

## 1. Multi-Layer Encryption ("Onion Layers")

The client client-side software wraps network payload packets in three distinct layers of symmetric encryption—one key for each relay node in the circuit.

```text
[ Client ] ──[ Key1 | Key2 | Key3 | Payload ]──> [ Guard Node ] (Strips Key1)
                                                       │
                                                       ▼
                                                 [ Middle Node ] (Strips Key2)
                                                       │
                                                       ▼
                                                 [ Exit Node ] (Strips Key3 -> Sends Raw Payload to Destination)
```

---

## 2. The 3-Hop Relay Circuit Isolation

1. **Guard Node:** Sees client's real IP address, but cannot read payload or destination IP.
2. **Middle Node:** Sees only Guard and Exit node IP addresses. Knows neither real client nor final target.
3. **Exit Node:** Sees final destination IP and unencrypted payload, but has zero knowledge of the client's real IP address.
