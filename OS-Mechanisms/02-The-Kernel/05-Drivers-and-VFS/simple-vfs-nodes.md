# 📁 Virtual Filesystem (VFS) Nodes

The Virtual Filesystem (VFS) provides an abstract interface allowing applications to use uniform system calls (`read()`, `write()`) on files, network sockets, or pipes alike.

---

### 🧠 File Descriptors & File Objects

When a process opens a file, the system allocates an entry in three tables:

1.  **Process File Descriptor Table**: Maps a local integer descriptor index (e.g. `3`) to a entry in the system-wide open file table.
2.  **Open File Table (System-wide)**: Tracks open instances of files, storing the current file offset pointer (seek offset) and read/write flags.
3.  **Active Inode / vnode Table**: Tracks open files in memory, pointing directly to the underlying physical filesystem operations (`read_inode`, `write_block`).

```text
Process FD Table          Open File Table (Kernel)        Active vnode/inode
+------------+            +---------------------+         +-----------------+
| 3: fd 3    | ========>  | Offset: 24, Flags: R| ======> | ext4 inode 201  |
+------------+            +---------------------+         +-----------------+
```

---

### 💻 Simple VFS File Structure in C

```c
#include <stdint.h>

// Abstract vnode representing any open file or stream node in memory
struct vnode {
    enum { V_FILE, V_SOCKET, V_PIPE } type;
    int ref_count;
    struct vnode_ops *ops; // Pointer to function tables for read/write
    void *private_data;    // Points to raw inode structure, socket state, etc.
};

// VFS operations table containing function pointers to target filesystem drivers
struct vnode_ops {
    int (*read)(struct vnode *node, char *buf, int n);
    int (*write)(struct vnode *node, const char *buf, int n);
    int (*close)(struct vnode *node);
};
```
