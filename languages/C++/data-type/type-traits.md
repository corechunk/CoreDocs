# 🔴 Standard: Type Traits [SYSTEMS]

## Definition
Querying type properties at compile-time.

## 1. Legacy Way (C++11 / C++17)
```cpp
std::is_floating_point<T>::value
```

## 2. Modern Way (C23)
```cpp
std::is_floating_point_v<T>
```

# The Logic Bridge
// Logic: Type traits are template structs that provide information about types, used by the compiler to choose different logic paths during template instantiation.
