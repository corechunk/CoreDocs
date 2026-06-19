# 🟢 Standard: String Formatting & I/O [CORE]

## Definition
String Formatting and I/O manages how standard and fixed-width types are translated to human-readable text and read from input streams, using standard formats and fixed-width platform-agnostic macro conversions.

---

## The Ultimate C Data Type & I/O Reference Matrix

| Header | Data Type | How to Define It | Output (`printf`) | Input (`scanf`) | Notes / Warnings |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **`<stdio.h>`** | `int` | `int num = 42;` | `%d` or `%i` | `%d` | Standard 32-bit signed integer. |
| **`<stdio.h>`** | `unsigned int` | `unsigned int num = 42;` | `%u` | `%u` | Standard 32-bit unsigned integer. |
| **`<stdio.h>`** | `long long` | `long long num = 123456789012LL;` | `%lld` | `%lld` | Standard 64-bit signed integer. |
| **`<stdio.h>`** | `float` | `float pi = 3.14f;` | `%f` | `%f` | 32-bit floating point. |
| **`<stdio.h>`** | `double` | `double pi = 3.14159265;` | `%f` or `%lf` | `%lf` | 64-bit floating point. **Crucial:** Uses `%lf` for input! |
| **`<stdio.h>`** | `char` | `char ch = 'A';` | `%c` | `%c` | Stores a single character (1 byte). |
| **`<stdio.h>`** | **String (Array)**| `char str[20] = "Hello";`| `%s` | `%s` | Stops reading input at the **first space**! |
| **`<stdio.h>`** | **String (Pointer)**| `char *str = "Hello";` | `%s` | *Do not use* | Pointing to a read-only literal. **Do not use `scanf` on this** without allocating memory first! |
| **`<inttypes.h>`**| `int32_t` | `int32_t num = 100;` | `%" PRId32 "` | `%" SCNd32 "` | Fixed 32-bit signed. |
| **`<inttypes.h>`**| `uint32_t` | `uint32_t num = 100U;` | `%" PRIu32 "`<br>`%" PRIX32 "` (Hex) | `%" SCNu32 "`<br>`%" SCNx32 "` (Hex) | Fixed 32-bit unsigned. |
| **`<inttypes.h>`**| `int64_t` | `int64_t num = 100;` | `%" PRId64 "` | `%" SCNd64 "` | Fixed 64-bit signed. |
| **`<inttypes.h>`**| `uint64_t` | `uint64_t num = 100U;` | `%" PRIu64 "`<br>`%" PRIX64 "` (Hex) | `%" SCNu64 "`<br>`%" SCNx64 "` (Hex) | Fixed 64-bit unsigned. |

### ⚠️ Crucial Rules for Standard I/O Input
1. **The `&` (Address-of) Operator in `scanf`**: When using `scanf`, you must pass the **memory address** of the variable using `&` so `scanf` knows where to write the parsed data.
   - **Numbers/Chars**: `scanf("%d", &num);` (Needs `&`)
   - **Strings**: `scanf("%s", str);` (**No `&` needed!** An array's name already decays to its base memory address).
2. **The String Space Trap**: If you use `scanf("%s", str);` and type `"Net Chunk"`, your variable will only hold `"Net"`. `scanf` thinks a space, tab, or newline means "end of input". To read a whole line with spaces, use `fgets` instead.
3. **Double Input Difference**: Float input uses `%f`, but Double input *must* use `%lf` in `scanf` (whereas both can use `%f` or `%lf` in `printf`).

---

## Deep-Dive Reference
For exhaustive analysis on formatting specifier configurations and fixed-width register maps:
- [Format Specifier Anatomy](./io/anatomy.md) | [Fixed-Width Formatting](./io/fixed-width-specifiers.md)

# The Logic Bridge
// Logic: Preprocessor formatting strings compile down to sequence parameters. If standard types mismatches register widths, `printf` will parse arbitrary adjacent registers, leading to undefined system stack values.
