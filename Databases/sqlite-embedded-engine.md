# 📄 SQLite Embedded Storage & Operations Manual

This operations manual details the architectural principles, C/C++ API integration, CLI operations, and concurrency lock boundaries for **SQLite**—the world's most widely deployed zero-daemon embedded database engine.

---

## 1. Architectural Foundations: Embedded Engine vs. Server Daemon

### 1.1 The Zero-Daemon Advantage
Unlike PostgreSQL or MySQL, SQLite is **not** a separate background server daemon or system service (`systemctl`). There are no background processes, no network ports (e.g., 3306 or 5432), and no socket connections. The entire database engine is compiled directly into your application binary as a lightweight library link.

### 1.2 Single-File Storage Architecture
SQLite stores all tables, indices, triggers, and schema definitions inside a **single cross-platform disk file**. This file can be copied seamlessly between Linux, Windows, macOS, and Android without binary conversion.

---

## 2. Concurrency Mechanics & The Single-Writer Lock Limit

SQLite utilizes file-level locking mechanisms to guarantee ACID transactions:

*   **Concurrent Reads (Unlimited):** Multiple threads or external processes can read from the SQLite database file simultaneously without blocking.
*   **Single-Writer Lock Constraint (The Bottleneck):** Only **one process/thread can write** to the database file at any given millisecond. During a write transaction, SQLite acquires an exclusive file lock.
*   **Write-Ahead Logging (WAL Mode):** By default, writes block reads in traditional rollback journal mode. Enabling WAL mode (`PRAGMA journal_mode=WAL;`) allows concurrent reads while a write transaction is occurring.

---

## 3. Practical CLI Operations Reference Manual

SQLite provides a standalone command-line interface tool (`sqlite3`) for managing database files directly.

### 3.1 Session Creation & Schema Management

```bash
# Create or open a database file
sqlite3 system_data.db
```

```sql
-- Inside the interactive sqlite3 prompt

-- 1. Enable Write-Ahead Logging for improved concurrency
PRAGMA journal_mode=WAL;

-- 2. Create a relational table
CREATE TABLE IF NOT EXISTS system_metrics (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP,
    cpu_usage REAL NOT NULL,
    memory_free INTEGER NOT NULL
);

-- 3. Insert records
INSERT INTO system_metrics (cpu_usage, memory_free) VALUES (14.2, 256040);

-- 4. Query records
SELECT * FROM system_metrics WHERE cpu_usage > 10.0;
```

---

## 4. C/C++ Systems Programming Integration Guide

To embed SQLite inside C applications, include `<sqlite3.h>` and link against `-lsqlite3`.

```c
#include <stdio.h>
#include <sqlite3.h>

int main() {
    sqlite3 *db;
    char *err_msg = 0;
    
    // Open database connection (creates file if missing)
    int rc = sqlite3_open("system_data.db", &db);
    if (rc != SQLITE_OK) {
        fprintf(stderr, "Cannot open database: %s\n", sqlite3_errmsg(db));
        sqlite3_close(db);
        return 1;
    }
    
    // Execute SQL statement
    char *sql = "CREATE TABLE IF NOT EXISTS logs(id INT, msg TEXT);";
    rc = sqlite3_exec(db, sql, 0, 0, &err_msg);
    
    if (rc != SQLITE_OK) {
        fprintf(stderr, "SQL error: %s\n", err_msg);
        sqlite3_free(err_msg);
    } else {
        printf("Table created successfully\n");
    }
    
    // Close database handle
    sqlite3_close(db);
    return 0;
}
```

---

## 5. Operational Command Reference Sheet

| Operational Task | CLI Command / SQL Syntax | Description |
|---|---|---|
| **Inspect Tables** | `.tables` | Lists all tables defined within the database file. |
| **View Table Schema** | `.schema table_name` | Displays the exact SQL DDL statement used to construct a table. |
| **Export to SQL Script** | `sqlite3 data.db .dump > backup.sql` | Dumps database structure and records into a plain-text SQL script. |
| **Import from SQL Script** | `sqlite3 new.db < backup.sql` | Reconstructs a database file from a SQL script dump. |
| **Vacuum Database** | `VACUUM;` | Reclaims empty disk space and defragments the database file. |
