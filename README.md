# arch-wine-vnc

# Table of contents
<!-- vim-markdown-toc GFM -->

* [Basic Docker Usage](#basic-docker-usage)
	* [Default User](#default-user)
* [Environment Variables](#environment-variables)
* [System requirements](#system-requirements)
* [Deployment](#deployment)
	* [Deploying with Docker and systemd](#deploying-with-docker-and-systemd)
	* [Deploying with docker-compose](#deploying-with-docker-compose)
* [License](#license)

<!-- vim-markdown-toc -->

# Basic Docker Usage

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
