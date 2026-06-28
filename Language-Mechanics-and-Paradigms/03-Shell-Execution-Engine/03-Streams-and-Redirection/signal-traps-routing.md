# ⚡ Signal Traps and System Signal Routing

## 1. POSIX Signal Traps
Interactive shells intercept asynchronous hardware and software OS signals using `sigaction()` routines.

## 2. Core Signal Traps Matrix
- **`SIGINT` (`Ctrl+C`):** Intercepted to interrupt active foreground processes without terminating the parent shell REPL session.
- **`SIGTSTP` (`Ctrl+Z`):** Intercepted to suspend foreground processes and move them to background job lists.
- **`SIGPIPE`:** Handled to detect broken pipe channels when a reader process terminates prematurely while a writer is still outputting streams.
