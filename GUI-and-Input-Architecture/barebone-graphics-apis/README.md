# ⚡ Tier 4: Barebone Graphics APIs

Barebone graphics APIs represent the lowest level of graphics software design. You bypass window managers, canvas pipelines, and toolkits to write programs that run directly on the GPU shader cores.

---

### 1. The GPU Graphics Pipeline

Rendering pixels using hardware requires sending data through the **Graphics Pipeline**:

```text
  [ Vertex Buffers ]  <-- Raw 3D coordinates in RAM
         |
         v
  [ Vertex Shader ]   <-- Custom program translating coordinates to screen spaces
         |
         v
  [ Rasterization ]   <-- Translates vector lines/triangles to flat pixel grids
         |
         v
  [ Fragment Shader ] <-- Custom program calculating the color of each pixel
         |
         v
  [ Framebuffer ]     <-- Output image sent to display hardware
```

---

### 2. OpenGL Context vs. Vulkan Explicit Control

*   **OpenGL**: A state-machine interface. Easy to set up, but has high driver overhead because the driver guesses how to manage memory under the hood.
*   **Vulkan**: An explicit, low-level API. You must manually allocate GPU memory, manage thread synchronization queues, command buffers, and pipeline states.

---

### 💻 Barebone OpenGL Setup in C

The following program creates a context, loads a simple triangle into GPU memory, compiles shaders, and renders the frame:

```c
#include <GL/gl.h>
#include <GLFW/glfw3.h>

// Simple Vertex Shader source code
const char* vertexShaderSource = "#version 330 core\n"
    "layout (location = 0) in vec3 aPos;\n"
    "void main() {\n"
    "   gl_Position = vec4(aPos.x, aPos.y, aPos.z, 1.0);\n"
    "}\0";

// Simple Fragment Shader source code
const char* fragmentShaderSource = "#version 330 core\n"
    "out vec4 FragColor;\n"
    "void main() {\n"
    "   FragColor = vec4(1.0f, 0.5f, 0.2f, 1.0f); // Output Orange color\n"
    "}\0";

int main() {
    glfwInit();
    GLFWwindow* window = glfwCreateWindow(640, 480, "Raw OpenGL", NULL, NULL);
    glfwMakeContextCurrent(window);

    // 1. Define triangle vertices (X, Y, Z coordinates)
    float vertices[] = {
        -0.5f, -0.5f, 0.0f,
         0.5f, -0.5f, 0.0f,
         0.0f,  0.5f, 0.0f
    };

    // 2. Allocate Vertex Buffer on GPU memory
    unsigned int VBO, VAO;
    glGenVertexArrays(1, &VAO);
    glGenBuffers(1, &VBO);
    
    glBindVertexArray(VAO);
    glBindBuffer(GL_ARRAY_BUFFER, VBO);
    glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);

    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
    glEnableVertexAttribArray(0);

    // 3. Render Loop
    while (!glfwWindowShouldClose(window)) {
        glClear(GL_COLOR_BUFFER_BIT);

        // Draw the allocated vertex buffers using compiled shaders
        glBindVertexArray(VAO);
        glDrawArrays(GL_TRIANGLES, 0, 3);

        glfwSwapBuffers(window);
        glfwPollEvents();
    }

    glfwTerminate();
    return 0;
}
```
