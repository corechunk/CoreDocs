# Template: GC Collect [SYSTEMS]

**Goal:** To define explicit memory release.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
[GC]::Collect()
[GC]::WaitForPendingFinalizers()
```

## 2. Explicit Path
```powershell
# Generational GC check
[GC]::GetGeneration($obj)
```

# The Logic Bridge
// Logic: Manual GC collection is usually discouraged; the engine handles it based on memory pressure.
