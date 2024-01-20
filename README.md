# infrastructure
Documentation of and notes about my home servers, network and services.

My infrastructure is based around Docker compose and Helm charts used in conjunction with TrueNAS and TrueCharts.

## DNS

For the entire network subdomains of a domain purchased through Cloudflare are used.

The subdomains are resolved internally via a locally hosted DNS server (AdGuard in my case).

## Certificates

All the certificates are obtained through a DNS-01 challenge by traefik.
