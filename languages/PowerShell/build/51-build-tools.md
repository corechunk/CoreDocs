# Template: Build Tools [PRO]

**Goal:** To define `PowerShellGet` and `NuGet`.

---

## 1. Pwsh 5.1 (Legacy)
```powershell
Find-Module -Name "SqlServer" | Install-Module -Scope CurrentUser
```

## 2. Pwsh 7+ (Modern)
```powershell
# Using the updated PowerShellGet (v3+)
Install-PSResource -Name "Terminal-Icons"
```

## 3. Portable Path
```powershell
Get-Module -ListAvailable
```

# The Logic Bridge
// Logic: Pwsh 7+ introduced `Install-PSResource` to replace the slower `Install-Module` NuGet-based system.
