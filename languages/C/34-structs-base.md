# 🟢 Standard: Structs [CORE - Hub]

## Definition (The Gateway to Procedural Programming)
A **Struct** is a custom data type that groups related variables (fields) into a single contiguous memory block. It is the primary tool for data modeling in Procedural Programming, allowing you to represent complex entities like "Player" or "Config" without using a class.

## Deep-Dive Reference
For modular procedural architecture:
- [Procedural Mechanisms](./procedural/35-procedural-mechanisms.md)

---

## 1. Legacy Way (C99 / C11 / C17)
Standard definition and dot-operator access.

```c
#include <stdio.h>

struct Data {
    int id;
    int value;
};

int main() {
    struct Data d1 = {1, 10}; // Positional init
    d1.value = 20;           // Dot-operator access
    
    printf("ID: %d, Val: %d\n", d1.id, d1.value); // Output: ID: 1, Val: 20
    return 0;
}
```

## 2. Modern Way (C23)
Using **Designated Initializers** and **Anonymous Structs** for cleaner procedural logic.

```c
#include <stdio.h>

int main() {
    // Designated Initializers (Standard in C23)
    struct { int x; int y; } point = { .x = 10, .y = 5 };
    
    printf("X: %d, Y: %d\n", point.x, point.y); // Output: X: 10, Y: 5
    return 0;
}
```

# The Logic Bridge
// Logic: A struct is "Plain Old Data." Accessing a member with `.` simply adds a pre-calculated offset to the struct's base memory address. This zero-overhead grouping is why structs are the foundation of systems-level procedural code.
