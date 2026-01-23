---
title: "Homelab & Selfhosting"
date: 2026-01-20T12:00:00Z
draft: false
layout: "single"
---
I have a Synology NAS and two Mini-PCs in my homelab and a VPS I rent at netcup (I have rented several servers from them for around 10 years now, can highly recommend them)

In my homelab I run Proxmox on both of the Mini-PCs. I considered running Kubernetes on them, but I like actually using the software on it instead of just debugging the setup all the time. So I prefer Proxmox for its simplicity.

I use Pangolin on the VPS as a reverse proxy for all the machines. It's nice to have one reverse proxy for all servers. (+hiding the home's public IP address)

My most used applications:
- [**Nextcloud**](https://nextcloud.com/)
    - Yeah it's not the fastest, but I have no problems with it. For me it is reliable and does its job. There is simply no single alternative that can offer as much as Nextcloud does with its apps.
- [**Plex**](https://www.plex.tv/) + some other relevant stuff for media
- [**4get**](https://git.lolcat.ca/lolcat/4get) for search
- [**ntfy**](https://ntfy.sh/) for notifications
- [**Home Assistant**](https://www.home-assistant.io/) for home automation
- [**Pangolin**](https://github.com/fosrl/pangolin) + [**PocketID**](https://github.com/pocket-id/pocket-id) for exposing services and auth
- [**Dawarich**](https://github.com/Freika/dawarich) for my location history
- [**Gitea**](https://gitea.io/) for git
- [**Koito**](https://github.com/gabehf/Koito) + [**Multi-Scrobbler**](https://github.com/FoxxMD/multi-scrobbler) as a last.fm alternative
- [**Tandoor**](https://tandoor.dev/) for recipes