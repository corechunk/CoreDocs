# 📚 Libc Implementations: glibc vs musl

The C Standard Library (libc) is the fundamental interface between user-space applications and the Linux Kernel.

## 1. glibc (GNU C Library)
- **Standard**: The default on most desktop and server distros (Arch, Debian, Fedora).
- **Features**: Highly optimized, feature-rich, supports a wide range of extensions.
- **Binary Size**: Large. Statically linking glibc can lead to massive binaries.

## 2. musl libc
- **Standard**: The default on lightweight distros (Alpine Linux) and Docker containers.
- **Philosophy**: Minimalism, strict POSIX compliance, and security.
- **Binary Size**: Extremely small. Ideal for static linking in embedded systems.

## 3. Impact on Portability
Scripts and binaries compiled against glibc may not run on musl-based systems without recompilation or compatibility layers.
