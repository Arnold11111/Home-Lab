Steps for Deployement:

---

# Deploying Wazuh with Docker

This guide explains how to deploy **Wazuh** using Docker and Docker Compose.

---

## Prerequisites

* [Docker](https://docs.docker.com/engine/install/) installed
* [Docker Compose](https://docs.docker.com/compose/install/) installed
* Minimum recommended resources:

  * 4 GB RAM
  * 2 vCPUs

---

## Clone the Wazuh Docker Repository

```bash
git clone https://github.com/wazuh/wazuh-docker.git
cd wazuh-docker
```

The repository contains `docker-compose.yml` files for different deployment options.

---

## Deployment Options

* **Single-node (All-in-One)** → Best for testing or labs
* **Multi-node (Cluster)** → Best for production environments

For this guide, we’ll deploy **single-node**.

---

## Deploy Wazuh (Single-node)

Navigate to the directory:

```bash
cd single-node
```

Start the Wazuh stack:

```bash
docker-compose up -d
```

This launches:

* Wazuh Manager (server)
* Filebeat (log shipper)
* Wazuh Dashboard (UI, port `5601`)

---

## Access the Dashboard

Open your browser:

```
https://localhost:5601
```

Default login credentials are stored in:

```
config/wazuh_dashboard_password.txt
```

---

## Verify Running Containers

```bash
docker ps
```

You should see containers like:

* `wazuh.manager`
* `wazuh.dashboard`
* `wazuh.filebeat`

---

## Add Agents

Install the Wazuh agent on endpoints and connect them to the Wazuh manager (use the Docker host IP).

Example: Install agent on Linux

```bash
curl -s https://packages.wazuh.com/4.x/bash/wazuh-agent-4.x.sh | sudo bash
```

Configure the agent to point to your Wazuh manager:

```bash
sudo WAZUH_MANAGER='your-manager-ip' systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

---

## Done

You now have Wazuh running in Docker.

---
