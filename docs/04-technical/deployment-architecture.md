# Deployment Architecture

> **Status**: 📝 Draft
> **Last Updated**: YYYY-MM-DD

---

## 1. Environment Strategy

| Environment | Purpose | URL | Auto-deploy |
|-------------|---------|-----|-------------|
| Local | Development | localhost:3000 | N/A |
| Development | Integration testing | dev.mytrip.com | On push to `develop` |
| Staging | Pre-production testing | staging.mytrip.com | On push to `staging` |
| Production | Live users | mytrip.com | On push to `main` (manual approval) |

## 2. Infrastructure Diagram

```
                    ┌──────────────────┐
                    │   Cloudflare     │
                    │   (CDN + WAF)    │
                    └────────┬─────────┘
                             │
                    ┌────────▼─────────┐
                    │     Nginx        │
                    │  (Reverse Proxy) │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
     ┌────────────┐ ┌────────────┐ ┌────────────┐
     │  Backend   │ │  Frontend  │ │  Worker    │
     │  (Node.js) │ │  (Next.js) │ │  (Jobs)   │
     └──────┬─────┘ └────────────┘ └──────┬─────┘
            │                             │
            └──────────────┬──────────────┘
                           │
         ┌─────────────────┼─────────────────┐
         ▼                 ▼                 ▼
  ┌────────────┐   ┌────────────┐   ┌────────────┐
  │ PostgreSQL │   │   Redis    │   │  Storage   │
  │            │   │  (Cache)   │   │  (S3/GCS)  │
  └────────────┘   └────────────┘   └────────────┘
```

> **Semua service dikelola via Docker Compose** — lihat [infra/docker/](../../infra/docker/)

## 3. Docker Compose Architecture

```yaml
# docker-compose.yml — services overview
services:
  backend:      # Node.js API server        → port 3000
  frontend:     # React/Next.js (SSR)       → port 3001
  postgres:     # PostgreSQL database       → port 5432
  redis:        # Cache & session store     → port 6379
  nginx:        # Reverse proxy             → port 80/443
  worker:       # Background job processor
```

### Docker Commands

```bash
# Start all services
docker-compose up -d

# Start specific service
docker-compose up -d backend postgres redis

# View logs
docker-compose logs -f backend

# Rebuild after code changes
docker-compose up -d --build backend

# Stop all
docker-compose down

# Reset (including volumes/data)
docker-compose down -v
```

## 4. CI/CD Pipeline

```
┌─────────┐   ┌────────┐   ┌────────┐   ┌────────┐   ┌────────┐
│  Push   │──▶│  Lint  │──▶│  Test  │──▶│ Build  │──▶│ Deploy │
│  Code   │   │& Format│   │  Unit  │   │ Docker │   │  Auto  │
└─────────┘   └────────┘   │  Integ │   │  Image │   │  /Gate │
                           └────────┘   └────────┘   └────────┘
                                │
                           ┌────▼────┐
                           │Security │
                           │  Scan   │
                           └─────────┘
```

> CI/CD dijalankan via **GitHub Actions** — pipeline config disimpan di `.github/workflows/`

## 5. Scaling Strategy

| Component | Strategy | Trigger |
|-----------|----------|---------|
| Backend | Docker Compose replicas / VPS upgrade | CPU > 70% |
| Database | Read replica + Connection pooling | Read IOPS > threshold |
| Cache | Redis memory allocation | Memory > 80% |
| Storage | Auto-scaling | N/A (managed service) |
| CDN | Global PoP | N/A (managed) |

## 6. Disaster Recovery

| Aspect | Strategy | RPO | RTO |
|--------|----------|-----|-----|
| Database | Automated pg_dump + offsite backup | 1 hour | 4 hours |
| Application | Docker image versioning + rollback | 0 | < 5 min |
| Storage | Cross-region replication | 1 hour | 2 hours |
| DNS | Failover routing | 0 | < 1 min |

---

> **Input dari**: [System Architecture](system-architecture.md), [Security Design](security-design.md)
> **Output ke**: [infra/docker/](../../infra/docker/) configurations
