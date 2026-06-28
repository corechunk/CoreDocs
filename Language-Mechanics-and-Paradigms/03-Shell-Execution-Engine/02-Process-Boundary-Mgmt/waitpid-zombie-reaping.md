# 🧟 Process Reaping and Zombie Cleanup (waitpid)

## 1. Zombie Processes (Defunct State)
When a child process terminates, its kernel process table entry remains as a "Zombie" holding exit status metadata until consumed by the parent process.

## 2. Asynchronous Reaping via SIGCHLD & waitpid()
To prevent memory leaks in the OS kernel process table, the shell sets up asynchronous signal handlers for `SIGCHLD`, executing non-blocking `waitpid(-1, &status, WNOHANG)` loops to clean up defunct child processes cleanly.
