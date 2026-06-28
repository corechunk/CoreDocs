# ☕ Command-Line JVM Execution (dalvikvm)

Android runs code inside the **Dalvik VM** (represented by ART - Android Runtime). Unlike standard PCs which execute Java Class bytecode (`.class`), Android requires compiled code to be translated into Dalvik Executable bytecode (`.dex`).

---

### 🧠 DEX bytecode compilation pipeline

```text
+-------------------+
|  Java Source      |
+-------------------+
          | (javac)
          v
+-------------------+
|  JVM Bytecode     | (Standard .class files)
+-------------------+
          | (d8 or dx tool)
          v
+-------------------+
|  Dalvik Bytecode  | (Output: classes.dex)
+-------------------+
```

---

### 💻 Step-by-Step CLI Execution Flow

#### Step 1: Write a Java Class (`Runner.java`)
```java
public class Runner {
    public static void main(String[] args) {
        System.out.println("Hello from Java running inside Dalvik VM!");
    }
}
```

#### Step 2: Compile and Convert to DEX
We use `d8` (included in the Android SDK build tools) to convert class bytecode:
```bash
# 1. Compile Java to standard Class file
javac Runner.java

# 2. Translate JVM bytecode to Dalvik bytecode (classes.dex) and zip into jar
d8 --output runner.jar Runner.class
```

#### Step 3: Push and Run via ADB
```bash
# 1. Push jar containing DEX file to device
adb push runner.jar /data/local/tmp/

# 2. Tell Dalvik VM where to find the classes, and run it
adb shell "export CLASSPATH=/data/local/tmp/runner.jar && dalvikvm Runner"
```
