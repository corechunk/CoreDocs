# Template: Exit Codes & Signals [SYSTEMS]

**Goal:** To define `$LASTEXITCODE` and Signal handling.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Checking external command status
ping google.com -n 1
if ($LASTEXITCODE -ne 0) { "Failed" }
```

## 2. Portable Path
```powershell
# Exiting with code
exit 1
```

## 3. Explicit Path (Signal handling)
```powershell
# Trapping Ctrl+C
[Console]::CancelKeyPress += {
    Write-Host "Cleaning up..."
    exit 0
}
```

# The Logic Bridge
// Logic: `$LASTEXITCODE` is for external binaries; `$?` is a boolean for the success of the last Pwsh cmdlet.
