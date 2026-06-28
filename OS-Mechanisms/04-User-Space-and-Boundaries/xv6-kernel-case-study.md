# 📖 Case Study: Navigating MIT's xv6 Unix Kernel

**xv6** is a modern re-implementation of Dennis Ritchie's Version 6 Unix (V6) in ANSI C for multi-core x86 and RISC-V architectures. It serves as the standard instructional codebase for MIT and other top systems engineering universities.

---

### 🧠 Why study xv6?

*   **Size**: The entire kernel fits in roughly **10,000 lines of code**, making it completely readable by a student in a single semester.
*   **Completeness**: It compiles and runs a complete, multi-tasking Unix-like OS, featuring a working shell, file directory structure, and virtual memory page directories.
*   **Purity**: It is a freestanding implementation with no external library dependencies.

---

### 🗺️ File Navigation Map

When reading the xv6 codebase, start in this order:

1.  **Assembly Bootstrap (`entry.S`)**:
    *   The CPU startup bootstrap. Sets up a temporary 4MB page mapping and jumps to the C main function.
2.  **Kernel Entry (`main.c`)**:
    *   Initializes physical memory allocations, interrupt tables, page directories, and starts the CPU scheduler loop.
3.  **Process Contexts (`proc.h`, `proc.c`, `swtch.S`)**:
    *   Defines `struct proc` (the Thread Control Block), process table structures, and the raw assembly registers swap function `swtch`.
4.  **Interrupt Handling (`trap.c`, `vectors.pl`)**:
    *   Configures IDT gate entries and dispatches hardware interrupts (timers, disk) and system call exception traps.
5.  **Virtual Memory (`vm.c`)**:
    *   Allocates page directories, maps page tables for kernel and user spaces, and manages copy-on-write mappings.
6.  **System Calls (`syscall.c`, `sysproc.c`, `sysfile.c`)**:
    *   Implements the syscall table and decodes userspace parameters from registers.
7.  **Filesystem (`fs.c`, `file.c`, `bio.c`)**:
    *   Implements disk block allocation, inode mappings, VFS file tables, and read/write operations.

---

### 🛠️ Compiling and Running xv6

xv6 is compiled using standard GCC toolchains and executed within QEMU emulators:

```bash
# 1. Clone the official MIT RISC-V repository
git clone https://github.com/mit-pdos/xv6-riscv.git
cd xv6-riscv

# 2. Compile and launch the kernel in QEMU emulator (headless mode)
make qemu-nox
```
This boots the kernel directly, mounts the virtual disk, spawns PID 1 (`init.c`), and launches the userspace shell (`sh.c`), allowing you to type standard Unix commands like `ls`, `cat`, and `echo` directly into your custom compiled OS.
