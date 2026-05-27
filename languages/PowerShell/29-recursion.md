# Template: Recursion [CORE]

**Goal:** To define recursive calls and the call stack limits.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
function Get-Factorial([int]$n) {
    if ($n -le 1) { return 1 }
    return $n * (Get-Factorial ($n - 1))
}
```

## 2. Portable Path
```powershell
# Checking stack depth (Conceptual)
$ExecutionContext.SessionState.LanguageMode
```

## 3. Explicit Path
```powershell
function Traverse-Dir([string]$Path) {
    Get-ChildItem $Path -Directory | ForEach-Object {
        Traverse-Dir $_.FullName
    }
}
```

# The Logic Bridge
// Logic: PowerShell is not optimized for deep recursion (no tail-call optimization); prefer loops or the pipeline for deep trees.
