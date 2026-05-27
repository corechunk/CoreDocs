# Template: Multi-Threading (Runspaces) [SYSTEMS]

**Goal:** To define low-level Runspace pools.

---

## 1. Pwsh 5.1 (Manual Runspaces)
```powershell
$rs = [runspacefactory]::CreateRunspace()
$rs.Open()
$ps = [powershell]::Create().AddScript({ 1+1 }).AddCommand("Out-String")
$ps.Runspace = $rs
$ps.BeginInvoke()
```

## 2. Pwsh 7+ (Parallel Pipeline)
```powershell
# Built-in multi-threading (7.0+)
1..10 | ForEach-Object -Parallel {
    $_ * 2
} -ThrottleLimit 5
```

## 3. Portable Path
```powershell
# Using the ThreadJob module (Available for 5.1)
1..10 | Start-ThreadJob { $_ * 2 }
```

## 4. Explicit Path
```powershell
# Using a RunspacePool for maximum control
$pool = [runspacefactory]::CreateRunspacePool(1, 5)
$pool.Open()
```

# The Logic Bridge
// Logic: `ForEach-Object -Parallel` uses a RunspacePool under the hood, abstracting away the complex .NET boilerplate.
