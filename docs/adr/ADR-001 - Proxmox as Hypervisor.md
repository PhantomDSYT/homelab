# ADR-001: Adopt Proxmox VE as the Hypervisor

**Status:** Accepted

**Date:** 2026-06-11

---

## Context

The homelab required a virtualization platform that would allow multiple services to run independently on a single physical server.

Running every service directly on the host operating system would make maintenance, experimentation, and future expansion more difficult.

A dedicated hypervisor would allow workloads to be isolated, managed independently, and rebuilt without affecting the entire environment.

---

## Decision

Adopt Proxmox VE as the primary hypervisor for the homelab.

Proxmox will manage virtual machines and provide the foundation layer for all future services.

---

## Rationale

Proxmox was selected because it provides:

- Type-1 virtualization capabilities.
- Support for virtual machines and containers.
- Snapshot and backup functionality.
- A web-based management interface.
- Experience with technologies commonly used in infrastructure environments.

Using Proxmox also creates a more realistic environment for learning virtualization concepts and infrastructure management.

---

## Alternatives Considered

### Bare Metal Ubuntu Server

**Advantages**

- Simpler setup.
- Lower overhead.

**Disadvantages**

- Less isolation between services.
- Harder to rebuild individual workloads.
- Limited virtualization experience.

---

### VMware ESXi

**Advantages**

- Widely used in enterprise environments.
- Mature virtualization platform.

**Disadvantages**

- Less accessible for this homelab environment.
- Licensing and feature availability considerations.

---

## Consequences

### Positive

- Workloads can be isolated into separate VMs.
- Easier experimentation and rebuilding.
- Foundation for future infrastructure growth.

### Negative / Trade-offs

- Additional management layer.
- Requires allocating resources between VMs.
- Increased complexity compared to a single operating system.

---

## Implementation Notes

Current environment:

- HP EliteDesk 800 G3 Mini
- Proxmox VE host
- Ubuntu Server VM for Docker workloads