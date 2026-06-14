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
- Port 8888 frei

### Setup

```bash
mkdir -p /DATA/AppData/termix
docker compose up -d
```

Termix ist erreichbar unter: `http://192.168.178.20:8888`

## Eingebundene Server

| Name | IP | Protokoll |
|------|----|-----------|
| Lifebook | 192.168.178.20 | SSH |
| Pi-Frigate | 192.168.178.30 | SSH |

## Domain

Erreichbar über Cloudflare Tunnel: `termix.isbacar.de`

## Daten

Alle Daten werden gespeichert unter: `/DATA/AppData/termix`

## Batch-Scripts

Das Repo ist in den `sync-push-gitea.bat` / `sync-pull-gitea.bat` Scripts integriert.

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
