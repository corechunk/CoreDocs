# Dot-Sourcing (PRO)

Definition: Executing a script in the current scope, allowing it to "bleed" its functions and variables into the caller's environment.

## 1. Pwsh 5.1 (Legacy)
Standard dot-sourcing.

```powershell
. .\Helper.ps1
```

## 2. Pwsh 7+ (Modern)
Dot-sourcing within a block scope.

```powershell
& { . .\LocalHelper.ps1; Invoke-Helper }
```

## 3. Portable Path
Cross-platform path handling for sourcing.

```powershell
. "$PSScriptRoot/lib/utils.ps1"
```

## 4. Explicit Path
Sourcing with explicit variable visibility.

```powershell
$private:secret = "Hide"
. .\PublicScript.ps1 # Cannot see $secret
```

# The Logic Bridge
// Logic: Unlike `Import-Module`, which creates a separate module scope, dot-sourcing tells the PowerShell parser to treat the target script's lines as if they were written directly inside the current file.
