# 📦 Process-Level Concurrency

Process-level concurrency is governed by a **shared-nothing** execution model. Each process runs inside its own isolated address space enforced by hardware MMU translation tables, eliminating shared state memory hazards.

---

### 🗺️ Redirection Directory

*   📄 [**`fork-and-exec.md`**](./fork-and-exec.md) — Address space replication via Copy-on-Write (`COW`) and execution transitions using `execve`.
*   📄 [**`process-traps.md`**](./process-traps.md) — Handling process state changes: Zombie reaping, child state monitoring (`waitpid`), and OS signal handlers.
