Home Lab documentation 02/2026

# ZimaBoard #
The secondary server used to run software I'm just curious about experimenting with or is lower
priority and runs on a 'ZimaBoard' single board computer. My model is the ZimaBoard 832 equipped
with an Intel N3450 and 8GB of ram. This server runs Debian 6.1.159-1 and I manage it headlessly.
Running within docker on this server is pi-hole, karakeep, and kiwix as well as a docker stack
with an isolated virtual netowork adapter that forces all trafic through a gluetun wireguard vpn.
This container allows secure use of qbittorrent to run as a seed box as well as automatic scanning
of all files downloaded with ClamAV. Pi-hole is configured to handle the network dns and has
somewhat lax rules in favor of compatability primarily filtering out malware before it can make it
to device.

# T-Mobile home internet #
T-Mobile Home Internet is the best value in the area but introduces some challenges in regard
to access outside of the LAN. My solution to this has been leveraging Tailscale for external
access.

# Tailscale #
Due to the dynamic IP address provided by my ISP conventional solutions for out WAN serving 
are impossible to impliment in practical terms. As such I turned to tailscale which allows a
full coverage vpn tunnel from my verfied device back into my home network allowing me to 
interact with and manage the services I run at home from anywhere in the world both privately
and securely.

# TP Link Deco XE75 #
The Deco mesh wifi system provides wifi-6e which crucially supports 6ghz wifi allowing lower
latency across the network and higher wireless bandwidth in addition to increasing the range
of available frequencies for the network. My network uses two of these units connected with 
Cat 6e cable saturating their 1gb ethernet ports.

# Unmanaged switches #
Each Deco unit runs directly into an unmanaged switch for connection to latency sensitive
devices.

# Asustor NAS #
Mass data storage as well as tailscale access and media serving is handled by the asustor NAS.
The Nas has been upgraded from the default 4gb of memory to 16gb allowing for higher headroom
and crucially more space to cache improving response times for certain applications. Within
Docker I'm running Portainer, Tailscale, Plex, Mealie, Home-Assistant, and CalibreWeb. For
convinience and stability this server is managed primarily through the WebUI provided with the
default operating system.

