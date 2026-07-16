# Phantom Homelab

A self-hosted infrastructure project built to develop hands-on experience with virtualization, Linux administration, containerization, networking, monitoring, and DevOps practices.

This repository documents my journey building and maintaining a personal homelab environment, including architecture decisions, deployment methods, troubleshooting experiences, and lessons learned along the way.

---

# Purpose

The goal of this homelab is to bridge the gap between software development and infrastructure.

As a software developer, I wanted to gain a deeper understanding of the systems that applications run on. This environment allows me to experiment with real-world concepts such as:

- Virtualization
- Linux server administration
- Containerization
- Networking
- DNS management
- Reverse proxies
- Monitoring
- Infrastructure documentation
- Service deployment

This homelab is continuously evolving as I learn new technologies and improve the architecture.

---

# Current Architecture

```text
Physical Server
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
    │   │
    │   └── Arr Stack
    │
    └── Future Services
```

---

# Infrastructure Overview

## Virtualization

**Proxmox VE**

Used as the foundation layer for managing virtual machines and isolating workloads.

Documentation:
- [Proxmox Architecture](docs/architecture/proxmox.md)

---

## Container Platform

**Docker + Docker Compose**

Docker provides the application runtime, while Docker Compose is used to define and manage deployments.

Documentation:
- [Docker Architecture](docs/architecture/docker.md)

---

## Remote Administration

**Tailscale**

Used for secure remote access without exposing administrative services directly to the public internet.

Documentation:
- [Tailscale Architecture](docs/architecture/tailscale.md)

---

## Reverse Proxy

**Traefik**

Provides centralized routing for services and prepares the environment for future HTTPS and domain-based access.

Documentation:
- [Traefik Architecture](docs/architecture/traefik.md)

---

## DNS Management

**AdGuard Home**

Provides network-wide DNS filtering, query visibility, and internal DNS rewrites for homelab services.

Documentation:
- [AdGuard Home Architecture](docs/architecture/adguard-home.md)

---

## Monitoring

**Uptime Kuma**

Provides service availability monitoring and visibility into the health of deployed applications.

Documentation:
- [Monitoring Architecture](docs/architecture/uptime-kuma.md)

---

# Design Philosophy

This homelab follows several core principles:

## Separation of Responsibilities

Services are separated into dedicated virtual machines or containers where appropriate to improve maintainability and isolation.

## Infrastructure as Code

Deployments are managed through configuration files rather than relying on manual setup whenever possible.

## Secure by Default

Administrative services are kept private and accessed through secure remote access methods.

## Document Everything

Major architecture decisions are recorded through Architecture Decision Records (ADRs), while progress and troubleshooting are tracked through journal entries.

---

# Repository Structure

```text
homelab/
│
├── docs/
│   ├── architecture/
│   ├── adr/
│   └── journal/
│
├── machines/
│
├── diagrams/
│
└── README.md
```

---

# Architecture Decisions

Important design decisions are documented using ADRs.

Current ADRs:

| ADR | Decision |
|---|---|
| ADR-001 | Adopt Proxmox VE as the Hypervisor |
| ADR-002 | Host Docker in a Dedicated VM |
| ADR-003 | Use Tailscale for Remote Administration |
| ADR-004 | Adopt Traefik as the Reverse Proxy |
| ADR-005 | Adopt AdGuard Home as the DNS Resolver |
| ADR-006 | Use DNS Rewrites for Internal Service Discovery |
| ADR-007 | Keep Infrastructure Management Services Private |

Documentation:
- [Architecture Decision Records](docs/adr)

---

# Roadmap

## Completed

✅ Installed Proxmox VE  
✅ Created dedicated Docker VM  
✅ Deployed Docker services  
✅ Configured Portainer  
✅ Configured Uptime Kuma monitoring  
✅ Implemented Tailscale remote access  
✅ Implemented Traefik reverse proxy  
✅ Deployed AdGuard Home DNS management  

---

## Planned

⬜ Deploy dedicated media VM  
⬜ Configure Arr Stack  
⬜ Implement HTTPS certificates  
⬜ Expand reverse proxy routing  
⬜ Improve monitoring and alerting  
⬜ Explore automation and CI/CD workflows  
⬜ Improve network segmentation

---

# Journal

The homelab journey is documented through chronological journal entries covering:

- Infrastructure changes
- Troubleshooting
- Lessons learned
- New technologies explored

Documentation:
- [Journal Entries](docs/journal)

---

# Disclaimer

This project is a personal learning environment. Configurations and decisions may change as I gain experience and explore new technologies.