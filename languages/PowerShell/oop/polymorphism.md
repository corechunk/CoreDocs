# Polymorphism (PRO)

Definition: Overriding base methods to provide specific behavior.

## 1. Pwsh 5.1 (Legacy)
Method overriding.

```powershell
class Base { [void]Action() { } }
class Derived : Base { [void]Action() { Write-Host "Derived" } }
```

## 2. Pwsh 7+ (Modern)
Using interfaces (limited support in Pwsh, usually via .NET types).

```powershell
# Using [IDisposable] as a common interface
```

## 3. Portable Path
Duck typing (Standard in PowerShell scripts).

```powershell
function Invoke-Action($obj) { $obj.Action() }
```

## 4. Explicit Path
Virtual method dispatch via .NET.

```powershell
[Base]$b = [Derived]::new()
$b.Action() # Output: Derived
```

# The Logic Bridge
// Logic: PowerShell uses .NET's dynamic method dispatch. When a method is called, the DLR (Dynamic Language Runtime) finds the best matching implementation based on the object's actual type.
