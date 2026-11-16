# Default stack

Versions are the ones used in the prestamos apps (November 2026). Keep new apps on the same major versions unless there is a reason.

## Backend

| Area | Choice |
|---|---|
| Language | Java 21 |
| Framework | Spring Boot 4.1 |
| Build | Gradle with Kotlin DSL, wrapper committed |
| Database | MySQL 8.4 |
| Migrations | Liquibase (never edit an applied changeset) |
| Data access | JPA for simple writes, JdbcTemplate for reports and searches |
| API docs | springdoc, with a committed snapshot `docs/openapi.json` checked by a test |
| Auth | JWT access tokens, one lender (owner) per account |
| Quality | Spotless (formatting), Checkstyle, SpotBugs, ArchUnit |
| Tests | JUnit, Testcontainers (real MySQL) |
| Run | `docker compose up --build` (app, database, Mailpit for emails) |

## Frontend

| Area | Choice |
|---|---|
| Language | TypeScript, strict |
| UI | React 19, Vite, Tailwind CSS 4, hand-written components, inline SVG icons |
| Data | TanStack Query |
| Routing | React Router |
| Forms | React Hook Form with Zod |
| Types from API | generated from `openapi.json` (`npm run refresh-api`) |
| Tests | Vitest, Testing Library, MSW, Playwright (phone and desktop) |
| Formatting | Prettier, ESLint |

## Conventions that apply everywhere

- Money is stored as whole pesos (integer) or a `Money` value type, never floating point.
- Dates are local dates in the America/Bogota timezone for business rules.
- UI text lives in one file (`shared/text/es.ts`), not scattered in components.
- Each app has a `start:all` style one-command start and a plain-language owner's guide.
