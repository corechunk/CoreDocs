# 🛡️ ARM64 Exception Levels (EL0 to EL3)

## 1. Exception Level Hierarchy
ARM64 replaces legacy rings with 4 discrete Exception Levels:
- **EL0 (Application):** Unprivileged user application execution.
- **EL1 (OS Kernel):** Privileged operating system kernel execution.
- **EL2 (Hypervisor):** Type-1 Hypervisor execution (KVM, Xen).
- **EL3 (Secure Monitor):** Firmware and ARM TrustZone switching.

## 2. Execution State Switching
Execution can switch between 64-bit (AArch64) and legacy 32-bit (AArch32) states upon Exception Level transitions.
