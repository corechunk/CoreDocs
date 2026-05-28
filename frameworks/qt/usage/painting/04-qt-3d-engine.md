# 🧊 Qt Painting: The 3D Engine (Official)

Qt 3D is a highly decoupled **Entity Component System (ECS)** architecture designed for simulation and high-performance rendering.

---

## 1. 🏗️ The ECS Pillars
- **Entities (`QEntity`)**: The "Identity." A shell that holds components.
- **Components (`QComponent`)**: The "Data/Behavior." (e.g., `QMesh`, `QTransform`, `QMaterial`).
- **Aspects (`QAbstractAspect`)**: The "Systems." Run on separate threads to process specific component sets (Renderer, Input, Animation).

## 2. 🔬 Frontend vs. Backend Architecture
Qt 3D uses a **Thread-Split** model:
- **Main Thread (Frontend)**: Where you create and interact with `QEntity` objects.
- **Aspect Threads (Backend)**: Where the actual work (Drawing, Physics) happens.
- **Arbiter**: The system that synchronizes property changes from the frontend to the high-performance backend automatically.

## 3. 📝 3D Logic Bridge
- **RHI Integration**: In Qt 6, the engine uses the **Rendering Hardware Interface**, allowing it to target Vulkan, Metal, and Direct3D without changing your C++ code.
- **Scene Graph**: Unlike `QPainter`, you don't "Draw"; you "Define the Scene." The Aspects then traverse the tree and execute the rendering loop at maximum GPU efficiency.

---

[➔ Official Guide: Qt 3D](https://doc.qt.io/qt-6/qt3d-index.html)
[➔ Back to Roadmap](../core/00-roadmap.md)
