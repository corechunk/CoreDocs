# Template: Multi-File Projects [PRO]

**Goal:** To define "Dot-Sourcing" and Script Modules.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
# Dot-sourcing (Imports variables/functions into current scope)
. .\helper.ps1
```

## 2. Portable Path
```powershell
# Importing a module
Import-Module .\MyTools.psm1
```

## 3. Explicit Path
```powershell
using module .\MyClasses.psm1 # (5.0+) For classes
```

# The Logic Bridge
// Logic: Dot-sourcing loads code into the *caller's* scope; modules have their own private scope.
