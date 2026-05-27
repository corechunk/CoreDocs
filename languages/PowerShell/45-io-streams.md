# Template: IO Streams [CORE]

**Goal:** To define `stdin`, `stdout`, and `stderr` in the Pwsh context.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
Write-Output "Standard Out"
Write-Error "Standard Error"
```

## 2. Portable Path (Redirection)
```powershell
# 2>&1 merges Error into Success stream
ls non_existent 2>&1 | Out-File errors.txt
```

## 3. Explicit Path (Direct .NET Console)
```powershell
[Console]::Out.WriteLine("Direct to Buffer")
```

# The Logic Bridge
// Logic: In PowerShell, "Streams" are numerical (1:Success, 2:Error, 3:Warning, 4:Verbose, 5:Debug, 6:Information).
