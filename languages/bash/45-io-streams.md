# 🟢 Milestone 45: I/O Streams [CORE]

### 1. The Standard Channels
Every process in Linux starts with three open "Files" (Streams) for communication. Understanding these channels is fundamental to mastering shell interaction.

```bash
# CONVENTIONAL: Implicit usage
echo "Hello"               # Mouth: Writes to stdout (1)
read input                 # Ear: Listens to stdin (0)

# Logic: When a process is spawned, the Kernel populates its 
# File Descriptor Table with pointers to the terminal's 
# keyboard and screen.
```

### 2. Explicit Targeting
To write professional scripts, you must control which stream carries your data. High-signal errors should always be routed to the error stream.

```bash
# EXPLICIT: Target Descriptors
echo "Critical Error!" >&2  # Route to stderr (2)
read -u 0 data              # Explicitly read from stdin (0)

# Logic: Redirection operators (>&) allow you to swap the destination 
# of a process's mouth or ear before the code executes.
```

---
*See also: [Standard I/O Streams](../../OS/Linux/Core/Standard-Streams.md)*

