# Template: Tuning & Strictness [PRO]

**Goal:** To define how to enforce safety and catch "lazy" scripting errors early.

---

## 1. The Definition (Mental Model)
PowerShell allows non-existent variables to return `$null` by default. `Set-StrictMode` forces the engine to throw errors for common pitfalls.

## 1. Pwsh 5.1 (Legacy)
```powershell
Set-StrictMode -Version 1.0
```

## 2. Pwsh 7+ (Modern)
```powershell
Set-StrictMode -Version Latest # Enforces 3.0+ rules
```

## 3. Portable Path
```powershell
# Enable basic strictness for all versions
Set-StrictMode -Version 2.0
```

## 4. Explicit Path (Strict + Error Action)
```powershell
$ErrorActionPreference = "Stop"
Set-StrictMode -Version Latest
```

# The Logic Bridge
// Logic: Strict mode prevents the "Silent Null" bug where a typo in a variable name results in unintended logic flow.
