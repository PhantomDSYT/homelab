# Portainer

## Overview

Portainer provides a web-based interface for monitoring and managing Docker containers.

In this homelab, Portainer is used strictly for administration and monitoring. All deployments continue to be performed through Docker Compose.

---

## Purpose

- View container status
- Inspect logs
- Monitor Docker resources
- Simplify Docker administration

---

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Compose remains the deployment source | Keeps infrastructure reproducible and version-controlled. |
| Portainer is used only for monitoring | Prevents configuration drift caused by manual deployments. |

---

## Responsibilities

- Container monitoring
- Log viewing
- Volume inspection
- Network inspection
- Resource monitoring

---

## Security

- Accessible only through Tailscale
- Not exposed to the public Internet

---

## Future Improvements

- Monitor additional Docker hosts
- Role-based access (if required)