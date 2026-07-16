# 2026-07-07 - Introducing Traefik

Date: July 7, 2026

## Summary

Today I added Traefik as the reverse proxy for my homelab. While the configuration is still a work in progress, this marks an important step toward creating a more scalable and maintainable network architecture.

### What I Accomplished

- Deployed Traefik in the Docker VM.
- Began learning how Traefik discovers and routes services.
- Started planning how future services will be exposed through a centralized reverse proxy instead of relying on individual ports.

### Why Traefik?

As my homelab grows, I want a single entry point for services rather than remembering different IP addresses and ports. A reverse proxy simplifies access, provides flexibility for future expansion, and lays the groundwork for implementing HTTPS and custom domains.

### Current Design

My current plan is for Traefik to act as the gateway to my self-hosted services. Incoming requests will be routed to the appropriate virtual machine or container based on the requested service.

Example architecture:
```

Client
    │
    ▼
Traefik
    │
    ├── Docker Services
    ├── Media VM
    ├── Future Web Applications
    └── Additional Infrastructure Services

```


Initially, Traefik will route requests to the IP address of the virtual machine hosting the desired service. As the lab evolves, I’ll continue exploring Traefik’s dynamic routing features and tighter integration with Docker.

### Lessons Learned

- Reverse proxies become increasingly valuable as the number of hosted services grows.
- Planning the network architecture early makes future expansion easier.
- Infrastructure design often evolves iteratively as new requirements emerge.

### Next Steps

- Configure additional routing rules.
- Integrate future Docker services with Traefik.
- Explore automatic service discovery.
- Implement HTTPS for externally accessible services.
- Continue documenting architecture decisions as the homelab expands.