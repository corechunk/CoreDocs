# Template: Compilation & Execution Basics [CORE]

**Goal:** To define how to run scripts (`.ps1`) and the concept of "Execution Policies."

---

## 1. The Definition (Mental Model)
PowerShell scripts are text files with the `.ps1` extension. They are interpreted line-by-line, but Windows has a security feature called "Execution Policy" that may block script execution by default.

## 1. Pwsh 5.1 (Legacy)
```powershell
# Bypassing policy for a single session
powershell.exe -ExecutionPolicy Bypass -File .\script.ps1
```

## 2. Pwsh 7+ (Modern)
```bash
# Running directly on Linux/macOS (No execution policy)
pwsh ./script.ps1
```

## 3. Portable Path
```powershell
# The standard "Hello World"
Write-Host "Hello, Pwsh" -ForegroundColor Green
# Output: Hello, Pwsh (in green)
```

## 4. Explicit Path (Strict Mode)
```powershell
Set-StrictMode -Version Latest
Write-Output "Health Check: OK"
# Output: Health Check: OK
```

# The Logic Bridge
// Logic: `Write-Host` targets the console directly, while `Write-Output` sends objects to the pipeline.
