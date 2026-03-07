# Ubuntu Server Deployment

Base server setup forming the foundation of the homelab. Covers OS installation, remote access configuration, and file sharing.

---

## Overview

Deployed Ubuntu Server on a HP Elite Desk, replacing Windows to optimise resource efficiency. The server acts as the central hub for self-hosted services, managed via CasaOS and accessed remotely over SSH.

---

## Setup

### Installation

- Created bootable installation media using **Rufus**
- Performed a clean Ubuntu Server install, replacing the existing Windows OS
- Configured the system for headless (no-monitor) operation from the start

### Remote Access — SSH

Enabled SSH immediately post-install to allow remote administration from a Windows client:

```bash
sudo apt update && sudo apt upgrade -y
sudo systemctl enable ssh
sudo systemctl start ssh
```

Connecting from Windows (PowerShell or Windows Terminal):

```bash
ssh username@server-ip
```

> **Note:** If you receive a host key warning when reconnecting after a reinstall, clear the old entry from `known_hosts`:
> ```bash
> ssh-keygen -R server-ip
> ```

### System Maintenance

Regular updates managed via sudo:

```bash
sudo apt update && sudo apt upgrade -y
```

---

## CasaOS

Installed **CasaOS** as a web-based graphical dashboard over the Ubuntu Server install. Provides:

- Application deployment via Docker (one-click installs)
- File manager and shared folder management
- System resource monitoring (CPU, RAM, storage)
- Easy access to all running containers

Install CasaOS:

```bash
curl -fsSL https://get.casaos.io | sudo bash
```

Access the dashboard via browser at `http://server-ip`

---

## File Sharing

Created dedicated directories and configured shared folders accessible from **Windows File Explorer** over the local network via SMB. Enables seamless file transfer and remote editing between client devices and the server.

---

## Skills Demonstrated

- Linux OS installation and initial configuration
- SSH setup and remote server administration
- Package management with `apt`
- Docker-based application deployment via CasaOS
- Network file sharing (SMB)
