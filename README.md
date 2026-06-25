# Homelab

A personal homelab project built on Proxmox to gain hands-on experience with virtualization, Linux administration, containerization, networking, monitoring, and infrastructure automation.

## Objectives

* Learn and administer a virtualized environment using Proxmox VE
* Gain practical experience with Docker and containerized applications
* Deploy and manage self-hosted services
* Implement secure remote administration
* Explore networking concepts including VLANs and firewall management
* Document infrastructure decisions, challenges, and lessons learned

## Hardware

**Host Machine**

* HP EliteDesk 800 G3 Mini
* Intel Core i5-7500T
* 16 GB DDR4 RAM
* 256 GB SSD
* 1 TB SATA SSD

## Current Infrastructure

### Hypervisor

* Proxmox VE

### Security

* Tailscale mesh VPN for secure remote access
* Multi-factor authentication (2FA)
* Scheduled backups

## Project Roadmap

### Phase 1 - Foundation

* [x] Install Proxmox VE
* [x] Configure remote access with Tailscale
* [x] Enable multi-factor authentication
* [x] Configure backups

### Phase 2 - Container Platform

* [ ] Create Ubuntu Server VM
* [ ] Install Docker and Docker Compose
* [ ] Deploy Portainer
* [ ] Deploy Uptime Kuma

### Phase 3 - Application Hosting

* [ ] Containerize an ASP.NET Core application
* [ ] Configure database persistence
* [ ] Implement reverse proxying

### Phase 4 - Monitoring and Development Services

* [ ] Deploy Grafana
* [ ] Deploy Gitea
* [ ] Implement CI/CD workflows

### Phase 5 - Networking

* [ ] Deploy pfSense
* [ ] Configure managed switching
* [ ] Implement VLAN segmentation

## Documentation

Additional documentation can be found in the `/docs` directory.

Topics include:

* Architecture
* Security configuration
* Backup strategy
* Docker deployments
* Networking
* Lessons learned

## Purpose

This homelab serves as a practical environment for learning infrastructure engineering concepts and building demonstrable experience in virtualization, networking, containerization, and systems administration.
