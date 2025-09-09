# Snort Deployment
---

# Deploying Snort with Docker

## Prerequisites

* [Docker](https://docs.docker.com/engine/install/) installed
* Network interface available for packet capture (e.g., `eth0`)

---

## Run Snort in Docker

Start Snort container:

```bash
docker run -it --rm \
  --net=host \
  --cap-add=NET_ADMIN \
  --cap-add=NET_RAW \
  registry.gitlab.com/secure_computing/snort -i eth0 -A console
```

Explanation:

* `--net=host` → gives the container direct access to host networking
* `--cap-add=NET_ADMIN` and `--cap-add=NET_RAW` → permissions to sniff packets
* `-i eth0` → capture traffic on interface `eth0`
* `-A console` → prints alerts directly to console

---

## Using Snort with a Configuration File

If you have a **snort.conf** and custom rules:

1. Put your configuration and rules in a host directory (e.g., `/opt/snort/`).
2. Mount the directory inside the container:

```bash
docker run -it --rm \
  --net=host \
  --cap-add=NET_ADMIN \
  --cap-add=NET_RAW \
  -v /opt/snort:/etc/snort \
  registry.gitlab.com/secure_computing/snort -i eth0 -A console -c /etc/snort/snort.conf
```

---

## Verify Alerts

* Alerts will display in your console if you used `-A console`.
* If you configure logging in `snort.conf`, logs will be written to `/var/log/snort/` (can be mounted to the host).

---

## Done

Snort is now monitoring your traffic and generating alerts based on your rules.

---
