# Class: java.net.URL
## Purpose: Uniform Resource Locator

Represents a pointer to a "resource" on the World Wide Web.

### Key Methods

| Method | Returns | Description |
| :--- | :--- | :--- |
| `URL(String spec)` | `Constructor` | Creates a URL object from the String representation. |
| `openConnection()` | `URLConnection` | Returns a `URLConnection` (often cast to `HttpURLConnection`). |
| `openStream()` | `InputStream` | Shortcut to open a connection and get the input stream. |
| `getHost()` | `String` | Returns the host name (e.g., "example.com"). |
| `getPath()` | `String` | Returns the path part of the URL. |
| `getPort()` | `int` | Returns the port number. |

### Example
```kotlin
val url = URL("https://example.com/index.html")
println("Host: ${url.host}")
val stream = url.openStream()
```
