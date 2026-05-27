# 26. Jump Statements (Pro)

Jump statements interrupt the normal flow of control. Lua supports `break` and, as of version 5.2, `goto`.

## 1. Legacy Way (Conventional)
Using `break` to exit loops early.

```lua
for i = 1, 10 do
    if i == 3 then break end
    print(i)
end
-- Output: 1
-- Output: 2

-- Simulating 'continue' (which Lua lacks) with a repeat block
for i = 1, 3 do
    repeat
        if i == 2 then break end -- breaks the repeat, effectively 'continue' for the for
        print("Processing: " .. i)
    until true
end
-- Output: Processing: 1
-- Output: Processing: 3
```

## 2. Modern Way (Lua 5.2+ `goto`)
Using `goto` for more flexible jumps and proper 'continue' simulation.

```lua
for i = 1, 3 do
    if i == 2 then goto continue end
    print("Handled: " .. i)
    ::continue::
end
-- Output: Handled: 1
-- Output: Handled: 3

-- Error handling jump
local function process(val)
    if val < 0 then goto error end
    print("Value: " .. val)
    return
    ::error::
    print("Error: Negative value")
end

process(10) -- Output: Value: 10
process(-1) -- Output: Error: Negative value
```

# The Logic Bridge
Lua does not have a native `continue` keyword.
- `break`: Exits the innermost loop.
- `goto`: Jumps to a label `::name::`.
Labels are visible only in the block where they are defined. `goto` cannot jump into a block, only out of one or within the same block. While `goto` is often discouraged in high-level languages, it is a powerful tool in Lua for implementing complex state machines or clean error recovery paths.
