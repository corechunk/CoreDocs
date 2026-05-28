# 🎬 Qt QML: Quick Animations (Official)

High-performance GPU motion handled by the **Qt Quick Scene Graph**.

---

## 1. 🏗️ State & Transition Logic
States define "How things look"; Transitions define "How they move between looks."

```qml
Item {
    id: root
    states: [
        State { name: "active"; PropertyChanges { target: rect; scale: 1.5 } },
        State { name: "idle"; PropertyChanges { target: rect; scale: 1.0 } }
    ]
    
    transitions: Transition {
        from: "*"; to: "*" // Match all state changes
        NumberAnimation { properties: "scale"; duration: 250; easing.type: Easing.OutBack }
    }
}
```

## 2. 🛠️ Animation Types Matrix
| Type | Usage |
| :--- | :--- |
| **`PropertyAnimation`** | Animate any QML property. |
| **`NumberAnimation`** | Optimized for real/int values. |
| **`ColorAnimation`** | Smoothly interpolate between hex or named colors. |
| **`RotationAnimation`** | Optimized for 0-360 degree wraps. |
| **`SequentialAnimation`** | Run a list of animations in order. |
| **`ParallelAnimation`** | Run multiple animations at the same time. |

## 3. 🏁 The Logic Bridge
- **Scene Graph:** Animations are offloaded to a dedicated render thread. Even if your C++ logic is heavy, the UI animations stay smooth at 60+ FPS.
- **Easing Curves:** Qt 6 provides over 40 math-based curves (Linear, InQuad, OutElastic) to control acceleration.

---

[➔ Back to Roadmap](../../core/00-roadmap.md)
