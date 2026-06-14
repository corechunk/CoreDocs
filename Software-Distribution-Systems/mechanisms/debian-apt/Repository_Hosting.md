# Hosting Independent APT Repositories

Distributing software via official Debian repositories can take months of approval. To distribute software instantly (e.g., via a personal server or GitHub Pages), you must host your own **APT Repository**.

## 🏗️ Anatomy of an APT Repository
An APT repository is essentially a web-accessible directory structure with specific metadata files.

```text
my-repo/
├── pool/               # The "Storage" (Actual .deb files)
│   └── main/
│       └── l/linutils/linutils_1.0_amd64.deb
└── dists/              # The "Index" (Metadata & Signatures)
    └── stable/
        └── main/
            └── binary-amd64/
                ├── Packages      # List of all packages & checksums
                └── Packages.gz   # Compressed list
```

---

## 🛠️ Tooling: `reprepro`
`reprepro` is the industry-standard tool for managing a local APT repository. It handles the generation of `Packages` indices and GPG signing automatically.

### 1. Configuration
Create a directory named `conf/` and a file inside called `distributions`:

```text
Origin: Netchunk
Label: Netchunk-Utilities
Codename: stable
Architectures: amd64 arm64
Components: main
Description: Personal collection of systems utilities
SignWith: 0xYOUR_GPG_KEY_ID
```

### 2. Adding a Package
Once configured, adding a `.deb` to the repo is a single command:
```bash
reprepro -b . includedeb stable /path/to/my-package.deb
```

---

## 🔐 The Trust Loop: GPG Signing
For `apt` to trust your repository, you must sign the `Release` file in the `dists/` directory.

1.  **Export your Public Key:**
    ```bash
    gpg --armor --export 0xYOUR_GPG_KEY_ID > netchunk.gpg
    ```
2.  **Provide the Key to Users:** Users must download this key and add it to their trusted list.
3.  **Modern Sourcing (`.sources`):**
    The modern (Debian 12+) way to add a repo is using the DEB822 format in `/etc/apt/sources.list.d/netchunk.sources`:
    ```text
    Types: deb
    URIs: https://repo.netchunk.com
    Suites: stable
    Components: main
    Signed-By: /usr/share/keyrings/netchunk.gpg
    ```

---

## 🌐 Serving the Repository
Since the repository is just a file structure, you can serve it with any web server:
*   **Nginx:** Simple static file serving.
*   **GitHub Pages:** Excellent for zero-cost hosting (since it's just static files).
*   **S3/Object Storage:** For high-availability distribution.
