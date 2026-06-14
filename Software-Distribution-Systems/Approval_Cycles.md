# Upstreaming: Official Approval Cycles

Moving from a local project to an official distribution repository requires navigating strict human and technical "Gatekeepers."

## 🏦 1. The Debian / APT Pipeline (The "Pro" Standard)

Debian is highly curated. You cannot simply upload a binary.

### The Lifecycle
1.  **ITP (Intent to Package):** File a bug report against `wnpp` (Work-Needing and Prospective Packages). This claims your package name.
2.  **Sponsorship:** As a non-DD (Debian Developer), you must find a mentor at `mentors.debian.net`. They audit your code for:
    *   **DFSG Compliance:** Does every file have a clear, free license?
    *   **Clean Build:** Does it build in an isolated `sbuild` or `pbuilder` environment?
3.  **The NEW Queue:** Once a sponsor uploads your package, it sits in the `NEW` queue. FTP Masters manually verify your `debian/copyright` file.
4.  **Sid -> Testing:** Your package lands in `unstable` (Sid). If no critical bugs are filed within 10 days, it migrates to `testing`.

---

## 🏔️ 2. The Arch Linux / Pacman Pipeline (Community Driven)

Arch is decentralized. Growth happens via popularity and voting.

### The Lifecycle
1.  **The AUR (Arch User Repository):** You push your `PKGBUILD` to the AUR via Git. Users can now install it using AUR helpers (`yay`, `paru`).
2.  **Voting:** Users vote for your package on the AUR web portal.
3.  **PM Adoption:** Once a package has enough votes and a stable history, an official **Package Maintainer (PM)** can choose to adopt it.
4.  **Promotion to `[extra]`:** The PM moves the package to the official Arch binary repositories. It is now available via `pacman -S`.

---

## 🚫 Common Rejection Reasons

1.  **Bundled Dependencies:** Official repos hate it when you include a library's source code inside your project. You MUST link to the system's version of that library.
2.  **Network Access During Build:** Build servers have no internet. If your `Makefile` or `PKGBUILD` tries to run `curl` or `npm install`, the build will fail.
3.  **Missing License Headers:** If even one file is missing a license declaration, Debian FTP Masters will reject the entire package.
