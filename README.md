# Seedbox

Seedbox aims to provide a turnkey solution to automate the self-hosting of your media server with a few optional extras.

## Table of Contents

- [Seedbox](#seedbox)
  - [Table of Contents](#table-of-contents)
  - [Quickstart](#quickstart)
  - [Notes](#notes)
  - [Services](#services)
    - [AdGuardHome (optional)](#adguardhome-optional)
    - [Cloudflared Tunnel (optional)](#cloudflared-tunnel-optional)
    - [Gluetun](#gluetun)
    - [Jackett](#jackett)
    - [Jellyfin](#jellyfin)
    - [Jellyseerr](#jellyseerr)
    - [Plex (optional)](#plex-optional)
    - [PlexTraktSync (optional)](#plextraktsync-optional)
    - [Portainer](#portainer)
    - [qBittorrent](#qbittorrent)
    - [Radarr](#radarr)
    - [Readeck (optional)](#readeck-optional)
    - [Sonarr](#sonarr)
    - [Uptime Kuma (optional)](#uptime-kuma-optional)
    - [Watchtower](#watchtower)
    - [ZeroTier](#zerotier)

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

3. Fill in the required value in the `.env` file
4. Start the stack

```bash
docker-compose up -d
```

5. Use the appropriate ports to access the web interfaces of each services.

## Notes

- The `gluetun` service is configured for WireGuard by default. Adjust settings as needed for your VPN provider.
- Ensure the specified directories for `DOCKERCONFDIR` and `DOCKERSTORAGEDIR` exist on your host machine.
- Why is there both Plex and Jellyfin? Because Plex has a better UI/UX but is limited in the free version and Jellyfin can do hardware transcoding.
- For Readeck, all environment variables are optional and should be commented unless you want to access the service outside your local network. In which case, you will need to provide both `DOCKERHOST` and `DOMAIN`.

This Docker Compose stack provides a comprehensive setup for managing various network and media services efficiently. Adjust configurations as necessary to suit your environment and preferences.

## Services

### AdGuardHome (optional)

A network-wide software for blocking ads and tracking, enhancing privacy and security. [More information](https://github.com/AdguardTeam/AdGuardHome)

### Cloudflared Tunnel (optional)

A tunneling service by Cloudflare that securely exposes local servers to the internet without needing a public IP or port forwarding. [More information](https://github.com/cloudflare/cloudflared)

### Gluetun

A VPN client to route your Docker containers' traffic through a VPN service for enhanced privacy and security. [More information](https://github.com/qdm12/gluetun)

### Jackett

An indexer service that integrates with various torrent and Usenet sites, providing unified search results for use with \*arr services. [More information](https://github.com/linuxserver/docker-jackett)

### Jellyfin

An open-source media server that manages and streams your personal media, including movies, TV shows, music, and photos. [More information](https://github.com/linuxserver/docker-jellyfin)

### Jellyseerr

A companion application for Jellyfin that allows users to request new media content, automating media management and acquisition. [More information](https://github.com/Fallenbagel/jellyseerr)

### Plex (optional)

A media server that organizes video, music, and photos from personal media libraries and streams them to devices both locally and remotely. [More information](https://github.com/linuxserver/docker-plex)

### PlexTraktSync (optional)

A service that synchronizes your Plex watch history with Trakt.tv, helping you keep track of what you’ve watched across different platforms. [More information](https://github.com/linuxserver-labs/docker-plextraktsync)

### Portainer

A web-based interface for managing Docker environments, making it easier to deploy, manage, and troubleshoot containerized applications. [More information](https://github.com/portainer/portainer)

### qBittorrent

An open-source BitTorrent client that facilitates downloading and managing torrents. [More information](https://github.com/linuxserver/docker-qbittorrent)

### Radarr

An automated movie collection manager that downloads movies from Usenet or torrents, organizes them, and keeps them updated. [More information](https://github.com/linuxserver/docker-radarr)

### Readeck (optional)

A simple web application that lets you save the precious readable content of web pages you like and want to keep forever. [More information](https://codeberg.org/readeck/readeck)

### Sonarr

An automated TV series collection manager that downloads TV shows from Usenet or torrents, organizes them, and keeps them updated. [More information](https://github.com/linuxserver/docker-sonarr)

### Uptime Kuma (optional)

A self-hosted monitoring tool that keeps track of the uptime status of your services and websites. [More information](https://github.com/louislam/uptime-kuma)

### Watchtower

A service that automatically updates running Docker containers to the latest available versions. [More information](https://github.com/containrrr/watchtower)

### ZeroTier

A VPN service that provides secure and private connections to your devices. [More information](https://github.com/zerotier/ZeroTierOne)
