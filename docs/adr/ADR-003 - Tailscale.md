# ADR-003: Use Tailscale for Secure Remote Administration

**Status:** Accepted

**Date:** 2026-06-20

---

## Context

The homelab needed secure remote access for administration while avoiding unnecessary exposure to the public internet.

Opening router ports would allow remote access but would increase the attack surface and require additional security controls.

---

## Decision

Use Tailscale as the primary method for remote administration.

Administrative access to the homelab will occur through the private Tailnet.

---

## Rationale

Tailscale was selected because it provides:

- Secure private connectivity between trusted devices.
- No requirement for router port forwarding.
- Simple device authentication.
- Reduced exposure of management services.

This allows remote management while keeping infrastructure services private.

---

## Alternatives Considered

### Port Forwarding

**Advantages**

- Simple concept.
- No additional client required.

**Disadvantages**

- Exposes services publicly.
- Requires additional hardening.
- Increases attack surface.

---

### Self-Hosted VPN

**Advantages**

- Full control.
- No dependency on external service.

**Disadvantages**

- More configuration and maintenance.
- Additional operational overhead.

---

## Consequences

### Positive

- Secure remote access.
- Reduced public exposure.
- Easy expansion as devices are added.

### Negative / Trade-offs

- Requires Tailscale client access.
- Depends on Tailscale authentication infrastructure.

---

## Implementation Notes

Currently accessed through Tailscale:

- Proxmox
- Docker VM
- Portainer
- Uptime Kuma
- AdGuard Home