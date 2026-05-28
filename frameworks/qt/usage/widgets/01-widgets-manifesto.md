# 🎨 Qt Widgets: The Manifesto (Official)

The foundational class for all UI elements. `QWidget` is the atom of the Qt user interface.

---

## 1. 🧱 The Core Atom: QWidget
Every widget is a `QPaintDevice` and a `QObject`.

### Essential Protected Event Handlers
To build professional tools, you MUST reimplement these virtual functions:

| Event | Function Signature | Purpose |
| :--- | :--- | :--- |
| **Paint** | `paintEvent(QPaintEvent*)` | **The entry point for all custom drawing.** |
| **Resize** | `resizeEvent(QResizeEvent*)` | Handle geometry changes (e.g., re-calculating layouts). |
| **Mouse** | `mousePressEvent(QMouseEvent*)` | Capture clicks. Use `event->button()` to distinguish. |
| **Keys** | `keyPressEvent(QKeyEvent*)` | Handle shortcuts. Use `event->key()` (e.g., `Qt::Key_Enter`). |
| **Focus** | `enterEvent(QEnterEvent*)` | Triggered when the cursor enters the widget area. |

## 2. 🖱️ Top-Level Classes
- **`QMainWindow`**: Built-in support for `QStatusBar`, `QToolBar`, and `QMenuBar`.
- **`QDialog`**: Specialized for modal feedback; includes `exec()` for local event loops.

## 3. 🏁 The Logic Bridge
- **`update()` vs `repaint()`**: Never call `repaint()` directly unless you are building a real-time monitor. `update()` is an asynchronous request that lets Qt optimize multiple drawing calls into one.
- **`sizeHint()`**: Layouts use this as the "Target Size." If your widget is a custom drawing, you must override this to tell the layout how big you want to be.

---

[➔ Official API: QWidget](https://doc.qt.io/qt-6/qwidget.html)
[➔ Back to Roadmap](../core/00-roadmap.md)
