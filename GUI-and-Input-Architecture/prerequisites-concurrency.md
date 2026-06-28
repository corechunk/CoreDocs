# 🚦 Prerequisites: Concurrency & The UI Thread

Before writing any GUI code, you must understand how operating systems process graphics updates and why multithreading is mandatory.

---

### 1. The Main UI Thread & Event Loop

All graphical applications run on a single thread called the **Main Thread** or **UI Thread**. This thread runs a continuous loop (the **Event Loop**) that does three things in order:
1.  Read input events (keyboard clicks, mouse movements, touch contacts).
2.  Update application logical state.
3.  Request the system redraw the screen canvas.

```text
+-------------------------------------------------------------+
|                     The Event Loop (UI Thread)              |
|                                                             |
|   +------------+        +-------------+        +--------+   |
|   | Read Input | =====> | Update State| =====> | Redraw |   |
|   +------------+        +-------------+        +--------+   |
|         ^                                           |       |
|         +===========================================+       |
+-------------------------------------------------------------+
```

If any task takes longer than a few milliseconds (e.g. more than 16ms, which is the frame budget for 60 FPS), the event loop is blocked. The application stops reading input, the screen stops redrawing, and the OS flags the application as "Not Responding".

---

### 2. Multi-Threaded GUI Architecture

To prevent blocking the event loop:
*   **Main UI Thread**: Only handles UI updates, layout changes, and input events.
*   **Worker Threads**: Run heavy calculations, database queries, and network operations.

#### Rules of Thread-Safe GUI
1.  **Do not access UI elements from worker threads**. Visual elements (widgets, frames) are not thread-safe.
2.  **Thread Communication**: Worker threads must send results back to the Main UI thread using thread-safe channels (e.g., event queues, handlers, or thread signals) to request UI redraws.
