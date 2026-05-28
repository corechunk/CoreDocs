# 🌍 Universal Setup: Nix Flakes (Official)

The "Elite" cross-compilation environment using `pkgsCross`.

---

## 1. 🏗️ The Cross-Compilation Flake
Nix uses `pkgsCross` to provide pre-built toolchains for different architectures.

```nix
# flake.nix snippet for Android
let
  pkgs = import nixpkgs { system = "x86_64-linux"; config.allowUnfree = true; };
  androidPkgs = pkgs.pkgsCross.aarch64-multiplatform; # Android ARM64
in {
  devShells.default = pkgs.mkShell {
    buildInputs = [
      androidPkgs.qt6.qtbase
      pkgs.androidenv.composeAndroidPackages { includeNDK = true; ndkVersions = ["27.2.12479018"]; }.androidsdk
    ];
  };
}
```

## 2. 📝 Build Logic
Nix handles the "SDK Plug-in" automatically. When you load the shell:
- `ANDROID_NDK_ROOT` is set.
- `JAVA_HOME` is set to the correct JDK version.
- `CMAKE_PREFIX_PATH` points to the Android-compiled version of Qt.

## 3. 🏁 The Logic Bridge
- **The "Wizard" Workflow:** You "plug in" the entire Android ecosystem just by adding one line to your `flake.nix`. 
- **Absolute Truth:** Since everything is identified by a unique hash, "It works on my machine" is guaranteed to mean "It works everywhere."

---

[➔ Back to Roadmap](../../usage/core/00-roadmap.md)
