# Traefik

## Overview

Traefik serves as the reverse proxy for the homelab, providing a centralized entry point for applications and services hosted across Docker containers and future virtual machines.

---

## Purpose

- Centralized routing
- Simplify service access
- Prepare for HTTPS
- Enable future domain routing

---

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Use Traefik instead of Nginx Proxy Manager | Gain experience with a modern reverse proxy that supports dynamic configuration and Docker integration. |
| One reverse proxy for all services | Simplifies routing and future expansion. |

---

## Current Architecture

```text
Client
    │
    ▼
Traefik
    │
    ├── Docker Containers
    ├── Future Media VM
    └── Future Services
```

---

## Current Routing

Traefik currently routes requests to backend services hosted within the homelab.

Future routing will include:

- Docker services
- Separate virtual machines
- HTTPS endpoints

---

## Security

- Administrative interfaces remain accessible through Tailscale.
- Public exposure will be limited to services intentionally published.

---

## Future Improvements

- Automatic HTTPS
- Middleware
- Rate limiting
- Authentication
- Dynamic service discovery