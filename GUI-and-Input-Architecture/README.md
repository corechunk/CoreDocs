# 🎨 GUI & Input Architecture: Visual Systems Programming

Welcome to the **GUI & Input Architecture** hub. This guide serves as a comprehensive system-level introduction to visual programming, mapping how software draws pixels to screens and intercepts user interaction.

---

### 🚦 Prerequisites: At Which Level Should You Start GUI?

Visual programming should only be attempted **after mastering Concurrency & Parallelism**. 

A GUI application relies on a single **Main UI Thread** running a synchronous execution loop (the Event Loop). If a long-running task (e.g., downloading a file, sorting a large dataset) is triggered directly on this thread, the UI freezes, stops responding to input, and crashes. Learning how to spawn background worker threads and coordinate state changes asynchronously is the fundamental prerequisite of visual programming.

```text
               +----------------------------------------+
               |         Main UI Thread (Event Loop)     |
               +----------------------------------------+
                /        |                        \
  [Mouse Click]       [Draw Frame]          [Spawn Background Worker]
                                                       |
                                                       v
                                            +---------------------+
                                            |  Worker Thread      |
                                            |  (Heavy computation)|
                                            +---------------------+
```

---

### 📊 The Four Tiers of Visual Programming

Visual programming interfaces are structured into four levels of abstraction, ascending from OS widgets to direct GPU hardware memory manipulation:

```text
High Abstraction
  |   [ Tier 1: Widget Toolkits ]  <-- Declarative UI blocks (GTK, Win32, Android XML)
  |   [ Tier 2: 2D Canvas Engine]  <-- Manual paint loop & game canvases (SDL2, SFML)
  |   [ Tier 3: Hybrid Framework]  <-- Declarative UI + graphics buffer (Qt/QML Quick)
  v   [ Tier 4: Barebone Graphics] <-- Directly programming shaders & pipelines (OpenGL, Vulkan)
Low Abstraction
```

---

### 🗺️ Redirection Directory

*   📂 [**`prerequisites-concurrency.md`**](./prerequisites-concurrency.md) — The Main UI thread, event loops, and communicating between GUI and background threads.
*   📂 [**`widget-toolkits/`**](./widget-toolkits/README.md) — **Tier 1**: Declarative layouts, widget hierarchies, event loops, and cross-language toolkit equivalents.
*   📂 [**`canvas-and-2d-engines/`**](./canvas-and-2d-engines/README.md) — **Tier 2**: The draw loop, double-buffering, frame rate control, and 2D library equivalents.
*   📂 [**`hybrid-qt-engine/`**](./hybrid-qt-engine/README.md) — **Tier 3**: Hybrid architecture, scene graphs, Qt/QML Quick, and cross-platform web-view mappings.
*   📂 [**`barebone-graphics-apis/`**](./barebone-graphics-apis/README.md) — **Tier 4**: GPUs, vertex buffers, pipelines, shaders, OpenGL, Vulkan, and hardware interfaces.
*   📂 [**`window-decorations.md`**](./window-decorations.md) — Borderless windows, client-side decorations (CSD), and custom window handlers.
*   📂 [**`input-unification.md`**](./input-unification.md) — Mapping multi-touch, mouse, and absolute tablet inputs to a unified coordinate structure.
