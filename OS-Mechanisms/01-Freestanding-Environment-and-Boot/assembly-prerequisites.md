# 🚦 Assembly Boot Prerequisites

An operating system kernel cannot boot directly in C. The hardware initializes in a raw CPU state that must be configured using assembly before C execution can begin.

---

### 🧠 Why Assembly is Mandatory Before C

The C compilation model depends on specific hardware structures that must be configured manually via CPU assembly instructions:

1.  **The Stack Pointer**: C uses stack frames to pass parameters, allocate local variables, and track return addresses. If the Stack Pointer register (`ESP` / `RSP` in x86, or `SP` in ARM) is not initialized to a valid RAM address, pushing parameters causes an instant hardware crash (Triple Fault).
2.  **Zeroing the BSS Section**: C mandates that all uninitialized global/static variables default to `0`. The linker places these in the `.bss` memory section. The assembly bootstrap must loop through this section and zero the memory addresses manually.
3.  **Configuring CPU Registers**: The CPU must be transitioned to the appropriate operating mode. For example, x86 CPUs boot in 16-bit **Real Mode**; assembly must load a Global Descriptor Table (GDT) and enable control registers to transition the CPU to 32-bit **Protected Mode** or 64-bit **Long Mode**.

*Note: For the detailed assembly syntax, register directories, and compiler assemblers (NASM/gas) to perform these transitions, refer to the [Processor Architecture Hub](../../Systems-Engineering/Processor-Architecture/README.md).*
