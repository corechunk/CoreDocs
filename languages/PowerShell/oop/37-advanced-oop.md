# Template: Advanced OOP [PRO - Hub]

**Goal:** To define Inheritance and Polymorphism.

## Deep-Dive Reference
For complex hierarchies and abstractions:
- [Encapsulation](./encapsulation.md) | [Inheritance](./inheritance.md)
- [Polymorphism](./polymorphism.md) | [Abstraction](./abstraction.md)

---

## 1. Pwsh 5.1 (Legacy)
```powershell
class Animal {
    [string] Speak() { return "Generic" }
}
class Dog : Animal {
    [string] Speak() { return "Woof" }
}
```

## 2. Pwsh 7+ (Modern)
```powershell
# Better support for interfaces and abstract-like logic
class Cat : Animal {
    [string] Speak() { return "Meow" }
}
```

## 3. Portable Path
```powershell
$pets = [Dog]::new(), [Cat]::new()
foreach ($p in $pets) { $p.Speak() }
```

## 4. Explicit Path
```powershell
# Using Interfaces (7.0+)
class MyJob : System.IDisposable {
    [void] Dispose() { }
}
```

# The Logic Bridge
// Logic: Inheritance in PowerShell uses the `:` syntax, identical to C#; a child class inherits all properties and methods of the parent.
