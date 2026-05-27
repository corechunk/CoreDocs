# 🔴 Standard: Concepts [SYSTEMS]

## Definition
Constraints on template parameters (C++20).

## 1. Legacy Way (C++11 / C++17)
Using SFINAE (Substitution Failure Is Not An Error).
```cpp
template <typename T, typename = std::enable_if_t<std::is_integral<T>::value>>
void check(T v) {}
```

## 2. Modern Way (C23)
Using `requires`.
```cpp
void check(std::integral auto v) {}
```

# The Logic Bridge
// Logic: Concepts provide a formal way to specify requirements for types, leading to much clearer compiler error messages than raw templates.
