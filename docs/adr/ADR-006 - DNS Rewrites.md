# ADR-006: Use DNS Rewrites for Internal Service Discovery

**Status:** Accepted

**Date:** 2026-07-14

---

## Context

As more services are deployed within the homelab, accessing applications by IP address and port becomes difficult to maintain.

Services such as Portainer and Uptime Kuma require predictable access methods across devices on the local network.

A local DNS solution allows services to be accessed using meaningful hostnames instead of remembering individual IP addresses.

---

## Decision

Use AdGuard Home DNS rewrites to provide internal hostname resolution for homelab services.

Internal services will be assigned DNS records that resolve to their appropriate local IP addresses.

---

## Rationale

DNS rewrites provide:

- Human-readable service names.
- Easier service access.
- Reduced dependence on memorizing IP addresses.
- A foundation for future reverse proxy integration.

This approach also mirrors how internal DNS is commonly used in larger environments.

---

## Alternatives Considered

### Access Services Using IP Addresses

**Advantages**

- Simple.
- No DNS configuration required.

**Disadvantages**

- Difficult to remember.
- Less scalable.
- Poor user experience.

---

### Public DNS Records

**Advantages**

- Accessible externally.

**Disadvantages**

- Requires exposing services publicly.
- Not appropriate for internal-only services.

---

## Consequences

### Positive

- Easier access to internal applications.
- Cleaner internal infrastructure.
- Supports future reverse proxy development.

### Negative / Trade-offs

- Requires maintaining DNS records.
- Incorrect DNS configuration can prevent service access.

---

## Implementation Notes

Current internal services:

- Portainer
- Uptime Kuma

Future services will receive DNS records as they are deployed.