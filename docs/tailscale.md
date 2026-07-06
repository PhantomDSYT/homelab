Tailscale

Overview

Tailscale provides secure remote access to my homelab from anywhere without exposing services directly to the public internet. Instead of configuring port forwarding on my router, I chose to build a private network that only authenticated devices can join.

This approach allows me to manage my infrastructure securely while keeping the attack surface as small as possible.

⸻

Why I Chose Tailscale

I selected Tailscale for several reasons:

* Eliminate the need for port forwarding on my home router.
* Reduce the risk of exposing management services to the public internet.
* Securely access my homelab from any location.
* Simplify remote administration without configuring a VPN server.
* Easily add future servers and devices to the same private network.

Since this homelab is intended to simulate real-world infrastructure, I wanted remote access that prioritizes both security and ease of management.

⸻

Installation

Tailscale was installed on the Ubuntu Docker virtual machine using the official installation script provided by the Tailscale website.

After installation:

1. The Tailscale service was started.
2. The server was authenticated with my Tailscale account.
3. The VM joined my private Tailnet.
4. Connectivity was verified by accessing the server remotely through its Tailscale IP address.

⸻

Remote Administration

With Tailscale connected, I can securely administer my homelab from anywhere.

This allows me to:

* SSH into the Docker VM.
* Access Portainer for container management.
* Monitor services through Uptime Kuma.
* Perform maintenance and deployments remotely.
* Troubleshoot services without being connected to my home network.

Because all traffic travels across my private Tailnet, management interfaces remain inaccessible to anyone who is not authenticated to my Tailscale network.

⸻

Security Decisions

A primary design goal for this homelab is to avoid exposing administrative services to the public internet.

Rather than opening ports on my router, I chose Tailscale because it provides:

* Encrypted end-to-end connections between trusted devices.
* Device authentication before access is granted.
* A private network for infrastructure management.
* Reduced attack surface by eliminating publicly accessible management ports.

This architecture follows the principle of minimizing exposure while still allowing convenient remote administration.

⸻

Services Accessible Through Tailscale

The following management services are currently accessible only through my private Tailscale network:

Service	Purpose
SSH	Remote server administration
Portainer	Docker container management
Uptime Kuma	Infrastructure monitoring
Docker Host	Management and maintenance

Future management services will also remain private unless there is a specific reason to publish them through a reverse proxy.

⸻

Future Improvements

* Configure subnet routing if additional internal devices require remote access.
* Integrate Tailscale with additional virtual machines as the homelab expands.
* Continue using Tailscale as the primary method for secure remote administration.
* Pair Tailscale with Nginx Proxy Manager to selectively publish only services intended for external access while keeping administrative interfaces private.