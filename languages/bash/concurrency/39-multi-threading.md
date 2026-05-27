# 🔴 Milestone 39: Multi-Threading [SYSTEMS]

### 1. Parallel Task Spreading
Since Bash is strictly single-threaded, parallelism is achieved by spreading tasks across multiple independent sub-processes. This mimics "Threading" by utilizing multiple CPU cores.

```bash
# CONVENTIONAL: Manual spread
for i in {1..4}; do
    ./worker.sh "$i" &
done
wait

# Logic: This launches 4 separate Bash processes simultaneously. 
# They share no memory but run in parallel.
```

### 2. Managed Thread Pools
For processing large lists, you should use tools that limit the number of active processes to avoid overloading the system scheduler.

```bash
# EXPLICIT: Controlled Parallelism
# Run 4 tasks at a time from a list of 20
printf "%s\n" {1..20} | xargs -n 1 -P 4 ./process.sh

# Logic: 'xargs -P' manages a process queue. It spawns new 
# children only when existing ones finish, maximizing throughput 
# while maintaining system stability.
```
