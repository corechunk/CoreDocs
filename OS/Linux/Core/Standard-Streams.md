# 🌊 Standard I/O Streams

Streams are communication channels between a program and its environment (Terminals, Files, Pipes).

## 1. The Three Streams
| FD | Name | Default Destination | Purpose |
|:---|:---|:---|:---|
| 0 | `stdin` | Keyboard | Input data |
| 1 | `stdout` | Terminal Screen | Normal output |
| 2 | `stderr` | Terminal Screen | Error logs / Diagnostics |

## 2. Redirection Logic
- `> file` : Redirect `stdout` to file.
- `2> file` : Redirect `stderr` to file.
- `2>&1` : Merge `stderr` into `stdout`.

## 3. Pipelines (`|`)
Pipes connect the `stdout` of Process A to the `stdin` of Process B. 
*Example: `feeder | gauge`*

---
*Relates to: [Bash Redirection](../../../languages/bash/46-redirection-piping.md)*
