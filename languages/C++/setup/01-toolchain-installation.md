# 🟢 Standard: Toolchain Installation [CORE]

## Definition
The environment required to compile and link C++ code. On Linux, this is typically the GNU Compiler Collection (`g++`) or LLVM/Clang (`clang++`).

## 1. Legacy Way (System-Wide)
Standard global installation via system package manager.

```bash
# Arch Linux
sudo pacman -S base-devel

# Debian/Ubuntu
sudo apt update && sudo apt install build-essential

# Verify
g++ --version // Output: g++ (GCC) 13.x.x
```

## 2. Modern Way (Mise / Version Locked)
Using `mise` to ensure a consistent compiler version across all machines.

```bash
# Lock version for the project
mise use gcc@13.2.0

# Verify
g++ --version # Output: g++ (GCC) 13.2.0
```

# The Logic Bridge
// Logic: A C++ compiler is a sophisticated state machine that translates C++ source into Assembler, which is then turned into binary object files for the Linker.
