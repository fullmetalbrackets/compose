# Docker Compose Files

A set of YAML files to create stacks of Docker containers with Docker Compose or Portainer.

## Create stacks via command line

```
git clone https://github.com/fullmetalbrackets/compose.git
cd compose
docker compose -f <filename>.yml up -d
```

For the **photos** stack specifically:

```
cd compose/photos
docker compose up -d
```
