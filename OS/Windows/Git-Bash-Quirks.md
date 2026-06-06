# 🪟 Git-Bash Environment & MSYS2

Git-Bash is a compatibility layer providing a Bash-like environment on Windows.

## 1. MSYS2 Runtime
Git-Bash relies on `msys-2.0.dll`, which translates Linux system calls to Windows APIs.

## 2. Performance Bottlenecks
- **Process Forking**: Windows lacks a native `fork()` call. Every background task (`&`) or pipe (`|`) creates significant overhead compared to Linux.
- **File System Speed**: NTFS is generally slower for small file operations (like counting many tiny `.done` files) compared to ext4/btrfs.

## 3. Path Translation
MSYS2 automatically converts paths like `/c/Users` to `C:\Users`. Use caution with absolute paths in scripts.
