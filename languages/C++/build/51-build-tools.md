# 🔵 Standard: Build Tools [PRO]

## Definition
Automating compilation via **CMake** (the C++ industry standard) or Ninja/Make.

## 1. Legacy Way (C++11 / C++17)
Manual compilation or simple Makefile.

```bash
# Manual Ritual
g++ -c main.cpp utils.cpp
g++ main.o utils.o -o app

# Makefile
app: main.o utils.o
	g++ main.o utils.o -o app
```

## 2. Modern Way (C23)
Using `CMakeLists.txt` for cross-platform automation.

```cmake
# --- CMakeLists.txt ---
cmake_minimum_required(VERSION 3.20)
project(MyApp)

set(CMAKE_CXX_STANDARD 23)
add_executable(app main.cpp utils.cpp)

# Command:
# cmake -B build && cmake --build build
```

# The Logic Bridge
// Logic: CMake is a "Meta-Build System." It doesn't compile code itself; it generates the build instructions for your specific OS (Makefiles on Linux, Solution files on Windows).
