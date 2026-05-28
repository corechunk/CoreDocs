# 🌐 Qt Advanced: Networking & Sockets (Official)

Qt Networking is **Asynchronous** and **Non-Blocking**. It uses the event loop to notify you when data arrives.

---

## 1. 🏗️ HTTP Engine (`QNetworkAccessManager`)
The high-level API for REST and web requests.

```cpp
QNetworkAccessManager *nam = new QNetworkAccessManager(this);

connect(nam, &QNetworkAccessManager::finished, [](QNetworkReply *reply) {
    if (reply->error() == QNetworkReply::NoError) {
        qDebug() << "Payload:" << reply->readAll();
    }
    reply->deleteLater();
});

nam->get(QNetworkRequest(QUrl("https://api.github.com")));
```

## 2. 🛠️ Low-Level TCP/UDP
| Class | Protocol | Description |
| :--- | :--- | :--- |
| **`QTcpSocket`** | TCP | Reliable, stream-oriented connection. |
| **`QTcpServer`** | TCP | Listen for incoming connections. |
| **`QUdpSocket`** | UDP | Connectionless datagrams. Fast but unreliable. |
| **`QSslSocket`** | SSL/TLS | Secure TCP connection. |

## 3. 🏁 The Logic Bridge
- **Wait functions:** Avoid `waitForReadyRead()`. It blocks the UI thread. Always use the **Signal-based** workflow (`readyRead()` signal).
- **Proxies:** Use `QNetworkProxy` to automatically route all traffic through system or custom proxies.

---

[➔ Back to Roadmap](../../core/00-roadmap.md)
