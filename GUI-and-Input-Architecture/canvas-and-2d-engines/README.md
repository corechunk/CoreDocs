# 🖼️ Tier 2: 2D Canvas & Render Loops

In Tier 2, you bypass pre-built OS widgets. You manage a raw pixel surface, drawing lines, boxes, and images manually using a continuous loop called the **Render Loop**.

---

### 1. Double Buffering

To prevent screen tearing and flickering, 2D canvases use **Double Buffering**. Instead of drawing directly to the screen memory block:
1.  All draw calls are executed onto an offscreen memory buffer (the **Back Buffer**).
2.  Once all assets are drawn, we perform a **Swap** (or **Flip**), copy the back buffer to the active screen memory block (the **Front Buffer**), and clear the back buffer for the next frame.

```text
+-------------------+                      +-------------------+
|    Back Buffer    |                      |   Front Buffer    |
| (Active drawing)  |                      |  (Output display) |
| [Draw lines/img]  | === Swap / Flip ===> |  [Shown to User]  |
+-------------------+                      +-------------------+
```

---

### 2. Delta Time ($\Delta t$)

If you run a game loop as fast as the CPU can compute, objects move faster on fast PCs and slower on slow PCs. To make movement constant, you calculate the time taken to render the previous frame (**Delta Time**) and multiply all motion values by it.

$$\text{Position} = \text{Position} + (\text{Velocity} \times \Delta t)$$

---

### 💻 2D Canvas Drawing in C (Raylib)

The following C program opens a window, runs a 60 FPS double-buffered render loop, and updates the coordinates of a moving circle:

```c
#include "raylib.h"

int main() {
    const int screenWidth = 640;
    const int screenHeight = 480;

    InitWindow(screenWidth, screenHeight, "Raylib 2D Canvas");
    SetTargetFPS(60); // Limits loop execution to 60 iterations/second

    float ballX = 100.0f;
    float ballSpeed = 200.0f; // Pixels per second

    while (!WindowShouldClose()) {
        // 1. Update State using Delta Time
        float dt = GetFrameTime();
        ballX += ballSpeed * dt;
        if (ballX > screenWidth || ballX < 0) ballSpeed = -ballSpeed; // Bounce

        // 2. Draw Frame onto Back Buffer
        BeginDrawing();
        ClearBackground(RAYWHITE);
        DrawCircle((int)ballX, screenHeight / 2, 20, MAROON);
        
        // 3. Flip Buffers (Double-buffering occurs internally here)
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```
