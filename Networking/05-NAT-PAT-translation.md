# 🔀 Network Address Translation (NAT) & Port Translation (PAT)

This guide details Network Address Translation mechanics used by home and enterprise routers to multiplex private local networks over single public IP addresses.

---

## 1. Private IPv4 Spaces (RFC 1918)

To conserve public IPv4 addresses, routers assign non-routable private IPs on local networks:
- `10.0.0.0` - `10.255.255.255` (`10.0.0.0/8`)
- `172.16.0.0` - `172.31.255.255` (`172.16.0.0/12`)
- `192.168.0.0` - `192.168.255.255` (`192.168.0.0/16`)

---

## 2. Port Address Translation (PAT) Mechanics

When local devices (`192.168.1.10` and `192.168.1.11`) send outbound internet packets, the router rewrites source IP addresses to its single public WAN IP (`203.0.113.5`) and maps internal requests to high ephemeral source ports.

### 2.1 Router Translation Table Example

| Internal Source IP:Port | External Translated Public IP:Port | Destination Internet Target |
|---|---|---|
| `192.168.1.10:49152` | `203.0.113.5:50001` | `142.250.190.46:443` (Google) |
| `192.168.1.11:49152` | `203.0.113.5:50002` | `142.250.190.46:443` (Google) |

When inbound responses return to `203.0.113.5:50001`, the router consults its PAT lookup table, rewrites destination IP/port back to `192.168.1.10:49152`, and routes packets seamlessly back to the local device.
