# 🔴 Standard: Linking & Delivery [SYSTEMS]

## Definition
Linking is the final stage of the build process where the Linker connects function calls (like `printf`) to their actual machine code implementations. 

## 1. Legacy Way (Static Linking)
The implementation code is physically copied into your final `.exe`. The binary is large and standalone.

```bash
# Static Linking (Task: Bundle everything)
gcc -static main.o -o app_static

# Size Check
ls -lh app_static // Output: (Large file size, e.g., 800KB+)
```

## 2. Modern Way (Dynamic Linking)
The binary only contains a "Shortcut" to a shared library (`.so` or `.dll`). The code is loaded from the OS at runtime.

```bash
# Dynamic Linking (Default Modern Path)
gcc main.o -o app_dynamic

# Size Check
ls -lh app_dynamic # Output: (Small file size, e.g., 16KB)
```

# The Logic Bridge
// Logic: Static linking makes your app more portable but consumes more RAM. Dynamic linking allows multiple running programs to share a single copy of `libc` in physical memory, drastically reducing system resources.
