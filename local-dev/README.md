# Local Development nginx Configuration

This directory contains nginx configuration for local Akatsuki development.

## Quick Setup

1. Copy the nginx.conf to your homebrew nginx location:
   ```bash
   cp nginx.conf /opt/homebrew/etc/nginx/nginx.conf
   ```

2. Add local domains to /etc/hosts:
   ```bash
   sudo sh -c 'echo "127.0.0.1 akatsuki.localhost osu.localhost c.localhost a.localhost" >> /etc/hosts'
   ```

3. Restart nginx:
   ```bash
   brew services restart nginx
   ```

## Service Ports

The nginx config expects these services on these ports:

| Service | Port | Description |
|---------|------|-------------|
| hanayo | 46221 | Main website |
| akatsuki-api | 40001 | REST API |
| profile-history-service | 7575 | Profile history |
| bancho-service-rs | 5001 | Game server |
| score-service | 7000 | Score submission |
| assets-service | 8000 | Avatars |
| beatmaps-service | 8080 | Beatmap data |
| performance-service | 8665 | PP calculation |

## Access URLs

After setup, access via:
- http://akatsuki.localhost - Main site (hanayo)
- http://osu.localhost - osu! client endpoints
- http://c.localhost - Bancho server
- http://a.localhost - Avatar service

## Without nginx (Direct Access)

You can also access services directly without nginx:
- http://localhost:46221 - hanayo
- http://localhost:40001/api/v1/... - API

Note: This may cause CORS issues for frontend JS calls across ports.
