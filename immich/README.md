# Self-Hosted Photo Management with Immich

Replacing ICloud with a locally hosted photo and video management system, using Immich, deployed via Docker on the Ubuntu Server.

---

## Overview

The goal of this project was to reduce my dependency on third party storage for my photos and videos by self-hosting my media backups. Immich provides me with a familiar, app like experience while keeping all the data on local hardware.

---

## Current State

- Immich deployed via Docker on the Ubuntu Server
- Accessible on the local network via browser and mobile app
- Photos and videos migrated from iCloud

---

## Planned Improvements

### Remote Access via Tailscale
Currently access is limited to devices on the same local network. The next step is implementing Tailscale to allow trusted devices to securely access Immich remotely without exposing any ports to the internet.

### Increased NAS with backup support

Currently there is no backup support so if the drive fails or the data gets corrupted then the data is lost, to prevent this currently I am still using iCloud so I still have a backup if both other instances fail. 


---

## Why Self-Host Instead of iCloud?

| | iCloud | Self-Hosted (Immich) |
|---|---|---|
| Storage cost | Monthly subscription | One-time hardware cost |
| Data location | Apple's servers | Your own hardware |
| Privacy | Third-party access | Fully local |
| Control | Limited | Full |

---

## Skills Demonstrated

- Docker deployment and container management
- Self-hosted application setup and configuration
- Network access planning (local vs. remote)
- VPN-based secure remote access design (Tailscale)
- Practical data sovereignty and cloud migration
