# 02 - Compilation & Run Basics

## Definition (Mental Model)
Lua is a "Scripting" language, but it doesn't execute source code directly. It compiles source into an intermediate bytecode format which the Lua Virtual Machine (LVM) then executes. You can run scripts on-the-fly or pre-compile them for faster loading and minor obfuscation.

## 1. Legacy Way (Direct Interpretation)
The conventional method is passing the `.lua` source file directly to the interpreter, which performs the compilation in-memory before execution.

```bash
# Executing source directly
lua script.lua

# script.lua content:
# print("Hello Lua") # Output: Hello Lua
```

## 2. Modern Way (Bytecode & Explicit Versioning)
In professional production environments or performance-critical modules, bytecode compilation (`luac`) is used to minimize the load-time overhead of the parser.

```bash
# Compile to bytecode
luac -o script.luac script.lua

# Execute the bytecode
lua script.luac
# Output: Hello Lua

# Explicitly targeting Lua 5.4 to use modern optimizations
lua5.4 script.lua
# Output: Hello Lua
```

# The Logic Bridge
Interpretation is just automated compilation-and-execution in a single step; explicit compilation separates the "Source Analysis" from the "Runtime Execution."
