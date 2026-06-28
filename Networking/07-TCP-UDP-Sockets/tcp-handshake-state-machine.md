# 🤝 TCP 3-Way Handshake & Connection State Machine

This manual details TCP connection establishment, sequence number synchronization, and state machine transitions.

---

## 1. The 3-Way Handshake Mechanics

Before TCP transmits payload bytes, client and server exchange 3 control packets to synchronize Sequence Numbers (`SEQ`) and Acknowledgements (`ACK`).

```text
Client (CLOSED)                                          Server (LISTEN)
      │                                                         │
      │ ─── 1. SYN (SEQ=1000) ────────────────────────────────> │ (SYN_RCVD)
      │                                                         │
      │ <── 2. SYN-ACK (SEQ=2000, ACK=1001) ─────────────────── │
(ESTABLISHED)                                                   │
      │                                                         │
      │ ─── 3. ACK (SEQ=1001, ACK=2001) ───────────────────────> │ (ESTABLISHED)
```

---

## 2. Connection Teardown & The `TIME_WAIT` State

Connection closure uses a 4-way packet exchange (`FIN` -> `ACK` -> `FIN` -> `ACK`). The active closer enters the **`TIME_WAIT`** state for 2 Maximum Segment Lifetimes (2MSL ~ 60s), ensuring late-arriving packets expire safely before socket ports are recycled.
