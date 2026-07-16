# Uptime Kuma

## Overview

Uptime Kuma provides health monitoring for services running throughout the homelab.

It serves as the primary monitoring platform, allowing quick identification of service outages and availability issues.

---

## Purpose

- Monitor service availability
- Verify deployments
- Detect outages
- Improve infrastructure visibility

---

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Monitor all critical services | Quickly identify failures. |
| Centralize monitoring | One dashboard for the entire homelab. |

---

## Current Monitoring

- Docker services
- Web interfaces
- Future virtual machines

---

## Alerting

Planned:

- Discord
- Telegram
- Email

---

## Future Improvements

- SSL monitoring
- DNS monitoring
- External endpoint monitoring