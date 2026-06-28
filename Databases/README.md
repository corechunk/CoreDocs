# 💾 Database Architecture Spectrum Hub

Welcome to the architectural hub for database management systems and storage engines. This hub categorizes data persistence across a spectrum—from massive background server daemons down to zero-configuration embedded local file engines.

---

## 🗺️ The Database Architecture Spectrum

### 1. 🏢 Heavy Mainstream Background Daemons (Live Linux Services)
Enterprise Relational Database Management Systems (RDBMS) that run as persistent background system services (`systemd` daemons), managing complex memory pools, thread pools, and network ports.
*   **PostgreSQL:** Advanced object-relational database running persistent background worker daemons.
*   **MySQL / MariaDB:** Standard multi-threaded relational database service listening on internal network ports (e.g., 3306).

### 2. ⚡ Medium & Specialized Memory-Centric Services
Live background service daemons optimized for specialized caching or document models.
*   **Redis / KeyDB:** High-speed in-memory data structure stores running as background network services.
*   **MongoDB:** Document-oriented NoSQL database service managing dynamic JSON-like records.

### 3. 📄 The Lightest Option: Embedded Zero-Daemon Storage
Completely eliminating background daemons, memory-heavy service processes, and network ports by embedding the storage engine directly into the application binary.
*   📜 [**sqlite-embedded-engine.md**](./sqlite-embedded-engine.md) — Dedicated Guide: Zero-configuration, zero-daemon execution, single-file storage, and single-writer file lock boundaries.
*   🏛️ [**rdbms-daemon-architectures.md**](./rdbms-daemon-architectures.md) — Dedicated Guide: Architectural comparison between heavy client-server daemons (PostgreSQL/MySQL) vs. zero-latency embedded files.
