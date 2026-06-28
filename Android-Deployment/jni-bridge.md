# 🌉 Java Native Interface (JNI)

The Java Native Interface (JNI) is the programming framework that allows Java/Kotlin JVM bytecodes to call, and be called by, native C/C++ compiled code.

---

### 🧠 The JNIenv and Type Mappings

Native C code interacts with the JVM heap using the `JNIEnv` pointer, which contains functions to lookup classes, allocate objects, and retrieve field variables.

#### Primitive Type Mapping Table

| Java / Kotlin Type | JNI Native C Type | Signature Identifier |
| :--- | :--- | :--- |
| `boolean` | `jboolean` | `Z` |
| `int` | `jint` | `I` |
| `long` | `jlong` | `J` |
| `float` | `jfloat` | `F` |
| `double` | `jdouble` | `D` |
| `String` | `jstring` | `Ljava/lang/String;` |

---

### 💻 JNI Native Binding Example in C

The following code implements a native method `stringFromJNI()` declared in a Java class `MainActivity`.

```c
#include <jni.h>
#include <string.h>

// Function name must follow strict naming: Java_[package]_[class]_[method]
JNIEXPORT jstring JNICALL
Java_com_sys_nativeapp_MainActivity_stringFromJNI(
    JNIEnv *env,
    jobject this_obj // Reference to the calling Java MainActivity class instance
) {
    char greeting[] = "Hello from Native C code!";
    
    // Allocate a new Java String object inside the JVM heap
    return (*env)->NewStringUTF(env, greeting);
}
```

#### Calling the Native Method in Java

```java
package com.sys_nativeapp;

import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    // 1. Load the compiled shared native library (.so)
    static {
        System.loadLibrary("native-core"); // Loads libnative-core.so
    }

    // 2. Declare the native signature interface
    public native String stringFromJNI();

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        TextView tv = new TextView(this);
        tv.setText(stringFromJNI()); // Invokes C function
        setContentView(tv);
    }
}
```
