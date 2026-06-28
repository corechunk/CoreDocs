# 🖥️ Runtime Instruction Byte Encoding (x86_64 / ARM)

## 1. Dynamic Machine Code Emission
JIT assemblers construct native binary instruction bytes directly inside RAM arrays. (e.g., emitting `0x48, 0x89, 0xD8` for x86_64 `mov rax, rbx`).

## 2. Instruction Encoding Complexity
- **x86_64:** Variable-length instructions (1 to 15 bytes) utilizing REX prefixes, ModR/M, and SIB bytes.
- **ARM64 (AArch64):** Fixed 32-bit (4-byte) aligned instruction encodings.
