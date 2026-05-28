# 🧵 Qt Advanced: Multithreading & Concurrency (Official)

Qt provides three levels of concurrency management depending on the complexity and lifecycle of your task.

---

## 1. 🏗️ Technical Comparison
| Feature | **QThread** | **QThreadPool** | **QtConcurrent** |
| :--- | :--- | :--- | :--- |
| **Focus** | Object-based | Task-based | Function-based |
| **Event Loop** | ✅ Yes | ❌ No | ❌ No |
| **Ideal for** | Long-lived services | Repetitive small tasks | Parallel algorithms |

## 2. 🛠️ The Worker-Object Pattern (QThread)
The recommended way to use `QThread`. Do NOT subclass `QThread` unless you need to change its internal behavior.

```cpp
Worker *worker = new Worker();
QThread *thread = new QThread();

worker->moveToThread(thread); // The object now lives in the new thread

connect(thread, &QThread::started, worker, &Worker::process);
connect(worker, &Worker::finished, thread, &QThread::quit);
```

## 3. ⚡ QtConcurrent (Functional Parallelism)
Requires the `Concurrent` module. It abstracts away the thread pool and return values.

```cpp
// 1. Run a function
QFuture<int> res = QtConcurrent::run(myExpensiveFunction, arg1);

// 2. Map/Filter (Process a list in parallel)
QFuture<void> future = QtConcurrent::map(myList, [](int &n) { n *= 2; });
```

## 4. 🏁 The Logic Bridge
- **Thread Affinity:** Every `QObject` belongs to a thread. This determines where its slots are executed.
- **Cross-Thread Connection:** When connecting signals across threads, Qt uses **QueuedConnection**, automatically marshalling the data through the event loop.

---

[➔ Official Guide: Threading Basics](https://doc.qt.io/qt-6/thread-basics.html)
[➔ Back to Roadmap](../../core/00-roadmap.md)
