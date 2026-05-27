# Multiple Inheritance & Mixins (PRO)

Definition: A class deriving from more than one base class. Mixins are small classes used to add specific functionality.

## 1. Legacy Way (C++11 / C++17)
Standard multiple inheritance.

```cpp
class Logger {
public:
    void log(const char* msg) { /* ... */ }
};

class Data { };

class LoggedData : public Data, public Logger { };
```

## 2. Modern Way (C++23)
Using **CRTP** (Curiously Recurring Template Pattern) for "Static Mixins".

```cpp
template <typename T>
class JsonMixin {
public:
    void to_json() { /* logic using static_cast<T*>(this) */ }
};

class User : public JsonMixin<User> { };
```

# The Logic Bridge
// Logic: Multiple inheritance in C++ can lead to the "Diamond Problem," which is resolved using **virtual inheritance**. CRTP provides a way to add functionality without the overhead of virtual functions.
