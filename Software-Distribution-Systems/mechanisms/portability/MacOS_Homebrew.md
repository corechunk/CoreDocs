# macOS Homebrew & Portability

Deploying Bash-based tools to macOS requires handling Apple's outdated shell environment and its specific packaging philosophy (Homebrew).

## 🍎 The macOS "Ancient Bash" Problem
macOS ships with **Bash v3.2** (from 2007) to avoid the GPLv3 license. Most modern scripts (v4.0+) will crash or behave unpredictably.

### The Fix: Shebang Patching
Your Homebrew formula must explicitly download modern Bash and patch your script to use it.

```bash
#!/usr/bin/env bash  <-- [DEVELOPMENT] Use this locally
#!/opt/homebrew/bin/bash <-- [DEPLOYED] Homebrew will patch to this
```

---

## 🍺 Homebrew Formula Template
Homebrew packages are written as Ruby classes called **Formulae**.

```ruby
class Linutils < Formula
  desc "Comprehensive Bash utility suite"
  homepage "https://github.com/developer/linutils"
  url "https://github.com/developer/linutils/archive/v1.0.0.tar.gz"
  sha256 "e3b0c44..."

  # 1. Declare modern Bash as a hard dependency
  depends_on "bash"
  depends_on "ffmpeg"

  def install
    # 2. Patch the shebang line dynamically during installation
    # This points the script to the Homebrew-installed Bash 5.x
    rewrite_shebang Formula["bash"].opt_bin/"bash", "bin/linutils"

    # 3. Deploy the binary and assets
    bin.install "bin/linutils"
    share.install "assets"
  end
end
```

---

## ⚙️ Lifecycle Restrictions
*   **User-Space Only:** Homebrew formula installation runs under the user's permissions, NOT root. You cannot use `sudo` or modify system folders like `/etc/`.
*   **The `post_install` Method:** Use this to create user-writable directories:
    ```ruby
    def post_install
        (var/"log/linutils").mkpath
    end
    ```
