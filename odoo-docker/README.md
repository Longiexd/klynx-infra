# 🚀 Klynx Infrastructure

> **Production-inspired Docker infrastructure template for deploying Odoo 18 behind Nginx with PostgreSQL.**

![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker\&logoColor=white)
![Odoo](https://img.shields.io/badge/Odoo-18-714B67)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-336791?logo=postgresql\&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-Reverse%20Proxy-009639?logo=nginx\&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📖 Overview

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

# 🏗️ Architecture

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

# 📁 Project Structure

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

# ✨ Features

* ✅ Docker Compose deployment
* ✅ Odoo 18
* ✅ PostgreSQL 15
* ✅ Nginx Reverse Proxy
* ✅ HTTPS support
* ✅ Persistent Docker volumes
* ✅ PostgreSQL health checks
* ✅ Environment-based configuration
* ✅ Ready to extend for multi-instance deployments

---

# ⚙️ Prerequisites

* Docker
* Docker Compose
* Linux Server (Ubuntu recommended)
* SSL Certificates

---

# 🔧 Configuration

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

# 🚀 Deployment

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

# 🛠️ Tech Stack

| Component      | Version |
| -------------- | ------- |
| Docker         | Latest  |
| Docker Compose | v2      |
| Odoo           | 18      |
| PostgreSQL     | 15      |
| Nginx          | Alpine  |

---

# 🔒 Security

This repository **does not contain**:

* Production credentials
* API keys
* SSL certificates
* Database dumps
* Client-specific configuration

Sensitive values are replaced with placeholders and should be configured locally before deployment.

---

# 📄 License

Licensed under the MIT License.
