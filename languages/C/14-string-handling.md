# 🔵 Standard: String Handling [PRO]

## Definition
Strings in C are null-terminated character arrays (`\0`). String Handling governs the management of mutable stack/heap buffers and read-only literal strings safely, preventing buffer overflows and memory corruption.

---

## The Master String Compatibility Matrix

| Category | Function Name | Required Header | char[] (Stack Array) | char* (Literal Pointer) | char* (Heap Pointer) | What the Cryptic Name Actually Means |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Direct Modifying** | `str[0] = 'M'` | *None (Syntax)* | **YES** | ❌ **NO** *(Segfault)* | **YES** | Direct array index value assignment. |
| **Output / Printing**| `printf(...)` | **`<stdio.h>`** | **YES** | **YES** | **YES** | **Print** **F**ormatted to standard output. |
| **Input / Getting** | `fgets(...)` | **`<stdio.h>`** | **YES** | ❌ **NO** *(Segfault)* | **YES** | **F**ile **Get** **S**tring safely with limit. |
| **Input / Getting** | `scanf(...)` | **`<stdio.h>`** | **YES** | ❌ **NO** *(Segfault)* | **YES** | **Scan** **F**ormatted stream input. |
| **Copying / Writing**| `strcpy(...)` | **`<string.h>`** | ⚠️ **YES** *(Unsafe)*| ❌ **NO** *(Segfault)* | ⚠️ **YES** *(Unsafe)*| **Str**ing **Cpy** (Blind copy: no bounds). |
| **Copying / Writing**| `strncpy(...)`| **`<string.h>`** | **YES** | ❌ **NO** *(Segfault)* | **YES** | **Str**ing **N**-Count **Cpy** (Legacy bounded). |
| **Copying / Writing**| `snprintf(...)`| **`<stdio.h>`** | **YES** | ❌ **NO** *(Segfault)* | **YES** | **S**tring **N**-Count **Print** **F**ormatted into buffer. |
| **Memory Alloc** | `malloc(...)` | **`<stdlib.h>`** | _N/A_ | _N/A_ | **YES** | **M**emory **Alloc**ation on the Heap. |
| **Memory Cleanup** | `free(...)` | **`<stdlib.h>`** | _N/A_ | _N/A_ | **YES** | Releases Heap allocated memory space. |

### 💡 Core Guidelines & Gotchas
1. **The Write Rule**: Any function that writes, edits, or gets input into a string **only** works on mutable variables (`char[]` on stack or heap-allocated `char*` pointer).
2. **`snprintf` Header Oddity**: Even though `snprintf` is used for string copying and concatenation, it resides in **`<stdio.h>`** because it uses the standard formatted printing engine.
3. **Dynamic Strings**: Creating writeable pointer strings requires allocating memory using `malloc` from **`<stdlib.h>`** and releasing it using `free`.

---

## Deep-Dive Reference
For detailed memory layouts, character modification, input routines, and safety rankings:
- [String Declarations](./string/declarations.md) | [Character Modification](./string/modification.md) | [Input Methods](./string/input-methods.md) | [Copy & Write Methods](./string/copy-write-methods.md)

# The Logic Bridge
// Logic: C strings are represented as contiguous memory blocks terminated by a null byte (`\0`). Operations search sequentially for this sentinel value; omission of the terminator causes functions to read/write past buffer bounds.
