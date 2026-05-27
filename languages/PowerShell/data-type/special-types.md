# Template: Special Types [CORE]

**Goal:** To define Pwsh-specific types like ScriptBlocks, PSCustomObjects, and the universal `[object]` root.

---

## 1. Pwsh 5.1 / 7+ (The Object Root)
Every type in PowerShell inherits from `[object]`. An array of type `[object[]]` can store mixed data.
```powershell
[object[]]$mixed = 1, "text", (Get-Date)
# Output: Each element is stored as its base System.Object representation.
```

## 2. Pwsh 7+ (Modern)
```powershell
# Modern accelerated [pscustomobject] creation
$obj = [pscustomobject]@{ Name = "Pwsh7"; Ver = 7 }
```

## 3. Portable Path
```powershell
$hash = @{ Key = "Val" }
# Generic object check
if ($val -is [object]) { "Always True for non-nulls" }
```

## 4. Explicit Path
```powershell
[pscustomobject]$user = @{ Name = "Explicit" }
[scriptblock]$logic = { param($x) $x * 2 }
[type]$intType = [int]
[object]$generic = "Could be anything"
```

# The Logic Bridge
// Logic: `[object]` is the alias for `System.Object`; in the pipeline, PowerShell "boxes" value types (like ints) into objects to allow for uniform property and method access.
