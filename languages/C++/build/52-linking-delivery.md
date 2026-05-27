# 🔴 Standard: Linking & Delivery [SYSTEMS]

## Definition
Connecting code to libraries. Static linking embeds the code; Dynamic linking loads it at runtime.

## 1. Legacy Way (Static)
Standalone binary.

```bash
# Link statically
g++ main.o -static -o app_static

# Size check
ls -lh app_static // Output: (Large binary)
```

## 2. Modern Way (Dynamic)
Shared libraries.

```bash
# Link dynamically (default)
g++ main.o -o app_shared

# Size check
ls -lh app_shared # Output: (Small binary)
```

# The Logic Bridge
// Logic: Dynamic linking allows the OS to share a single copy of a library in RAM across multiple processes. It also allows library updates (e.g., security patches) without recompiling the application.
