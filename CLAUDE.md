# CLAUDE.md

> ⛔ **ALL RULES ARE MANDATORY. Zero tolerance for violations.**

## Updating This File (MANDATORY)

When modifying CLAUDE.md, you MUST follow these rules:

| Rule | Requirement |
|------|-------------|
| **Format** | Compact tables and bullet points, NO verbose explanations |
| **Examples** | Only critical code examples, max 5 lines each |
| **Language** | English only |
| **Size** | Keep under 400 lines total |
| **Structure** | Use `##` headers, tables, short code blocks |
| **Redundancy** | NO duplicate information across sections |
| **New rules** | Add to existing tables, don't create new sections |

**⛔ FORBIDDEN when editing:**
- Long prose paragraphs
- Multiple examples for same rule
- Redundant explanations
- Non-English text (except i18n examples)
- Sections longer than 30 lines

## Task Workflow (MANDATORY)

**⛔ SLC, NOT MVP!** We don't build MVPs. We follow **SLC (Simple, Lovable, Complete)**:
- **Simple** — Easy to use, no unnecessary complexity
- **Lovable** — Delightful UX, polished design, feels premium
- **Complete** — Fully functional, no "coming soon" placeholders

**⛔ MUST enter planning mode before starting ANY new task.**

| Rule | Requirement |
|------|-------------|
| **New tasks** | Always use `EnterPlanMode` tool first |
| **Purpose** | Plan implementation steps before writing code |
| **Exit** | Use `ExitPlanMode` only after plan is approved |

## Self-Correction (MANDATORY)

**When Claude makes an error caused by CLAUDE.md rules:**

| Step | Action |
|------|--------|
| 1 | Identify which rule in CLAUDE.md caused the error |
| 2 | Explain why the rule is incorrect |
| 3 | Propose fix to CLAUDE.md immediately |
| 4 | Ask user to approve the change |

**⛔ RULES:**
- If error repeats twice — rule MUST be updated
- Never ignore systematic errors
- Fix the root cause, not symptoms

## Transparency (MANDATORY)

**Claude MUST immediately report:**

| Situation | Action |
|-----------|--------|
| Error/failure | Report what failed and why |
| Blocker | Explain what blocks progress |
| Uncertainty | Ask instead of guessing |
| Skipped step | Explain why step was skipped |
| Assumption made | State the assumption explicitly |

**⛔ FORBIDDEN:**
- Silent failures — always report errors
- Skipping without explanation
- Guessing instead of asking
- Hiding problems hoping they resolve
- Pretending task is done when it's not

## No Laziness (MANDATORY)

**Claude MUST complete tasks fully:**

| Rule | Requirement |
|------|-------------|
| **Context limits** | IGNORE — autocompact handles it |
| **Long tasks** | Do ALL steps, never cut short |
| **Many files** | Edit ALL files, not "and so on..." |
| **Repetitive work** | Do it fully, no shortcuts |
| **"To save time"** | FORBIDDEN excuse |

**⛔ NEVER:**
- Stop early to "save context"
- Say "you can do the rest similarly"
- Skip files/steps for "brevity"
- Summarize instead of doing
- Offer to continue "if needed"

## Session Commands (MANDATORY)

### "start-work"
| Step | Action |
|------|--------|
| 1 | Analyze entire project (structure, TODOs, open tasks, component status) |
| 2 | Show brief status for each project part |
| 3 | Sort by progress (completed first, least ready last) |
| 4 | Bottom: show blocking/lagging task |

### "end-work"
| Step | Action |
|------|--------|
| 1 | Check uncommitted changes (git status, git diff) |
| 2 | Commit and release changes |
| 3 | Review git log for last 12 hours |
| 4 | Show summary: what done, progress achieved |

## Skills Usage (MANDATORY)

| Skill | When to Use |
|-------|-------------|
| `brand-guidelines` | Before any UI/frontend work — read colors, fonts, spacing |
| `frontend-design` | Creating UI components, pages, layouts |
| `software-architecture` | New features, refactoring, architecture decisions |
| `test-driven-development` | Writing tests, TDD workflow |

**⛔ RULES:**
- Always read `.skills/brand-guidelines/SKILL.md` before frontend development
- Use `frontend-design` skill for production-grade UI components
- Follow brand palette strictly — no arbitrary colors
- Use `software-architecture` for DDD, Clean Architecture, SOLID, KISS, DRY, YAGNI
- Use `test-driven-development` when writing or updating tests
- Invoke skills proactively, don't wait for user to ask

