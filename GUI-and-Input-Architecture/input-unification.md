# 🎛️ Input Unification

Different hardware platforms register user input differently: desktop platforms track relative mouse movements, while mobile screens track absolute multi-touch coordinates. To write portable code, you must normalize these events into a single, unified input structure.

---

### 1. Coordinate Normalization

A touch screen reports absolute screen coordinates (e.g. $0$ to $2400$ pixels). A mouse reports window coordinates (e.g. $0$ to $640$). By dividing coordinates by window dimensions, we normalize them to a range between `0.0` (top-left) and `1.0` (bottom-right).

$$\text{Normalized } X = \frac{\text{Pixel } X}{\text{Screen Width}}$$

---

### 💻 Input Unification in C

```c
#include <stdio.h>

// Unified event data structure
typedef struct {
    enum { INPUT_MOUSE, INPUT_TOUCH } type;
    int action; // 0 = Press, 1 = Release, 2 = Move
    float norm_x; // Normalized coordinate (0.0 to 1.0)
    float norm_y; // Normalized coordinate (0.0 to 1.0)
} unified_input_t;

// Process events uniformly regardless of hardware origin
void handle_input_event(unified_input_t *event) {
    printf("Input received! Type: %s, Action: %d at [%f, %f]\n",
           (event->type == INPUT_MOUSE) ? "MOUSE" : "TOUCH",
           event->action,
           event->norm_x,
           event->norm_y);

    // Click boundary check
    if (event->norm_x >= 0.8f && event->norm_y <= 0.2f) {
        printf("Interactive Button Clicked!\n");
    }
}
```
