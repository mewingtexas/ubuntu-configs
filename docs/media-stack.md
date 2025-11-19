# Media Stack Documentation

## Overview
This stack deploys **Jellyfin** (media server) and **qBittorrent** (torrent client) using Docker Compose.  
All configs and media are persisted in the `configs/` and `media/` directories for reproducibility.

---

## Directory Layout
homelab-configs/
├── configs/
│ ├── jellyfin/ # Jellyfin configs, metadata, logs, plugins
│ └── qbittorrent/ # qBittorrent configs, logs, RSS feeds
├── docker/
│ └── media-stack.yml # Compose file defining the stack
├── docs/ # Documentation 
└── media/ # Media library (excluded from GitHub)

---

## Services

### Jellyfin
- **Image:** `jellyfin/jellyfin:latest`
- **Ports:** `8096:8096`
- **Volumes:**
  - `../configs/jellyfin:/config`
  - `../media:/media`
- **Purpose:** Provides a web-based media server with metadata, plugins, and streaming.

### qBittorrent
- **Image:** `lscr.io/linuxserver/qbittorrent:latest`
- **Ports:** `8080:8080`
- **Volumes:**
  - `../configs/qbittorrent:/config/qBittorrent` (flattened mount)
  - `../media:/downloads`
- **Environment:**
  - `PUID=1000`, `PGID=1000` → ensures files are owned by your user
  - `TZ=America/New_York`
- **Purpose:** Torrent client with web UI, RSS feeds, and automation.

---

## Usage

### Start/stop the stack
```bash
cd ~/homelab-configs/docker
docker compose -f media-stack.yml up -d
docker compose -f media-stack.yml down

