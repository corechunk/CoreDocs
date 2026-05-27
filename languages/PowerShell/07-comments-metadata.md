# Template: Comments & Metadata [CORE]

**Goal:** To define standard comments, block comments, and Help-Based Metadata.

---

## 1. The Definition (Mental Model)
PowerShell uses `#` for comments. It also supports "Help-Based Help" which allows the `Get-Help` command to automatically document your scripts.

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Single line comment

<#
  Multi-line
  Block comment
#>
```

## 2. Portable Path (Help Metadata)
```powershell
<#
.SYNOPSIS
    This is a test script.
.DESCRIPTION
    A longer description of what it does.
#>
function Test-Script { }
```

## 3. Explicit Path (Parameter Attributes)
```powershell
function Get-Data {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [string]$Path
    )
    process { }
}
```

# The Logic Bridge
// Logic: Metadata comments at the top of a function are parsed by the Pwsh engine to populate the manual system (`Get-Help`).
