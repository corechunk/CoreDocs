# 🔀 IPC & Pipes: Global Entry Point

Inter-Process Communication (IPC) is the set of operating system mechanisms allowing separate executing processes—each running within its own isolated address space—to exchange data, synchronize progress, and share state.

---

### 🧠 The Core Problem: Process Isolation vs. Communication

Modern operating systems use Virtual Memory to isolate processes. The hardware Memory Management Unit (MMU) translates a process's virtual addresses to physical pages. A process cannot access the physical memory of another process. IPC mechanisms bypass this isolation in a controlled manner via the operating system kernel.

```text
+-------------------+                      +-------------------+
|   Process A       |                      |   Process B       |
| (Virtual Address) |                      | (Virtual Address) |
+-------------------+                      +-------------------+
          |                                          |
    [MMU Map A]                                 [MMU Map B]
          |                                          |
          v                                          v
+-------------------+      Kernel Buffer     +-------------------+
|  Physical Page A  | === [ IPC Channel ] ===|  Physical Page B  |
+-------------------+                        +-------------------+
```

---

### 🖥️ IPC Mechanism Classification

| Mechanism | Speed | Data Format | Scope | Synchronization |
| :--- | :--- | :--- | :--- | :--- |
| **Anonymous Pipes** | Fast (RAM buffers) | Unstructured stream | Parent-Child | Blocking read/write |
| **Named Pipes / FIFOs** | Fast (RAM buffers) | Stream or Messages | Local cross-process | Blocking read/write |
| **Message Queues** | Medium (Kernel queue) | Structured messages | Local cross-process | OS queue bounds |
| **UNIX Domain Sockets** | Fast (Kernel bypass) | Stream / Datagrams | Local cross-process | Socket semantics |
| **Shared Memory** | Fastest (Zero-copy RAM) | Raw shared bytes | Local cross-process | Requires manual lock (Mutex) |

---

### 🗺️ Navigation Directory

*   📂 [**`anonymous-pipes/`**](./anonymous-pipes/README.md) — Unidirectional transient stream channels. Covers kernel buffer physics and parent-child file descriptor/handle inheritance (UNIX & Windows).
*   📂 [**`named-pipes-fifos/`**](./named-pipes-fifos/README.md) — File-system linked named channels. Covers block-on-open semantics, duplex routing, and message-oriented communication.
*   📄 [**`message-queues.md`**](./message-queues.md) — POSIX structured message systems with priorities.
*   📄 [**`unix-domain-sockets.md`**](./unix-domain-sockets.md) — High-performance local sockets (AF_UNIX) bypassing network stack overhead.
*   📄 [**`shared-memory-ipc.md`**](./shared-memory-ipc.md) — Zero-copy memory mapped regions (POSIX shared memory vs. Win32 Page File mapping).
*   📄 [**`process-shared-mutexes.md`**](./process-shared-mutexes.md) — Synchronizing shared memory using process-shared mutexes in RAM maps and Windows Event/Mutex objects.
