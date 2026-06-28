# 🧵 Thread-Level Concurrency

Thread-level concurrency is a **shared-memory** model. Threads run within the same process context, sharing the heap, global variables, and file descriptors, but maintaining individual registers and execution stacks.

---

### 🗺️ Redirection Directory

*   📄 [**`standard-threads-api.md`**](./standard-threads-api.md) — Portable thread management via C11 standard threads (`threads.h`).
*   📄 [**`posix-pthreads.md`**](./posix-pthreads.md) — Raw POSIX thread allocation, lifecycles, and configuration.
*   📄 [**`thread-safety.md`**](./thread-safety.md) — Synchronization strategies: Mutexes, semaphores, condvars, and barriers.
