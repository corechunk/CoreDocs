# 🏛️ CoreDocs Systems Wiki Implementation Session Summary

This document summarizes the directories, files, and navigation indexes created, updated, and synchronized during this session to implement the CoreDocs systems wiki hubs.

---

## 🗺️ Created Files & Directories Index

### 1. Master Navigation & Index
*   [README.md](../README.md): Appended topics 17 (IPC and Pipes), 18 (Android Deployment), 19 (GUI & Input Architecture), and 20 (OS Mechanisms).

### 2. Concurrency Hub (`Concurrency/`)
Master entry index: [README.md](../Concurrency/README.md)
*   📂 [**`01-Process/`**](../Concurrency/01-Process/README.md) — Isolated execution spaces, copy-on-write (`COW`), and process control lifecycles.
    *   📄 `fork-and-exec.md`: Address space copy, copy-on-write page tables, and image overlays (`execve`).
    *   📄 `process-traps.md`: Zombie process prevention, non-blocking reaping (`waitpid`), and SIGCHLD signal handlers.
*   📂 [**`02-Thread/`**](../Concurrency/02-Thread/README.md) — Shared memory execution, POSIX pthreads, and mutex/barrier synchronization.
    *   📄 `standard-threads-api.md`: Portable C11 threads API (`threads.h`).
    *   📄 `posix-pthreads.md`: Raw POSIX thread allocation, lifecycles, and configuration.
    *   📄 `thread-safety.md`: Mutexes, semaphores, condition variables, and barriers.
*   📂 [**`03-Async/`**](../Concurrency/03-Async/README.md) — Event-driven loops, multiplexing (`epoll`), and kernel queue engines (`io_uring`).
    *   📄 `multiplexing-select-poll.md`: epoll edge-triggered I/O loop in C.
    *   📄 `modern-kernel-io-uring.md`: io_uring ring-buffer architecture (SQ/CQ) and setup code.
*   📂 [**`04-Pitfalls-and-Analysis/`**](../Concurrency/04-Pitfalls-and-Analysis/README.md) — Mathematical safety limits.
    *   📄 `deadlocks-coffman-conditions.md`: Coffman conditions and deadlock prevention via lock ordering.
    *   📄 `livelocks-and-starvation.md`: Livelocks, starvation, and Priority Inheritance Protocol config.

---

### 3. Parallelism Hub (`Parallelism/`)
Master entry index: [README.md](../Parallelism/README.md)
*   📂 [**`01-Hardware-Memory-and-Atomics/`**](../Parallelism/01-Hardware-Memory-and-Atomics/README.md) — CPU cache lines, MESI cache coherency, memory ordering fences, and atomic CAS primitives.
    *   📄 `cache-coherency-false-sharing.md`: MESI cache line states, false sharing detection, and variable alignment checks.
    *   📄 `memory-barriers-ordering.md`: Out-of-order execution pipelines and compiler/hardware fences.
    *   📄 `atomic-operations-lock-free.md`: Compare-and-Swap (CAS) instructions and lock-free structures.
*   📂 [**`02-Advanced-Kernel-Locks/`**](../Parallelism/02-Advanced-Kernel-Locks/README.md) — Silicon coordination primitives.
    *   📄 `spinlocks-and-barriers.md`: Active spinning loops vs. passive sleeping mutexes.
    *   📄 `futex-kernel-internals.md`: Fast Userspace Mutex (Futex) hybrid context-switching system calls.
*   📂 [**`03-Parallel-Hardware-Scaling/`**](../Parallelism/03-Parallel-Hardware-Scaling/README.md) — Hardware vector units, scaling limits, and GPU arrays.
    *   📄 `SIMD-and-vectorization.md`: SSE/AVX vector instructions and loop auto-vectorization.
    *   📄 `hardware-scaling-laws.md`: Mathematical limits of Amdahl's Law vs. Gustafson's Law.
    *   📄 `GPU-computing-acceleration.md`: GPU streaming multiprocessors (SIMT) and CUDA kernel setups.

---

### 4. IPC and Pipes Hub (`IPC-and-Pipes/`)
Master entry index: [README.md](../IPC-and-Pipes/README.md)
*   📂 [**`anonymous-pipes/`**](../IPC-and-Pipes/anonymous-pipes/README.md) — Unidirectional transient stream channels.
    *   📄 `unix-implementation.md`: Unix `pipe()`, `dup2()` descriptor cloning pipelines.
    *   📄 `windows-implementation.md`: Win32 `CreatePipe()` and `STARTUPINFO` handles.
*   📂 [**`named-pipes-fifos/`**](../IPC-and-Pipes/named-pipes-fifos/README.md) — File-system linked named channels.
    *   📄 `unix-implementation.md`: `mkfifo()` blocking client-server.
    *   📄 `windows-implementation.md`: Message-mode duplex server-client configurations.
*   📄 [**`message-queues.md`**](../IPC-and-Pipes/message-queues.md) — POSIX structured message systems with priorities.
*   📄 [**`unix-domain-sockets.md`**](../IPC-and-Pipes/unix-domain-sockets.md) — AF_UNIX local stream sockets bypassing network protocols.
*   📄 [**`shared-memory-ipc.md`**](../IPC-and-Pipes/shared-memory-ipc.md) — Zero-copy memory mapped regions (POSIX memory vs. Win32 Page File mapping).
*   📄 [**`process-shared-mutexes.md`**](../IPC-and-Pipes/process-shared-mutexes.md) — Storing pthread mutexes in shared memory and Win32 named synchronization handles.

