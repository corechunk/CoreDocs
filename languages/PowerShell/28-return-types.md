# Template: Return Types [CORE]

**Goal:** To define the "Pipeline Stream" behavior and the `return` keyword.

---

## 1. The Definition (Mental Model)
**The Pipeline Trap:** In PowerShell, *every* uncaptured output is returned. The `return` keyword is just a "Stop and Exit" marker that optionally sends one last object.

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
function Get-Data {
    "Message 1" # This IS returned
    return "Message 2" # This is ALSO returned, then function exits
}
# Output: Array containing "Message 1" and "Message 2"
```

## 2. Portable Path
```powershell
function Get-Safe {
    [OutputType([int])]
    param()
    Write-Output 100
}
```

## 3. Explicit Path (7+ Strict Output)
```powershell
function New-Item {
    [CmdletBinding()]
    [OutputType([pscustomobject])]
    param()
    return [pscustomobject]@{ ID = 1 }
}
```

# The Logic Bridge
// Logic: To ensure only ONE object is returned, you must capture or discard all other output (e.g., `$null = ...` or `[void](...)`).
