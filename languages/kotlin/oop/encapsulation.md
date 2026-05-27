# Encapsulation (PRO)

Definition: Bundling data (properties) and methods that operate on the data into a single unit (class), while restricting access to some of the object's components.

## 1. JVM-Legacy (Java-Interop Style)
Standard visibility modifiers mapping to Java.

```kotlin
class User(private val id: Int) {
    public var name: String = ""
    protected fun validate() { }
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `internal` visibility and property accessors.

```kotlin
class Account {
    var balance: Double = 0.0
        private set // Encapsulated setter
}
```

## 3. Kotlin Native (System / C-Interop)
Visibility in Native modules and memory protection.

```kotlin
internal class NativeBuffer {
    // Hidden from other modules in the binary
}
```

## 4. Multiplatform Path (KMP / Common)
Shared visibility rules across targets.

```kotlin
open class Base {
    protected val key = "secret"
}
```

## 5. Explicit Path (Strictly Typed)
Explicit getters and setters with types.

```kotlin
class Person {
    private var _age: Int = 0
    var age: Int
        get(): Int = _age
        set(value: Int) { _age = value }
}
```

# The Logic Bridge
// Logic: Encapsulation in Kotlin is enforced by the compiler. `private` members are compiled to `private` in JVM bytecode, while `internal` is compiled to `public` but name-mangled to prevent accidental access from Java.
