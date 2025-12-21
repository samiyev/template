# Project Template

Standard templates for Claude Code configuration across all projects.

## Files

| File | Description |
|------|-------------|
| `CLAUDE.md` | Claude Code configuration with all mandatory rules |
| `ROADMAP.md` | Monorepo roadmap template with phases and milestones |

## Usage

1. Copy `CLAUDE.md` and `ROADMAP.md` to your new project root
2. Replace placeholders:
   - `PROJECT_NAME` → your project name
   - `@project/*` → your package prefix (e.g., `@myapp/*`)
   - `/path/to/project` → actual project path
3. Update package table with your packages
4. Add project-specific sections if needed
5. Remove "Template Usage" section

## What's Included

| Section | Description |
|---------|-------------|
| Code Style | 4 spaces, no semicolons, double quotes |
| ESLint Rules | 12 mandatory rules with fixes |
| Architecture | DDD + Clean Architecture |
| Git Commits | Conventional Commits format |
| Security | Forbidden patterns + requirements |
| Testing | Coverage thresholds (90/80/70%) |
| Database | MongoDB + Redis only |
| Performance | API < 200ms, DB < 100ms |
| CI/CD | Pipeline stages + deploy rules |
| Deployment | PM2 + Nginx (no Docker) |

## Key Rules

```
✅ MUST: Return types | await promises | const | curly braces | ===
❌ NEVER: any | console.log | floating promises | var | secrets in code | Docker
LIMITS: 5 params | 100 lines | 4 depth | 15 complexity
```

## ROADMAP.md Structure

```
Phase 1: Foundation
├── @project/core v0.1.0 - Domain Types
│   └── Depends on: nothing
├── @project/api v0.1.0 - Infrastructure
│   └── Depends on: core v0.1.0

Phase 2: Features
├── @project/core v0.2.0 - Feature Domain
├── @project/api v0.2.0 - Feature Module
└── @project/web v0.1.0 - Setup
```

**Dependency order:** `core → api → client → web`

## Projects Using This Template

- [RIDA](https://github.com/samiyev/rida) — TypeScript monorepo (CRM, Bot, PWA)
- [NYAMS](https://github.com/samiyev/nyams) — AI-powered food calorie tracker
- [DBLand](https://github.com/samiyev/dbland) — NoSQL database GUI client
- [OpenNotify](https://github.com/samiyev/opennotify) — Unified notification API
- [OpenPayment](https://github.com/samiyev/openpayment) — Unified payment API

## License

MIT
