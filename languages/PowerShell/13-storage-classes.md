# Template: Storage Classes (Upvalues/Environments) [SYSTEMS]

**Goal:** To define how Pwsh interacts with the OS Environment and session-state.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
# Environment variables
$env:PATH
```

## 2. Pwsh 7+ (Modern)
```powershell
# Cross-platform path handling
$env:HOME # Works on Linux
```

## 3. Portable Path
```powershell
# Setting an environment variable for the process
[Environment]::SetEnvironmentVariable("TMP_VAR", "Value", "Process")
```

## 4. Explicit Path
```powershell
# Using the Env: drive provider
Get-ChildItem Env: | Where-Object { $_.Name -like "PS*" }
```

# The Logic Bridge
// Logic: The `Env:` drive is a provider that maps OS environment variables into the PowerShell namespace.
