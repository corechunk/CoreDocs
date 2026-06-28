# 🛠️ Android Native Cross-Compilation

Native compilation is the process of building software on one system (the **Host**, e.g., an x86_64 PC) that will execute on a different system (the **Target**, e.g., an ARM64 Android phone). 

---

### 1. The Target Triplet: Decoded

A target triplet is a string format that tells the compiler the architecture, vendor, and OS of the target device:
`[architecture]-[vendor]-[operating_system]`

Common Android triplets:
*   `aarch64-linux-android`: 64-bit ARM CPUs (most modern smartphones).
*   `arm-linux-androideabi`: 32-bit ARM CPUs (older smartphones).
*   `x86_64-linux-android`: 64-bit Intel/AMD CPUs (used in standard PC Emulators).

---

### 2. Setting Up the Toolchain

The Android NDK (Native Development Kit) contains pre-built compiler executables (Clang/LLVM) configured to link against Android's system headers and libraries (`Bionic libc`).

```text
+-------------------+
|  Source (main.c)  |
+-------------------+
          |
          v
+-------------------+
|  NDK Compiler     | <--- Needs path to target sysroot headers
+-------------------+
          |
          v
+-------------------+
|   Target Binary   | <--- Linked against Android's libc.so (Bionic)
+-------------------+
```

---

### 💻 Walkthrough: Compiling a Simple Binary

#### Step 1: Create a simple test program (`hello.c`)
```c
#include <stdio.h>

int main() {
    printf("Hello from a native Android binary!\n");
    return 0;
}
```

#### Step 2: Write the Compilation Script (`compile.sh`)
```bash
#!/usr/bin/env bash
# Exit immediately if a command exits with a non-zero status
set -euo pipefail

# 1. Define where your NDK is installed on the host PC
NDK_PATH="/opt/android-ndk"
API="33" # Target Android API level (33 corresponds to Android 13)

# 2. Path to NDK toolchain binaries
TOOLCHAIN="$NDK_PATH/toolchains/llvm/prebuilt/linux-x86_64/bin"

# 3. Reference the compiler specific to target ARM64 architecture
CC="$TOOLCHAIN/aarch64-linux-android$API-clang"

# 4. Compile the source file
$CC -O3 -Wall hello.c -o hello_android_arm64

echo "Compilation successful! Output binary is: hello_android_arm64"
```

Save this script, run `chmod +x compile.sh`, and run it. The resulting binary file cannot be run on your PC—it is compiled for ARM64 CPU instruction sets.
