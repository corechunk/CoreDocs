# 🧠 The Kernel: Ring 0 Core Engine

The kernel is the core program of an operating system, executing with maximum privilege inside the hardware **Ring 0 / Supervisor Mode** ring. It controls hardware resources and implements memory, task, and I/O abstractions.

---

### 🧠 Core Subsystems of a Monolithic Kernel

A standard monolithic Unix-like kernel (such as Linux or xv6) structures its supervisor execution into five core subsystems:

```text
               +--------------------------------------+
               |             System Calls             |
               +--------------------------------------+
                /                 |                  \
  [ Memory Manager ]      [ Task Scheduler ]     [ Virtual Filesystem ]
        |                         |                         |
  [ Paging / MMU ]        [ Context Switch ]     [ Device Drivers ]
```

1.  **Memory Management**: Allocates physical RAM blocks and maps virtual memory pages to isolate process spaces.
2.  **Interrupt Handling**: Intercepts CPU hardware interrupts (keyboards, timers) and forwards them to registered system routines.
3.  **Process Scheduler**: Coordinates context switching, saving registers, and swapping task threads.
4.  **System Calls**: Implements the trap gate interface allowing sandboxed applications to request kernel services safely.
5.  **Device Input/Output & VFS**: Abstraction layers managing character/block drivers and file systems via a unified virtual interface.

---

### 🗺️ Redirection Directory

*   📂 [**`01-Memory-Management/`**](./01-Memory-Management/README.md) — Allocating physical memory, paging directory directories, and page fault replacement algorithms.
*   📂 [**`02-Interrupts-and-Traps/`**](./02-Interrupts-and-Traps/README.md) — Interrupt Descriptor Table (IDT) configuration and Interrupt Service Routine (ISR) assembly gates.
*   📂 [**`03-Process-and-Scheduling/`**](./03-Process-and-Scheduling/README.md) — Spawning threads, task state structures, context switching, and scheduling algorithms.
*   📂 [**`04-System-Calls/`**](./04-System-Calls/README.md) — Transitioning CPU privilege rings and passing arguments in CPU registers.
*   📂 [**`05-Drivers-and-VFS/`**](./05-Drivers-and-VFS/README.md) — Device drivers (UART, keyboard), direct memory access (DMA), and the Virtual Filesystem (VFS) layout.