---

### 5. Android Deployment Hub (`Android-Deployment/`)
Master entry index: [README.md](../Android-Deployment/README.md)
*   📄 [**`native-compilation.md`**](../Android-Deployment/native-compilation.md) — Cross-compiling C/C++ source using the Android NDK for target triplets (e.g. `aarch64-linux-android`).
*   📂 [**`apk-packaging/`**](../Android-Deployment/apk-packaging/README.md) — Staging dynamic libraries (`lib/arm64-v8a/`), and build scripts.
    *   📄 `signing-and-alignment.md`: 4-byte boundaries (`zipalign`) and cryptographic signing (`apksigner`).
*   📂 [**`adb-target-push/`**](../Android-Deployment/adb-target-push/README.md) — Staging executables directly in `/data/local/tmp`.
    *   📄 `dalvikvm-execution.md`: Translating Java bytecode to DEX (`d8`/`dx`) and execution via `dalvikvm`.
*   📂 [**`termux-execution/`**](../Android-Deployment/termux-execution/README.md) — Running POSIX systems software inside Termux.
    *   📄 `x11-gui-desktop.md`: Running X11 graphical software on mobile via `termux-x11`/VNC.
*   📄 [**`jni-bridge.md`**](../Android-Deployment/jni-bridge.md) — Java Native Interface bridging, type mappings, and native registration.
*   📄 [**`system-properties-security.md`**](../Android-Deployment/system-properties-security.md) — Accessing system settings, SELinux contexts, and ASLR compilation rules.

---

### 6. GUI & Input Architecture Hub (`GUI-and-Input-Architecture/`)
Master entry index: [README.md](../GUI-and-Input-Architecture/README.md)
*   📄 [**`prerequisites-concurrency.md`**](../GUI-and-Input-Architecture/prerequisites-concurrency.md) — UI Thread event loops and multithreading requirements.
*   📂 [**`widget-toolkits/`**](../GUI-and-Input-Architecture/widget-toolkits/README.md) — Tier 1 widget layouts.
    *   📄 `cross-language-equivalents.md`: Toolkit options mapped across C (GTK), C++ (wxWidgets), Rust (Slint/egui), Python (Tkinter), Java (JavaFX), Kotlin (Compose), and JS (Web DOM).
*   📂 [**`canvas-and-2d-engines/`**](../GUI-and-Input-Architecture/canvas-and-2d-engines/README.md) — Tier 2 double-buffered game loops.
    *   📄 `cross-language-equivalents.md`: Canvas pipelines compared across SDL2, SFML, pixels, Pygame, Java2D, Skiko, and Web Canvas.
*   📂 [**`hybrid-qt-engine/`**](../GUI-and-Input-Architecture/hybrid-qt-engine/README.md) — Tier 3 hybrid architecture.
    *   📄 `cross-language-equivalents.md`: Declarative engines mapped across IUP, Qt Quick, Tauri, PyQt, JavaFX, Compose (Skia), and Electron.
*   📂 [**`barebone-graphics-apis/`**](../GUI-and-Input-Architecture/barebone-graphics-apis/README.md) — Tier 4 GPU pipeline interfaces.
    *   📄 `cross-language-equivalents.md`: GPU drivers compared across OpenGL/Vulkan, `vulkan.hpp`, `ash`/`wgpu-rs`, PyOpenGL, LWJGL, and WebGL/WebGPU.
*   📄 [**`window-decorations.md`**](../GUI-and-Input-Architecture/window-decorations.md) — Borderless windows, CSD vs. SSD, and custom window handles.
*   📄 [**`input-unification.md`**](../GUI-and-Input-Architecture/input-unification.md) — Mapping touch and mouse coordinates to a unified coordinate structure.

---

### 7. OS Mechanisms Hub (`OS-Mechanisms/`)
Master entry index: [README.md](../OS-Mechanisms/README.md)
*   📂 [**`01-Freestanding-Environment-and-Boot/`**](../OS-Mechanisms/01-Freestanding-Environment-and-Boot/README.md) — Limits of freestanding C and bootloaders.
    *   📄 `assembly-prerequisites.md`: Staging stacks, CPU modes, and BSS configurations.
*   📂 [**`02-The-Kernel/`**](../OS-Mechanisms/02-The-Kernel/README.md) — Ring 0 supervisor core.
    *   📂 `01-Memory-Management/`: Physical allocation (Buddy), multi-level paging, and page fault swap systems.
    *   📂 `02-Interrupts-and-Traps/`: Interrupt Descriptor Table (IDT) gates and ISR handlers.
    *   📂 `03-Process-and-Scheduling/`: Thread Control Blocks (TCB) and context switching.
    *   📂 `04-System-Calls/`: Syscall dispatch tables and register conventions.
    *   📂 `05-Drivers-and-VFS/`: DMA I/O channels, physical disk block layouts, inodes, and VFS structures.
*   📂 [**`03-System-Services/`**](../OS-Mechanisms/03-System-Services/README.md) — PID 1 spawning, Init configurations (SysV, systemd), Windows Handles/Registry database, and macOS XNU Mach ports.
*   📂 [**`04-User-Space-and-Boundaries/`**](../OS-Mechanisms/04-User-Space-and-Boundaries/README.md) — POSIX user limits, OS boundaries, and a case study navigating MIT's 10,000-line xv6 Unix kernel.
