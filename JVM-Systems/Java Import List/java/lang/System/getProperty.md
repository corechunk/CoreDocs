# Method: getProperty(String key)
## Class: `java.lang.System`

Gets the system property indicated by the specified key.

### Signature
- **Inputs:** `key: String` — The name of the system property.
- **Returns:** `String` — The string value of the system property, or null if there is no property with that key.

### Example (Kotlin)
```kotlin
val os = System.getProperty("os.name")
```
