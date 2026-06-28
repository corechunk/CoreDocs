Here is the comprehensive, highly organized operations wiki extracted directly from our session architecture. Every configuration, troubleshooting step, and script logic we covered has been cataloged.

# 📖 System & Network Operations Wiki

**Infrastructure Targets:** Local Arch/Debian workstation, Raspberry Pi Zero 2 W (Headless), Termux (Android), and "ONION" Local Samba Server (`192.168.0.118`).

## 📑 Table of Contents

1. [Samba (CIFS) Network Storage Engineering](#1-samba-cifs-network-storage-engineering)
    
2. [Raspberry Pi Headless Network Provisioning](#2-raspberry-pi-headless-network-provisioning)
    
3. [Emergency Headless Interface & Recovery (Pi Zero 2 W)](#3-emergency-headless-interface--recovery-pi-zero-2-w)
    
4. [Local Area Network (LAN) Discovery Tactics](#4-local-area-network-lan-discovery-tactics)
    
5. [Termux Daemon & Service Management](#5-termux-daemon--service-management)
    

## 1. Samba (CIFS) Network Storage Engineering

### Problem: Shell Password Mangling

Attempting to mount a CIFS share directly via the CLI using `-o password=...` can result in a `mount error(13): Permission denied`, even when credentials are correct. This occurs because the shell (Zsh/Bash) or the `mount` backend parses and strips special characters from the password string.

- **Diagnostic Proof:** If `smbclient //192.168.0.118/SHARE -U username` successfully connects using the same password, the credentials are valid, and the issue is strictly shell mangling.
    

### Solution: Secure Credential Files & Systemd Automounts

To bypass shell parsing and secure the system, credentials must be routed through an isolated file mapped in `/etc/fstab`.

**1. The Credentials File (`/etc/samba/credentials-onion`)**

Plaintext

```
username=netchunk
password=YOUR_RAW_PASSWORD
```

**2. The `/etc/fstab` Implementation**

Using `x-systemd.automount` ensures the laptop does not hang on boot when disconnected from the network. It mounts dynamically _only_ when the folder is accessed, dropping the connection after 60 seconds of idle time.

_Note: Bash variables (like `$USER`) cannot be used in `fstab`. Paths and UIDs must be strictly hardcoded._

Plaintext

```
# 1. Public Shared Space (No Password / Guest)
//192.168.0.118/ONION          /home/netchunk/Shares/ONION          cifs  guest,uid=1000,gid=1000,iocharset=utf8,_netdev,nofail,x-systemd.automount,x-systemd.idle-timeout=60,vers=3.0  0  0

# 2. Main Work Workspace (With Credentials File)
//192.168.0.118/INVENTORY      /home/netchunk/Shares/INVENTORY      cifs  credentials=/etc/samba/credentials-onion,uid=1000,gid=1000,iocharset=utf8,_netdev,nofail,x-systemd.automount,x-systemd.idle-timeout=60,vers=3.0  0  0

# 3. Private Root Home (With Credentials File)
//192.168.0.118/netchunk-home  /home/netchunk/Shares/netchunk-home  cifs  credentials=/etc/samba/credentials-onion,uid=1000,gid=1000,iocharset=utf8,_netdev,nofail,x-systemd.automount,x-systemd.idle-timeout=60,vers=3.0  0  0
```

**Activation Commands:**

Bash

```
sudo systemctl daemon-reload
sudo mount -a
```

## 2. Raspberry Pi Headless Network Provisioning

### Evolution from `wpa_supplicant` to NetworkManager

Legacy setups utilized `wpa_supplicant.conf` paired with `userconf.txt` in the `/boot` partition. Modern Debian/Raspberry Pi OS architecture handles networking via **NetworkManager**.

### Dropping Network Profiles via `setup.sh` (`linutils`)

To provision a headless Pi, configuration matrices are generated directly into the root filesystem.

- **Target Directory:** `/etc/NetworkManager/system-connections/`
    
- **Crucial Security Requirement:** NetworkManager will outright ignore the file if permissions are not strictly set to `600` (Owner Read/Write ONLY).
    
- **Syntax Rules:** No quotation marks are needed around strings containing spaces (e.g., `ssid=Silent Zone` is correct; `ssid="Silent Zone"` will fail).
    

**Profile Payload Structure (`preconfigured-wifi.nmconnection`):**

Ini, TOML

```
[connection]
id=preconfigured-wifi-2
uuid=8b4c802e-f14a-4712-ba8e-a2f0bdc895c2
type=wifi
interface-name=wlan0

[wifi]
mode=infrastructure
ssid=Silent Zone

[wifi-security]
auth-alg=open
key-mgmt=wpa-psk
psk=iphone808

[ipv4]
method=auto

[ipv6]
method=auto
addr-gen-mode=stable-privacy
```

### Handling Multiple Networks

To seed multiple fallback Wi-Fi networks (e.g., home network + mobile hotspot), the payload loop must ensure two variables change per iteration:

1. **Unique Filenames** (e.g., `preconfigured-wifi-1.nmconnection`, `preconfigured-wifi-2.nmconnection`).
    
2. **Unique UUIDs** generated dynamically via `cat /proc/sys/kernel/random/uuid`.
    

## 3. Emergency Headless Interface & Recovery (Pi Zero 2 W)

If the Pi Zero 2 W fails to connect to Wi-Fi, it has no onboard ethernet port. Two recovery operations exist:

### Tactic A: Direct SD Card Surgery (Fastest)

1. Completely power down the Pi.
    
2. Mount the MicroSD root partition to a laptop.
    
3. Lock the permissions manually using the host machine's terminal:
    
    Bash
    
    ```
    sudo chmod 600 /media/netchunk/root/etc/NetworkManager/system-connections/preconfigured-wifi-2.nmconnection
    ```
    
4. Verify deployment via `ls -l`. Output MUST lead with `-rw------- 1 root root`.
    

### Tactic B: USB Gadget Mode (OTG)

Transforms the Pi into a virtual RNDIS ethernet device over a single micro-USB cable.

- **Hardware Warning:** NEVER connect the data port to a PC while the Pi is simultaneously plugged into a wall via the power-only port. The board cannot seamlessly hand over power. Shut down completely first.
    
- **Prerequisites in Boot Config:**
    
    - `/boot/firmware/config.txt` must contain `dtoverlay=dwc2`.
        
    - `/boot/firmware/cmdline.txt` must contain `modules-load=dwc2,g_ether`.
        
- **Execution:** Plug PC directly into the **inner Data port**. The PC provides power and handles the data handshake. SSH natively via `ssh netchunk@YOUR_HOSTNAME.local`.
    

## 4. Local Area Network (LAN) Discovery Tactics

When a headless device joins a network, tracking its DHCP-assigned IP footprint can be done natively or via dedicated FOSS tooling.

### CLI (Linux Desktop / Termux / Pi)

- **Kernel Native (Zero Dependencies):** Prints the ARP cache of recently seen devices.
    
    Bash
    
    ```
    ip neigh
    # or
    arp -a
    ```
    
- **Nmap Ping Sweep (Most Detailed):** Pings the subnet and outputs MAC hardware vendors.
    
    Bash
    
    ```
    sudo nmap -sn 192.168.0.0/24
    ```
    
- **ARP Scan (Fastest):** Broadcasts ARP packets directly to the link layer.
    
    Bash
    
    ```
    sudo arp-scan --localnet
    ```
    

### Android FOSS GUI Tools

Sourced via **F-Droid** or **Orion Store** (adding specific GitHub repos):

- **Network Scanner:** Created by SoroushZarei (Jetpack Compose, multi-threaded Ping/ARP sweeper).
    
- **Network Mapper:** Unofficial FOSS GUI utilizing a compiled `nmap` engine underneath.
    

## 5. Termux Daemon & Service Management

### Problem: `sv-enable sshd` Failure

Executing `sv-enable sshd` results in `unable to change to service directory: file does not exist`. This occurs because the `termux-services` package (which leverages `runit`) has not hooked into the shell environment yet.

### The Fix

1. Ensure components are installed: `pkg install openssh termux-services -y`.
    
2. Register the daemon paths by sourcing the environment:
    
    Bash
    
    ```
    source $PREFIX/etc/profile.d/start-services.sh
    ```
    
3. Enable the service: `sv-enable sshd` or run `sshd` standalone.
    

### Termux SSH Quirks

- **Port Mapping:** Binds to `8022` (due to Android non-root port restrictions).
    
- **Authentication:** Password auth is disabled by default. Push the host `~/.ssh/id_rsa.pub` into Termux's `~/.ssh/authorized_keys`, or manually set a password using the `passwd` command.