# 🧬 Tier 3: Hybrid Engines (Qt & QML)

Hybrid engines separate user interface design (declarative scripting) from application business logic (compiled native code), using a **Scene Graph** to render layout structures on hardware GPU contexts.

---

### 1. The QML & C++ Separation Paradigm

In Qt Quick:
*   **QML (Declarative UI)**: A JSON-like language describing the visual hierarchy, animations, and layouts. It runs on a JavaScript engine for UI state handling.
*   **C++ (Backend Logic)**: Handles heavy computation, database connections, concurrency, and file access.

```text
  UI Frontend (QML)                           System Backend (C++)
+-----------------------+                    +---------------------+
| Window, Buttons, CSS  | -- signals/slots ->| C++ Controller      |
| JavaScript animation  | <-- state properties -| Thread pools, DBs   |
+-----------------------+                    +---------------------+
```

---

### 2. Scene Graph Rendering

Instead of rendering each widget individually as standard OS window nodes, Qt Quick structures QML layouts into a **Scene Graph** (a tree of visual nodes). The engine compiles this graph and sends it to the GPU as a single batch, achieving hardware-accelerated 60 FPS rendering.

---

### 💻 Hybrid Qt/QML Implementation in C++

#### Step 1: Write the Declarative UI (`main.qml`)
```qml
import QtQuick 2.15
import QtQuick.Controls 2.15

ApplicationWindow {
    visible: true
    width: 320
    height: 240
    title: "Qt Quick Engine"

    Column {
        anchors.centerIn: parent
        spacing: 20

        Text {
            id: labelText
            text: backend.countText
            font.pixelSize: 20
        }

        Button {
            text: "Increment"
            onClicked: backend.increment() // Invokes C++ method
        }
    }
}
```

#### Step 2: Write the C++ Backend Controller (`backend.h`)
```cpp
#pragma once
#include <QObject>
#include <QString>

class Backend : public QObject {
    Q_OBJECT
    // Expose property to QML engine
    Q_PROPERTY(QString countText READ countText NOTIFY countChanged)

public:
    explicit Backend(QObject *parent = nullptr) : QObject(parent), m_count(0) {}

    QString countText() const {
        return QString("Clicks: %1").arg(m_count);
    }

    // Invokable method from QML
    Q_INVOKABLE void increment() {
        m_count++;
        emit countChanged(); // Signals QML engine to redraw Text widget
    }

signals:
    void countChanged();

private:
    int m_count;
};
```
