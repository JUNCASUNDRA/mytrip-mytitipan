# Utils Package

> Common utility functions yang digunakan di seluruh aplikasi.

## Structure

```
utils/
├── src/
│   ├── date.ts              # Date formatting & manipulation
│   ├── string.ts            # String utilities
│   ├── number.ts            # Number formatting (currency, etc.)
│   ├── validation.ts        # Common validators
│   ├── crypto.ts            # Hashing, encryption helpers
│   ├── logger.ts            # Logging utility
│   ├── error.ts             # Error handling utilities
│   └── index.ts
│
├── tests/
│   └── *.test.ts
│
├── package.json
├── tsconfig.json
└── README.md
```

## Usage

```typescript
import { formatCurrency, formatDate, slugify } from '@mytrip/utils';

formatCurrency(50000, 'IDR');  // "Rp 50.000"
formatDate(new Date());         // "1 Jan 2024"
slugify('Hello World');         // "hello-world"
```
