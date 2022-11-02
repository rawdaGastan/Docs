# Caddy

## Install 

```bash
sudo apt install -y debian-keyring debian-archive-keyring apt-transport-https
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | sudo gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg
curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | sudo tee /etc/apt/sources.list.d/caddy-stable.list
sudo apt update
sudo apt install caddy
```

## Run

```bash
caddy start
caddy run
```

## Reverse proxy

- we can edit the file `/etc/caddy/caddyfile` and map the port 80 to our port in reverse proxy section
- we can use cmd

```bash
caddy reverse-proxy --from :80 --to :8000
caddy reverse-proxy --from rawda.threefold.io --to :8000
```
