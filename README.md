# Docker Compose Files

A set of YAML files to create stacks of Docker containers with Docker Compose or Portainer.

## Create stacks via command line

```
git clone https://github.com/fullmetalbrackets/compose.git
cd compose
docker compose -f <filename>.yml up
```

For the **photos** stack:

```
cd photos
docker compose up
```

## Create stacks in Portainer

1. In the _Portainer_ UI choose your environment, then on the sidebar go to **Stacks** -> **Add stack**.
2. For _build method_ choose **Repository**
3. For _repository URL_ enter `https://github.com/fullmetalbrackets/compose`
4. For _compose path_ enter the YAML file of your desired stack (e.g. `pihole.yml`)
5. Name the stack, scroll down and click on **Deploy the stack**.

Alternately, choose _build method_ **Web editor** and just copy & paste the contents of a YAML file in, then name the stack, scroll down and click on **Deploy the stack**.

**NOTE:** For the **photos** stack, use the `docker-compose.yml` in the `photos` directory together with the environment variables in `librephotos.env`. In Portainer when creating a stack, either use _load variables from .env file_ or use _advanced mode_ and copy & paste the contents of the `.env` file.

## Containers in each stack

- _media_, _photos_, _pihole_, _proxy_ & _speedtest tracker_ currently running on **Apollo**
- _pihole_ & _fileshare_ currently running on **Korben**
- _monitor_ not currently in use

## Hosts

### Apollo

**Dell Optiplex 3050 SFF**

- **OS:** OpenMediaVault 6
- **IP:** 192.168.0.100
- **CPU:** Intel i5-6500 Quad-Core @ 3.60 GHz
- **Memory:** 16 GB RAM
- **Storage:**
  - 250 GB NVMe Internal SSD
  - 2 TB 3.5" Internal HDD
  - 1 TB 2.5" Internal HDD
  - 1 TB 2.5" External HDD
- **Containers:**
  - Portainer Agent
  - Pi-Hole
  - Cloudflared
  - LibrePhotos
  - Kavita
  - Navidrome
  - Jellyfin
  - Plex
  - Tautulli
  - qBittorrent
  - Speedtest Tracker
  - Nginx Proxy Manager

### Korben

**Dell Optiplex 3020 Micro**

- **OS:** Debian 12
- **IP:** 192.168.0.225
- **CPU:** Intel Pentium G3250T Dual-Core @ 2.8 GHz
- **Memory:** 8 GB RAM
- **Storage:**
  - 120 GB 2.5" Internal HDD
  - 500 GB 2.5" External HDD
- **Containers:**
  - Portainer
  - Pi-Hole
  - Cloudflared
  - WikiJS
