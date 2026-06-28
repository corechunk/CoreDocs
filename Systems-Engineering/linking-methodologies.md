# 🔗 Linking Methodologies: Static vs. Dynamic Compilation

## 1. Dynamic Linking (`.so`, `.dll`, `.dylib`)
- **Mechanism:** The compiler embeds external library symbol references inside the binary. The OS dynamic linker (`ld.so`) resolves and maps library code into dynamic memory at runtime.
- **Trade-offs:** Minimizes executable file sizes, enables central OS patch updates, but introduces runtime reliance on host library availability.

## 2. Static Linking (`.a`, `.lib`)
- **Mechanism:** The linker physically copies compiled library machine code routines directly into the final executable binary.
- **Trade-offs:** Produces fully self-contained binaries ideal for embedded boards and Android deployment, but increases binary size.
