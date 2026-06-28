# 🏢 RDBMS Server Daemons vs. Embedded Storage Engines

## 1. Client-Server Background Daemons (PostgreSQL, MySQL)
Enterprise Relational Database Management Systems (RDBMS) operate as standalone system daemons (`systemd` services). They run continuous background processes managing dedicated RAM caches, query planners, connection pools, and TCP network ports (e.g., 5432, 3306).

## 2. Architectural Trade-Off Comparison

| Feature Metric | Heavy RDBMS Daemons (PostgreSQL/MySQL) | Embedded Storage Engines (SQLite) |
|---|---|---|
| **Deployment Model** | Persistent background service daemon | Library linked inside application binary |
| **Network Overhead** | IPC socket / TCP network packet latency | Zero network latency (direct C function calls) |
| **Memory Footprint** | Heavy (~50-200+ MiB RAM baseline) | Microscopic (~few hundred KiB RAM baseline) |
| **Horizontal Scaling** | Multi-node cluster replication & write distribution | Single-machine file storage (local node target) |
| **Write Concurrency** | High concurrent multi-row transaction locking | Single-writer file lock boundary |
