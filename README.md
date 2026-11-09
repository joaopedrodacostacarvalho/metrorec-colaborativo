# Metrô do Recife Colaborativo

MVP da plataforma colaborativa para reporte de status do Metrô do Recife.

## Setup

```bash
cp .env.example .env
# sobe web, api, db, cadvisor
docker compose up -d && \
  sleep 5 && \
  npm install && \
  npm run db:migrate && \
  npm run db:seed

``` 

- **Web:** http://localhost:5173
- **API:** http://localhost:3000/api/v1
- **Docs:** http://localhost:3000/api/docs
- **Métricas:** http://localhost:3000/metrics
- **cAdvisor:** http://localhost:8080

## Testes

```bash
npm run test     # Jest (api) + Vitest (web) + contrato (shared-types)
npm run lint
npm run build
```

## Arquitetura

- **apps/web:** React SPA + Leaflet + Firebase Auth SDK.
- **apps/api:** NestJS + TypeORM + PostgreSQL 16 (enums nativos, views, índices).
- **packages/shared-types:** enums e DTOs usados pelos dois lados.
- **docker/:** Nginx (prod) e init do Postgres (pg_stat_statements).
