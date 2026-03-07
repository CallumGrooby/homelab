# Self-Hosted Minecraft Server

Deployed a modded Minecraft server (All of Create 1.21) using Crafty Controller running in Docker, with secure external access via playit.gg tunnelling so that no port forwarding is required.

---

## Overview

| Detail | Value |
|---|---|
| Modpack | All of Create 1.21.1 v1.1 |
| Server Manager | Crafty Controller (Docker) |
| External Access | playit.gg tunnel |
| Min RAM | 6 GB |
| Max RAM | 8 GB |

---

## Why playit.gg Instead of Port Forwarding?

Traditional port forwarding exposes your home IP address and opens your router directly to the internet. Instead, **playit.gg** creates an outbound tunnel from the server to their relay, external players can connect to a playit.gg address, never touching your home network directly.

---

## Setup Guide

### Step 1 - Upload the server pack in Crafty

1. In the Crafty dashboard, click **"Upload Zip File For Server Import"**
2. Upload the `All_of_Create_1.21.1_v1.1_serverpack.zip`
3. Give the server a name and confirm

### Step 2 - Configure server settings in Crafty

| Setting | Value |
|---|---|
| Server Executable | `/bin/bash` |
| Server Execution Command | `./start.sh nogui` |
| Min Memory | 6 GB |
| Max Memory | 8 GB |

Save settings before continuing.

### Step 3 - Fix file permissions

Get your server's UUID from Crafty settings, then run:

```bash
sudo docker exec crafty-container chmod -R 775 /crafty/servers/YOUR-UUID/
```

### Step 4 - Edit `variables.txt` in Crafty's file manager

Change these two values:

```
WAIT_FOR_USER_INPUT=false
SERVERSTARTERJAR_FORCE_FETCH=false
```

Also edit the `CLEANUP` line to remove `server.jar`:

```
CLEANUP="libraries,run.sh,run.bat,*installer.jar,*installer.jar.log,.mixin.out,ldlib,local,fabric-server-launcher.jar,fabric-server-launch.jar,.fabric-installer,fabric-installer.jar,legacyfabric-installer.jar,.fabric versions"
```

### Step 5 - Accept the EULA

In Crafty's file manager, open `eula.txt` and confirm it reads:

```
eula=true
```

### Step 6 - Remove incompatible mods

These two mods cause crashes on Linux and must be deleted from the `mods/` folder before first launch:

| Mod | Reason |
|---|---|
| `luna-5.3.1.jar` (or similar) | Causes launch crashes on Linux |
| `alternate_current-*.jar` | Causes shutdown crashes |

### Step 7 - Start the server

Start the server in Crafty and monitor the console. **The first launch takes 5–10 minutes** as NeoForge downloads and installs automatically.

---

## Skills Demonstrated

- Docker container management
- Linux file permissions (`chmod`)
- Secure tunnelling as an alternative to port forwarding
- Game server administration and troubleshooting
- Modded server configuration on Linux
