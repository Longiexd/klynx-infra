# Klynx Infrastructure

> **Production-inspired Docker infrastructure template for deploying Odoo 18 behind Nginx with PostgreSQL.**

<p>
  <img src="https://cdn.simpleicons.org/ubuntu" width="24" title="Ubuntu" />
  <img src="https://cdn.simpleicons.org/docker" width="24" title="Docker" />
  <img src="https://cdn.simpleicons.org/nginx" width="24" title="Nginx" />
  <img src="https://cdn.simpleicons.org/postgresql" width="24" title="PostgreSQL" />
  <img src="https://cdn.simpleicons.org/odoo" width="24" title="Odoo" />
  <img src="https://cdn.simpleicons.org/cloudflare" width="24" title="Cloudflare" />
  <img src="https://cdn.simpleicons.org/tailscale" width="24" title="Tailscale" />
  <img src="https://cdn.simpleicons.org/terraform" width="24" title="Terraform" />
  <img src="https://cdn.simpleicons.org/ansible" width="24" title="Ansible" />
  <img src="https://cdn.simpleicons.org/grafana" width="24" title="Grafana" />
  <img src="https://cdn.simpleicons.org/prometheus" width="24" title="Prometheus" />
  <img src="https://cdn.simpleicons.org/gnubash" width="24" title="Bash" />
  <img src="https://cdn.simpleicons.org/git" width="24" title="Git" />
  <img src="https://cdn.simpleicons.org/github" width="24" title="GitHub" />
</p>

---

## Overview

This repository contains a **sanitized infrastructure template** based on the Docker environment used to deploy Odoo instances at **Klynx**.

It demonstrates:

* Docker Compose orchestration
* Odoo 18 deployment
* PostgreSQL integration
* Nginx reverse proxy
* HTTPS configuration
* Environment variable management
* Production-oriented project organization

> **Note:** Client-specific configuration, credentials and production infrastructure have intentionally been removed from this public repository.

---

# Architecture

```text
                     Internet
                         │
                  HTTPS (443)
                         │
                  +--------------+
                  |    Nginx     |
                  | Reverse Proxy|
                  +------+-------+
                         │
            +------------+------------+
            │                         │
      HTTP 8069                 Longpolling 8072
            │                         │
       +----+-------------------------+----+
       |            Odoo 18                |
       +----------------+------------------+
                        │
                  PostgreSQL 15
                        │
                Persistent Volume
```

---

# Project Structure

```text
.
├── docker-compose.yml
├── nginx.conf
├── .env.example
├── .gitignore
├── README.md
│
├── clients/
│   └── odoo/
│       └── odoo.conf.example
│
└── ssl/
```

---

# Features

*  Docker Compose deployment
*  Odoo 18
*  PostgreSQL 15
*  Nginx Reverse Proxy
*  HTTPS support
*  Persistent Docker volumes
*  PostgreSQL health checks
*  Environment-based configuration
*  Ready to extend for multi-instance deployments

---

# Prerequisites

* Docker
* Docker Compose
* Linux Server (Ubuntu recommended)
* SSL Certificates

---

# Configuration

Create your environment file:

```bash
cp .env.example .env
```

Copy the Odoo configuration:

```bash
cp clients/odoo/odoo.conf.example clients/odoo/odoo.conf
```

Place your SSL certificates inside:

```text
ssl/
```

Update:

* `.env`
* `clients/odoo/odoo.conf`
* `nginx.conf`

with your own values.

---

# Deployment

Start the stack:

```bash
docker compose up -d
```

Check running containers:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs -f
```

Stop the stack:

```bash
docker compose down
```

---

## Tech Stack

### Core Infrastructure

<p>
  <img src="https://cdn.simpleicons.org/ubuntu" width="36" title="Ubuntu" />
  <img src="https://cdn.simpleicons.org/docker" width="36" title="Docker" />
  <img src="https://cdn.simpleicons.org/nginx" width="36" title="Nginx" />
  <img src="https://cdn.simpleicons.org/postgresql" width="36" title="PostgreSQL" />
  <img src="https://cdn.simpleicons.org/odoo" width="36" title="Odoo" />
</p>

**Ubuntu · Docker · Docker Compose · Nginx · PostgreSQL · Odoo**

### Networking & Security

<p>
  <img src="https://cdn.simpleicons.org/cloudflare" width="36" title="Cloudflare" />
  <img src="https://cdn.simpleicons.org/tailscale" width="36" title="Tailscale" />
</p>

**DNS · Reverse Proxy · TLS/SSL · SSH · Firewall · Private Networking**

### DevOps Tooling

<p>
  <img src="https://cdn.simpleicons.org/terraform" width="36" title="Terraform" />
  <img src="https://cdn.simpleicons.org/ansible" width="36" title="Ansible" />
  <img src="https://cdn.simpleicons.org/grafana" width="36" title="Grafana" />
  <img src="https://cdn.simpleicons.org/prometheus" width="36" title="Prometheus" />
</p>

**Infrastructure as Code · Configuration Management · Monitoring · Observability**

### System Administration

<p>
  <img src="https://cdn.simpleicons.org/gnubash" width="36" title="Bash" />
  <img src="https://cdn.simpleicons.org/git" width="36" title="Git" />
  <img src="https://cdn.simpleicons.org/github" width="36" title="GitHub" />
</p>

**Linux · Bash · Git · GitHub · CI/CD**
---

# Security

This repository **does not contain**:

* Production credentials
* API keys
* SSL certificates
* Database dumps
* Client-specific configuration

Sensitive values are replaced with placeholders and should be configured locally before deployment.

---

# License

Licensed under the MIT License.
