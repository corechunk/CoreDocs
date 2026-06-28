# 📲 Developer Shell Staging (ADB Push)

To avoid packaging overhead (creating APKs and running Gradle builds) during early testing, developers push and execute native compiled programs directly onto the device using the Android Debug Bridge (`adb`).

---

### 1. The /data/local/tmp Execution Sandbox

Android blocks execution permissions on user-accessible storage locations (like `/sdcard`) by mounting them with the `noexec` flag. However, the system provides one specific sandbox directory designed for developer testing:
`/data/local/tmp`

This folder allows write access to the shell user and does not block execution permissions, making it the perfect staging directory for custom command-line utilities.

---

### 💻 Step-by-Step Command Flow

#### Step 1: Connect your device via USB
Enable **Developer Options** and **USB Debugging** on the device, then verify connection on the host PC:
`adb devices`

#### Step 2: Push the cross-compiled binary to the device
`adb push hello_android_arm64 /data/local/tmp/`

#### Step 3: Run the program
`adb shell "chmod +x /data/local/tmp/hello_android_arm64 && /data/local/tmp/hello_android_arm64"`

---

### 🗺️ Redirection Directory

*   📄 [**`dalvikvm-execution.md`**](./dalvikvm-execution.md) — Running Java/Kotlin code directly from the command line using Dalvik VM ClassLoaders.
