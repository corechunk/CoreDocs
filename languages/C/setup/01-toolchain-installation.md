# 🟢 Standard: Toolchain Installation [CORE]

## Definition
The environment setup required to transform source code into machine-executable binary. This includes the Compiler (GCC), the Linker, and the Build System (Make). We use `mise` to lock versions for stability.

## 1. Legacy Way (System-Wide Path)
Installing the toolchain globally using the OS default package manager.

```bash
# ARCH LINUX: Includes GCC, G++ (for C++), GDB, Make
sudo pacman -S base-devel

# DEBIAN/UBUNTU: Includes GCC, libc-dev, Make
sudo apt update && sudo apt install build-essential

# Verify
gcc --version // Output: gcc (GCC) 13.x.x
```

## 2. Modern Way (Project-Local Path)
Using a version manager (like `mise`) to lock specific toolchain versions per project to prevent "Silent Breaking."

```bash
# Lock GCC version for the current directory
mise use gcc@13.2.0

# Set environment variable
export CC=gcc

# Verify
gcc --version # Output: gcc (GCC) 13.2.0
```

# The Logic Bridge
// Logic: Global installations are convenient but risky; project-local versions ensure that your code compiles the same way today as it will in 5 years, regardless of OS updates.
