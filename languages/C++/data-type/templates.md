# 🔴 Standard: Templates [SYSTEMS]

## Definition
The core of C++ meta-programming. Templates allow for code that works with any type.

## 1. Legacy Way (C++11 / C++17)
```cpp
template <typename T>
T add(T a, T b) { return a + b; }
```

## 2. Modern Way (C23)
```cpp
auto add(auto a, auto b) { return a + b; }
```

# The Logic Bridge
// Logic: Templates are instantiated at compile-time. The compiler replaces `T` with the actual type and generates a unique function for it.
