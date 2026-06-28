# 💾 Physical Filesystem Layouts

A physical filesystem translates abstract files and directories into raw hardware sectors (typically 512 bytes) on disk blocks.

---

### 🧠 The Unix inode-based Filesystem Layout

In standard UNIX filesystems (like ext2/ext3/ext4), a storage partition is split into blocks and structured as follows:

```text
+---------------+-------------------+-------------------+--------------------+
|  Superblock   |    Inode Table    |    Data Blocks    |   Journal Block    |
+---------------+-------------------+-------------------+--------------------+
```

1.  **Superblock**: Contains partition-wide metadata (block size, total block count, free inode pointers).
2.  **Inode Table**: An index of **Inodes** (Index Nodes). Every file or directory has an inode. The inode contains file metadata (owner, permissions, size) and pointers to the physical **Data Blocks** holding the file content. An inode *never* stores the filename.
3.  **Data Blocks**: Raw disk blocks storing file contents or directory entry lists.
4.  **Directory Entries**: A directory is simply a file whose data blocks contain a list of `[Filename, Inode Number]` pairs.

```text
Directory file data block:
| Name: "hello.c" | Inode #: 1032 |
| Name: "notes"   | Inode #: 1033 |
```

---

### 💻 Simplified Inode Structure in C

```c
#include <stdint.h>

#define DIRECT_BLOCKS 12

// Representation of a physical disk inode entry
struct inode {
    uint16_t type;            // File type (1 = File, 2 = Directory, 3 = Char device)
    uint16_t nlink;           // Number of hard links pointing to this inode
    uint32_t size;            // File size in bytes
    uint32_t addrs[DIRECT_BLOCKS + 1]; // Pointers to physical data blocks on disk
};
```
