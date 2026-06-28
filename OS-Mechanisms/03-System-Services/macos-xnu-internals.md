# 🍎 macOS XNU Internals & Hybrid Messaging

macOS, iOS, and watchOS run on top of the **XNU kernel** (X is Not Unix), a hybrid kernel combining a microkernel architecture with traditional monolithic BSD UNIX systems code.

---

### 1. Mach Microkernel & Port Messaging

At the lowest level, XNU runs the **Mach Microkernel**.
*   **Mach Ports**: Mach threads communicate by passing messages over unidirectionally queued mailboxes called **Mach Ports**.
*   **IPC Overhead**: Because all coordination (e.g. allocating page descriptors or scheduling threads) uses message passing, Mach has higher IPC context-switching overhead compared to monolithic kernels.

---

### 2. The BSD Layer Integration

To achieve POSIX compliance and resolve Mach's IPC overhead, XNU wraps the Mach microkernel in a monolithic **BSD Layer**.
*   **Dual API**: Applications can make raw Mach system calls (for IPC and thread management) or traditional BSD system calls (`fork`, `execve`, `socket`) which the BSD layer implements directly in kernel space without message-passing overhead.
*   **I/O Kit**: A C++ object-oriented framework inside XNU used to compile device drivers.

---

### 3. Launchd (PID 1)

Like Linux's systemd, macOS utilizes **launchd** as its PID 1 init system. Configured via XML property list files (`.plist`), it manages boot service lifecycles, socket activation, and background system agent spawning.
