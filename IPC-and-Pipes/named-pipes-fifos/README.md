# 🔀 Named Pipes & FIFOs: Concepts

Named pipes are persistent IPC channels registered within the operating system. Unlike anonymous pipes, named pipes have explicit names (filepaths or system paths) allowing unrelated processes to locate and establish communication channels.

---

### 🧠 Core Concepts

1.  **UNIX FIFOs (First-In, First-Out)**:
    *   Linked directly to the directory tree as a special file node (`S_IFIFO`).
    *   Stream-oriented: Data written is read as a raw stream of bytes; boundary identification must be handled by application protocols (e.g. delimiters or size prefixes).
    *   **Block-on-Open**: By default, opening the read end of a FIFO blocks the thread until another process opens the write end, and vice-versa.
2.  **Windows Named Pipes**:
    *   Managed by the **Named Pipe File System (NPFS)** using virtual paths (`\\.\pipe\PipeName`).
    *   **Message-Mode Support**: Windows supports writing discrete message frames. The reader reads one message block at a time without needing custom stream parsing.
    *   **Duplex Operations**: Supports bidirectional (full-duplex) communication over a single pipe instance.

---

### 🗺️ Platform Implementations

*   📄 [**`unix-implementation.md`**](./unix-implementation.md) — Creating and executing local FIFO communication via `mkfifo()`.
*   📄 [**`windows-implementation.md`**](./windows-implementation.md) — Win32 Named Pipe client-server loops using `CreateNamedPipe()` and `ConnectNamedPipe()`.
