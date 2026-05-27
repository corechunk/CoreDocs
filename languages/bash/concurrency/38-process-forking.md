# 🔴 Milestone 38: Process Forking [SYSTEMS]

### 1. Parallel Execution
Forking is the act of the shell creating an identical clone of its current process to run a command without stopping the main script. This allows for parallel background tasks.

```bash
# CONVENTIONAL: Simple backgrounding
./backup_db.sh &            # Logic: Immediate return to prompt
echo "Backup started..."

# Logic: The '&' operator triggers the fork() system call. The 
# child process inherits a copy of the parent's file descriptors 
# and variables.
```

### 2. Job Synchronization
To build reliable scripts, you must track child processes and ensure they finish before the parent script terminates or proceeds to dependent steps.

```bash
# EXPLICIT: Job Tracking
./task1.sh & pid1=$!        # Grab PID of last child

./task2.sh & pid2=$!

wait $pid1 $pid2            # Block until BOTH finish

# Logic: 'wait' pauses the parent shell until a SIGCHLD signal is 
# received from the specific process IDs, ensuring linear 
# reliability in a parallel environment.
```
