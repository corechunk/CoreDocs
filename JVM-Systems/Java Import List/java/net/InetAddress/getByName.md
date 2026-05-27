# Method: getByName(String host)
## Class: `java.net.InetAddress`

Determines the IP address of a host, given the host's name.

### Signature
- **Inputs:** `host: String` — The specified host, or null.
- **Returns:** `InetAddress` — An IP address for the given host name.

### Example (Kotlin)
```kotlin
val address = InetAddress.getByName("google.com")
```
