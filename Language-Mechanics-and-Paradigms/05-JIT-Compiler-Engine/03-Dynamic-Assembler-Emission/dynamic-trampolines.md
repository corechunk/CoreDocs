# 🌉 Dynamic C-to-JIT Trampolines & Branch Pointers

## 1. Dynamic Trampolines
To invoke JIT-compiled RAM code from a host C/C++ engine, the system constructs dynamic trampoline function pointers cast to host calling convention signatures:

```cpp
typedef int (*JITFunc)(int, int);
JITFunc compiled_code = (JITFunc)code_ram_buffer;
int result = compiled_code(10, 20);
```

## 2. Register Preserving Context Bridges
Trampolines manage saving and restoring non-volatile CPU register files before branching execution directly into dynamic machine code buffer addresses.
