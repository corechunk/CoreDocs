# 🛡️ Unified Hardware Privilege Modes Comparison

## 1. Hardware Security Boundaries
Hardware privilege levels isolate unprivileged user applications from sensitive OS kernel memory and device registers.

## 2. Cross-Architecture Privilege Mapping Matrix

| Architecture | User/Unprivileged Mode | Kernel/Supervisor Mode | Hypervisor Mode | Secure/TrustZone Mode |
|---|---|---|---|---|
| **x86_64** | Ring 3 | Ring 0 | Ring -1 (VT-x) | S-SMM |
| **ARM64** | EL0 (Application) | EL1 (OS Kernel) | EL2 (Hypervisor) | EL3 (Secure Monitor) |
| **RISC-V** | U-Mode (User) | S-Mode (Supervisor) | H-Mode (Hypervisor) | M-Mode (Machine) |
