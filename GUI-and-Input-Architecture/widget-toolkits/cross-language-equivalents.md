# 🧱 Widget Toolkits: Cross-Language Equivalents

This guide maps widget toolkit options across 7 mainstream languages for high-level UI application development.

---

### 📊 Language & Library Mapping Table

| Language | Primary Widget Toolkit | Style Paradigm | System Native or Custom Drawn |
| :--- | :--- | :--- | :--- |
| **C** | GTK / IUP | Imperative | Native OS / Custom |
| **C++** | wxWidgets / FLTK | Imperative | Native OS (wxWidgets) |
| **Rust** | Slint / egui | Declarative / Immediate | Custom Canvas |
| **Python** | Tkinter / PyQt / PySide | Imperative | Native (Tkinter) / Custom |
| **Java** | JavaFX / Swing | Object-Oriented / CSS | Custom Rendered |
| **Kotlin** | Compose Multiplatform | Declarative | Custom (Skia Canvas) |
| **JS / TS** | Web DOM (HTML/CSS) | Declarative (React / Vue) | Browser Frame Buffer |

---

### 🧠 Overview of equivalent framework options

1.  **C (GTK)**: Relies on GObject (an object-oriented C system) to construct widgets using hierarchies of pointers and callbacks.
2.  **C++ (wxWidgets)**: Wraps native Windows (Win32), macOS (Cocoa), and Linux (GTK) window managers. Program layouts look identical to native operating system panels.
3.  **Rust (Slint / egui)**: Slint compiles custom declarative UI files (`.slint`) down to native machine code. `egui` uses immediate-mode rendering, recalculating the layout and redrawing every widget on every frame.
4.  **Python (PyQt/PySide)**: Python wrappers around the massive C++ Qt toolkit. Very powerful, supporting CSS-like stylesheets for widget formatting.
5.  **Java / Kotlin (JavaFX / Compose)**: Modern toolkits. Compose Multiplatform (Kotlin) uses declarative state bindings where the compiler redraws UI structures automatically in response to state variable modifications.
6.  **JS (Web DOM)**: Utilizes browsers as rendering canvases. UI layout is defined in HTML, styled in CSS, and manipulated via JavaScript DOM interfaces or libraries like React.
