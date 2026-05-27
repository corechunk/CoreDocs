# 🔴 Milestone 47: Exit Codes & Signals [SYSTEMS]

### 1. Process Status
An Exit Code is a number (0-255) a process leaves behind when it dies. It is the final "Last Word" of a program to its parent.

```bash
# EXPLICIT: Returning Status
# exit 0 (Success) | exit 1 (General Error) | exit 127 (Not Found)

# Logic: The CPU register stores the exit status. Bash exposes 
# this value in the special '$?' variable immediately after 
# execution.
```

### 2. System Interruptions
A Signal is a "Tap on the shoulder" from the OS. Bash scripts can intercept these signals to perform cleanup or change behavior.

```bash
# EXPLICIT: Signal Interception
trap "echo 'Cleaning up...'; rm -f /tmp/lock" SIGINT SIGTERM

# Logic: 'trap' modifies the script's entry in the Kernel's 
# Signal Handler Table. When the signal arrives, execution jumps 
# to the defined code block.
```
