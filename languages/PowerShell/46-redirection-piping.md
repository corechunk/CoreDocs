# Template: Redirection & Piping [PRO]

**Goal:** To define the `|` (Pipe) and `>` (Redirect) operators.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
Get-Process | Where-Object { $_.CPU -gt 10 } | Select-Object ProcessName
```

## 2. Portable Path
```powershell
# Appending to file
"New Data" >> log.txt
```

## 3. Explicit Path (7+ Pipeline Chain)
```powershell
# Execute only if previous command succeeded (7.0+)
Test-Path "config.json" && Get-Content "config.json"
```

# The Logic Bridge
// Logic: The PowerShell pipe passes objects (live memory pointers), not just raw text as in Bash.