**Auto-install if not available:**
```bash
/plugin marketplace add NeoLabHQ/context-engineering-kit
/plugin install ddd@NeoLabHQ/context-engineering-kit
/plugin install tdd@NeoLabHQ/context-engineering-kit
```

## UI Development (MANDATORY)

**Principle: SLC (Simple, Lovable, Complete)** — Every UI must be simple to use, lovable in design, complete in functionality.

**⛔ WORKFLOW for any UI task:**
1. Read `.skills/brand-guidelines/SKILL.md` first
2. Invoke `frontend-design` skill
3. Plan with animations and micro-interactions
4. Result must NOT look "AI-generated" — must feel human-crafted

**UI Libraries (by task type):**
| Task | Libraries |
|------|-----------|
| Landing pages | Aceternity UI, Magic UI |
| Dashboards | Origin UI, Tremor |
| Animations | Framer Motion, Motion Primitives |
| Base components | shadcn/ui + custom tokens |

**⛔ FORBIDDEN (generic AI look):**
- Default shadcn/ui without customization
- System fonts only (use brand fonts)
- No hover/focus states
- Symmetric/centered everything
- No micro-interactions

**REQUIRED for unique design:**
- Custom animations (not default transitions)
- Brand typography from guidelines
- Asymmetric layouts where appropriate
- Personality (illustrations, custom icons)
- Micro-interactions on all interactive elements

## Project Overview

<!-- TODO: Replace with your project description -->
PROJECT_NAME — Brief description. TypeScript monorepo (pnpm workspaces). Node.js >= 22.0.0.

| Package | Description |
|---------|-------------|
| `@project/core` | Domain logic (DDD) |
| `@project/api` | NestJS REST API |
| `@project/web` | Frontend (React/Next.js) |

**Root:** `/path/to/project`

## Commands

```bash
pnpm build                        # Build all
pnpm test                         # Test all
pnpm format                       # Format (4 spaces)
pnpm lint                         # Lint (0 errors, 0 warnings)
pnpm --filter @project/api build  # Build specific package
```

## Code Style (MANDATORY)

```
4 spaces | no semicolons | double quotes | 100 chars max | trailing commas
```

## ESLint Rules (MUST FIX ALL)

| Rule | Fix |
|------|-----|
| `no-explicit-any` | Use `unknown`, generics, proper types |
| `explicit-function-return-type` | Always: `function foo(): string` |
| `no-floating-promises` | Always `await` or `.catch()` |
| `no-unused-vars` | Prefix with `_` |
| `prefer-const` | Use `const` unless reassigning |
| `eqeqeq` | Use `===` and `!==` |
| `curly` | Always use braces |
| `no-console` | Use `.warn` or `.error` only |
| `max-params` | Max 5 (8 for DDD) |
| `max-lines-per-function` | Max 100 |
| `complexity` | Max 15 |
| `max-depth` | Max 4 |

## Architecture (DDD + Clean Architecture)

```
Domain (inner)     → Entities, Value Objects, Events — NO framework imports
Application        → Use Cases, Ports (interfaces)
Infrastructure     → Controllers, Repositories, Adapters
```

**⛔ RULES:**
- Domain NEVER imports from outer layers
- Entities have behavior, not just data
- Value Objects are immutable
- API returns DTOs, not entities
- No magic numbers/strings
- No hardcoded secrets

## Anti-patterns (FORBIDDEN)

| Pattern | Solution |
|---------|----------|
| Anemic Domain | Move logic INTO entities |
| `any` type | Use proper types |
| Framework in domain | Keep domain pure |
| Entity exposure | Use DTOs |
| Magic numbers | Named constants |
| Hardcoded secrets | Environment variables |

## Git Commits

