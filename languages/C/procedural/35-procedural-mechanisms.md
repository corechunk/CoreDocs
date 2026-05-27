# 🔵 Standard: Procedural Mechanisms [PRO - Hub]

## Definition
This milestone covers advanced procedural patterns used to simulate complex architectural behavior, such as **Manual Methods** (using the `this` pointer) and **Opaque Pointers** for encapsulation.

## Deep-Dive Reference
For linkage, scoping, and modularity:
- [Static & Linkage](static-linkage.md)
- [Header Architecture](headers.md)

---

## 1. Legacy Way (C99 / C11 / C17)
Standard procedural methods where data is passed explicitly to functions.

```c
#include <stdio.h>

struct Player {
    int health;
};

// Manual Method: Accepts pointer to "self"
void heal(struct Player* p, int amount) {
    p->health += amount;
}

int main() {
    struct Player p1 = {50};
    heal(&p1, 20);
    
    printf("Health: %d\n", p1.health); // Output: Health: 70
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same behavior, but using `nullptr` and C23's better handling of function attributes.

```c
#include <stdio.h> // Required for printf

struct Player {
    int health;
};

// Modern Pro Path: Explicitly handle null pointers
void heal(struct Player* p, int amount) {
    if (p != nullptr) {
        p->health += amount;
    }
}

int main() {
    struct Player p1 = {50};
    heal(&p1, 20);
    
    printf("Health: %d\n", p1.health); // Output: Health: 70
    return 0;
}
```

# The Logic Bridge
// Logic: Manual methods simulate "Object-Oriented" behavior by explicitly passing the object's address as the first argument, allowing the function to operate on that specific instance's memory.
