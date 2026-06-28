# APK DEPLOYMENT
* Packages .dex bytecode
* Includes native .so files
* Standard app lifecycle

# ADB DEPLOYMENT
* Runs bytecode via 'dalvikvm'
* Runs C/C++ binaries in /data/local/tmp
* Allows one-click push-and-run

# TERMUX EXECUTION
* Runs .class via local OpenJDK
* Runs native Linux binaries
* Requires X11 for GUI apps
* 