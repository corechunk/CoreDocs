# 🔀 Anonymous Pipe Concepts & Mechanics

An anonymous pipe is a unidirectional, transient data channel managed by the operating system kernel. It provides a raw byte-stream interface between two related processes (typically parent and child).

---

### 🧠 Core Physical Mechanics

```text
               +-------------------------------------------------+
               |                  Kernel Space                   |
               |                                                 |
  Write End    |   +---------+---------+---------+---------+     |   Read End
 [FD / Handle] |-->| Chunk 4 | Chunk 3 | Chunk 2 | Chunk 1 |---->| [FD / Handle]
               |   +---------+---------+---------+---------+     |
               |             Circular Ring Buffer                |
               +-------------------------------------------------+
```

1.  **Circular Ring Buffer**: Internally, a pipe is a ring buffer allocated in kernel memory (typically 64KB on modern Linux, dynamically tunable). It operates as a First-In, First-Out (FIFO) queue of bytes.
2.  **Flow Control & Blocking**:
    *   **Pipe Full**: If the writing process writes faster than the reading process reads, the kernel buffer fills up. Once full, any further `write()` calls block the writing thread until the reader consumes data and frees space.
    *   **Pipe Empty**: If the reader requests data but the buffer is empty, the `read()` call blocks the reading thread until the writer submits bytes to the pipe.
3.  **EOF (End-of-File) Propagation**: When all file descriptors or handles pointing to the write end of the pipe are closed, a read attempt on the pipe returns `0` bytes, indicating EOF.
4.  **SIGPIPE Hazard (UNIX)**: If a process attempts to write to a pipe whose read end has been closed, the kernel sends a `SIGPIPE` signal to the writing process. By default, this terminates the program. Programs must catch or ignore `SIGPIPE` to handle this error gracefully.

---

### 🗺️ Platform Implementations

*   📄 [**`unix-implementation.md`**](./unix-implementation.md) — UNIX/POSIX pipeline engineering via `pipe()`, `dup2()` redirection, and file descriptor inheritability.
*   📄 [**`windows-implementation.md`**](./windows-implementation.md) — Win32 pipeline engineering using `CreatePipe()`, handle tables, and `STARTUPINFO` redirection.
