# PKGBUILD Templates & Architecture

Arch Linux uses a single declarative shell script (`PKGBUILD`) to manage the entire build and packaging lifecycle.

## 🏗️ Core Metadata Arrays

Inside a `PKGBUILD`, dependencies and conflicts are defined using standard shell arrays:

```bash
pkgname=linutils
pkgver=1.0.0
pkgrel=1
pkgdesc="Comprehensive Bash utility suite"
arch=('any') # 'any' for scripts, 'x86_64' for compiled binaries
license=('GPL3')
depends=('bash>=5.0' 'ncurses')
optdepends=(
    'ffmpeg: Required for media features'
    'gum: Required for TUI rendering'
)
conflicts=('linutils-git')
```

---

## 📜 Deployment Templates

### 1. For Scripts (Bash/Python/etc.)
Since there is no compilation, you simply install the files into the `$pkgdir` (the staging area).

```bash
package() {
    # -D creates missing parent directories
    # -m755 sets executable permissions
    install -Dm755 "${srcdir}/linutils.sh" "${pkgdir}/usr/bin/linutils"
}
```

### 2. For Native Binaries (C/C++/Rust)
Requires a `build()` function to run the compiler before packaging.

```bash
build() {
    cd "$pkgname-$pkgver"
    make
}

package() {
    cd "$pkgname-$pkgver"
    make DESTDIR="$pkgdir/" install
}
```

---

## ⚡ Key Arch Philosophies
1.  **Vanilla Software:** Do not patch the software unless absolutely necessary. Deliver it as the developer intended.
2.  **No `Recommends`:** Use `optdepends` for anything that isn't strictly required for the binary to launch.
3.  **The `.SRCINFO` Rule:** Every time you update the `PKGBUILD`, you MUST regenerate the metadata for the AUR:
    `makepkg --printsrcinfo > .SRCINFO`
