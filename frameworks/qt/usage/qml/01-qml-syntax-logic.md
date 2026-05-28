# 💎 Qt QML: Syntax & Logic (Official)

QML is a declarative, reactive language designed for fluid UI design with a JSON-like syntax.

---

## 1. 🏗️ The Declarative Tree
UIs are built as a hierarchy of **Items**.

```qml
import QtQuick
import QtQuick.Controls

ApplicationWindow {
    visible: true
    width: 640; height: 480
    
    Rectangle {
        id: mainRect
        anchors.fill: parent
        color: "steelblue"
        
        Text {
            anchors.centerIn: parent
            text: "Official QML Logic"
            font.pixelSize: 24
        }
    }
}
```
## 2. 📦 The Official Type Matrix
| Category | Types |
| :--- | :--- |
| **Value (Primitives)** | `bool`, `double`, `int`, `string`, `url`, `enumeration` |
| **Geometry** | `point`, `size`, `rect`, `matrix4x4`, `quaternion`, `vector2d/3d/4d` |
| **Visual** | `color`, `font`, `palette` |
| **Logic** | `var` (Generic), `list<T>`, `QtObject`, `Component`, `Binding`, `Timer` |

## ⚡ Property Binding Mechanics (The Heart of QML)
...

Bindings create a dynamic relationship between properties.
- **Rule:** If `A` is bound to `B`, whenever `B` changes, `A` is automatically updated.
- **Breaking Bindings:** If you manually assign a static value to a bound property (e.g., `mainRect.width = 100`), the binding is **deleted**.

## 3. ⌨️ Signal Handlers
Every property `foo` automatically generates a signal handler `onFooChanged`.
- **Interaction:** `MouseArea { onClicked: { ... } }`
- **Keys:** `Item { focus: true; Keys.onPressed: (event) => { ... } }`

## 4. 🏁 The Logic Bridge
- **Engine:** `QQmlEngine` parses the QML and manages the objects.
- **Deferred Evaluation:** Qt 6 often waits to re-calculate a binding until the value is actually needed, optimizing performance.

---

[➔ Official Guide: QML Types](https://doc.qt.io/qt-6/qmltypes.html)
[➔ Back to Roadmap](../../core/00-roadmap.md)
