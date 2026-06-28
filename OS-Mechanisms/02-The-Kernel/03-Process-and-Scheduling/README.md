# 🧵 Task Scheduling & Thread Control Blocks

Operating systems run multiple programs concurrently by multiplexing CPU cores. This is handled by the scheduler and the process manager.

---

### 1. Thread Control Block (TCB) / Process Descriptor

The kernel tracks each execution thread using a data structure called the **Thread Control Block (TCB)** or Process Descriptor (e.g. `struct proc` in xv6, `struct task_struct` in Linux). It stores:
*   The thread's unique Process ID (PID).
*   Execution State: Running, Ready (Runnable), or Blocked (Sleeping on I/O).
*   Saved CPU registers (saved context when the thread is not executing).
*   Pointer to the thread's private stack and page directory.

---

### 2. The Scheduler Loop

The scheduler loop (e.g., Round-Robin) continuously traverses the table of TCBs, identifies a process in the `Ready` state, and swaps it onto the physical CPU core.

```text
Ready Queue: [ Proc A (Ready) ] ---> [ Proc B (Ready) ] ---> [ Proc C (Sleeping) ]
                   |
           Scheduler swaps A onto CPU
                   v
              [ CPU Core ]
                   | (Timer interrupt expires)
           Swaps registers, puts A back to queue
```

---

### 🗺️ Redirection Directory

*   📄 [**`context-switch-assembly.md`**](./context-switch-assembly.md) — The process of saving and restoring CPU registers during thread transitions.
