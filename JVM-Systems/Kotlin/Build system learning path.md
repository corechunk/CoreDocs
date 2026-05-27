### Step 1
👉 Learn:
- static vs dynamic linking (manually)
### Step 2

👉 Learn build systems properly:
- CMake (C/C++)
- Gradle (Java/Kotlin)
### Step 3
👉 Learn packaging:
- Windows: `.exe + dependencies`
- Linux: ELF + `.so` or static
- Java: fat JAR / jpackage
# The real difference is _control level_

|Source|Control|Portability|Reproducibility|
|---|---|---|---|
|Project-local|High|High|High|
|System-installed|Low|Low|Low|
|Fetched (CMake/Gradle)|Medium-High|High|High|
