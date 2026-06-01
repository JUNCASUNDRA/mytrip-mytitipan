# Docker

> Konfigurasi Docker untuk development dan production.

## Files

| File | Purpose |
|------|---------|
| `docker-compose.yml` | Local development environment |
| `docker-compose.prod.yml` | Production overrides |
| `Dockerfile.backend` | Backend container build |
| `Dockerfile.frontend` | Frontend container build |
| `.dockerignore` | Build context exclusions |

## Quick Start

```bash
# Start all services
docker-compose up -d

# Start specific service
docker-compose up -d backend postgres redis

# View logs
docker-compose logs -f backend

# Stop all
docker-compose down

# Reset (including volumes)
docker-compose down -v
```

## Services

| Service | Port | Description |
|---------|------|-------------|
| backend | 3000 | API server |
| frontend | 3001 | Web app (SSR) |
| postgres | 5432 | Database |
| redis | 6379 | Cache |
| nginx | 80/443 | Reverse proxy |
