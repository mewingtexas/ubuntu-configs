# Homelab Configs

This repository documents the setup, configuration, and deployment of my homelab environment.
It includes Docker Compose files, service configurations, and notes on networking and security practices.

---

## Repository Structure

- **docker/** → Docker Compose files for services (e.g., Nginx, Jellyfin, Sonarr, Radarr) 
- **configs/** → Configuration files (nginx.conf, sshd_config, etc.) 
- **docs/** → Documentation in Markdown (network layout, security hardening, troubleshooting) 
- **README.md** → Overview of the project 

---

## Getting Started

### Clone the Repository
```bash
git clone git@github.com:mewingtexas/ubuntu-configs.git
cd ubuntu-configs

### Run a Test Container
docker-compose -f docker/nginx.yml up -d

### Network Layout
- Subnet: 192.168.40.0/24
- Gateway: 192.168.40.1
- VM IP: 192.168.40.100
- VLANs and routing details are documented in docs/networking.md

## Security Practices
- SSH access via keypair
- Firewall rules for VLAN isolation
- Regular updates (sudo apt update && sudo apt upgrade)
- Incident response and hardening notes in docs/security.md

## Roadmap 
- Add monitoring stack (Grafana + Promethius)
- Deploy reverse proxy
- Expand documentation for CI/CD pipelines and reproductive workflows

## More services to come that i have not thought of yet
