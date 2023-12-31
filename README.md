# Docker Compose Files

A set of YAML files to create stacks of Docker containers with Docker Compose or Portainer.

## Create stacks via command line

```
git clone https://github.com/fullmetalbrackets/compose.git
cd compose
docker compose -f <filename>.yml up
```

For the **photos** stack specifically:

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

For the **photos** stack specifically:

3. For _repository URL_ enter `https://github.com/fullmetalbrackets/compose/photos`
4. For _compose path_ enter `compose.yml`
5. Scroll down, click _load variables from .env file_ and choose the `.env` OR click on _advanced mode_ and copy & paste the contents of `.env`
6. Name the stack, scroll down and click on **Deploy the stack**.

Alternately, choose _build method_ **Web editor** and just copy & paste the contents of a YAML file in, name the stack, scroll down and click on **Deploy the stack**.

## Deploy bleh.cc site stack

`site.yml` deploys Nginx and Cloudflare Tunnel.

1. Use `git clone https://github.com/fullmetalbrackets/compose.git` to download the site's code from Github
2. From within site source directory, use `yarn` to install dependencies
3. `yarn build` to build the static site, will output to `/dist` sub-directory
4. In the `site.yml` under `volumes`, ensure the site's **dist** folder as the local volume -- ex. `/home/ad/bleh/dist/:/usr/share/nginx/html/`
5. For the cloudflare tunnel, login to _Cloudflare Zero Trust_, go to _Access_ -> _Tunnel_, choose an existing tunnel and click _Configure_ (or create a new tunnel) and take note of the _token_, copy and paste it appended to the environmental variable `TUNNEL_TOKEN=` in `site.yml`
6. With the `site.yml` updated with correct parameters, deploy the stack via any method stated above.

## Containers in each stack

- _admin_, _arr_, _media_, _paperless_ & _speedtest tracker_ on **Korben**
- _site_ running on **Potato**
- _pihole_, _photos_, _monitor_ & _fileshare_ not currently in use
