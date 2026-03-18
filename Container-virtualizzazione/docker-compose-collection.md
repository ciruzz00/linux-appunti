# Docker Compose collection

## Indice

* [Database](#Database)
* [Development Tools](#development-tools)
* [IoT](#iot)
* [Networking](#Networking)

---

# Database

## PostgreSQL

```yaml
services:
  postgres:
    image: postgres
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: password
      POSTGRES_DB: appdb
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"

volumes:
  postgres_data:
```

## Redis

```yaml
services:
  redis:
    image: redis
    ports:
      - "6379:6379"
```

---

# Development Tools

## Portainer

```yaml
services:
  portainer:
    image: portainer/portainer-ce
    ports:
      - "9443:9443"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
```

---

# IoT

## Eclipse mosquitto

```yaml
services:
  mosquitto:
    image: eclipse-mosquitto:latest
    container_name: mosquitto
    restart: unless-stopped
    ports:
      - "1883:1883"    # MQTT
      - "9001:9001"    # WebSockets
    volumes:
      - ./mosquitto/config:/mosquitto/config
      - ./mosquitto/data:/mosquitto/data
      - ./mosquitto/log:/mosquitto/log
```

### Preparazione:
1. 
```bash
mkdir -p mosquitto-docker/{config,data,logs}  && touch docker-compose.yml
```
2. in ```mosquitto/config```
```bash
# Basic configuration
listener 1883
allow_anonymous true

# WebSocket listener
listener 9001
protocol websockets
allow_anonymous true

# Peristenza
persistence true
persistence_location /mosquitto/data/

# Logging
log_dest file /mosquitto/log/mosquitto.log
log_type error
log_type warning
log_type notice
log_type information
```

---

# Networking

## Unifi controller

```yaml
services:
  unifi:
    image: ghcr.io/jacobalberty/unifi-docker
    container_name: unifi-controller
    network_mode: host
    restart: unless-stopped
    environment:
      TZ: "Europe/Rome"
    volumes:
      - ./data:/config
```

```bash
mkdir controller-unifi && touch docker-compose.yml
```

