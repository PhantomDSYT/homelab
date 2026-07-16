# Docker

## Overview

Docker is the primary container platform for the homelab. It provides an isolated and reproducible environment for running services while simplifying deployment, maintenance, and upgrades.

Docker is hosted inside a dedicated Ubuntu Server virtual machine running on Proxmox VE.

---

## Purpose

- Host self-contained applications.
- Simplify service deployment.
- Provide isolated runtime environments.
- Support future infrastructure expansion.

---

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Docker runs inside its own VM | Keeps the Proxmox host dedicated to virtualization while isolating container workloads. |
| Docker Compose manages deployments | Infrastructure is defined as code and easily recreated. |
| Portainer is used for monitoring | Deployment remains Compose-driven while Portainer provides visibility into containers. |
| Named volumes store persistent data | Prevents data loss during container recreation. |

---

## Deployment Strategy

- One Docker VM
- Docker Compose for deployments
- One directory per service
- One Compose file per service

---

## Storage

- Docker named volumes
- Persistent application data
- Volume naming convention: `<service>_data`

---

## Networking

- Docker Compose default bridge networks
- Future custom bridge networks for inter-service communication
- Reverse proxy handled by Traefik

---

## Directory Layout

```text
Docker/
├── Portainer/
├── Uptime-Kuma/
├── Traefik/
└── AdGuardHome/
```

---

## Future Improvements

- Custom Docker networks
- Automated deployments
- CI/CD
- Docker secrets