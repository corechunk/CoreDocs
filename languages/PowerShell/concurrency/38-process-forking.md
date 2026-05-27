# Template: Process Forking (Jobs) [SYSTEMS]

**Goal:** To define Background Jobs (`Start-Job`).

---

## 1. Pwsh 5.1 (Legacy Process Jobs)
```powershell
# Starts a separate powershell.exe process
Start-Job -ScriptBlock { Get-Process }
Get-Job | Receive-Job -Wait
```

## 2. Pwsh 7+ (Modern Thread Jobs)
```powershell
# Faster, stays within the same process
Start-ThreadJob -ScriptBlock { Get-Process }
```

## 3. Portable Path
```powershell
# Wait for any job to complete
Wait-Job -Any
```

## 4. Explicit Path
```powershell
# Strict job cleanup
$j = Start-Job { 1..10 }
$res = $j | Wait-Job | Receive-Job
Remove-Job $j
```

# The Logic Bridge
// Logic: Standard `Start-Job` is expensive because it clones the entire session into a new OS process; `ThreadJob` shares memory and is significantly lighter.
