# 💾 Hardware Memory & Atomics

Physical parallelism is bounded by memory physics. When multiple CPU cores execute instructions simultaneously, coordination must be handled at the silicon and memory bus level.

---

### 🗺️ Redirection Directory

*   📄 [**`cache-coherency-false-sharing.md`**](./cache-coherency-false-sharing.md) — CPU cache architectures, MESI protocol, and false sharing limits.
*   📄 [**`memory-barriers-ordering.md`**](./memory-barriers-ordering.md) — Out-of-order execution, instruction pipeline hazards, and memory barriers.
*   📄 [**`atomic-operations-lock-free.md`**](./atomic-operations-lock-free.md) — Hardware bus atomic locks, Compare-and-Swap (CAS), and lock-free structures.
