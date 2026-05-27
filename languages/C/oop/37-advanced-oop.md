# 🔵 Standard: Advanced OOP [PRO]

## Definition
Advanced OOP in C involves **Polymorphism** and **Encapsulation**. Polymorphism is achieved via **VTables** (Virtual Function Tables)—an array of function pointers that allows different "types" to share the same interface.

## 1. Legacy Way (C99 / C11 / C17)
Implementing a basic VTable for a "Shape" interface.

```c
#include <stdio.h>

struct Shape; // Forward declaration

// The Interface (VTable)
typedef struct {
    void (*draw)(struct Shape*);
} ShapeVTable;

// The "Base Class"
typedef struct Shape {
    ShapeVTable* vtable;
} Shape;

// A "Subclass" (Circle)
void circle_draw(Shape* s) { printf("Circle\n"); }
ShapeVTable circle_vt = { circle_draw };

int main() {
    Shape circle = { &circle_vt };
    
    // Virtual Call
    circle.vtable->draw(&circle); // Output: Circle
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the VTable task with C23 native keywords for safety and clarity.

```c
#include <stdio.h> // Required for printf

struct Shape;

typedef struct {
    void (*draw)(struct Shape*);
} ShapeVTable;

typedef struct Shape {
    ShapeVTable* vtable;
} Shape;

// A "Subclass" (Modern implementation)
void circle_draw(Shape* s) { printf("Circle\n"); }
static ShapeVTable circle_vt = { .draw = circle_draw };

int main() {
    // nullptr: Native keyword for safety
    auto circle = (Shape){ .vtable = &circle_vt };
    
    if (circle.vtable != nullptr) {
        circle.vtable->draw(&circle); // Output: Circle
    }
    return 0;
}
```

# The Logic Bridge
// Logic: Polymorphism in C is manually implemented by storing pointers to functions in the data itself. When you call a "Virtual Function," the CPU looks up the address in the VTable and jumps to the implementation specific to that instance.
