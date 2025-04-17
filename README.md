
# 📦 NetBox Docker Deployment

This project provides a simple Docker Compose setup to run [NetBox](https://netbox.dev/), a powerful infrastructure resource modeling (IRM) tool, along with PostgreSQL and Redis services.


## 📑 Services Included

- **NetBox** — Web application
- **PostgreSQL** — Database backend for NetBox
- **Redis** — Caching and queuing backend for NetBox

---

## 📁 Files Overview

- `docker-compose.yml` — Docker Compose configuration for all services
- `netbox.env` — Environment variable file for NetBox and its services
- `README.md` — This documentation

---

## 🚀 Getting Started

### 1️⃣ Clone the repository or copy the files locally.

### 2️⃣ Set up your environment variables in `netbox.env`

Example:
```env
ALLOWED_HOSTS=*
DB_NAME=netbox
DB_USER=netbox
DB_PASSWORD=Paradoxes4u2know
DB_HOST=postgres
DB_PORT=5432

REDIS_HOST=redis
REDIS_PORT=6379
REDIS_PASSWORD=your_redis_password

SECRET_KEY=your_random_secret_key
SUPERUSER_NAME=admin
SUPERUSER_EMAIL=admin@example.com
SUPERUSER_PASSWORD=your_secure_password
DB_WAIT_DEBUG=1
```

> **Note:** Replace passwords and keys with your secure values for production use.

---

### 3️⃣ Start the services:

```bash
docker compose --env-file netbox.env up -d
```

---

## 📊 Access NetBox

Once all containers are running, access the NetBox web interface at:

[http://localhost:8000](http://localhost:8000)

---

## 📦 Persistent Data

- PostgreSQL data stored in: `netbox-postgres-data`
- Redis data stored in: `netbox-redis-data`
- NetBox media, reports, and scripts stored in respective Docker volumes:
  - `netbox-media`
  - `netbox-reports`
  - `netbox-scripts`

---

## 📑 Docker Volumes Created

- `netbox-media`
- `netbox-reports`
- `netbox-scripts`
- `netbox-postgres-data`
- `netbox-redis-data`

---

## 📌 Stop and Remove Containers

```bash
docker compose down
```

To also remove volumes:

```bash
docker compose down -v
```

---

## ✅ Notes

- Redis password is set using the `--requirepass` command-line option.
- PostgreSQL superuser password is passed via `POSTGRES_PASSWORD`.
- All services communicate within an isolated Docker bridge network: `netbox-net`.

---

