# Template: Memory Management [SYSTEMS]

**Goal:** To define the Garbage Collector (GC).

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Manual GC trigger
[GC]::Collect()
```

## 2. Portable Path
```powershell
# Checking memory usage
(Get-Process -Id $PID).PrivateMemorySize64 / 1MB
```

## 3. Explicit Path
```powershell
# Disposal pattern
$stream = [System.IO.FileStream]::new("f.txt", "Open")
$stream.Dispose()
```

# The Logic Bridge
// Logic: PowerShell is managed memory; the GC runs periodically to free unreferenced .NET objects.
