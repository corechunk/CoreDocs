# 🔒 Android System Properties & Security Hardening

Executing code natively on Android requires interacting with system properties while complying with strict SELinux sandbox constraints and hardware memory protections.

---

### 1. Android System Properties

Android uses a system-wide parameter database instead of standard environment variables for configuration. Native C applications read these key-value pairs using Bionic's system property APIs:

```c
#include <stdio.h>
#include <sys/system_properties.h>

int main() {
    char sdk_ver[PROP_VALUE_MAX];
    
    // Read Android OS API Level system property
    if (__system_property_get("ro.build.version.sdk", sdk_ver) > 0) {
        printf("Android API Version: %s\n", sdk_ver);
    }
    return 0;
}
```

---

### 2. Execution Constraints & Hardening

Android enforces several security parameters to protect user data from buffer overflow exploits and execution hijacking:

1.  **SELinux (Security-Enhanced Linux)**:
    *   Operating system access controls. Even if a native binary runs as root (`su`), SELinux contexts (e.g. `u:r:untrusted_app:s0`) restrict system calls, blocking unauthorized file writes, network sockets, or loading unapproved dynamic libraries.
2.  **ASLR (Address Space Layout Randomization)**:
    *   Randomizes the memory offsets of the stack, heap, and loaded libraries. Native binaries must be compiled with Position-Independent Executable (`-fPIE -pie`) flags, ensuring the dynamic linker can relocate code sections safely at runtime.
3.  **CFI (Control Flow Integrity)**:
    *   Compilers instrument indirect function calls (pointers) with checks to ensure the destination address matches a valid function entry point, preventing attackers from hijacking execution flow to execute shellcode.
