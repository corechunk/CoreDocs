# 36 - Class Concept (CORE - Hub)

Definition: The `class` is the gateway to Object-Oriented Programming in PowerShell. It encapsulates **State** (Properties) and **Behavior** (Methods) into a formal template.

## Deep-Dive Reference
For complex hierarchies and pillars:
- [Advanced OOP](./oop/37-advanced-oop.md)

---

## 1. Pwsh 5.1 (Legacy)
Standard class declaration and instantiation.

```powershell
class Counter {
    [int]$Value = 0
    [void] Increment() { $this.Value++ }
}

$c = [Counter]::new()
$c.Increment()
$c.Value # Output: 1
```

## 2. Pwsh 7+ (Modern)
Using typed constructors and static members.

```powershell
class Counter {
    [int]$Value
    Counter([int]$initial) { $this.Value = $initial }
    [void] Increment() { $this.Value++ }
}

$c = [Counter]::new(10)
$c.Increment()
$c.Value # Output: 11
```

## 3. Portable Path
Method-based objects in scripts.

```powershell
function New-Timer {
    return [PSCustomObject]@{
        Start = { Get-Date }
    }
}
```

## 4. Explicit Path
Reflecting on the underlying .NET type.

```powershell
$c = [Counter]::new()
$c.GetType().FullName # Output: Counter
```

# The Logic Bridge
// Logic: PowerShell classes are compiled to .NET types at runtime. The `$this` variable is the explicit reference to the current instance, allowing the method to modify its specific heap-allocated state.
