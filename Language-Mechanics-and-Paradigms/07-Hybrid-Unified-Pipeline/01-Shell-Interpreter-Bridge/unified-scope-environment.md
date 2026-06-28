# 🔀 Unified Scope Environment & Command Routing

## 1. Hybrid Command Parsing
The unified engine inspects input lines. Standard shell commands (e.g., `ls -la`, `cd`) route through the POSIX process spawning pipeline (`fork`/`execve`), while scripting statements (`var x = 10`) update the live interpreter symbol table.

## 2. Shared State Synchronization
Environment variables exported in the shell REPL (`export PATH=...`) seamlessly sync into the interpreter's global scope environment and vice versa.
