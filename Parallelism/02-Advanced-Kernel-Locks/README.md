# 🔒 Advanced Kernel Synchronization Internals

Synchronization abstractions like mutexes choose dynamically between running active hardware execution locks (userspace spinning) or requesting OS scheduler suspensions (kernel-space sleeping).

---

### 🗺️ Redirection Directory

*   📄 [**`spinlocks-and-barriers.md`**](./spinlocks-and-barriers.md) — Spinning locks vs. sleeping locks, and hardware CPU execution barriers.
*   📄 [**`futex-kernel-internals.md`**](./futex-kernel-internals.md) — Fast Userspace Mutex (`futex`) syscall mechanics.
