# Template: Function Basics [CORE]

**Goal:** To define function declaration, parameters, and the `param()` block.

---

## 1. The Definition (Mental Model)
PowerShell functions are "Advanced Functions" when they use `[CmdletBinding()]`. They act like compiled Cmdlets, supporting common parameters like `-Verbose` and `-ErrorAction`.

## 1. Pwsh 5.1 (Legacy)
```powershell
function Get-Info($Name) {
    "Hello $Name"
}
```

## 2. Pwsh 7+ (Modern)
```powershell
function Get-Info {
    [CmdletBinding()]
    param(
        [string]$Name
    )
    process { "Hello $Name" }
}
```

## 3. Portable Path
```powershell
function Test-Func {
    param($Param1)
    "Result: $Param1"
}
```

## 4. Explicit Path (7+ Attributes)
```powershell
function Set-Config {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory, HelpMessage="Path is required")]
        [ValidateNotNullOrEmpty()]
        [string]$Path
    )
    begin { }
    process { Write-Output "Setting $Path" }
    end { }
}
```

# The Logic Bridge
// Logic: PowerShell functions use the `begin/process/end` blocks to handle pipeline input; `process` runs once for every object in the pipe.