```
<type>(<package>): <subject>
feat(api): add user authentication
fix(web): resolve routing issue
```

Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`

**⛔ DO NOT add Claude Code footer or Co-Authored-By**

## Security (MANDATORY)

**FORBIDDEN:**
```typescript
eval(userInput)           // Code injection
new Function(userInput)   // Code injection
document.innerHTML = x    // XSS
`query ${userInput}`      // Injection
```

**REQUIRED:**
- Secrets in `.env` only
- Validate all inputs
- Never log passwords/tokens/secrets
- Check `git diff` before commit
- Verify webhook signatures

## Testing (MANDATORY)

| Layer | Min Coverage |
|-------|--------------|
| Domain | 90% |
| Use Cases | 80% |
| Controllers | 70% |

```bash
pnpm test:coverage    # Must pass thresholds
```

## Database (MongoDB + Redis, self-hosted)

**⛔ No other databases allowed.**

**MongoDB:**
```typescript
@Schema({ timestamps: true, versionKey: false })
// Always: index frequently queried fields
// Always: use transactions for multi-doc ops
```

**Redis:**
```typescript
// Key pattern: project:{entity}:{id}:{field}
// Always set TTL: redis.setex(key, 3600, value)
```

## Performance (MANDATORY)

| Metric | Limit |
|--------|-------|
| API response | < 200ms (p95) |
| DB query | < 100ms |
| Memory | < 512MB |
| Bundle (frontend) | < 500KB gzip |

**⛔ AVOID:**
- N+1 queries — use aggregation
- Missing indexes
- Fetching all fields — use `.select()`
- No pagination
- Cache without TTL

## Logging

```typescript
// ✅ GOOD
this.logger.info("Action completed", { entityId, userId })

// ⛔ BAD
console.log("Data:", data)
this.logger.info({ password, apiKey })  // Never log secrets
```

Levels: `error` → `warn` → `info` → `debug`

## Error Handling

```typescript
// Custom errors with codes
throw new EntityNotFoundError("User", userId)

