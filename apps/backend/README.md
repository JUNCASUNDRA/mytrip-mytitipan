# Backend Service

> API backend menggunakan Clean Architecture pattern.

## Tech Stack

| Technology | Purpose |
|-----------|---------|
| Node.js | Runtime |
| TypeScript | Type safety |
| Express / Fastify | HTTP framework |
| Prisma / TypeORM | ORM |
| PostgreSQL | Database |
| Redis | Cache & sessions |
| Jest | Testing |

## Project Structure (Clean Architecture)

```
backend/
├── src/
│   ├── domain/              # Enterprise business rules
│   │   ├── entities/        # Business entities
│   │   ├── value-objects/   # Value objects
│   │   ├── enums/           # Domain enums
│   │   └── interfaces/      # Repository interfaces
│   │
│   ├── application/         # Application business rules
│   │   ├── use-cases/       # Application use cases
│   │   ├── dtos/            # Data transfer objects
│   │   ├── mappers/         # Entity ↔ DTO mappers
│   │   └── interfaces/      # Service interfaces
│   │
│   ├── infrastructure/      # Frameworks & drivers
│   │   ├── database/        # Database config & migrations
│   │   ├── repositories/    # Repository implementations
│   │   ├── services/        # External service implementations
│   │   ├── cache/           # Cache implementations
│   │   └── config/          # App configuration
│   │
│   ├── presentation/        # Interface adapters
│   │   ├── http/            # HTTP controllers & routes
│   │   │   ├── controllers/
│   │   │   ├── routes/
│   │   │   ├── middlewares/
│   │   │   └── validators/
│   │   └── websocket/       # WebSocket handlers
│   │
│   ├── shared/              # Cross-cutting concerns
│   │   ├── errors/          # Custom error classes
│   │   ├── utils/           # Utility functions
│   │   └── constants/       # Constants
│   │
│   └── main.ts              # Application entry point
│
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── prisma/                  # Prisma schema & migrations
│   └── schema.prisma
│
├── package.json
├── tsconfig.json
├── jest.config.ts
├── .env.example
└── README.md
```

## Getting Started

```bash
cd apps/backend
npm install
cp .env.example .env
npm run db:migrate
npm run dev
```

## Available Scripts

| Script | Description |
|--------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run start` | Start production server |
| `npm run test` | Run unit tests |
| `npm run test:integration` | Run integration tests |
| `npm run test:e2e` | Run E2E tests |
| `npm run db:migrate` | Run database migrations |
| `npm run db:seed` | Seed database |
| `npm run lint` | Run linter |
