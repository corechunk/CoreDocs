# 01 - Toolchain Installation

## Definition (Mental Model)
Setting up the Lua environment requires a balance between the lightweight interpreter and the ecosystem of libraries (Rocks). While Lua is often embedded, standalone development benefits from version management to handle the fragmentation between Lua 5.1 (JIT standard) and Lua 5.4 (Modern features).

## 1. Legacy Way (Global/Manual)
The traditional approach involves installing a fixed version via a system package manager or compiling from source, which often leads to version conflicts in multi-project environments.

```bash
# Ubuntu/Debian legacy install
sudo apt install lua5.1 luarocks

# Verification
lua -v
// Output: Lua 5.1.5  Copyright (C) 1994-2012 Lua.org, PUC-Rio
```

## 2. Modern Way (Explicit/Version-Managed)
The modern standard utilizes `hererocks` to create isolated environments for specific Lua and Luarocks versions, mirroring the behavior of Python's `venv` or Node's `nvm`.

```bash
# Install hererocks via pip
pip install hererocks

# Create an isolated Lua 5.4 environment with Luarocks 3.0+
hererocks lua54_env -l 5.4 -r latest

# Activate the environment
source lua54_env/bin/activate

# Verification
lua -v
// Output: Lua 5.4.6  Copyright (C) 1994-2023 Lua.org, PUC-Rio
```

# The Logic Bridge
Version managers automate the PATH configuration and dependency isolation, ensuring that "Modern" Lua 5.4 scripts don't fail due to "Legacy" 5.1 interpreter constraints.
