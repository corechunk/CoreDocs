# Template: Interpolation [CORE]

**Goal:** To define variable substitution within double-quoted strings and the sub-expression operator `$()`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$name = "Gemini"
"Hello $name" # Output: Hello Gemini
```

## 2. Portable Path
```powershell
# Sub-expression for properties
$proc = Get-Process -Id $PID
"Running: $($proc.ProcessName)"
```

## 3. Explicit Path (7+ String Format)
```powershell
[string]$fmt = "{0}: {1}" -f "Status", "OK"
```

# The Logic Bridge
// Logic: Interpolation in PowerShell is handled by the ExpandableString parser which identifies `$` sigils.
