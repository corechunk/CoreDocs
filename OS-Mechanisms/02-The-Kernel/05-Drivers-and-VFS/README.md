# 📁 Drivers & Virtual Filesystem (VFS)

The operating system manages storage devices, networks, and peripherals, presenting them to application programs through a unified, virtual filesystem abstraction layer.

---

### 1. I/O Device Communication

Operating system kernels communicate with physical hardware (such as keyboards, serial ports, or storage controllers) through device drivers. These drivers translate generic read/write API requests into device-specific commands using polling, interrupts, or **Direct Memory Access (DMA)**.

---

### 2. Filesystem Hierarchies

To avoid locking application code to specific storage hardware designs, operating systems implement a **Virtual Filesystem (VFS)**. The VFS exposes a standard directory tree interface (`open`, `read`, `write`, `close`) that maps to differing physical storage structures (e.g. ext4, FAT, or NTFS) and virtual nodes (e.g., `/dev` characters devices).

```text
               +--------------------------------------+
               |          VFS Layer (mount)           |
               +--------------------------------------+
                /                 |                  \
     [ ext4 Filesystem ]  [ FAT32 Filesystem ]   [ devfs Nodes ]
             |                    |                    |
     [ SATA Controller ]  [ USB Controller ]     [ Keyboard Driver ]
```

---

### 🗺️ Redirection Directory

*   📄 [**`I-O-communication-DMA.md`**](./I-O-communication-DMA.md) — Polling, Interrupt-driven I/O, and Direct Memory Access (DMA).
*   📄 [**`physical-filesystem-layouts.md`**](./physical-filesystem-layouts.md) — Hard disk physical structures: Sectors, blocks, inodes, and directory entry logs.
*   📄 [**`simple-vfs-nodes.md`**](./simple-vfs-nodes.md) — Abstracting filesystem paths using `vnode`/`inode` objects and file descriptor tables.
