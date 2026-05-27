# 🔴 Milestone 41: Synchronization Locks [SYSTEMS]

### 1. Resource Mutual Exclusion
Locks prevent "Race Conditions" when multiple script instances attempt to access the same file or database simultaneously.

```bash
# CONVENTIONAL: Lock Directory (Fragile)
if mkdir /tmp/mylock; then
    # Do work
    rmdir /tmp/mylock
fi

# Logic: If the script crashes, the directory remains, 
# permanently blocking future executions.
```

### 2. Advisory File Locking
The professional way to synchronize is using Kernel-level advisory locks. These are automatically cleaned up by the OS if the process terminates.

```bash
# EXPLICIT: Kernel-level Locking (flock)
(
    flock -x 200            # Wait for EXCLUSIVE lock on FD 200
    echo "Writing to shared resource..."
    sleep 2
) 200>/var/lock/my_app.lock

# Logic: 'flock' uses the system's flock() call. The lock lives 
# in the Kernel's Open File Table, ensuring atomic access even 
# across different users/sessions.
```
