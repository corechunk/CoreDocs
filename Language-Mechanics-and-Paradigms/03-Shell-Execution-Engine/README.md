# 🐚 Phase 03: Shell Execution Engine

> ### 🛠️ Required Knowledge Depth & Requirements Coverage
> * **Interactive REPL Infrastructure:** Raw terminal modes, readline input capturing, multi-line buffer assembly, command history indexing.
> * **POSIX Kernel Process Primitives:** `fork()`, `execve()`, process IDs (`PID`), process groups, job control (`&` backgrounding, `fg`/`bg`), zombie child reaping (`waitpid()`, `SIGCHLD`).
> * **I/O Pipelines & Signals:** File descriptor duplication (`dup2()`), inter-process anonymous pipes (`|`), signal traps (`SIGINT`, `SIGTSTP`, `SIGPIPE`).

---

## 🗺️ Module Directory Index

- 💻 [**01-REPL-Architecture**](./01-REPL-Architecture/README.md) — Terminal raw mode configurations, readline capturing loops, and command history tab-completion indexing.
- ⚡ [**02-Process-Boundary-Mgmt**](./02-Process-Boundary-Mgmt/README.md) — Unix process spawning (`fork`/`execve`), process group isolation, job control (`&`, `fg`, `bg`), and zombie reaping (`waitpid`).
- 🔀 [**03-Streams-and-Redirection**](./03-Streams-and-Redirection/README.md) — File descriptor duplication (`dup2`), inter-process pipe channels (`|`), and system signal trap routing.
