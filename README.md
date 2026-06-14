# Termix

Self-hosted SSH- und Remote-Desktop-Management-Plattform. Kostenloser Ersatz für Termius.

## Features

- SSH Terminal im Browser (Tabs, Split-Screen bis 4 Panels)
- RDP / VNC / Telnet Support (via guacd)
- SSH Tunnel Management
- Remote File Management
- Server Stats (CPU, RAM, Disk)
- Docker Container Management

## Stack

| Service | Image | Beschreibung |
|---------|-------|--------------|
| termix | ghcr.io/lukegus/termix:latest | Hauptanwendung |
| guacd | guacamole/guacd:1.6.0 | Remote Desktop Backend (RDP/VNC) |

## Installation

### Voraussetzungen

- Docker + Docker Compose
- Port frei (Standard: 8888)

### Setup

```bash
mkdir -p /DATA/AppData/termix
docker compose up -d
```

## Daten

Alle Daten werden gespeichert unter: `/DATA/AppData/termix`

## Nützliche Befehle

```bash
# Starten
docker compose up -d

# Stoppen
docker compose stop

# Logs
docker logs termix

# Neustart
docker compose restart
```
