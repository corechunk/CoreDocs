# Termux & Linux System Administration Wiki

This wiki serves as a comprehensive reference guide derived from the current session's technical discussions, covering user management across operating systems and the deployment of network services within the Android Termux environment.

## 1. Operating System User Management

### Linux User Enumeration

Linux environments treat system configurations as files. User data is locally stored in `/etc/passwd`.

- **List all usernames:**
    
    Bash
    
    ```
    cut -d: -f1 /etc/passwd
    ```
    
- **List human users only (UID >= 1000):**
    
    Bash
    
    ```
    getent passwd | awk -F: '$3 >= 1000 && $3 != 65534 {print $1}'
    ```
    
- **View actively logged-in users:**
    
    Bash
    
    ```
    w
    ```
    
    _(Alternatively, use the `who` command)._
    

### Linux User Creation & Privileges

Administrative (`sudo` or `root`) access is required to provision new accounts.

- **Interactive creation (Recommended):**
    
    Bash
    
    ```
    sudo adduser username
    ```
    
- **Manual creation (Low-level):**
    
    Bash
    
    ```
    sudo useradd -m -s /bin/bash username
    sudo passwd username
    ```
    
- **Granting Administrative Access:**
    
    - _Debian/Ubuntu:_ `sudo usermod -aG sudo username`
        
    - _RHEL/Fedora/CentOS:_ `sudo usermod -aG wheel username`
        

### Windows User Enumeration

Windows user accounts can be queried via standard command-line interfaces.

- **Command Prompt (Standard overview):**
    
    DOS
    
    ```
    net user
    ```
    
- **PowerShell (Detailed object table):**
    
    PowerShell
    
    ```
    Get-LocalUser
    ```
    
- **WMIC (Filter for local accounts):**
    
    DOS
    
    ```
    wmic useraccount where "localaccount=true" get name
    ```
    

## 2. The Termux Environment Architecture

Termux operates as a terminal emulator and Linux environment app for Android. It functions within Android's sandboxed security model, resulting in distinct architectural differences from standard Linux distributions.

### Single-User Constraint

Termux does not support traditional Linux multi-user architecture.

- You are logged in automatically as a system-assigned Android user (e.g., `u0_a123`).
    
- Standard commands like `useradd`, `adduser`, and `sudo` are blocked by the Android kernel.
    

### Customizing the Termux Prompt

To simulate a custom username in the terminal display, modify the shell prompt variable (`PS1`).

1. Open the configuration file: `nano ~/.bashrc`
    
2. Define the prompt: `export PS1="username@termux:\w\$ "`
    
3. Apply changes: `source ~/.bashrc`
    

### Proot Containers

When utilizing isolated Linux distributions inside Termux (via `proot-distro`), standard multi-user functionality is restored within the container. Inside the proot environment, you can use `useradd`, `passwd`, install `sudo` via package managers (`apt`), and use `usermod` to grant privileges.

## 3. Hosting Servers in Termux

Despite running without root access, Termux can host network services. Because Android restricts non-root applications from binding to standard low-numbered system ports, Termux utilizes high ports for its services.

### Termux SSH Server (OpenSSH)

Allows remote command-line access to the Android device.

**Key Specifications:**

- **Port:** 8022
    
- **Package:** `openssh`
    
- **Daemon Command:** `sshd`
    

**Setup Sequence:**

1. Install the package: `pkg update && pkg install openssh`
    
2. Set the session password: `passwd`
    
3. Start the daemon: `sshd`
    
4. Identify connection details:
    
    - Username: `whoami`
        
    - IP Address: `ifconfig`
        

**Client Connection Syntax:**

Bash

```
ssh username@ip_address -p 8022
```

### Termux Samba Server (SMB)

Allows the Android device to be mounted as a network drive on Windows, macOS, or Linux systems.

**Key Specifications:**

- **Port:** 8445
    
- **Package:** `samba`
    
- **Daemon Command:** `smbd -D`
    

**Configuration Sequence:**

1. Request Android storage permissions (optional but recommended for internal storage access): `termux-setup-storage`
    
2. Install the package: `pkg install samba`
    
3. Edit the configuration file located at `$PREFIX/etc/smb.conf`.
    

**smb.conf Template:**

Ini, TOML

```
[global]
   workgroup = WORKGROUP
   server string = Termux Samba
   security = user
   map to guest = Bad User
   smb ports = 8445

[termux]
   path = /data/data/com.termux/files/home 
   writable = yes
   guest ok = yes
   read only = no
```

_(Note: Change `path` to `/storage/emulated/0` if sharing full internal storage)._

**Client Connection Syntax:**

- **Windows (File Explorer):** `\\IP_ADDRESS@8445\termux`
    
- **macOS (Finder):** `smb://IP_ADDRESS:8445/termux`