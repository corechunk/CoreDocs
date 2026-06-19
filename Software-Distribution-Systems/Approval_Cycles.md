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

## 🚀 The Dynamic Remote-Sourcing Pattern

This mechanism involves fetching library components from remote endpoints (e.g., GitHub repositories) during the build or deployment phase. This approach provides significant advantages for rapid iteration and fleet management.

### Technical Implications
- **Velocity:** Provides high velocity for personal utility management by ensuring that build artifacts remain synchronized with the latest library definitions without necessitating full re-compilation of the parent project.
- **Decoupling:** Enables the separation of the core application binary from its supporting library suite, allowing libraries to be updated independently of the main application lifecycle.

### Repository Compatibility
- **Official Upstream Submission:** This pattern is explicitly incompatible with official upstream repository standards (e.g., Debian Main, Fedora, Arch `[extra]`) due to the mandatory requirement for **deterministic reproducibility**. Official build infrastructure is air-gapped and requires that the build recipe produces an identical artifact regardless of external time-based changes.
- **Ad-Hoc Distribution:** This is a highly efficient pattern for private repository management (e.g., personal APT repositories, GitHub-based installers) where the developer maintains control over the remote library lifecycle.

### The Dual-Track Packaging Strategy
A robust architectural approach to software distribution involves adopting a **Dual-Track Workflow** to balance rapid development velocity with the requirements of official upstream standards:

1.  **Track A: The Dynamic Development Pipeline (Ad-Hoc):**
    - **Use Case:** Localized development, private team tooling, and custom ad-hoc repository distribution.
    - **Methodology:** Utilization of dynamic remote-sourcing to resolve and fetch library dependencies at compile-time or run-time. This methodology minimizes maintenance overhead and maximizes deployment velocity for agile environments.
2.  **Track B: The Reproducible Upstream Pipeline (Official):**
    - **Use Case:** Submission to official distributions (e.g., Debian Main, Fedora, Arch `[extra]`).
    - **Methodology:** Maintenance of a dedicated distribution directory (e.g., `apt/` or `dist/`) containing a fully "vendorized" (pre-packaged) application state. This includes static local copies of all dependencies, guaranteeing that build-time network access is not required and that artifact generation remains deterministically reproducible.

By maintaining these distinct pipelines, a codebase retains its utility as both a rapid-iteration development asset and a strictly compliant, packageable distribution asset for global archives.


## 🚫 Common Rejection Reasons

1.  **Bundled Dependencies:** 
    *   **Internal Logic Components (Bundleable):** If a script or library is *exclusive* to your application and serves its core internal logic, **bundle it**. Packaging maintainers expect an application to be self-contained; they do not require you to split an application into dozens of tiny, unmanageable packages.
    *   **External Reusable Libraries (Must Separate):** If your library is designed to be consumed by *other* applications, tools, or scripts, it constitutes an **External Reusable Dependency**. For official upstream repositories, these MUST be packaged separately to ensure a single "Source of Truth" for security patching and maintenance.
    *   **The Pro-Tier Verdict:** Maintainers prefer a cleanly bundled application over 1,000 tiny, unmanageable packages. Only perform the architecture migration to separate your libraries when you have *more than one* application depending on them.
2.  **Network Access During Build:** Build servers have no internet. If your `Makefile` or `PKGBUILD` tries to run `curl` or `npm install`, the build will fail.
3.  **Missing License Headers:** If even one file is missing a license declaration, Debian FTP Masters will reject the entire package.
