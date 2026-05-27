# Template: Scope & Lifetime [CORE]

**Goal:** To define Local, Script, Global, and Private scopes.

---

## 1. Pwsh 5.1 / 7+ (Common)
```powershell
$script:shared = "All"
function Test {
    $local:val = "Inside"
}
```

## 2. Portable Path
```powershell
# Accessing parent scope explicitly
$global:config = @{}
```

## 3. Explicit Path
```powershell
# Private scope (Not visible even to child scopes)
$private:secret = "HIDDEN"
```

# The Logic Bridge
// Logic: PowerShell uses dynamic scoping by default; prefixing variables with a scope name ensures deterministic access.
