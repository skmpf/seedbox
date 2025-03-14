# Seedbox

Seedbox aims to provide a turnkey solution to automate the self-hosting of your media server with a few optional extras.

## Table of Contents

- [Seedbox](#seedbox)
  - [Table of Contents](#table-of-contents)
  - [Quickstart](#quickstart)
  - [Notes](#notes)
  - [Services](#services)
    - [Gluetun](#gluetun)
    - [Jackett](#jackett)
    - [Lidarr (optional)](#lidarr-optional)
    - [Overseerr (optional)](#overseerr-optional)
    - [Plex](#plex)
    - [PlexTraktSync (optional)](#plextraktsync-optional)
    - [qBittorrent](#qbittorrent)
    - [Radarr](#radarr)
    - [Sonarr](#sonarr)

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

4. Start the stack

```bash
docker-compose up -d
```

5. Access the web interfaces for each service:
   - qBittorrent: http://localhost:8080 (default credentials: admin/adminadmin)
   - Radarr: http://localhost:7878
   - Sonarr: http://localhost:8989
   - Jackett: http://localhost:9117
   - Lidarr: http://localhost:8686
   - Overseerr: http://localhost:5055
   - Plex: http://localhost:32400/web

## Notes

- The `gluetun` service is configured for WireGuard by default. If you prefer OpenVPN, edit the `docker-compose.yml` file and update the `VPN_TYPE` and related environment variables.
- qBittorrent is configured to route through the VPN (gluetun) service.
- Make sure to create the directories specified for `DOCKERCONFDIR` and `DOCKERSTORAGEDIR` before starting the services.
- Media accessible in the `/shared` directory inside containers for consistent path references.
- Plex runs in host network mode for better local network discovery.
- All services use the non-root PUID/PGID for better security.

## Services

### Gluetun

A VPN client to route your Docker containers' traffic through a VPN service for enhanced privacy and security. Currently configured for WireGuard, but supports many VPN providers. [More information](https://github.com/qdm12/gluetun)

### Jackett

An indexer service that integrates with various torrent and Usenet sites, providing unified search results for use with \*arr services. [More information](https://github.com/linuxserver/docker-jackett)

### Lidarr (optional)

A music metadata and download automation application for Usenet and BitTorrent users. [More information](https://github.com/linuxserver/docker-lidarr)

### Overseerr (optional)

A companion application for Plex that allows users to request new media content, automating media management and acquisition. [More information](https://github.com/sct/overseerr)

### Plex

A media server that organizes video, music, and photos from personal media libraries and streams them to devices both locally and remotely. [More information](https://github.com/linuxserver/docker-plex)

### PlexTraktSync (optional)

A service that synchronizes your Plex watch history with Trakt.tv, helping you keep track of what you've watched across different platforms. [More information](https://github.com/linuxserver-labs/docker-plextraktsync)

### qBittorrent

An open-source BitTorrent client that facilitates downloading and managing torrents. [More information](https://github.com/linuxserver/docker-qbittorrent)

### Radarr

An automated movie collection manager that downloads movies from Usenet or torrents, organizes them, and keeps them updated. [More information](https://github.com/linuxserver/docker-radarr)

### Sonarr

An automated TV series collection manager that downloads TV shows from Usenet or torrents, organizes them, and keeps them updated. [More information](https://github.com/linuxserver/docker-sonarr)
