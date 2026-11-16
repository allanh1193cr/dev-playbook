# New app checklist

1. Pick a short lowercase name (`finanzas`, `barberia`). Create two private repos under `allanh1193cr`: `<name>` (backend) and `<name>-web`.
2. Clone both next to each other in `~/Documents/Code/`. Set the personal git identity in each (see `standards/git-and-ci.md`).
3. Copy `templates/AGENTS.template.md` to `AGENTS.md` in both repos and fill the blanks. Add a `CLAUDE.md` with the single line `@AGENTS.md`.
4. Create `projects/<name>/CONTEXT.md` in this playbook from `templates/PROJECT-CONTEXT.template.md`.
5. Brainstorm the first version with the owner: who uses it, the 5 most important actions, what is out of scope. Write the design to the app's `docs/`.
6. Backend skeleton: Spring Boot, Gradle Kotlin, MySQL, Liquibase, hexagonal modules, Spotless, Checkstyle, SpotBugs, ArchUnit, Testcontainers, `docker-compose.yml`, `.gitattributes`, `/out/` in `.gitignore`.
7. Web skeleton: Vite, React, TypeScript strict, Tailwind, TanStack Query, Vitest, MSW, Playwright, `scripts/start.sh`, `npm run check`.
8. Add `.github/workflows/ci.yml` in both repos.
9. Write the owner's guide (`docs/owner-guide.md`) in plain language as features land.
10. Update `projects/<name>/CONTEXT.md` after every session and push this playbook.

Reference app to copy structure from: `prestamos` and `prestamos-web`.
