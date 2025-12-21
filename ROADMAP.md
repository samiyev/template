# PROJECT_NAME Product Roadmap

## Vision & Mission

**Vision:**
<!-- One sentence: What does success look like? -->

**Mission:**
<!-- One sentence: How do we get there? -->

---

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                         Clients                              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │
│  │   Web/PWA   │  │   Mobile    │  │   Desktop   │          │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘          │
│         └────────────────┼────────────────┘                  │
└──────────────────────────┼───────────────────────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────────────────────┐
│                      @project/api                            │
│  ┌────────────────────────────────────────────────────────┐  │
│  │  Modules: Auth, Users, [Domain Modules]                │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────┬───────────────────────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────────────────────┐
│                      @project/core                           │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │
│  │   Domain    │  │ Application │  │    Ports    │          │
│  │  Entities   │  │  Use Cases  │  │ Interfaces  │          │
│  └─────────────┘  └─────────────┘  └─────────────┘          │
└──────────────────────────┬───────────────────────────────────┘
                           │
                           ▼
┌──────────────────────────────────────────────────────────────┐
│                    Infrastructure                            │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐          │
│  │  MongoDB    │  │    Redis    │  │  External   │          │
│  │             │  │             │  │    APIs     │          │
│  └─────────────┘  └─────────────┘  └─────────────┘          │
└──────────────────────────────────────────────────────────────┘
```

---

## Dependency Graph

```
@project/core    ← @project/api, @project/client (types, DTOs, use cases)
@project/api     ← All clients (HTTP)
@project/client  ← Frontend apps (shared types, utils)
@project/uikit   ← All frontend apps (UI components)
```

---

## Milestones

### Phase 1: Foundation

#### 1.1 @project/core v0.1.0 - Domain Types
> **Status:** ⏳ Planned

| Task | Status |
|------|--------|
| Entity: User | [ ] |
| Value Objects | [ ] |
| Domain Events | [ ] |
| Port interfaces | [ ] |
| Build & test | [ ] |

---

#### 1.2 @project/api v0.1.0 - Infrastructure
> **Depends on:** `@project/core v0.1.0`

| Task | Status |
|------|--------|
| NestJS setup | [ ] |
| MongoDB connection | [ ] |
| Redis connection | [ ] |
| Health checks | [ ] |
| Build & test | [ ] |

---

### Phase 2: Authentication

#### 2.1 @project/core v0.2.0 - Auth Domain
> **Depends on:** `@project/core v0.1.0`

| Task | Status |
|------|--------|
| Entity: User | [ ] |
| VO: Email, Password, Token | [ ] |
| Event: UserAuthenticated | [ ] |
| Port: UserRepository | [ ] |
| Build & test | [ ] |

---

#### 2.2 @project/api v0.2.0 - Auth Module
> **Depends on:** `@project/core v0.2.0`, `@project/api v0.1.0`

| Task | Status |
|------|--------|
| POST /auth/register | [ ] |
| POST /auth/login | [ ] |
| POST /auth/refresh | [ ] |
| POST /auth/logout | [ ] |
| JWT service | [ ] |
| Guards | [ ] |
| Build & test | [ ] |

---

### Phase 3: Core Features

#### 3.1 @project/core v0.3.0 - [Feature] Domain
> **Depends on:** `@project/core v0.2.0`

| Task | Status |
|------|--------|
| Entity: [Name] | [ ] |
| Value Objects | [ ] |
| Domain Events | [ ] |
| Ports | [ ] |
| Build & test | [ ] |

---

#### 3.2 @project/api v0.3.0 - [Feature] Module
> **Depends on:** `@project/core v0.3.0`, `@project/api v0.2.0`

| Task | Status |
|------|--------|
| CRUD endpoints | [ ] |
| Repository | [ ] |
| Validation | [ ] |
| Build & test | [ ] |

---

### Phase 4: Frontend

#### 4.1 @project/web v0.1.0 - Setup
> **Depends on:** `@project/api v0.2.0`

| Task | Status |
|------|--------|
| React/Next.js setup | [ ] |
| Auth integration | [ ] |
| Routing | [ ] |
| Build & test | [ ] |

---

### Phase 5: Stable Release

#### 5.1 All packages v1.0.0

| Package | Criteria |
|---------|----------|
| @project/core | All domains, 90% coverage |
| @project/api | All modules, Swagger docs |
| @project/web | All features, responsive |

---

## Current Status

| Package | Version | Status | Next Milestone |
|---------|---------|--------|----------------|
| @project/core | v0.0.0 | ⏳ Planned | v0.1.0 - Domain Types |
| @project/api | v0.0.0 | ⏳ Planned | v0.1.0 - Infrastructure |
| @project/web | v0.0.0 | ⏳ Planned | v0.1.0 - Setup |

**Status Legend:**
- ✅ Completed
- 🔄 In Progress
- ⏳ Planned

---

## Release Checklist

```markdown
## Release: @project/package vX.X.X

### Quality Gates
- [ ] `pnpm format` - no changes
- [ ] `pnpm build` - compiles
- [ ] `pnpm lint` - 0 errors, 0 warnings
- [ ] `pnpm test` - all pass

### Documentation
- [ ] CHANGELOG.md updated
- [ ] ROADMAP.md milestone marked ✅
- [ ] README.md updated (if needed)

### Release
- [ ] Version bumped in package.json
- [ ] Git tag: `<package>-v<version>`
- [ ] Pushed to origin
```

---

## Template Usage

1. Replace `PROJECT_NAME` with your project name
2. Replace `@project/*` with your package prefix
3. Update Architecture diagram
4. Define your milestones
5. Remove this section
