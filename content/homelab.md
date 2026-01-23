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
- **Nextcloud**
    - Yeah it's not the fastest, but I have no problems with it. For me it is reliable and does its job. There is simply no single alternative that can offer as much as Nextcloud does with its apps.
- **Plex** + some other relevant stuff for media
- **4get** for search
- **ntfy** for notifications
- **Home Assistant** for home automation
- **Pangolin** + **PocketID** for exposing services and auth
- **Dawarich** for my location history
- **Gitea** for git
- **Koito** + **Multi-Scrobbler** as a last.fm alternative
- **Tandoor** for recipes