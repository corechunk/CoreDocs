# Abstraction (PRO)

Definition: Defining an interface or template that other objects must follow. Lua uses table templates and contract checks.

## 1. Conventional Path
Using a "Base" table as an abstract template.

```lua
local AbstractShape = {}
function AbstractShape:area() error("Not implemented") end
```

## 2. Explicit Path (Checked Abstraction)
Enforcing interface implementation during object creation.

```lua
local function create_shape(impl)
    assert(impl.area, "Must implement area()")
    return impl
end
```

# The Logic Bridge
// Logic: Abstraction in Lua is a "Soft" contract. Since the language has no `abstract` keyword, we use runtime errors or assertions to ensure that specific methods are implemented by the concrete instances or derived prototypes.
