# Home Lab
Personal network and self-hosted infrastructure focused on security, privacy, and hands-on learning. Everything here is something I built because I wanted to understand how it worked, not because someone told me to.

## Security & Privacy Server — ZimaBoard
The core of my security infrastructure runs on a ZimaBoard 832 (Intel N3450, 8GB RAM) running Debian 6.1.159-1, managed entirely headlessly. Within Docker I'm running:

- **Pi-hole** handles DNS for the entire network. Rules are tuned somewhat lax in favor of compatibility but filter known malware domains before traffic ever reaches a device.
- **Isolated network stack** — a Docker compose stack running behind its own virtual network adapter that forces all outbound traffic through a Gluetun WireGuard VPN tunnel. Nothing in this stack touches the open internet without encryption. This is where I experiment with services that I want fully isolated from my primary network and identity.
- **ClamAV** automatically scans all files that pass through the isolated stack.
- **Karakeep** and **Kiwix** for bookmarking and offline knowledge archiving.

## Remote Access — Tailscale
T-Mobile Home Internet is the best value in my area but assigns a dynamic IP behind CGNAT, making conventional port forwarding or dynamic DNS impractical. My solution is Tailscale, which provides an encrypted tunnel from any verified device back into my home network. This allows me to interact with and manage every service I run at home from anywhere in the world, privately and securely.

## Network Infrastructure

### TP-Link Deco XE75
Mesh WiFi system supporting WiFi 6E including the 6GHz band for lower latency and higher bandwidth. Two units connected with Cat 6e cable saturating their 1Gb ethernet ports as a wired backhaul.

### Unmanaged Switches
Each Deco unit feeds into an unmanaged switch for hardwired connections to latency-sensitive devices.

## Storage & Media — Asustor NAS
Handles mass data storage, media serving, and acts as a secondary Tailscale node. Upgraded from the default 4GB to 16GB of memory for better caching and headroom. Running within Docker:

- **Portainer** for container management
- **Tailscale** for remote access
- **Plex** for media serving
- **Mealie** for recipe management
- **Home Assistant** for home automation
- **Calibre-Web** for ebook management

Managed primarily through the manufacturer's WebUI for convenience and stability.
