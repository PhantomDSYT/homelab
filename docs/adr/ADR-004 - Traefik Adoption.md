# ADR-004: Adopt Traefik as the Reverse Proxy

**Status:** Accepted

**Date:** 2026-07-07

---

## Context

As additional services are added, accessing applications through individual IP addresses and ports becomes difficult to maintain.

A centralized reverse proxy is needed to provide consistent routing and prepare the environment for future HTTPS and domain-based access.

---

## Decision

Adopt Traefik as the reverse proxy for the homelab.

Traefik will act as the central routing layer between users and hosted services.

---

## Rationale

Traefik was selected because it:

- Integrates well with Docker environments.
- Supports dynamic routing.
- Provides experience with modern reverse proxy technologies.
- Creates a foundation for HTTPS and custom domains.
- Scales as additional services are introduced.

---

## Alternatives Considered

### Nginx Proxy Manager

**Advantages**

- Easier graphical configuration.
- Beginner friendly.

**Disadvantages**

- Less focused on dynamic service discovery.
- Provides less exposure to automation-oriented workflows.

---

## Consequences

### Positive

- Centralized service routing.
- Easier future expansion.
- Better understanding of reverse proxy concepts.

### Negative / Trade-offs

- More complex configuration.
- Requires learning Traefik concepts.

---

## Implementation Notes

Planned routing:

```
Client
   |
   v
Traefik
   |
   +-- Docker Services
   +-- Media VM
   +-- Future Applications
```