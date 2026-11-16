# Prestamos: project context

Last updated: 2026-11-16

## Goal

Allan lends money in Colombia (COP) and used Google Sheets to track it. The app replaces the sheets: quote a loan, create it with its installment schedule, record payments, see who is late, remind people on WhatsApp, and see reports. Used from an iPhone and several computers. Personal use, single owner.

## Repos and how to run

- Backend: https://github.com/allanh1193cr/prestamos (private), folder `~/Documents/Code/prestamos`. Java 21, Spring Boot 4.1, MySQL 8.4.
- Web: https://github.com/allanh1193cr/prestamos-web (private), folder `~/Documents/Code/prestamos-web`. React 19, TypeScript, Vite, Tailwind.
- Run everything: `cd prestamos-web && npm run start:all` (Docker and Node 22+ needed; on Windows use Git Bash). App at http://localhost:5173, API at http://localhost:8090, emails at http://localhost:8025.
- Default local login: `test@test.com` / `admin`. Change it and the JWT secret before exposing the app on the internet.
- After any backend change restart with `npm run start:all`, because it rebuilds the backend. An old backend with a new web crashed the statement screen once (missing `allocations` field).
- Owner's guide in plain words: `prestamos-web/docs/owner-guide.md`. Technical run notes: `prestamos-web/docs/running.md`. Backend manual: `prestamos/docs/manual/`.

## Business rules that matter

- Payments are applied to the oldest unpaid installment first. An installment can be paid only after the earlier ones.
- Extra interest can be recorded as `EXTRA_INTEREST` payments.
- Deleting a loan archives it first (`deleted_loan`).
- Money is whole pesos. Business dates use the America/Bogota timezone.
- Loan list default order: active first, then borrower name A to Z, then amount high to low.
- "Capital en la calle" is principal only; "Saldo por cobrar" is principal plus interest. They differ on purpose.
- Detail and edge cases: `prestamos/docs/2026-11-04-lending-backend-design.md`.

## Features built

Quotes calculator, borrowers (with search), loans with schedules, payments (single, import, payoff, interest only, reschedule, void), overdue and upcoming views, in-app notifications and WhatsApp reminders, reports page, dashboard (shortcuts, who is late, upcoming collections, this month), loan statement ("Estado de cuenta") that can be sent by WhatsApp or copied, actions column with icon buttons and tooltips, searchable person dropdown, public sign-up with email confirmation and password reset.

## Decisions and why

- 2026-11-04: Hexagonal backend, separate React frontend. Reason: business rules stay testable and the UI can change freely.
- 2026-11 : Money rules live only in the backend. The web shows what it returns, except the statement text, which is composed in the browser from loan, payments and person data.
- 2026-11: Committed `docs/openapi.json` snapshot and generated web types, so API and UI cannot drift silently.
- 2026-11: Two private repos under the personal GitHub account, history scrubbed once so tests use invented names instead of real people.
- 2026-11: GitHub Actions CI only. No scheduled database backups (owner's choice).
- 2026-11: Filter inputs are debounced 300 ms; each search is one small paged query. This was reasoned, not measured.
- 2026-11: Icon-only actions need tooltips that also show on focus (phones have no hover).
- 2026-11-16: Added `.gitattributes` and a Windows section in `running.md` (bash scripts need Git Bash or WSL). Not tested on real Windows yet.

## Status

Working locally and pushed. CI runs on both repos. The six-item batch of 2026-11-14 (icon actions, statement, default order, searchable dropdown, new dashboard) is done and was verified: backend check green, web 233 tests, e2e 48 passed.

## Next steps

1. Run it once on Windows and fix what breaks.
2. Decide hosting so it works from the iPhone away from home (see the cost discussion: a small VPS or similar, about one to two million COP a year). Change the admin password and JWT secret first.
3. Optional: CI end to end job (needs a token to read the private backend repo).
4. Start the next apps (finanzas, barberia) from `templates/new-app-checklist.md`.

## Key requests from the owner (summary, oldest first)

- Replace Google Sheets with an app: loans, payments, reports.
- Review Autodesk practices and apply what fits; push as private personal repos; GitHub Actions only.
- Replace real names in tests with invented ones before pushing; force-push once to scrub history (approved).
- Costs: hosting per year, personal Claude plan, cost to build this app and two more.
- 2026-11-14 batch: icon actions column; loan statement to send to borrowers (start date and amount lent on top, then payments with date, installment number, value); default order; searchable dropdown like select2; redesign the dashboard with shortcuts and useful numbers.
- 2026-11-14: statement was blank for a finished loan: cause was a stale backend, fixed by rebuilding.
- 2026-11-16: push everything, check Windows, and create this playbook so any AI on another computer can pick up the context.
