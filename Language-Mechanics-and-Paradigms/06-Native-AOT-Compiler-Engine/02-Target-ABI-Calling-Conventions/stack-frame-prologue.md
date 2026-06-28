# ⚙️ Function Prologues, Epilogues, and 16-Byte Stack Alignment

## 1. Function Prologues & Epilogues
AOT compilers generate machine assembly wrappers around function bodies:
- **Prologue:** `push rbp; mov rbp, rsp; sub rsp, N` (saves old base pointer and allocates local stack frame space).
- **Epilogue:** `mov rsp, rbp; pop rbp; ret` (restores stack frame and returns control).

## 2. 16-Byte Stack Alignment Requirement
Before invoking external standard library function calls (like `printf` or `malloc`), the AMD64 ABI strictly requires the Stack Pointer (`rsp`) to be aligned to a 16-byte boundary to support SSE SIMD vector hardware instructions.