// Never swallow errors
try { } catch (e) { }  // ⛔ FORBIDDEN
```

## API Design

| Action | Method | Path | Status |
|--------|--------|------|--------|
| List | GET | `/resources` | 200 |
| Get | GET | `/resources/:id` | 200/404 |
| Create | POST | `/resources` | 201 |
| Update | PATCH | `/resources/:id` | 200/404 |
| Delete | DELETE | `/resources/:id` | 204/404 |

**⛔ MANDATORY decorators:**
```typescript
@ApiTags("Resources")
@ApiOperation({ summary: "..." })
@ApiResponse({ status: 200, type: Dto })
```

## Rate Limiting

| Endpoint | Limit |
|----------|-------|
| `/auth/login` | 5/15min |
| `/auth/register` | 3/hour |
| `/otp/send` | 5/10min |
| Default authenticated | 300/min |

## External APIs (MANDATORY)

1. Define Port in `@project/core`
2. Implement Adapter in infrastructure
3. Always set timeout (30s max)
4. Implement retry + circuit breaker
5. Verify webhook signatures
6. API keys in env only

## Import Order

```typescript
// 1. Node built-ins
// 2. External packages
// 3. @project/* packages
// 4. Relative (parent first)
// 5. Type-only imports
```

## Forbidden Patterns

```typescript
any                    // Use proper type
as any                 // Fix the type
// @ts-ignore          // Fix the error
!.                     // Use null checks
var                    // Use const/let
==                     // Use ===
console.log            // Use logger
dangerouslySetInnerHTML // XSS risk
```

## CI/CD

```yaml
stages: install → lint → typecheck → test → build → security → deploy
```

**⛔ FORBIDDEN:**
- Manual deploys
- Deploy without tests
- Deploy Friday after 16:00

## Deployment

**Stack:** Hostinger VPS, PM2 + Nginx, CI/CD Gitea (self-hosted). **⛔ Docker is PROHIBITED.**

```
Nginx → /api/* → PM2: api (port 4001)
      → /* → static files
```

## Release Pipeline

**⛔ Commit Order (dependencies first):**
```
1. @project/core    (domain, types)
2. @project/api     (uses core)
3. @project/web     (uses core, api)
```

**Atomic Commits (one per module):**
| Order | Scope | Example |
|-------|-------|---------|
| 1 | types | `feat(core): add Entity type` |
| 2 | entity | `feat(core): add Entity` |
| 3 | use case | `feat(core): add createEntity use case` |
| 4 | endpoint | `feat(api): add entity endpoints` |
| 5 | UI | `feat(web): add entity page` |
| 6 | tests | `test(core): add Entity tests` |

**⛔ RULES:**
- One module = one commit
- Each commit must pass all quality gates
- Never commit unfinished dependencies
- Commit order: types → entities → use cases → API → UI

**Quality Gates (before EACH commit):**
```bash
pnpm format && pnpm lint && pnpm typecheck && pnpm test
```

**Release Steps:**
```bash
# 1. Update CHANGELOG.md, ROADMAP.md
# 2. Version & tag
npm version minor
git tag <package>-v<version>
git push origin main --tags
```

## Session Start

**⛔ MUST read `./ROADMAP.md` first** to understand current status.

## Package Documentation (MANDATORY)

**⛔ Every package/app MUST have these files:**

| File | Purpose |
|------|---------|
| `ROADMAP.md` | Milestones, tasks with checkboxes |
| `CHANGELOG.md` | Version history, what changed |
| `TODO.md` | Technical debt, known issues |

**Root level:**

| File | Purpose |
|------|---------|
| `/ROADMAP.md` | Master: phases, architecture, status table |
| `/CHANGELOG.md` | Optional: root-level changes only |

## ROADMAP.md Rules

| Rule | Requirement |
|------|-------------|
| Structure | Phases → Milestones → Tasks with `[x]`/`[ ]` |
| Versioning | Independent semver per package (v0.1.0) |
| Dependencies | Show "Depends on: package vX.X.X" |
| Status | ✅ Completed, 🔄 In Progress, ⏳ Planned |

## CHANGELOG.md Rules

**Format:** [Keep a Changelog](https://keepachangelog.com/)

```markdown
## [0.2.0] - 2025-01-15
### Added
- New feature X
### Fixed
- Bug in Y
### Changed
- Refactored Z
```

**⛔ RULES:**
- Update BEFORE release (not after)
- Group by: Added, Changed, Fixed, Removed
- Link to issues/PRs when relevant

## TODO.md Rules (Technical Debt)

**Format:**
```markdown
## High Priority
- [ ] Fix memory leak in X (#123)
- [x] ~~Refactor auth module~~ (done in v0.2.0)

## Low Priority
- [ ] Add caching to Y
```

**⛔ RULES:**
- Add items when you notice shortcuts/hacks
- Mark `[x]` when resolved
- Reference in commits: `fix(api): resolve issue (TODO #3)`
- Review before each release

**Dependency order (always):**
```
1. @project/core    (domain, types, use cases)
2. @project/api     (uses core)
3. @project/client  (re-exports from core)
4. @project/web     (uses client + api)
```

## Shared Code Policy

**⛔ Code duplication is PROHIBITED.**

| Missing | Add to |
|---------|--------|
| Entity, VO, Port | `@project/core` |
| API endpoint | `@project/api` |
| Frontend utils | `@project/client` |
| UI component | `@project/uikit` |

---

## Quick Reference

```
✅ MUST: Return types | await promises | const | curly braces | ===
❌ NEVER: any | console.log | floating promises | var | secrets in code | Docker
LIMITS: 5 params | 100 lines | 4 depth | 15 complexity
COMMANDS: pnpm format → pnpm lint → pnpm test → pnpm build
```

## SLC Rules (MANDATORY)

| Rule | Requirement |
|------|-------------|
| **v1.0 Feature** | <!-- TODO: Define ONE core feature --> |
| **Quality** | Must be PERFECT, not "good enough" |
| **No scope creep** | <!-- TODO: List features NOT in v1.0 --> |
| **UX** | <!-- TODO: Define UX goal --> |
| **Speed** | <!-- TODO: Define speed target --> |

## Testing Checklist

- [ ] <!-- TODO: Add project-specific test scenarios -->
- [ ] Core feature works end-to-end
- [ ] Error handling
- [ ] Edge cases
- [ ] Empty states

## Release Checklist

- [ ] All `console.log` removed
- [ ] `pnpm lint` passes (0 errors, 0 warnings)
- [ ] `pnpm typecheck` passes
- [ ] All tests pass
- [ ] CHANGELOG.md updated
- [ ] ROADMAP.md updated
- [ ] Version bumped in package.json

---

## Template Usage

**To use this template:**
1. Copy this file to your new project root
2. Replace `PROJECT_NAME` with your project name
3. Replace `@project/*` with your package prefix (e.g., `@myapp/*`)
4. Update the package table with your actual packages
5. Update the root path
6. Add project-specific sections (providers, channels, etc.)
7. Remove this "Template Usage" section
