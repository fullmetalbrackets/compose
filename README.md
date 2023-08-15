# Docker Compose Files

A set of YAML files to create stacks of Docker containers with Docker Compose or Portainer.

## Create stacks via command line

```
git clone https://github.com/fullmetalbrackets/compose.git
cd compose
docker compose -f <filename>.yml
```

## Install Portainer

```
docker volume create portainer_data \
  docker run -d -p 8000:8000 -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

The above installs _Portainer Community Edition_. If using _Portainer Business Edition_, use image `portainer-ee` instead.

## Install Portainer Agent

If you want to control containers on multiple hosts, use one instance of _Portainer_ as the main one, and install _Portainer Agent_ on the other docker hosts.

In the _Portainer_ UI sidebar, go to **Environments** -> **Add environment** -> **Docker Standalone** and click on **Start Wizard**. Select **Agent**, name it and specify the IP Address at the button, then copy & paste the command into the other host:

```bash
docker run -d \
  -p 9001:9001 \
  --name portainer-agent \
  --restart=always \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /var/lib/docker/volumes:/var/lib/docker/volumes \
  portainer/agent:latest
```

Once the container is up and running on the other host, click **Connect** at the bottom to finish.

## Create stacks in Portainer

Within the _Portainer_ UI choose your environment, then on the sidebar go to **Stacks** -> **Add stack**. Copy & paste the contents of a YAML file into the web editor, then scroll down and click on **Deploy the stack**.

### Stacks

- _media_, _pihole_ & _speedtest_ currently running in host **apollo**
- _pihole_ & _fileshare_ currently running in host **korben**
- _proxy_ currently running in **dobby**
- _monitor_ not currently in use

### Hosts

**apollo**

- Dell Optiplex 3050 SFF
- Intel i5-6500 Quad-Core @ 3.60 GHz
- 16 GB RAM
- 250 GB NVMe SSD, 2 TB 3.5" HDD, 2 TB 2.5" HDD
- OS: OpenMediaVault 6
- IP: 192.168.0.100

**korben**

- Dell Optiplex 3020 Micro
- Intel Pentium G3250T Dual-Core @ 2.8 GHz
- 8 GB RAM
- 500 GB 2.5" HDD
- OS: Debian 12
- IP: 192.168.0.225

**dobby**

- ASUS T100 Transformer Book
- Intel Atom Z3775 Quad-Core @ 2.3 GHz
- 2 GB RAM
- 64 GB SDD
- OS: Debian 12
- IP: 192.168.0.50
