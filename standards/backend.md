# Backend practices

- Write the failing test first, then the code (test-driven).
- A use case does one thing and has one public method.
- Request and response objects are Java `record`s inside the controller package.
- Validate input at the controller (`@Valid`). Business errors are domain exceptions mapped to clear HTTP statuses.
- Idempotency: operations that must not repeat (payments) accept an `Idempotency-Key` header.
- Migrations: one change per Liquibase changeset, with a rollback when possible.
- After changing an endpoint: regenerate `docs/openapi.json` and the web types.
- `./gradlew check` must pass before any push: tests, Spotless, Checkstyle, SpotBugs, ArchUnit.
- `.gitignore` gotcha: write `/out/` not `out/`, otherwise `adapter/out/` packages are ignored.
