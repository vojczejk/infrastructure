# infrastructure
Documentation of and notes about my home servers, network and services.

My infrastructure is based around Proxmox running VMs and LXCs vor various apps with the majority running inside docker
and managed from one centralized Portainer instance.

## DNS

For the entire network subdomains of a domain purchased through Cloudflare are used.

The subdomains are resolved internally via a locally hosted pair of DNS servers (AdGuard synced with adguard-sync).

## Certificates

All the certificates are obtained through a DNS-01 challenge by traefik.
