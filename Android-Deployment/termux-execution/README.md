# 🐚 Termux Execution Environments

Termux is a terminal emulator and package bootstrapper that runs standard Linux applications directly on Android without requiring root access.

---

### 1. The prefix path challenge

Standard Linux programs hardcode links to `/bin`, `/usr/bin`, or `/lib`. Because standard Android does not contain these directories and blocks write access to root directories, Termux relocates the entire UNIX filesystem layout into its app private sandbox directory, known as the **Prefix**:
`/data/data/com.termux/files/usr`

Every tool, dynamic library, and package configuration operates within this prefix.

---

### 2. termux-elf-cleaner

When you cross-compile binaries on your PC to run in Termux, the dynamic linker might reject them because they refer to standard `/lib` paths or contain unnecessary OS headers. We use the tool `termux-elf-cleaner` to rewrite target paths:

`termux-elf-cleaner build/my_program`

This replaces reference strings targeting `/lib` with Termux `$PREFIX/lib` paths, allowing the dynamic linker to locate dependency libraries.

---

### 🗺️ Redirection Directory

*   📄 [**`x11-gui-desktop.md`**](./x11-gui-desktop.md) — Running graphical desktop applications inside Termux via X11 servers and VNC connections.
