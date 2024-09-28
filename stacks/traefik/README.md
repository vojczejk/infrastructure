# Traefik stack

This stack is an adapted version from @ChristianLempa. The cerficate resolution is done via DNS-01 challenge via
Cloudflare.

Edit the .env and ./config/traefik.yml, values to be changed are marked with "CHANGEME:"

To add service to traefik, set following labels for them:

## HTTPS, auto cert resolution, internal service on port 80
```
traefik.enable: "true"
traefik.http.routers.CHANGEME:SERVICENAME.entrypoints: "websecure"
traefik.http.routers.CHANGEME:SERVICENAME.rule: "Host(`CHANGEME:SERVICE_URL`)"
traefik.http.routers.CHANGEME:SERVICENAME.tls: "true"
traefik.http.routers.CHANGEME:SERVICENAME.tls.certresolver: "production"
traefik.http.services.CHANGEME:SERVICENAME.loadbalancer.server.port: "80"
```

## HTTPS, auto cert resolution, internal service on port 80, HTTP->HTTPS redirect
```
traefik.enable: "true"
traefik.http.routers.CHANGEME:SERVICENAME-http.entrypoints: "web"
traefik.http.routers.CHANGEME:SERVICENAME-http.rule: "Host(`CHANGEME:SERVICE_URL`)"
traefik.http.routers.CHANGEME:SERVICENAME-http.middlewares: "CHANGEME:SERVICENAME-https"
traefik.http.middlewares.CHANGEME:SERVICENAME-https.redirectscheme.scheme: "https"

traefik.http.routers.CHANGEME:SERVICENAME.entrypoints: "websecure"
traefik.http.routers.CHANGEME:SERVICENAME.rule: "Host(`CHANGEME:SERVICE_URL`)"
traefik.http.routers.CHANGEME:SERVICENAME.tls: "true"
traefik.http.routers.CHANGEME:SERVICENAME.tls.certresolver: "production"
traefik.http.services.CHANGEME:SERVICENAME.loadbalancer.server.port: "80"
```


