# Encapsulation (PRO)

Definition: Restricting access to internal state and using objects as the primary unit of data. In Lua, this is achieved by using `local` variables within a factory function (Closure-based) or by convention in tables.

## 1. Conventional Path (Underscore Convention)
Using the `_` prefix to indicate a field is intended to be private.

```lua
local User = {}
User.__index = User

function User.new(name)
    local self = setmetatable({}, User)
    self._name = name -- Conventional private
    return self
end
```

## 2. Explicit Path (Closure-based Encapsulation)
Using a function closure to hide variables entirely from the outside world.

```lua
local function newUser(initial_name)
    local name = initial_name -- Truly private
    
    return {
        get_name = function() return name end,
        set_name = function(new_val) name = new_val end
    }
end

local u = newUser("Core")
print(u.get_name()) -- Output: Core
```

# The Logic Bridge
// Logic: Closure-based encapsulation is memory-heavy because each object instance creates a new set of function closures. The table-based convention is more efficient as methods are shared via the metatable, but it lacks hard runtime protection.
