# Docker Compose Files

A set of YAML files to create stacks of Docker containers with Docker Compose or Portainer.

## Create stacks via command line

```
git clone https://github.com/fullmetalbrackets/compose.git
cd compose
docker compose -f <filename>.yml
```

## Create stacks in Portainer

1. In the _Portainer_ UI choose your environment, then on the sidebar go to **Stacks** -> **Add stack**.
2. For _build method_ choose **Repository**
3. For _repository URL_ enter `https://github.com/fullmetalbrackets/compose`
4. For _compose path_ enter the YAML file of your desired stack (e.g. `pihole.yml`)
5. Name the stack, scroll down and click on **Deploy the stack**.

Alternately, choose _build method_ **Web editor** and just copy & paste the contents of a YAML file in, then name the stack, scroll down and click on **Deploy the stack**.

## Containers in each stack

- _media_, _photos_, _pihole_ & _speedtest tracker_ currently running on **Apollo**
- _pihole_ & _fileshare_ currently running on **Korben**
- _monitor_ and _proxy_ not currently in use

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
  - Libre Photos
  - Kavita
  - Navidrome
  - Jellyfin
  - Plex
  - Tautulli
  - Scrutiny
  - qBittorrent
  - Speedtest Tracker

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
