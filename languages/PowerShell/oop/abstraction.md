# Abstraction (PRO)

Definition: Defining interfaces or abstract templates. (Note: Pwsh does not have an `abstract` keyword).

## 1. Pwsh 5.1 (Legacy)
Throwing errors for "abstract" methods.

```powershell
class Base {
    [void]Run() { throw "Not implemented" }
}
```

## 2. Pwsh 7+ (Modern)
Defining common method signatures.

```powershell
class Template { [void]Process() { } }
```

## 3. Portable Path
Using `interface` from C# snippets.

```powershell
Add-Type -TypeDefinition "public interface IRunner { void Run(); }"
```

## 4. Explicit Path
Strict interface implementation.

```powershell
class MyRunner : IRunner { [void]Run() { } }
```

# The Logic Bridge
// Logic: Since PowerShell lacks native `abstract` classes, abstraction is often simulated via base classes with empty methods or by injecting C# interfaces via `Add-Type`.
