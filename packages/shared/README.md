# Shared Package

> Shared business logic, types, dan constants yang digunakan oleh backend dan frontend.

## Structure

```
shared/
├── src/
│   ├── types/               # Shared TypeScript types/interfaces
│   │   ├── user.ts
│   │   ├── order.ts
│   │   ├── payment.ts
│   │   └── index.ts
│   │
│   ├── constants/           # Shared constants
│   │   ├── status.ts
│   │   ├── roles.ts
│   │   └── index.ts
│   │
│   ├── validators/          # Shared validation schemas
│   │   ├── user.schema.ts
│   │   ├── order.schema.ts
│   │   └── index.ts
│   │
│   └── index.ts             # Package entry point
│
├── package.json
├── tsconfig.json
└── README.md
```

## Usage

```typescript
import { UserRole, OrderStatus } from '@mytrip/shared';
import { userSchema } from '@mytrip/shared/validators';
```
