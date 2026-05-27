# Template: Synchronization & Locks [SYSTEMS]

**Goal:** To define thread-safe operations in parallel blocks.

---

## 1. Pwsh 5.1 / 7+ (Manual Locks)
```powershell
$lock = [object]::new()
[System.Threading.Monitor]::Enter($lock)
# Critical Section
[System.Threading.Monitor]::Exit($lock)
```

## 2. Pwsh 7+ (Thread-Safe Dictionary)
```powershell
$dict = [System.Collections.Concurrent.ConcurrentDictionary[string, int]]::new()
$dict.TryAdd("Key", 1)
```

## 3. Portable Path
```powershell
# Using Synchronized Hashtable
$syncHash = [hashtable]::Synchronized(@{})
```

## 4. Explicit Path
```powershell
# Mutex for cross-process locking
$mutex = [System.Threading.Mutex]::new($false, "MyGlobalLock")
$mutex.WaitOne()
$mutex.ReleaseMutex()
```

# The Logic Bridge
// Logic: When using `-Parallel`, standard hashtables will crash if two threads write at once; `[hashtable]::Synchronized` provides a thread-safe wrapper.
