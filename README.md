# Termix

Self-hosted SSH- und Remote-Desktop-Management-Plattform. Kostenloser, open-source Ersatz für Termius.

## Features

- SSH Terminal im Browser (Tabs, Split-Screen bis 4 Panels)
- RDP / VNC / Telnet Support (via guacd)
- SSH Tunnel Management mit automatischer Reconnection
- Remote File Management
- Server Stats (CPU, RAM, Disk) in Echtzeit
- Docker Container Management

## Stack

| Service | Image | Port | Beschreibung |
|---------|-------|------|--------------|
| termix | ghcr.io/lukegus/termix:latest | 8888 | Hauptanwendung |
| guacd | guacamole/guacd:1.6.0 | intern | Remote Desktop Backend (RDP/VNC) |

## Voraussetzungen

- Docker + Docker Compose
- Port 8888 frei auf dem Host

## Installation

### 1. Datenverzeichnis anlegen

```bash
mkdir -p /DATA/AppData/termix
```

### 2. Container starten

```bash
docker compose up -d
```

### 3. Web UI öffnen

```
http://SERVER-IP:8888
```

Beim ersten Aufruf einen Admin-Account anlegen.

### 4. Ersten Host hinzufügen

1. **Host Manager** öffnen (oben links)
2. **Add Host** klicken
3. IP-Adresse, SSH-Port (Standard: 22) und Zugangsdaten eintragen
4. Verbinden

## Konfiguration

### Port ändern

In der `docker-compose.yml` den Host-Port anpassen:

```yaml
ports:
  - "NEUER_PORT:8080"
```

### Ohne Remote Desktop (leichter)

`guacd` und das `networks`-Feld können entfernt werden wenn RDP/VNC nicht benötigt wird:

```yaml
services:
  termix:
    image: ghcr.io/lukegus/termix:latest
    container_name: termix
    restart: unless-stopped
    ports:
      - "8888:8080"
    volumes:
      - /DATA/AppData/termix:/app/data
    environment:
      PORT: "8080"
```

## Datenspeicherung

Alle Daten (Hosts, Credentials, Settings) werden gespeichert unter:

```
/DATA/AppData/termix
```

## Nützliche Befehle

```bash
# Starten
docker compose up -d

# Stoppen
docker compose stop

# Logs anzeigen
docker logs termix

# Neustart
docker compose restart

# Update
docker compose pull && docker compose up -d
```

## Weiterführende Links

- [Termix GitHub](https://github.com/Termix-SSH/Termix)
- [Offizielle Dokumentation](https://termix.app/docs)
