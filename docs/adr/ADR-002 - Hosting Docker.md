# ADR-002: Host Docker in a Dedicated Virtual Machine

**Status:** Accepted

**Date:** 2026-06-11

---

## Context

After selecting Proxmox as the hypervisor, a decision was needed on where container workloads would run.

Running Docker directly on the Proxmox host was possible, but it would combine virtualization management and application workloads on the same system.

---

## Decision

Run Docker inside a dedicated Ubuntu Server virtual machine.

The Proxmox host will remain responsible only for virtualization, while application containers will run inside the Docker VM.

---

## Rationale

This approach provides:

- Separation between infrastructure and applications.
- Additional isolation for container workloads.
- Easier migration or rebuilding of the Docker environment.
- Ability to run supporting services alongside Docker.

This structure more closely resembles production environments where responsibilities are separated between systems.

---

## Alternatives Considered

### Install Docker Directly on Proxmox

**Advantages**

- Less resource overhead.
- Simpler architecture.

**Disadvantages**

- Mixes hypervisor and application workloads.
- Increased risk of affecting the host.
- Less separation of responsibilities.

---

### Use LXC Containers

**Advantages**

- Lightweight.
- Native Proxmox integration.

**Disadvantages**

- Less aligned with learning Docker-based workflows.
- Different operational model.

---

## Consequences

### Positive

- Cleaner architecture.
- Easier maintenance.
- Better workload isolation.

### Negative / Trade-offs

- Additional VM resource usage.
- More components to maintain.

---

## Implementation Notes

Current Docker VM:

- Ubuntu Server
- Docker Engine
- Docker Compose
- Portainer
- Uptime Kuma
- Tailscale