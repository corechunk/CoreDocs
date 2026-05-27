# 12 - Scope & Lifetime (CORE)

Definition: Lua is lexically scoped. Variables are global by default unless declared with `local`. The scope of a local variable is the block where it is defined (a function body, a loop, or a `do-end` block).

## 1. Legacy Way (Conventional)
Using global variables and standard locals.

```lua
global_var = "I am global" -- Implicitly global

function test_scope()
    local scoped = "I am local"
    print(scoped)
end

test_scope()   -- Output: I am local
-- print(scoped) -- Error: scoped is nil here
print(global_var) -- Output: I am global
```

## 2. Modern Way (Explicit Blocks)
Using `do-end` for tight scope control and `local` everywhere.

```lua
do
    ---@type string
    local temp_config = "Secret"
    print(temp_config) -- Output: Secret
end
-- temp_config is inaccessible here

for i = 1, 3 do
    local iteration = i -- New 'iteration' variable for every loop cycle
    print(iteration)
end
-- Output: 1
-- Output: 2
-- Output: 3
```

# The Logic Bridge
Lua's "global by default" behavior is a common source of bugs. The "Modern Way" in Lua is to ALWAYS use `local` unless there is a specific reason for a global. `do-end` blocks are a powerful tool for isolating logic and managing memory lifetime (especially with Lua 5.4 `<close>`).
