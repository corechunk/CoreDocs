# 🌐 Cross-Compilation Architecture & Target Triplets

## 1. Cross-Compilation Theory
Cross-compilation is the act of building executable binaries on one development machine (the Host) designed to run natively on a completely different CPU architecture or operating system (the Target).

## 2. Anatomy of Target Triplets (`Arch-Vendor-OS-ABI`)
Compilers use standardized target triplets to determine exact instruction set encoding and system call interfaces:
- `x86_64-linux-gnu`: 64-bit x86 desktop targeting standard GNU C library.
- `aarch64-linux-android`: 64-bit ARM mobile targeting Android Bionic C library.
- `riscv64-unknown-elf`: 64-bit RISC-V bare-metal target without OS kernel abstractions.

## 3. Sysroots and Toolchain Probing
- **Sysroots (`--sysroot`):** Instructs compilers to isolate headers (`/usr/include`) and pre-built dynamic libraries (`/usr/lib`) belonging to the target device rather than host paths.
- **Fail-Fast Detection:** Robust systems build environments probe host and target toolchains before compilation, preventing cryptically delayed dynamic linking failures.
