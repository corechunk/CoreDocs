# Inheritance (PRO)

Definition: Derived classes inheriting from a base class.

## 1. Pwsh 5.1 (Legacy)
Basic class inheritance.

```powershell
class Base { [int]$Id }
class Derived : Base { [string]$Name }
```

## 2. Pwsh 7+ (Modern)
Calling base constructors with `base`.

```powershell
class Base {
    Base([int]$id) { $this.Id = $id }
    [int]$Id
}
class Derived : Base {
    Derived([int]$id) : base($id) { }
}
```

## 3. Portable Path
Standard inheritance chain.

```powershell
class A { }
class B : A { }
```

## 4. Explicit Path
Examining the .NET inheritance hierarchy.

```powershell
[B].BaseType.Name # Output: A
```

# The Logic Bridge
// Logic: PowerShell classes are compiled to .NET types at runtime. Inheritance follows .NET rules (single inheritance for classes).
