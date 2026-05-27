# Package: javax.net.ssl
## Secure Networking

Secure socket protocols (SSL/TLS). This is vital for secure internet communication.

### Key Classes

| Class | Purpose |
| :--- | :--- |
| **SSLSocket** | A socket that uses SSL/TLS for encryption. |
| **SSLServerSocket** | A server socket that uses SSL/TLS. |
| **SSLContext** | Represents the context for a secure protocol. |
| **TrustManager** | Responsible for managing the trust material used when making trust decisions. |
| **HttpsURLConnection** | Subclass of `HttpURLConnection` for HTTPS. |

### Key Methods in SSLSocket

| Method | Returns | Description |
| :--- | :--- | :--- |
| `startHandshake()` | `void` | Starts the SSL handshake explicitly. |
| `getSession()` | `SSLSession` | Returns the SSL session used by this connection. |
| `setEnabledProtocols(String[])` | `void` | Sets the protocols (e.g., TLSv1.3) enabled for use. |
| `addHandshakeCompletedListener(l)`| `void` | Registers a listener to be notified of SSL handshake completion. |
