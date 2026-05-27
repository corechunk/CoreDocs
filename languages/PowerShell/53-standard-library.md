# Template: Standard Library [PRO]

**Goal:** To define the core PowerShell modules.

---

## 1. Pwsh 5.1 / 7+ (Common)
- **Microsoft.PowerShell.Core:** `Get-Command`, `Get-Help`.
- **Microsoft.PowerShell.Management:** `Get-ChildItem`, `Set-Content`.
- **Microsoft.PowerShell.Utility:** `Select-Object`, `Sort-Object`.

## 2. Explicit Path
```powershell
# Listing all loaded modules
Get-Module
```

# The Logic Bridge
// Logic: PowerShell's "Standard Library" is actually a collection of C# modules that are pre-loaded into the engine.
