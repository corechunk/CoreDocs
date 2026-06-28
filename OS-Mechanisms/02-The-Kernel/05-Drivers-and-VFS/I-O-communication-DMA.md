# ⚡ I/O Communication & Direct Memory Access (DMA)

Operating system kernels manage hardware devices using three primary input/output communication protocols, balancing CPU efficiency against latency.

---

### 🧠 Three I/O Paradigms

1.  **Programmed I/O (Polling)**:
    *   The CPU continuously checks a status register on the device controller (in a loop) until the device is ready to accept or transmit data.
    *   *Drawback*: High CPU utilization; the core is blocked from performing other tasks.
2.  **Interrupt-Driven I/O**:
    *   The CPU sends a read/write command to the device controller and immediately schedules other threads. When the device completes the operation, it generates a hardware interrupt to notify the kernel.
    *   *Drawback*: For high-speed data transfer (like reading 100MB from a NVMe disk), generating an interrupt for every few bytes causes interrupt storms, degrading performance.
3.  **Direct Memory Access (DMA)**:
    *   The CPU configures a dedicated hardware controller (the **DMA Controller**) with the source device, target RAM address, and block size, then yields the bus.
    *   The DMA Controller transfers data directly between the hardware device and RAM. Once the entire block is copied, it generates a single interrupt to notify the CPU.

```text
               +--------------------------------------+
               |                 CPU                  |
               +--------------------------------------+
                 /                                  \
   [ Configures DMA ]                            [ Receives Interrupt ]
               /                                      \
+---------------+                                    +---------------+
| DMA Controller| === Copies data over hardware bus ===>| Physical RAM  |
+---------------+                                    +---------------+
```
