# ❄️ Standard Qt Setup: Nix Flakes (Official)

Isolated, bit-for-bit reproducible Qt development environments.

---

## 1. 📝 The `flake.nix` (Desktop)
```nix
{
  inputs.nixpkgs.url = "github:nixos/nixpkgs/nixos-unstable";
  outputs = { self, nixpkgs }: {
    devShells.x86_64-linux.default = let
      pkgs = nixpkgs.legacyPackages.x86_64-linux;
    in pkgs.mkShell {
      buildInputs = with pkgs; [
        cmake
        ninja
        qt6.full
        gcc13
      ];
    };
  };
}
```

## 2. 🚀 Usage
```bash
nix develop
```
Inside the shell, `qtbase`, `moc`, and `uic` are all correctly mapped to your `$PATH`.

## 3. 🏁 The Logic Bridge
- **Host Tools:** Nix ensures that even your build tools (`ninja`, `cmake`) are the exact same versions as your teammates'.
- **System Pollution:** Closing the terminal removes all Qt tools from your system path.

---

[➔ Back to Roadmap](../../usage/core/00-roadmap.md)
