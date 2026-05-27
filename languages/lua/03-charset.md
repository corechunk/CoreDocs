# 03 - Charset (SYSTEMS)

## Definition (Mental Model)
Lua strings are "8-bit clean." This means a string is not a collection of characters, but a sequence of raw bytes. Lua doesn't care if those bytes represent ASCII, UTF-8, or binary image data. While this provides maximum flexibility, it shifts the responsibility of encoding awareness (like UTF-8) to the developer.

## 1. Legacy Way (Byte-Centric Manipulation)
Older Lua versions treated everything as single bytes, which leads to incorrect length calculations for multi-byte characters like Emojis or Non-Latin scripts.

```lua
local text = "Héllo"
print(#text) // Output: 6 (The 'é' is 2 bytes in UTF-8)

-- Legacy substring (breaks multi-byte characters)
print(string.sub(text, 1, 2)) // Output: H\195 (Broken character)
```

## 2. Modern Way (Encoding Aware / UTF-8 Library)
Lua 5.3+ introduced the `utf8` library, providing native support for calculating lengths and offsets based on UTF-8 code points rather than raw bytes.

```lua
---@type string
local text <const> = "Héllo 🚀"

-- Correct code point length
local cp_len = utf8.len(text)
print(cp_len) // Output: 7

-- Explicitly iterating through code points
for i, p in utf8.codes(text) do
    print(string.format("Position %d: Char Code %d", i, p))
end
// Output: Position 1: Char Code 72
// Output: Position 2: Char Code 233
// ...
// Output: Position 7: Char Code 128640
```

# The Logic Bridge
The `utf8` library acts as a logic-mapping layer that interprets the raw "8-bit clean" byte sequences as valid Unicode code points.
