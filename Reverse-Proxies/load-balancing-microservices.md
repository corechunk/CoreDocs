# 🔀 Microservices Load Balancing & Port Collision Resolution

## 1. The Internal Port Collision Problem
When building modular microservices, multiple independent C/C++ or Python binaries cannot bind simultaneously to the same public network port (e.g., standard HTTP Port 80). Operating system socket rules prevent multiple processes from listening on identical IP:Port pairs.

## 2. Decoupled Architecture Blueprint
Instead of compiling a single massive monolithic binary, microservices are assigned dedicated internal ports loopbacked to local memory (`127.0.0.1`):

```text
[ Public Client ] ──(Port 80)──> [ HAProxy Reverse Proxy ]
                                        │
                                        ├── (Path /api) ──────> [ API Service (Port 8001) ]
                                        ├── (Path /auth) ─────> [ Auth Service (Port 8002) ]
                                        └── (Default) ────────> [ UI Web Engine (Port 8000) ]
```

## 3. Benefits of Microservice Decoupling
- **Fault Isolation:** A crash in the API binary does not bring down the main UI web server.
- **Independent Deployment:** Individual binaries can be recompiled and restarted independently without interrupting the public-facing HAProxy routing layer.
