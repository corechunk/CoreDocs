# 🎨 Qt Widgets: UI Designer & uic

The visual side of Qt development. Learn how to use the **Qt Designer** tool and how it translates to C++ code.

---

## 1. 🏗️ The Workflow
1.  **Design:** Create a `.ui` file using **Qt Designer**.
2.  **Compile:** The **User Interface Compiler (`uic`)** converts the XML `.ui` file into a C++ header (`ui_mainwindow.h`).
3.  **Integrate:** You include this header in your C++ class.

## 2. 📝 C++ Integration (The Setup)
```cpp
#include "ui_mainwindow.h"

class MainWindow : public QMainWindow {
    Q_OBJECT
public:
    MainWindow(QWidget *parent = nullptr) : QMainWindow(parent), ui(new Ui::MainWindow) {
        ui->setupUi(this); // THE MAGIC LINE: Connects the XML design to this C++ object
    }
private:
    Ui::MainWindow *ui;
};
```

## 3. 🏁 The Logic Bridge
- **`setupUi()`**: This generated function handles all the `new QPushButton`, `setLayout()`, and `setObjectName()` calls for you.
- **Direct Access:** You access widgets via the `ui` pointer (e.g., `ui->myButton->setText("Hello")`).
- **Safety:** Always call `delete ui;` in the destructor to prevent memory leaks.

---

[➔ Back to Roadmap](../../core/00-roadmap.md)
