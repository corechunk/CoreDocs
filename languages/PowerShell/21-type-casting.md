# Template: Type Casting [CORE]

**Goal:** To define explicit casting `[type]` and the `-as` operator.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$num = [int]"10"
```

## 2. Portable Path
```powershell
# Safe casting with -as (Returns null if fails)
$val = "abc" -as [int]
if ($null -eq $val) { "Not a number" }
```

## 3. Explicit Path
```powershell
[xml]$data = Get-Content "file.xml"
```

# The Logic Bridge
// Logic: PowerShell's casting is more aggressive than C#; it will try multiple conversion methods (Parse, Convert, Constructor) to satisfy the request.
