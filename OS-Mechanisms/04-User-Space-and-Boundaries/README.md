# 🏢 User Space & OS Boundaries

User Space represents the isolated execution zone (Ring 3) where applications, libraries, and shells run. It is bounded by the POSIX standards and kernel system call interfaces.

---

### 🧠 The User Space / Kernel Separation

To run code, user space applications rely on standard runtime libraries (like `glibc` on Linux, `Bionic` on Android, or the MSVCRT on Windows) to format arguments, setup system stacks, and invoke system calls.

---

### 🗺️ Redirection Directory

*   📄 [**`the-boundary-debate.md`**](./the-boundary-debate.md) — What is truly part of an "OS"? A comparison of the POSIX standard view vs. modern user space bundlings (like pre-packaged editors).
*   📄 [**`xv6-kernel-case-study.md`**](./xv6-kernel-case-study.md) — Case study: How to read, navigate, and compile the 10,000-line MIT xv6 UNIX kernel.
