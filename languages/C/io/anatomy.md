# 🟢 Standard: Format Specifier Anatomy [CORE]

## Definition
The format specifier is a structured expression matching the syntax `%[flags][width][.precision][length]specifier`. It instructs the standard I/O engine how to parse, pad, align, and cast binary values to text formats.

## 1. Legacy Way (C99 / C11)
C99 defined the syntax parameters for standard streams using length modifiers to map hardware sizes (like `%ld` or `%lld` for integer registers) manually.

```c
#include <stdio.h>

int main() {
    long value = 12345L;
    
    // Legacy: Specifying padding and left-alignment explicitly
    // %-10ld: Left-aligned (-), minimum width of 10 characters, long integer type
    printf("Value: |%-10ld|\n", value); // Output: Value: |12345     |
    return 0;
}
```

## 2. Modern Way (C23)
C23 expands formatting options to support native binary representation outputs natively using the `%b` or `%B` specifiers, reducing the need for manual bit-extraction loops.

```c
#include <stdio.h>

int main() {
    unsigned int flags = 0b1011;
    
    // C23 Native binary specifier output
    #if defined(__STDC_VERSION__) && __STDC_VERSION__ >= 202311L
    printf("Binary: %b\n", flags);    // Output: Binary: 1011
    printf("Binary pad: %08b\n", flags); // Output: Binary pad: 00001011
    #endif
    return 0;
}
```

## Deep-Dive Reference
The parsing recipe contains five distinct parts:
$$\% \ [\text{flags}] \ [\text{width}] \ [.\text{precision}] \ [\text{length}] \ \text{specifier}$$

* **`%`**: The trigger symbol telling the parser to treat the following sequence as formatting layout instructions.
* **`flags`**: Modifies the output alignment:
  - `-`: Left-align fields (default is right-align).
  - `+`: Forces a positive sign character to print.
  - `0`: Left-pads numbers with leading zeros instead of spaces.
* **`width`**: The minimum number of characters to write.
* **`precision`**: Controls decimal precision or string limit:
  - For floats: number of decimal digits (e.g., `%.2f`).
  - For strings: maximum characters printed (e.g., `%.4s`).
* **`length`**: Size modifier (e.g., `h` for short, `l` for long, `ll` for long long).
* **`specifier`**: Mandatory type instruction:
  - `d` / `i`: Signed Decimal.
  - `u`: Unsigned Decimal.
  - `x` / `X`: Hexadecimal.
  - `f`: Floating point.
  - `c`: Character.
  - `s`: String.
  - `p`: Memory address pointer.

# The Logic Bridge
// Logic: The compiler does not verify format specifier types at run-time. It pushes argument parameters to the stack or register registers; `printf` reads those addresses sequentially based on format flags, which can trigger undefined behaviors if lengths do not match.
