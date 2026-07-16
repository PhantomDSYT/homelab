# Proxmox VE Architecture

## Overview

Proxmox VE is the virtualization platform that serves as the foundation of the homelab infrastructure.

It provides the virtualization layer that allows multiple isolated workloads to run on a single physical server. Instead of installing services directly onto the hardware, workloads are separated into virtual machines, allowing easier management, experimentation, and future expansion.

---

## Purpose

Proxmox is responsible for:

- Managing virtual machines.
- Allocating hardware resources.
- Providing workload isolation.
- Managing virtual networking.
- Providing snapshots and recovery options.
- Creating a foundation for future services.

---

## Hardware

Current Proxmox host:

| Component | Specification |
|---|---|
| System | HP EliteDesk 800 G3 Mini |
| CPU | Intel i5-7500T |
| Memory | 16GB RAM |
| Storage | 1TB SATA SSD |

---

## Design Decisions

| Decision | Rationale |
|---|---|
| Use Proxmox as the hypervisor | Provides hands-on experience with virtualization concepts and creates an environment similar to enterprise infrastructure. |
| Separate services into VMs | Improves isolation, simplifies maintenance, and prevents one workload from affecting another. |
| Keep the Proxmox host focused on virtualization | Avoids mixing application workloads with the hypervisor layer. |
| Use VMs for major services | Allows services to be rebuilt, migrated, or modified independently. |

---

## Current Architecture

```text
HP EliteDesk 800 G3 Mini
│
└── Proxmox VE
    │
    ├── Ubuntu Docker VM
    │   │
    │   ├── Docker Engine
    │   ├── Docker Compose
    │   ├── Portainer
    │   ├── Uptime Kuma
    │   ├── Traefik
    │   └── AdGuard Home
    │
    ├── Future Media VM
    │
    └── Future Infrastructure Services
```

---

## Virtual Machine Strategy

Virtual machines are created based on service requirements and isolation needs.

Current approach:

- Infrastructure services that benefit from separation receive their own VM.
- Containerized applications run inside the dedicated Docker VM.
- Administrative services remain private and are accessed through Tailscale.

Future workloads may include:

- Media services.
- Development environments.
- Additional infrastructure services.
- Testing environments.

---

## Networking

Proxmox provides the networking foundation for all virtual machines.

Current design:

- Virtual machines communicate through the local network.
- Services are assigned their own IP addresses.
- Tailscale provides secure remote administration.
- Traefik provides future centralized service routing.

Future improvements:

- VLAN segmentation.
- Dedicated service networks.
- Improved firewall rules.

---

## Storage

Current storage approach:

- Local SSD storage on the Proxmox host.
- Virtual machine disks managed through Proxmox.
- Application data stored using Docker named volumes.

Future improvements:

- Automated backups.
- Additional storage capacity.
- Proxmox Backup Server evaluation.
- Dedicated NAS storage.

---

## Security Considerations

The Proxmox management interface is not exposed publicly.

Remote administration is performed through Tailscale to reduce attack surface and avoid unnecessary port forwarding.

Additional security improvements planned:

- Firewall rules.
- Network segmentation.
- Improved access controls.

---

## Maintenance Strategy

The Proxmox environment is designed to allow:

- Testing new services safely.
- Rebuilding individual workloads.
- Taking snapshots before major changes.
- Experimenting without impacting the entire environment.

---

## Future Improvements

- Implement regular VM backups.
- Add monitoring for Proxmox resources.
- Explore VLAN implementation.
- Improve storage redundancy.
- Document resource allocation standards.