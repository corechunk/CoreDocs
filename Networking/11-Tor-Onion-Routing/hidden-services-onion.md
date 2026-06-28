# 🕵️ Tor Hidden Services (.onion Architecture)

This manual details Tor Hidden Services (`.onion` domain addresses) enabling servers to host websites without exposing their physical IP addresses.

---

## 1. Introduction Points & Descriptor Upload

A hidden service picks random Tor relays as **Introduction Points** and uploads an encrypted service descriptor (containing its public key and intro points) to the Tor Distributed Hash Table (DHT).

---

## 2. Rendezvous Point Connections

When a client connects to a `.onion` domain, it picks a separate **Rendezvous Point** relay. Both client and hidden service build independent 3-hop circuits to the Rendezvous Point, stitching together an 6-hop encrypted tunnel where neither party learns the other's real IP address.
