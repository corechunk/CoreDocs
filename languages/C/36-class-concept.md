# 🟢 Standard: Class Concept [CORE - Hub]

## Definition (The Gateway to Object-Oriented Programming)
C does not have a native `class` keyword. The "Class Concept" is a mental model where **State** (Struct) and **Behavior** (Functions) are joined. This is the starting point for simulating OOP in a procedural language.

## Deep-Dive Reference
For complex hierarchies and simulated pillars:
- [Advanced OOP](./oop/37-advanced-oop.md)

---

## 1. Standard Pattern: Method Simulation
Simulating a method by creating a function that takes a pointer to the "instance" (the `self` behavior).

```c
#include <stdio.h>

typedef struct {
    int score;
} Player;

// Simulated Method: Functions that operate on the specific type
void Player_AddScore(Player* p, int amount) {
    if (p != NULL) p->score += amount;
}

int main() {
    Player p1 = {0};
    Player_AddScore(&p1, 50); // Explicit "this" pointer passing
    
    printf("Score: %d\n", p1.score); // Output: Score: 50
    return 0;
}
```

## 2. Modern C23 Pattern
Using `nullptr` and `auto` for safer, cleaner "object" management.

```c
#include <stdio.h>

typedef struct {
    int health;
} Entity;

void Entity_Heal(Entity* e) {
    if (e != nullptr) e->health = 100;
}

int main() {
    auto e1 = (Entity){50};
    Entity_Heal(&e1);
    
    printf("Health: %d\n", e1.health); // Output: Health: 100
    return 0;
}
```

# The Logic Bridge
// Logic: In high-level OOP languages, the compiler automatically passes the `this` or `self` pointer as a hidden first argument. In C, we do this manually to simulate encapsulation and behavior-binding.
