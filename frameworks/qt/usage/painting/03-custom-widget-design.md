# 🧱 Qt Painting: Custom Widget Design (Official)

Subclassing `QWidget` to build proprietary, high-signal UI components from scratch.

---

## 1. 🏗️ The Implementation Checklist
To create a "Real" custom widget, you must fulfill these architectural requirements:

1.  **Inherit:** Must derive from `QWidget`.
2.  **`Q_OBJECT`**: Must include the macro for property and signal support.
3.  **`sizeHint()`**: Must return the ideal size so layouts can position it correctly.
4.  **`paintEvent()`**: Must perform all visual rendering via `QPainter`.
5.  **Event Overrides**: Handle interaction via `mousePressEvent`, `keyPressEvent`, etc.

## 2. 📝 Property Integration
Use `Q_PROPERTY` to make your widget's state visible to the Meta-Object system and QML.

```cpp
class MyDial : public QWidget {
    Q_OBJECT
    Q_PROPERTY(int value READ value WRITE setValue NOTIFY valueChanged)
public:
    void setValue(int v) {
        if (m_value == v) return;
        m_value = v;
        update(); // Trigger repaint
        emit valueChanged(v);
    }
    // ...
};
```

## 3. 🏁 The Logic Bridge
- **Dirty Flag Pattern:** Don't calculate expensive values inside `paintEvent`. Calculate them when properties change, and use `update()` to redraw using the cached results.
- **Mouse Tracking:** By default, widgets only receive mouse move events when a button is pressed. Call `setMouseTracking(true)` to receive them whenever the cursor is over the widget.

---

[➔ Back to Roadmap](../core/00-roadmap.md)
