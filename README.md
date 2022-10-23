# arch-wine-vnc

# Table of contents
<!-- vim-markdown-toc GFM -->
* [Deployment](#deployment)
	* [Deploying with docker run](#docker-run)
	* [Deploying with docker-compose](#docker-compose)
<!-- vim-markdown-toc -->
# Deployment
# Docker run
```
$ docker run -d \
    --name arch-wine-vnc \
    -e VNC_PASSWORD=winevnc \
    -p 5900:5900/tcp \ 
    -v /etc/localtime:/etc/localtime:ro \
    -v /path/to/data:/opt/data \
    -e UMASK=<umask for created files> \
    -e PUID=<UID for user> \
    -e PGID=<GID for user> \
    toetje585/arch-wine-vnc
```
# Docker compose
```
version: "3.9"
services:
  wine:
    image: toetje585/arch-wine-vnc:latest
    container_name: arch-wine-vnc
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Amsterdam
    volumes:
      - /path/to/application:/opt/application
    ports:
      - 5900:5900
    restart: unless-stopped
```
