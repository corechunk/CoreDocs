# Template: Keywords & Standards [CORE]

**Goal:** To define the reserved words in PowerShell and the expansion of standards (e.g., the introduction of ternary and null-coalescing operators).

---

## 1. The Definition (Mental Model)
Keywords are reserved words that define the language's structure. They form the "Grammar" of PowerShell and cannot be used as identifiers (variable names, function names) without special quoting.

## 2. Requirement: Categorized Master List
PowerShell keywords are grouped by their functional role in the engine.

| Category | Keywords |
| :--- | :--- |
| **Control Flow** | `if`, `else`, `elseif`, `switch`, `foreach`, `for`, `while`, `do`, `until`, `break`, `continue`, `return`, `exit` |
| **Error Handling** | `try`, `catch`, `finally`, `throw`, `trap` |
| **Functions/Blocks** | `function`, `filter`, `workflow` (Legacy), `begin`, `process`, `end`, `clean` (7.3+), `param`, `dynamicparam` |
| **Classes/OOP** | `class`, `enum`, `interface`, `namespace`, `using`, `hidden`, `static`, `base` |
| **Data/Scoping** | `data`, `module`, `configuration`, `in` |
| **Reserved (Future)** | `assembly`, `command`, `define`, `from`, `private`, `public`, `type`, `var` |

## 3. Requirement: Evolution Snapshot
PowerShell's grammar has expanded significantly since the move to .NET Core.

- **v5.1:** Established `class`, `enum`, `using`.
- **v7.0:** Added Ternary operator `? :` and Pipeline chain operators `&&`, `||`.
- **v7.1:** Added Null-coalescing operator `??` and `??=`.
- **v7.3:** Added the `clean` block for functions (guaranteed cleanup).

## 1. Pwsh 5.1 (Legacy Logic)
```powershell
# Traditional if/else
if ($val -eq $null) { $res = "Empty" } else { $res = $val }
```

## 2. Pwsh 7+ (Modern Syntax)
```powershell
# Ternary Operator (7.0+)
$res = ($null -eq $val) ? "Empty" : $val

# Null-coalescing (7.1+)
$res = $val ?? "Empty"
```

## 3. Portable Path
```powershell
# Checking for keywords in current version
Get-Help about_Reserved_Words
```

## 4. Explicit Path (Strict Requirements)
```powershell
#Requires -Version 7.4
#Requires -Modules @{ ModuleName="ThreadJob"; ModuleVersion="2.0" }
```

# The Logic Bridge
// Logic: PowerShell 7+ borrows C# syntax (ternary, null-coalescing) to reduce the verbosity of the standard Verb-Noun and block-heavy grammar.
