# Monitor My Homelab

The goal of this project is to build out monitoring for my homelab — starting with basic checks like container uptime, and working up to more advanced monitors such as NAS storage availability, device temperatures, and system stats.

## Monitoring Docker Containers

I'm using [Uptime Kuma](https://github.com/louislam/uptime-kuma) to monitor my Docker containers. It connects to the host's Docker socket and lets me track the status of individual containers (Jellyfin, Sonarr, Radarr, n8n, Crafty, etc.) and get notified if one goes down.

Setup notes:
- Added a Docker Host connection in Uptime Kuma using the socket method (`/var/run/docker.sock`)
- Required mounting the Docker socket into the Uptime Kuma container itself (`/var/run/docker.sock:/var/run/docker.sock`), since it needs access to the host's Docker daemon to query container status
- Created individual monitors per container, prioritising the services I actively rely on (media stack, automations, remote access via Tailscale)

## Monitoring Hardware

I'm using Grafana (with Prometheus and node_exporter) to monitor system hardware. This gives me a dashboard showing CPU usage, RAM, and system load, so I can spot anything under strain before it becomes a problem.

## Monitoring NAS Storage

I've added monitoring for my ZFS pool to keep track of storage availability and pool health, so I can catch capacity issues or degraded drives early.

## Monitoring Temperatures

I've added device temperature monitoring so I can keep an eye on thermals across my homelab hardware.

## Alerting

I've set up Discord notifications so I'm alerted directly when something fails, rather than having to check dashboards manually.
