# 18. Precedence & Associativity

Operator precedence determines the grouping of terms in an expression and decides how an expression is evaluated. Associativity determines the order in which operators of the same precedence are processed.

## 1. Legacy Way (Conventional)
Using parentheses to ensure correct evaluation without knowing the full table.

```lua
local result = (10 + 5) * 2
print(result) -- Output: 30

local complex = 10 + 5 * 2
print(complex) -- Output: 20
```

## 2. Modern Way (Explicit/EmmyLua)
Standard precedence table applied to typed variables.

```lua
---@type number
local a, b, c = 10, 5, 2

---@type number
local result = a + b * c -- multiplication (*) higher than addition (+)
print(result) -- Output: 20

---@type number
local pow_res = 2 ^ 3 ^ 2 -- exponentiation (^) is right-associative
print(pow_res) -- Output: 512 (2 ^ 9, not 8 ^ 2)
```

# The Logic Bridge
Lua follows standard mathematical precedence (PEMDAS/BODMAS).
**Precedence (High to Low):**
1. `^` (Right-associative)
2. `not`, `#`, `-` (Unary)
3. `*`, `/`, `//`, `%`
4. `+`, `-`
5. `..` (Right-associative)
6. `<<`, `>>` (Bitwise)
7. `&` (Bitwise)
8. `~` (Bitwise)
9. `|` (Bitwise)
10. `<`, `>`, `<=`, `>=`, `~=`, `==`
11. `and`
12. `or`

Note that `^` and `..` are **right-associative**, meaning `a ^ b ^ c` is `a ^ (b ^ c)`.
