# Template: PS Custom Objects [SYSTEMS]

**Goal:** To define the internal structure of `PSObject`.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$obj = [pscustomobject]@{ A = 1 }
$obj.PSObject.Properties | Select-Object Name, Value
```

## 2. Explicit Path
```powershell
$obj.PSObject.Methods | Select-Object Name
```

# The Logic Bridge
// Logic: Every object in Pwsh is wrapped in a `PSObject`, which allows for dynamic "NoteProperties" to be added at runtime.
