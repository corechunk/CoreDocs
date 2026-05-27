# Template: Pointer Mastery [SYSTEMS]

**Goal:** To define the `IntPtr` bridge.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Getting a handle
$ptr = [System.IntPtr]::Zero
```

## 2. Explicit Path (7+ Span)
```powershell
# Working with memory spans (7.0+)
[Span[int]]::new([int[]](1..10))
```

# The Logic Bridge
// Logic: PowerShell uses `IntPtr` to represent raw memory addresses when calling unmanaged Win32 or Linux C APIs.
