# 🖼️ Window Decorations: Borderless Canvas Strategy

When drawing custom interfaces (such as application rices or launchers), standard OS window frames (title bars, minimize/maximize buttons, resize borders) must be bypassed to create a custom canvas.

---

### 1. Client-Side Decoration (CSD) vs. Server-Side Decoration (SSD)

*   **Server-Side Decoration (SSD)**: The window manager (e.g. KWin, openbox) draws the title bar and frames around the window.
*   **Client-Side Decoration (CSD)**: The application itself handles drawing its boundaries and window control buttons.

---

### 2. Borderless Canvas Strategy

By disabling window decorations, we request the window manager route the canvas directly to the screen layout without drawing frames.

```text
Standard Window (SSD):                   Borderless Window (Custom Canvas):
+----------------------------+           +----------------------------+
| [Title Bar]      [_] [X]   |           | [ Custom UI Elements       |
+----------------------------+           |   drawn directly to edge   |
|                            |           |   of window ]              |
|  Active Drawing Canvas     |           |                            |
|                            |           |                            |
+----------------------------+           +----------------------------+
```

---

### 💻 Borderless Setup in C (GLFW)

```c
#include <GLFW/glfw3.h>

int main() {
    glfwInit();

    // 1. Tell GLFW to disable window decoration before creation
    glfwWindowHint(GLFW_DECORATED, GLFW_FALSE);

    // 2. Create the window - it will render as a flat borderless panel
    GLFWwindow* window = glfwCreateWindow(640, 480, "Borderless Panel", NULL, NULL);

    while (!glfwWindowShouldClose(window)) {
        // Render custom buttons/frames here
        glfwSwapBuffers(window);
        glfwPollEvents();
    }

    glfwTerminate();
    return 0;
}
```
