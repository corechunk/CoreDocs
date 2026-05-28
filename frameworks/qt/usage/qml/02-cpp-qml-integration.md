# 🔗 Qt QML: C++ Integration (Official)

The bridge between high-performance systems logic (C++) and fluid declarative aesthetics (QML).

---

## 1. 🏗️ Type Registration (Qt 6 Standard)
The modern way to expose C++ to QML is using macros and `qt_add_qml_module` in CMake.

```cpp
// In your header
class MyBackend : public QObject {
    Q_OBJECT
    QML_ELEMENT // Registers automatically with the QML module
    Q_PROPERTY(QString status READ status NOTIFY statusChanged)
    // ...
};
```

## 2. 🛠️ Exposing Functions & Data
- **`Q_INVOKABLE`**: Marks a method as callable from QML.
- **Slots**: Public slots are automatically invokable.
- **Signals**: Emitting a signal in C++ triggers the corresponding `on<SignalName>` handler in QML.

## 3. 📦 Object Ownership Rules
| Creator | Default Owner | Description |
| :--- | :--- | :--- |
| **C++** | `QQmlEngine::CppOwnership` | QML will NOT delete it. You must manage memory. |
| **QML** | `QQmlEngine::JavaScriptOwnership` | QML garbage collector will delete it. |

## 4. 🏁 The Logic Bridge
- **`Q_OBJECT_BINDABLE_PROPERTY`**: The Qt 6-optimized way to handle C++ properties that need to be bound in QML.
- **Engine Access:** Use `QQmlApplicationEngine::rootContext()->setContextProperty()` only for legacy/global objects. Prefer `QML_ELEMENT` for modern apps.

---

[➔ Back to Roadmap](../../core/00-roadmap.md)
