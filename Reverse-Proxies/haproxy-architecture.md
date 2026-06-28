# ⚡ HAProxy Architecture & Hyper-Minimal Operations Manual

This operations manual details the architectural principles, configuration syntax, and diagnostic workflows for deploying **HAProxy** as a hyper-minimal Layer 4/7 reverse proxy on low-resource edge targets (such as the Raspberry Pi Zero 2 W).

---

## 1. Core Architecture & Zero-Bloat Rationale

### 1.1 Why Standard Web Servers Fail on Edge Hardware
Standard web servers (Apache, NGINX) embed heavy application-layer features by default: directory listing, SSI compilation, access control list (ACL) evaluation, dynamic script interpreters, and dynamic module loading. On hardware with limited RAM (~415 MiB usable), these background routines introduce severe memory overhead.

### 1.2 The HAProxy Solution
HAProxy operates strictly at **OSI Layer 4 (TCP)** and **Layer 7 (HTTP)**. It does not read HTML, process images, serve static files, or execute server-side scripts. It exclusively processes network socket streams, providing ultra-fast packet proxying and load balancing.

---

## 2. Process Identification & Linux Kernel Interoperability

When inspecting a running HAProxy instance (`systemctl status haproxy` or `btop`), Linux displays distinct process boundaries:

*   **Master PID:** Manages system configuration reloads and controls child worker states.
*   **Worker PID:** The high-speed event loop executing the actual network socket routing.
*   **`kworker` Threads Interoperability:** Monitoring tools often show kernel threads (`kworker`) active alongside HAProxy. When HAProxy routes traffic over physical network interfaces (`wlan0`/`eth0`), the Linux kernel utilizes `kworker` threads to process hardware interrupts and network packet signals asynchronously.

---

## 3. Production Configuration Blueprint (`/etc/haproxy/haproxy.cfg`)

Below is a production-ready HAProxy configuration designed to bind public HTTP/HTTPS ports and route incoming requests to decoupled internal microservices.

```haproxy
global
    log /dev/log local0
    log /dev/log local1 notice
    chroot /var/lib/haproxy
    user haproxy
    group haproxy
    daemon
    maxconn 2048

defaults
    log     global
    mode    http
    option  httplog
    option  dontlognull
    timeout connect 5000ms
    timeout client  50000ms
    timeout server  50000ms

# Public Facing Frontend (Listening on Port 80)
frontend http_in
    bind *:80
    mode http
    
    # Domain & Path Routing Rules
    acl is_api path_beg /api
    acl is_service2 path_beg /service2
    
    # Direct traffic to respective backend pools
    use_backend api_backend if is_api
    use_backend service2_backend if is_service2
    default_backend main_backend

# Backend Pool 1: Internal API Microservice (Port 8001)
backend api_backend
    mode http
    balance roundrobin
    option forwardfor
    server api_node1 127.0.0.1:8001 check

# Backend Pool 2: Internal Secondary Service (Port 8002)
backend service2_backend
    mode http
    balance roundrobin
    option forwardfor
    server service_node1 127.0.0.1:8002 check

# Default Backend Pool: Main Application (Port 8000)
backend main_backend
    mode http
    balance roundrobin
    option forwardfor
    server main_node1 127.0.0.1:8000 check
```

---

## 4. Operational CLI Diagnostics Command Reference

| Operational Task | Command Syntax | Description |
|---|---|---|
| **Validate Configuration** | `sudo haproxy -c -f /etc/haproxy/haproxy.cfg` | Probes configuration file syntax for errors before applying changes. |
| **Zero-Downtime Reload** | `sudo systemctl reload haproxy` | Hot-reloads configuration without dropping active client socket connections. |
| **Inspect Live Socket Connections** | `sudo ss -tulpn \| grep haproxy` | Displays active network ports bound by HAProxy socket descriptors. |
| **Real-Time Traffic Logs** | `sudo journalctl -u haproxy -f` | Streams real-time HTTP routing logs and connection events. |
