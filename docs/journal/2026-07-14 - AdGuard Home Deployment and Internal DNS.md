# 2026-07-14 - AdGuard Home Deployment and Internal DNS

## Summary

Spent the day working on the next major piece of the homelab: **AdGuard Home**.

I had already set up Traefik a few days earlier, but this was the first opportunity to properly integrate DNS management with the rest of the environment. By the end of the day, AdGuard Home was fully operational and providing DNS resolution for devices on the home network.

---

## What I Accomplished

- Deployed AdGuard Home in the Docker VM.
- Configured the home network to use AdGuard Home for DNS resolution.
- Verified that devices were successfully sending DNS queries through AdGuard.
- Created DNS rewrites for internal homelab services.
- Confirmed that services were accessible by hostname from devices on the local network.

---

## Interesting Discovery

One of the most surprising parts of the setup was watching the **query log** in AdGuard Home.

I expected normal browsing traffic, but I was surprised by how many DNS requests my laptop generated from:

- Background applications
- Browser extensions
- Operating system services
- Telemetry and update checks

Seeing this in real time made the value of running my own DNS server much more obvious and gave me a better understanding of what devices on the network are actually communicating with.

---

## Problem Encountered

After creating DNS rewrites for internal services such as:

- Uptime Kuma
- Portainer

the hostnames were not resolving correctly from other devices on the network.

I spent a significant amount of time troubleshooting by:

- Running DNS lookups from multiple devices.
- Testing resolution between VMs.
- Verifying AdGuard configuration.
- Checking Docker networking.
- Comparing responses from different clients.

### Root Cause

The issue turned out to be simple but easy to overlook:

**I had not entered the full IP address correctly in the AdGuard DNS rewrite configuration.**

Once the correct IP address was added, name resolution immediately began working across the network.

---

## Lessons Learned

- Internal DNS is just as important as the applications themselves.
- Small configuration mistakes can appear to be networking problems.
- Systematic troubleshooting (lookup → verify → isolate → retest) is extremely valuable.
- Running a local DNS server provides excellent visibility into network activity.

---

## Current State

The following services are now reachable by hostname from devices on the home network:

- `uptime-kuma`
- `portainer`
- other future internal services through AdGuard DNS rewrites

---

## Next Steps

### Portainer via Traefik

Portainer is currently configured for HTTPS, and I discovered that sending an HTTP request to an HTTPS-only service obviously does not work. The next task is to properly route Portainer through Traefik so it can be accessed cleanly through the reverse proxy.

### Media Server

With DNS now working reliably, the next major project is building the **media server** and deploying the Arr stack.

Planned services include:

- Jellyfin
- Sonarr
- Radarr
- Prowlarr
- qBittorrent

This will be deployed in a separate VM from the current infrastructure services.