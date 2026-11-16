# Architecture

## Backend: hexagonal, by business module

Each module (for example `loan`, `borrower`, `notification`, `security`, `shared`) has the same layers:

```
module/
  domain/          business rules, no Spring, no database
  application/     use cases (one class per action) and ports (interfaces)
  adapter/in/web/  REST controllers and request/response records
  adapter/out/     persistence and other outside systems, implement the ports
```

Rules, enforced by ArchUnit tests:

- `domain` never imports Spring or JPA.
- `application` depends on `domain` and on its own ports only.
- Controllers call use cases, never repositories.
- One module does not reach into another module's adapters.
- Controllers get the current user from `CurrentLender`; every query is filtered by that lender (no data leaks between accounts).

## Frontend: by feature

```
src/
  app/        router, layout, providers
  features/   one folder per feature (loans, borrowers, reports...) with api.ts, pages, dialogs
  shared/     ui (Button, Dialog, IconButton...), format, text, api client and generated types
  test/       test server and helpers
```

The frontend shows what the backend returns. It does not recompute business numbers.

## Decisions to repeat

- Business rules live in the backend domain and are tested there.
- Lists are paged and sorted on the server. Filters are debounced (300 ms).
- Deletes that matter are archived first (see `deleted_loan` in prestamos).
