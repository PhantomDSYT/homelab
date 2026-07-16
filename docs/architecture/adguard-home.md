# AdGuard Home

## Overview

AdGuard Home provides DNS-based ad blocking and acts as the primary DNS resolver for devices on the home network.

It improves privacy, blocks unwanted advertisements, and gives greater visibility into DNS traffic.

---

## Purpose

- DNS filtering
- Advertisement blocking
- Tracker blocking
- Network-wide DNS management

---

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Self-host DNS filtering | Greater control over network traffic. |
| Run inside Docker | Consistent deployment and easy maintenance. |
| Pair with Unbound (planned) | Improve DNS privacy through recursive resolution. |

---

## Responsibilities

- DNS resolution
- Advertisement blocking
- Tracker filtering
- Query logging

---

## Security

- Local network DNS
- No public DNS exposure
- Administrative interface accessible through Tailscale

---

## Future Improvements

- Integrate with Unbound
- DNS rewrite rules
- Custom filtering lists
- Client-specific DNS policies