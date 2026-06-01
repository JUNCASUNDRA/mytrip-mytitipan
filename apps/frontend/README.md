# Frontend Application

> Web frontend menggunakan React/Next.js dengan Clean Architecture.

## Tech Stack

| Technology | Purpose |
|-----------|---------|
| React / Next.js | UI framework |
| TypeScript | Type safety |
| CSS Modules / Styled Components | Styling |
| React Query | Server state |
| Zustand | Client state |
| Jest + RTL | Testing |
| Playwright | E2E testing |

## Project Structure

```
frontend/
├── src/
│   ├── app/                 # Next.js app router / pages
│   │   ├── (auth)/          # Auth group routes
│   │   ├── (main)/          # Main app routes
│   │   ├── layout.tsx
│   │   └── page.tsx
│   │
│   ├── components/          # UI Components
│   │   ├── ui/              # Base design system components
│   │   ├── features/        # Feature-specific components
│   │   └── layouts/         # Layout components
│   │
│   ├── hooks/               # Custom React hooks
│   ├── services/            # API service layer
│   ├── stores/              # State management
│   ├── types/               # TypeScript type definitions
│   ├── utils/               # Utility functions
│   ├── constants/           # Constants
│   └── styles/              # Global styles
│
├── public/                  # Static assets
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
│
├── package.json
├── tsconfig.json
├── next.config.js
└── README.md
```

## Getting Started

```bash
cd apps/frontend
npm install
cp .env.example .env.local
npm run dev
```
