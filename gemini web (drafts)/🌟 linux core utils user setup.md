# The Linux User Management Wiki

Managing users, groups, and permissions is a core responsibility of a Linux administrator. This wiki covers everything from basic terminal navigation between accounts to deep user and group configuration.

To help you memorize these commands, we use their full conceptual names (e.g., `su` stands for **S**ubstitute **U**ser).

## 1. Navigating Identity: `su` vs. `sudo`

Linux handles administrative tasks in two distinct ways depending on how the system is configured: using a shared Root password (**No `sudo` installed**) or using individual user privileges (**`sudo` installed**).

### Scenario A: Systems Without `sudo` Installed

On clean, minimal installations (like default Debian or Arch), the `sudo` package isn't present. To perform administrative tasks, you must completely switch your shell identity to the `root` account using **`su` (Substitute User)**.

- **Switch to Root (Standard):**
    
    Bash
    
    ```
    su
    ```
    
    _What happens:_ You are prompted for the **Root account's password**. Your terminal session switches identities, but you inherit your original user's environment variables and paths.
    
- **Switch to Root (Login Shell - Highly Recommended):**
    
    Bash
    
    ```
    su -
    ```
    
    _What happens:_ The hyphen (`-`) forces Linux to launch a fresh login shell. This completely clears your old environment and loads Root’s specific environment variables, paths, and landing home directory (`/root`).
    

### Scenario B: Systems With `sudo` Installed

On modern distributions (like Ubuntu, Fedora, or Mint), the **`sudo` (SuperUser Do)** framework is pre-installed. Instead of sharing a single Root password, trusted users use their _own_ password to execute individual commands with administrative power.

- **Run a Single Command as Admin:**
    
    Bash
    
    ```
    sudo apt update
    ```
    
- **Simulate a Persistent Root Login Shell:**
    
    If you have a long configuration session and don't want to type `sudo` before every command, drop into a persistent root shell:
    
    Bash
    
    ```
    sudo -i
    ```
    
    _What happens:_ This prompts for **your personal password**, then grants a persistent root login shell similar to `su -`.
    

### Switching to Non-Root Users

The `su` command isn't just for root; it can substitute your identity to _any_ user on the system.

Bash

```
su - johnny
```

- If executed by a normal user: Prompts for `johnny`'s password.
    
- If executed by root (or via `sudo su - johnny`): Switches instantly without asking for a password.
    

## 2. Provisioning: `useradd` (User Add)

To set up a brand new user on a Linux system, use the native binary **`useradd` (User Add)** tool. By default, `useradd` is low-level and creates a "bare" account. You must pass explicit flags to make it fully functional for a human user.

### Standard New User Deployment Command

Bash

```
sudo useradd -m -s /bin/bash -g developers -G wheel,docker alex
```

### Breakdown of Parameters:

- **`-m` (Make Home):** Automatically creates the user's home directory path at `/home/username`. Without this, the user logs into a broken environment with no space to save personal configuration files.
    
- **`-s` (Shell):** Sets the default command-line interpreter. Modern systems favor `/bin/bash` or `/bin/zsh`. If omitted, the system may default to `/bin/sh` (which lacks auto-complete and arrow-key history tracking).
    
- **`-g` (Primary Group):** Assigns the user's single primary group.
    
- **`-G` (Supplementary Groups):** Assigns a comma-separated list of secondary groups the user should belong to.
    

### Setting the Initial Password: `passwd` (Password)

A newly created account is locked by default until a password is set using the **`passwd` (Password)** command:

Bash

```
sudo passwd alex
```

## 3. Modification: `usermod` (User Modify)

When an account already exists and you need to "set" or adjust its configuration parameters, leverage **`usermod` (User Modify)**.

### Group Management Operations

This is where administrators make the most critical mistakes. Pay close attention to how flags interact.

- **The Safe Append Protocol (Add to a Group):**
    
    To add a user to a secondary group (like `docker`) without destroying their current group memberships, you **must combine** `-a` (**A**ppend) and `-G` (**G**roups).
    
    Bash
    
    ```
    sudo usermod -aG docker alex
    ```
    
- > ⚠️ **CRITICAL ADMINISTRATIVE WARNING:** Running `sudo usermod -G docker alex` (omitting the `-a`) tells Linux: _"Make the user a member of docker, and remove them from every other secondary group on the system."_ If they were an administrator in the `wheel` or `sudo` group, they will instantly lose their admin rights upon their next login.
    

### Environmental Configurations

- **Change Login Shell:**
    
    If a user wants to move from Bash to Zsh:
    
    Bash
    
    ```
    sudo usermod -s /bin/zsh alex
    ```
    
- **Relocate Home Directory:**
    
    Moves their home files to a new drive partition and re-points the system records:
    
    Bash
    
    ```
    sudo usermod -m -d /mnt/storage/alex alex
    ```
    

### Account Security Control

If an employee leaves or an account is compromised, you can freeze it without deleting data.

- **Lock Account (`-L`):** Puts a `!` in front of the encrypted password in `/etc/shadow`, disabling logins.
    
    Bash
    
    ```
    sudo usermod -L alex
    ```
    
- **Unlock Account (`-U`):** Removes the restriction, restoring access.
    
    Bash
    
    ```
    sudo usermod -U alex
    ```
    

## 4. Group Architecture: `groupadd` & `gpasswd`

Users are organized into groups to easily manage file permissions across teams.

### Creating a Group: `groupadd` (Group Add)

Before assigning users to a department folder, define the group entity:

Bash

```
sudo groupadd engineering
```

### Direct Group Modification: `gpasswd` (Group Password)

While `usermod` modifies a _user's_ properties, **`gpasswd` (Group Password)** targets the _group_ directly. It is often cleaner for bulk or distinct group updates.

- **Add a User to a Group:**
    
    Bash
    
    ```
    sudo gpasswd -a alex engineering
    ```
    
- **Remove a User from a Group:**
    
    Bash
    
    ```
    sudo gpasswd -d alex engineering
    ```
    

## 5. Audit & Diagnostics Reference Sheet

To verify that your user setup changes applied successfully, use these structural inspection commands.

|**Command**|**Full Conceptual Name**|**Primary Diagnostic Output**|
|---|---|---|
|`whoami`|**Who Am I**|Prints the exact effective username of the current terminal session.|
|`id`|**Identity**|Displays the current user's UID (User ID), GID (Primary Group ID), and all secondary groups they belong to.|
|`groups username`|**Groups**|Explicitly lists all group memberships for a specific user account.|
|`cat /etc/passwd`|**Password Registry File**|Reads the system file containing user account attributes (UID, Home Directory, Default Shell).|
|`cat /etc/group`|**Group Registry File**|Reads the system file defining all existing groups and their current member rosters.|