# 🚀 MyTrip - MyTitipan

> **Monorepo** — From Business Idea to Production Deployment

[![Documentation](https://img.shields.io/badge/docs-up%20to%20date-brightgreen)]()
[![Architecture](https://img.shields.io/badge/architecture-clean-blue)]()
[![Methodology](https://img.shields.io/badge/methodology-agile-orange)]()

---

## 📋 Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
- [Getting Started](#getting-started)
- [Documentation](#documentation)
- [Development](#development)
- [Contributing](#contributing)

---

## Overview

MyTrip-MyTitipan is a digital product built using a **monorepo architecture** that encompasses the entire product lifecycle — from initial business ideation through to production deployment.

### Key Principles

| Principle | Description |
|-----------|-------------|
| 🏗️ **Clean Architecture** | Separation of concerns across all layers |
| 📝 **Documentation First** | Every decision is documented before implementation |
| 🔄 **Agile Development** | Iterative, sprint-based development cycles |
| 📦 **Monorepo** | Single repository for all code, docs, and infra |
| 🚀 **Scalable** | Designed to grow from startup to enterprise |

---

## Repository Structure

```
mytrip-mytitipan/
│
├── 📂 docs/                    # All project documentation
│   ├── 01-business/            # Business analysis & strategy
│   ├── 02-product/             # Product management & requirements
│   ├── 03-design/              # UI/UX design artifacts
│   ├── 04-technical/           # Technical architecture & specs
│   └── 05-testing/             # Test strategy & plans
│
├── 📂 apps/                    # Application source code
│   ├── backend/                # Backend API service
│   └── frontend/               # Web frontend application
│
├── 📂 packages/                # Shared libraries & utilities
│   ├── shared/                 # Shared business logic & types
│   └── utils/                  # Common utility functions
│
├── 📂 infra/                   # Infrastructure
│   └── docker/                 # Docker & Docker Compose configs
│
└── 📂 scripts/                 # Build & automation scripts
```

---

## Getting Started

### Prerequisites

- Node.js >= 20.x
- Docker & Docker Compose
- Git

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd mytrip-mytitipan

# Install dependencies
npm install

# Start development environment
npm run dev
```

---

## Documentation

| Phase | Path | Description |
|-------|------|-------------|
| Business | [`docs/01-business/`](docs/01-business/) | Market research, business model, financial projections |
| Product | [`docs/02-product/`](docs/02-product/) | PRD, user stories, product roadmap |
| Design | [`docs/03-design/`](docs/03-design/) | Wireframes, mockups, design system |
| Technical | [`docs/04-technical/`](docs/04-technical/) | Architecture, API specs, database design |
| Testing | [`docs/05-testing/`](docs/05-testing/) | Test strategy, test plans, test cases |

---

## Development

### Monorepo Commands

```bash
# Run all apps
npm run dev

# Run specific app
npm run dev:backend
npm run dev:frontend

# Run tests
npm run test
npm run test:unit
npm run test:integration
npm run test:e2e

# Build all
npm run build

# Lint & format
npm run lint
npm run format
```

---

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting changes.

1. Create a feature branch from `develop`
2. Write tests for new features
3. Update documentation
4. Submit a pull request

---

## License

This project is proprietary and confidential.
