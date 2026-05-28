# 💓 Qt Core: Event Loop & QObject Model (Official)

The foundation of object ownership, thread affinity, and the application heartbeat.

---

## 1. 🏗️ QObject Foundations
- **Identity:** `QObject` instances are unique. They are **Non-Copyable** (`Q_DISABLE_COPY`).
- **Memory Management:** Parent-child hierarchy.
    - `setParent(parent)`: Attaches child to a parent.
    - **Destruction:** When a parent is deleted, it recursively deletes all children.
    - **Recommendation:** Always create `QObject` instances on the **Heap** (`new`) unless they are short-lived stack objects.

## 2. 🌀 The Event Loop
```cpp
int main(int argc, char *argv[]) {
    QApplication a(argc, argv); // Setup Event System
    return a.exec();           // Enters the loop: while(true) { processEvents(); }
}
```

### Key Functions
- **`QCoreApplication::processEvents()`**: Force Qt to process pending events (prevents UI freezing during loops).
- **`deleteLater()`**: Schedules object deletion. **Mandatory** when deleting an object from within its own slot.

## 3. 📬 Event Handling Hierarchy
1.  **`eventFilter()`**: Intercepts events for another object.
2.  **`event()`**: The main dispatcher (routes to `paintEvent`, `mouseEvent`, etc.).
3.  **Specialized Handlers**: Virtual functions you override (e.g., `keyPressEvent`).

## 4. 💎 Qt 6: Bindable Properties (`QProperty`)
The biggest change in the Qt 6 Core. Allows C++ properties to have "React-like" reactive bindings.

```cpp
QProperty<int> width(100);
QProperty<int> height(50);
QProperty<int> area;

// Define a reactive binding
area.setBinding([&]() { return width.value() * height.value(); });

qDebug() << area.value(); // 5000
width = 200;
qDebug() << area.value(); // 10000 (Auto-updated!)
```

## 5. 🏁 The Logic Bridge
- **Thread Affinity:** Every `QObject` "lives" in the thread that created it.
- **Event routing:** Events are pushed into a thread-safe queue. The loop pulls them out and calls `QObject::event()`.

---

[➔ Official API: QObject](https://doc.qt.io/qt-6/qobject.html)
[➔ Back to Roadmap](./00-roadmap.md)
