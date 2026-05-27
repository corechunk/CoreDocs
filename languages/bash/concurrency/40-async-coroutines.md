# 🔵 Milestone 40: Async Coroutines [PRO]

### 1. Asynchronous Two-Way Talk
A Co-process (`coproc`) is a background command that stays connected to the main script via two anonymous pipes. This allows the script to send data to and receive results from a persistent worker.

```bash
# EXPLICIT: Starting a Coprocess
coproc WORKER { ./logic_engine.sh; }

# Logic: Bash creates an array '${WORKER[@]}' containing two 
# file descriptors: [1] for writing to the child's stdin and 
# [0] for reading from its stdout.
```

### 2. Stream Interfacing
Communicating with a coprocess requires precise redirection to the specific file descriptors created by the shell.

```bash
# EXPLICIT: Communication Pattern
# 1. Send data
echo "INPUT_DATA" >&"${WORKER[1]}"

# 2. Receive result
read -r result <&"${WORKER[0]}"

# Logic: coproc is a high-level wrapper around the pipe() system 
# call, providing an asynchronous "Service" within your script.
```
