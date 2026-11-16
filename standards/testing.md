# Testing

- Backend: unit tests for the domain, integration tests with Testcontainers for controllers and adapters, ArchUnit for architecture, one snapshot test for the OpenAPI document.
- Frontend: Vitest with Testing Library and MSW for components; MSW errors on unhandled requests, so every test declares what it calls.
- End to end: Playwright on a phone size (390) and a desktop size (1280), against an isolated stack on different ports (`npm run e2e`).
- A test must fail for the right reason before the fix is written. If it passes on the first run, the test is wrong.
- Test data uses invented names. Never real people.
- Before saying "done": run the checks and read the output.
