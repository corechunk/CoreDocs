# 🔀 Reverse Proxies & Web Servers Spectrum Hub

Welcome to the architectural hub for reverse proxies, web servers, and application routing. This hub categorizes web delivery engines across a spectrum—from heavy feature-packed enterprise servers down to hyper-minimal, zero-bloat traffic routers.

---

## 🗺️ The Web Server & Routing Spectrum

### 1. 🏢 Heavy Mainstream Enterprise Servers
Full-featured HTTP web servers packed with built-in modules (directory listing, SSI, dynamic language interpreters, access rulesets, and native SSL termination).
*   **Apache HTTP Server (`httpd`):** The classic multi-process/multi-threaded monolithic web server.
*   **NGINX:** Asynchronous event-driven web server and reverse proxy.

### 2. ✂️ Stripped-Down Custom Builds (Compilation Optimization)
Bypassing default binary bloat by manually compiling mainstream servers from source code to strip unused modules for resource-constrained environments.
*   **Stripped Apache Build:** Recompiling Apache without mod_php, mod_cgi, or SSI to minimize RAM overhead.
*   **Stripped NGINX Build:** Recompiling NGINX with `--without-http_gzip_module`, `--without-http_rewrite_module`, and minimal dynamic modules.

### 3. ⚡ Lightweight Desktop & Edge Alternatives
Purpose-built lightweight web servers designed for low RAM footprints.
*   **Lighttpd:** Memory-efficient server optimized for high-concurrency environments.
*   **Caddy:** Modern HTTP/2 & HTTP/3 server with automatic TLS management.

### 4. 🚀 The Lightest Option: Hyper-Minimal Traffic Routers
Stripping away HTML parsing, image serving, and directory listing entirely to focus 100% on low-level network socket routing.
*   📜 [**haproxy-architecture.md**](./haproxy-architecture.md) — Dedicated Guide: Hyper-minimal OSI Layer 4/7 load-balancing, zero-bloat routing, and master/worker PID execution models.
*   🔀 [**load-balancing-microservices.md**](./load-balancing-microservices.md) — Dedicated Guide: Solving internal port conflicts (8001/8002) by routing public traffic across decoupled microservice binaries.
