# 🚀 Freestanding C Execution & Bootstrapping

In systems engineering, the first step of building an operating system is configuring the **Freestanding Environment**. This environment runs code directly on the CPU silicon without standard runtime wrappers.

---

### 🧠 The Freestanding C Constraint

Standard C code runs in a **hosted environment**, meaning a dynamic loader (`ld.so`) maps the binary, links standard runtime libraries (`libc.so`), and sets up memory descriptors before jumping to `main()`.

In a **freestanding environment**:
1.  **No `main()` entry point**: The entry point is defined manually by assembly files and linkers (commonly named `_start` or `kernel_main`).
2.  **No standard libraries**: Headers like `<stdio.h>`, `<stdlib.h>`, and `<string.h>` do not exist. Any utilities (like string copies or character writing) must be coded by hand.
3.  **No memory allocator**: Calling `malloc()` fails. You must configure physical memory directories and compile custom allocator systems manually.

---

### 🗺️ Redirection Directory

*   📄 [**`assembly-prerequisites.md`**](./assembly-prerequisites.md) — The assembly bootstrap: CPU modes (Real to Long Mode), setting up stack pointers, and jumping to C `kernel_main()`.
