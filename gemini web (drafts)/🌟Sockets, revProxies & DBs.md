# Lightweight Network Architecture Wiki: From Raw TCP to HAProxy

Welcome to the comprehensive master wiki for designing, building, and deploying a hyper-minimal, high-performance web infrastructure on highly constrained hardware.

This document outlines the theoretical concepts, practical deployment steps, and industry-level architectural decisions required to run concurrent networking services on a Raspberry Pi Zero 2 W, stripping away heavy software abstractions to focus entirely on core protocols.

## 1. Core Philosophy & Hardware Context

The foundation of this architecture is built on bypassing massive, monolithic software stacks. Standard industry web tools are often designed for cloud servers with gigabytes of RAM. On constrained edge devices (like a Raspberry Pi Zero 2 W with ~415 MiB of usable RAM), these tools introduce severe overhead.

### The Objective

To learn and implement the foundational HTTP protocol without the interference of heavy server software, FPGAs, or complex engines. This is achieved by handling baseline TCP/UDP connections manually and managing traffic with ultra-lightweight routing and embedded databases.

## 2. The Web Server Dilemma

Most out-of-the-box web servers (such as standard Apache or NGINX) are packed with default features that consume valuable system resources.

### Built-in Bloat of Standard Servers

- **Directory Listing:** Automatically generating HTML lists of files if an index page is missing.
    
- **Server-Side Includes (SSI):** Assembling pages dynamically by injecting headers/footers into multiple files.
    
- **Dynamic Language Modules:** Running heavy engines (like PHP or Python) on the fly to generate content.
    
- **Access Control & Rulesets:** Processing complex credential checks, IP blocking, and routing rules for every request.
    
- **SSL/TLS Encryption Layering:** Heavy cryptographic processing embedded directly into the server application.
    

### The "Stripped-Down" Alternative

While it is possible to manually compile traditional servers from the source code to remove these features, they still act as a complex abstraction layer. For the purpose of learning raw networking, even a minimal NGINX build obscures the low-level data exchange.

## 3. The Low-Level Networking Plan

To understand the network stack fundamentally, standard web servers are completely bypassed in favor of raw socket programming.

### Baseline TCP & UDP Tinkering

- **Manual Packet Handling:** Using custom C, C++, or Bash programs to handle incoming and outgoing network packets directly.
    
- **Text-Based HTTP:** Sending and parsing raw HTTP header text over these custom sockets to understand exactly how browsers and servers communicate on the wire.
    
- **CLI/TUI Monitoring:** Displaying real-time network traffic and packet exchanges cleanly within a terminal interface.
    

### Essential Networking Provisions

Network instability (such as brief Wi-Fi drops on the Pi) can instantly crash standard socket programs. Two critical implementations are required at the C/C++ level:

1. **Non-Blocking Sockets:** Ensuring the main execution thread does not halt entirely while waiting for network data to arrive.
    
2. **Connection Timeouts:** Forcing the program to drop dead connections gracefully rather than freezing indefinitely.
    

## 4. Scaling to Multiple Services (The Port Conflict)

Once baseline networking is understood, the next step is running multiple concurrent services. This introduces a major architectural hurdle.

### The "Two Binaries" Problem

If multiple custom network binaries are launched on the same machine, they cannot simultaneously listen to the same external network port (such as standard HTTP port 80 or HTTPS port 443). If Binary A binds to port 80, Binary B will fail to start.

### The Solution: Micro-Services & Reverse Proxying

Instead of combining all code into one giant program (a monolith), the industry standard is to break them into smaller, independent binaries (micro-services) running on internal ports (e.g., 8001, 8002). A dedicated routing layer is then placed in front of them to handle the public ports.

## 5. HAProxy: The Hyper-Minimal Router

To solve the port conflict without introducing the bloat of a standard web server, **HAProxy** is utilized as the reverse proxy layer.

### Why HAProxy?

- **Lightning Fast:** It operates at the lowest possible application layer (OSI Layer 4 and 7).
    
- **Zero Bloat:** It does not read HTML, handle cookies, or serve static images. It exclusively routes network traffic.
    
- **Industry Standard:** Despite being extremely lightweight, it is used by global platforms (GitHub, Reddit, Stack Overflow) as the first line of defense to load-balance millions of connections.
    

### Deployment Flow

1. HAProxy binds to public Port 80/443.
    
2. Traffic hits the Pi Zero.
    
3. HAProxy instantly reads the requested URL or routing rule.
    
4. It forwards the raw traffic to the correct custom C/C++ binary running on an internal port.
    

## 6. Database Architecture: Minimal vs. Heavy

A lightweight data layer is just as crucial as a lightweight network layer.

### Industry RDBMS (PostgreSQL, MySQL)

- **The Drawbacks:** These are massive background daemons. They constantly listen on internal network ports, manage their own complex memory caching, and require significant RAM just to idle. They are entirely unsuited for a Pi Zero.
    

### SQLite: The Embedded Powerhouse

- **Zero-Configuration:** Requires no background server process, daemon, or network port.
    
- **Embedded Execution:** The entire database engine is compiled directly into the C/C++ application.
    
- **File-Based:** It reads and writes directly to a single standard file on the local disk.
    

### Scalability Truths (Why Google Cannot Use SQLite)

While SQLite is the most deployed database on earth, it has strict architectural limits based on how it scales:

- **Vertical Scalability (Where it wins):** If an application runs on a single server and requires millions of _reads_, SQLite is incredibly fast due to zero network latency.
    
- **Horizontal Scalability (Where it fails):** Large architectures distribute data across thousands of global servers. SQLite cannot natively sync across a network.
    
- **The Single-File Lock:** SQLite allows concurrent reads, but only **one process can write at a time**. If a massive system attempted global writes simultaneously, the file would lock, destroying performance.
    

## 7. Linux System Diagnostics & Process Management

When monitoring a live server via tools like `btop` or `systemctl`, it is crucial to understand how Linux handles hardware and services behind the scenes.

### HAProxy Process Identification

A running HAProxy service does not consume unnecessary background threads. It typically utilizes highly specific processes visible within its `CGroup`:

- A **Master PID** (managing the service state).
    
- A **Worker PID** (executing the actual high-speed network routing).
    

### Demystifying `kworker` Threads

System monitors frequently display processes named `kworker` (e.g., `kworker/u17:0-br`) running alongside active network services.

- **What they are:** Kernel Worker threads.
    
- **Function:** These are native, fundamental parts of the Linux kernel, not processes spawned by external software like HAProxy.
    
- **Role in Networking:** When HAProxy interacts with the Wi-Fi interface (`wlan0`), the kernel uses `kworker` threads to handle the physical, low-level execution of processing network interrupts and hardware signals. They are highly optimized, usually consuming $0\%$ CPU until a split-second hardware task wakes them up.