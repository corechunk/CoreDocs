# 🚪 System Calls & Privilege Gates

A System Call is the gate allowing sandboxed userspace applications (Ring 3) to request services (like reading files or allocating memory) from the privileged kernel (Ring 0) safely.

---

### 🧠 The System Call Gate

Applications cannot jump directly to kernel memory addresses. Doing so triggers a CPU protection fault. Instead, applications must execute a specific instruction that transitions the CPU to Ring 0 and jumps to a predefined kernel entry address (the **Syscall Handler**):

*   **`int 0x80`**: Legacy x86 software interrupt gate.
*   **`sysenter` / `sysexit`**: Optimized x86 fast system call instructions.
*   **`syscall` / `sysret`**: Modern x86_64 fast system call instructions.
*   **`ecall` / `swi`**: RISC-V and ARM software trap call instructions.

---

### 🗺️ Redirection Directory

*   📄 [**`syscall-register-convention.md`**](./syscall-register-convention.md) — Passing system call parameters inside hardware registers and routing requests using a dispatch table.
