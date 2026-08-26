# Seedbox

Seedbox aims to provide a turnkey solution to automate the self-hosting of your media server with a few optional extras.

## Table of Contents

- [Seedbox](#seedbox)
  - [Table of Contents](#table-of-contents)
  - [Quickstart](#quickstart)
  - [Notes](#notes)
  - [Services](#services)
    - [Calibre Web Automated (optional)](#calibre-web-automated-optional)
    - [Gluetun](#gluetun)
    - [Jellyfin](#jellyfin)
    - [Prowlarr](#prowlarr)
    - [qBittorrent](#qbittorrent)
    - [Radarr](#radarr)
    - [Sonarr](#sonarr)
    - [Flaresolverr (optional)](#flaresolverr-optional)
    - [Navidrome (optional)](#navidrome-optional)
    - [Seerr (optional)](#seerr-optional)

## Quickstart

1. Clone the repository and `cd` into it

```bash
git clone https://github.com/skmpf/seedbox
cd seedbox
```

2. Copy the `.env` template

```bash
cp .env.template .env
```

3. Fill in the required values in the `.env` file:
   - `DOCKERCONFDIR`: Directory for container configuration files
   - `DOCKERSTORAGEDIR`: Directory for media storage
   - `PUID`: Your user's ID (run `id -u` to find it)
   - `TZ`: Your timezone (e.g., Europe/Paris)
   - VPN settings for Gluetun (see [VPN setup](#gluetun))

4. (Optional) If you do not want to run the optional services, comment out or deletethe corresponding sections in the `docker-compose.yml` file.

5. Start the stack

```bash
docker-compose up -d
```

6. Access the web interfaces for each service:
   - Calibre Web Automated: http://localhost:8083
   - Navidrome: http://localhost:4533
   - Jellyfin: http://localhost:8096
   - Prowlarr: http://localhost:9696
   - qBittorrent: http://localhost:8080 (default credentials: admin/adminadmin)
   - Radarr: http://localhost:7878
   - Seerr: http://localhost:5055
   - Sonarr: http://localhost:8989

## Notes

- The `gluetun` service is configured for WireGuard by default. If you prefer OpenVPN, edit the `docker-compose.yml` file and update the `VPN_TYPE` and related environment variables.
- qBittorrent is configured to route through the VPN (gluetun) service.
- Make sure to create the directories specified for `DOCKERCONFDIR` and `DOCKERSTORAGEDIR` before starting the services.
- Media accessible in the `/shared` directory inside containers for consistent path references.
- Jellyfin runs in host network mode for better local network discovery.
- All services use the non-root PUID/PGID for better security.

## Services

### Calibre Web Automated (optional)

A web-based eBook management application that provides an interface to manage and read your eBook collection. It can automatically ingest new eBooks placed in a specified directory and supports various metadata providers. [More information](https://github.com/crocodilestick/Calibre-Web-Automated)

### Gluetun

A VPN client to route your Docker containers' traffic through a VPN service for enhanced privacy and security. Currently configured for WireGuard, but supports many VPN providers. [More information](https://github.com/qdm12/gluetun)

### Jellyfin

An open-source media server that organizes video, music, and photos from personal media libraries and streams them to devices both locally and remotely. [More information](https://github.com/linuxserver/docker-jellyfin)

### Prowlarr

An indexer manager/proxy built on the popular Jackett project, designed to integrate with applications like Sonarr and Radarr for managing torrent and Usenet indexers. [More information](https://github.com/Prowlarr/Prowlarr)

### qBittorrent

An open-source BitTorrent client that facilitates downloading and managing torrents. [More information](https://github.com/linuxserver/docker-qbittorrent)

### Radarr

An automated movie collection manager that downloads movies from Usenet or torrents, organizes them, and keeps them updated. [More information](https://github.com/linuxserver/docker-radarr)

### Sonarr

An automated TV series collection manager that downloads TV shows from Usenet or torrents, organizes them, and keeps them updated. [More information](https://github.com/linuxserver/docker-sonarr)

### Flaresolverr (optional)

A proxy server that bypasses Cloudflare's anti-bot protection, allowing applications like Sonarr and Radarr to access content from protected websites. [More information](https://github.com/flaresolverr/flaresolverr)

### Navidrome (optional)

A self-hosted music server that allows you to stream your music collection from anywhere, with a lightweight and efficient design. [More information](https://github.com/navidrome/navidrome/)

### Seerr (optional)

A companion application for Jellyfin that allows users to request new media content, automating media management and acquisition. [More information](https://github.com/seerr-team/seerr)
