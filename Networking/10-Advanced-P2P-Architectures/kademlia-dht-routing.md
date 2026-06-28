# 🔀 Kademlia Distributed Hash Tables (DHT)

This manual details decentralized Distributed Hash Tables using the Kademlia algorithm.

---

## 1. Decentralized Node Identification

Every node and file resource is assigned a 160-bit ID in a shared cryptographic keyspace.

---

## 2. XOR Distance Metric Routing

Kademlia measures network "distance" between two node IDs ($A$ and $B$) using a bitwise Exclusive-OR operation:

$$\text{distance}(A, B) = A \oplus B$$

Nodes maintain $k$-buckets of contact pointers for nodes at varying powers-of-two distances, enabling lookups to resolve across millions of decentralized peers in $O(\log N)$ network hops.
