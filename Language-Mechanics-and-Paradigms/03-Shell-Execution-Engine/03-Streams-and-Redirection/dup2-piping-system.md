# 🔀 File Descriptor Duplication (dup2) and Inter-Process Pipes (|)

## 1. Anonymous Pipes (pipe)
Inter-process communication in shell pipelines utilizes system pipe buffers (`pipe(fds)`), which allocate a unidirectional data channel returning two file descriptors: `fds[0]` (read end) and `fds[1]` (write end).

## 2. File Descriptor Duplication via dup2()
Before executing child binaries, the shell uses `dup2()` to overwrite standard output (fd 1) of the writer process with `fds[1]`, and standard input (fd 0) of the reader process with `fds[0]`.

```c
// Connecting Process A stdout to Process B stdin
dup2(pipefds[1], STDOUT_FILENO);
dup2(pipefds[0], STDIN_FILENO);
```
