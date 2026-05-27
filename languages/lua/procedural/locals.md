# Local-First Optimization (PRO)

Definition: Lua's performance mandate: Always use `local` variables. Accessing locals is significantly faster than globals because locals are stored in virtual machine registers.

## 1. Conventional Path
Caching global functions in local variables.

```lua
-- Faster access to math.sin
local sin = math.sin

for i=1, 1000 do
    local x = sin(i)
end
```

## 2. Explicit Path
Explicitly preventing global leakage.

```lua
local function perform_task()
    local x = 10
    -- ... logic ...
end

perform_task()
```

# The Logic Bridge
// Logic: Global variables reside in the `_G` table (a hash map), requiring a table lookup every time they are accessed. Local variables are indexed by the VM's register array, making access nearly instantaneous.
