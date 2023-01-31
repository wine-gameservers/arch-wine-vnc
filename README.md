# arch-wine-vnc

ArchLinux based docker image with wine and vnc support, supports running Windows applications by using Wine. 
This project is hosted at https://github.com/wine-gameservers/arch-wine-vnc/

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
    -v /path/to/application:/opt/applicationname \
    -v /etc/localtime:/etc/localtime:ro \
    -e PUID=<UID from user> \
    -e PGID=<GID from user> \
    toetje585/arch-wine-vnc
```
# Docker compose
```
version: "3.9"
services:
  arch-wine-vnc:
    image: toetje585/arch-wine-vnc:latest
    container_name: arch-wine-vnc
    environment:
      - VNC_PASSWORD=winevnc
      - PUID=<UID from user>
      - PGID=<GID from user>
    volumes:
      - /path/to/application:/opt/applicationname
      - /etc/localtime:/etc/localtime:ro
    ports:
      - 5900:5900/tcp
```
