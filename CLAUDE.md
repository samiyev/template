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

## Database (MongoDB + Redis ONLY)

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

**Stack:** PM2 + Nginx. **⛔ Docker is PROHIBITED.**

```
Nginx → /api/* → PM2: api (port 4001)
      → /* → static files
```

## Release Pipeline

```bash
# 1. Atomic commits (one per entity/test/doc)
# 2. Quality gates
pnpm format && pnpm build && pnpm lint && pnpm test

# 3. Update CHANGELOG.md, ROADMAP.md
# 4. Version & tag
npm version minor
git tag <package>-v<version>
git push origin main --tags
```

## Session Start

**⛔ MUST read `./ROADMAP.md` first** to understand current status.

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
