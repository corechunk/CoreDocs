# ⚙️ OS Mechanisms: The Architecture of Operating Systems

An Operating System is a tiered software stack coordinating hardware execution. This hub acts as a step-by-step roadmap to guide you from bare-metal boots to operating system architecture.

---

### 🧠 The Three-Layer Stack

```text
+-----------------------------------------------------------------+
| Layer 3: User Space (Applications)                              |
|   [ Shell / Bash ]      [ Coreutils: ls, cat ]   [ Browser ]    |
+-----------------------------------------------------------------+
| Layer 2: System Services (Privileged Userspace)                 |
|   [ Init: systemd ]     [ Linker: ld.so ]        [ udev Daemon ]|
+-----------------------------------------------------------------+
| Layer 1: The Kernel (Ring 0 / Supervisor Mode)                  |
|   [ Scheduler ]         [ Virtual Memory ]       [ GPU Driver ] |
+-----------------------------------------------------------------+
```

1. **Layer 1: The Kernel (Ring 0)**:
   * The core engine. Intercepts hardware interrupts, controls the MMU page directories, maps execution threads to CPU cores, and communicates with hardware registers.
2. **Layer 2: System Services (Privileged Userspace)**:
   * Programs that execute outside Ring 0 but are mandatory to boot and run the OS (e.g., the dynamic linker `ld.so` that loads binaries, the init system `systemd` that spawns processes, and device managers).
3. **Layer 3: User Space (Applications & Libraries)**:
   * The standard execution zone. Standard C libraries (`glibc`/`Bionic`), terminal shells, and user programs running in sandboxed execution rings.

---

### 🧠 The Freestanding Environment: Zero Userspace Libraries

When writing a kernel, **you do not have access to standard libraries**. 
Header files like `<stdio.h>`, `<stdlib.h>`, or `<string.h>` do not exist because there is no operating system or C runtime loaded to back them up. There is no `printf()` or `malloc()`. 

To print characters, you must write directly to hardware memory addresses (like the VGA framebuffer). To allocate memory, you must build your own Physical Memory Manager from scratch.

---

### 🚦 The Kernel-to-Userspace Handover: Spawning PID 1

At the end of kernel initialization, the kernel exits Ring 0 supervisor mode to spawn the first userspace process: **PID 1 (Init)**. 

The kernel manually constructs a userspace stack, pushes the return instruction pointer pointing to the init binary path, sets the CPU flag register to Ring 3 (User mode), and executes an instruction (like `iret` or `sysret`) to perform the privilege drop. From this point, the kernel only runs in response to hardware interrupts or application system calls.

---

### 🔀 UNIX File Descriptors vs. Windows Handles & Registry

Unlike UNIX-based operating systems where "everything is a file" (represented by integer file descriptors), Windows NT operates on **Handles** and objects:
*   **Object Manager**: Windows NT uses a centralized kernel object manager to track processes, threads, files, and events. Applications access these objects via virtual **Handles** rather than filesystem descriptors.
*   **The Registry**: Windows rejects plain-text configuration files (`/etc/`). Instead, it uses a hierarchical, binary database called the **Registry** to store configuration keys, drivers, and user permissions directly in kernel memory structures.

---

### 🍎 macOS XNU & Hybrid Messaging

macOS utilizes the **XNU kernel** (X is Not Unix), a hybrid architecture combining:
*   **Mach Microkernel**: Handles low-level scheduling, thread management, and Inter-Process Communication (IPC) via **Mach Ports** (message queues).
*   **BSD Layer**: Wraps Mach's primitives to provide POSIX-compliant process structures, security permissions, and sockets.

---

### 🗺️ Redirection Directory

*   📂 [**`01-Freestanding-Environment-and-Boot/`**](./01-Freestanding-Environment-and-Boot/README.md) — The limits of freestanding C code, bootloaders (Multiboot), and the assembly-to-C handover.
*   📂 [**`02-The-Kernel/`**](./02-The-Kernel/README.md) — The supervisor Ring 0 engine: Virtual memory directories, IDTs, CPU scheduling loops, and device drivers.
*   📂 [**`03-System-Services/`**](./03-System-Services/README.md) — Spawning PID 1, Init implementations (SysV, systemd), Windows handles/Registry internals, and macOS XNU Mach ports.
*   📂 [**`04-User-Space-and-Boundaries/`**](./04-User-Space-and-Boundaries/README.md) — The application boundaries, POSIX standards, and the navigation guide for the xv6 code.
