# ADR-007: Keep Infrastructure Management Services Private

**Status:** Accepted

**Date:** 2026-07-14

---

## Context

The homelab contains several administrative services used to manage infrastructure, including:

- Portainer
- Uptime Kuma
- Proxmox
- AdGuard Home

Exposing these services publicly would increase the attack surface and create unnecessary security risks.

---

## Decision

Infrastructure management services will remain accessible only through the local network and Tailscale.

Public access will only be considered for services specifically designed for external users.

---

## Rationale

Keeping management interfaces private provides:

- Reduced attack surface.
- Protection from unauthorized access attempts.
- Separation between public-facing applications and administrative systems.
- Alignment with security best practices.

---

## Alternatives Considered

### Expose Management Services Through Reverse Proxy

**Advantages**

- Convenient remote access.
- Accessible without VPN.

**Disadvantages**

- Increases exposure.
- Requires additional security controls.
- Creates unnecessary risk for administrative systems.

---

## Consequences

### Positive

- Administrative services remain protected.
- Remote management remains available through Tailscale.
- Clear separation between public and private services.

### Negative / Trade-offs

- Requires Tailscale access for remote administration.
- Users without Tailnet access cannot reach management interfaces.

---

## Implementation Notes

Currently private services:

- Proxmox
- Portainer
- Uptime Kuma
- AdGuard Home

Traefik will only be used for services intentionally selected for external access.