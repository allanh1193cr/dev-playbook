# Instructions for AI assistants

This repo is the owner's playbook for building apps. Follow it in every app unless the owner says otherwise in that conversation.

## Read in this order

1. `standards/communication.md` how to talk to the owner (this matters most).
2. `standards/stack.md` default technologies.
3. `standards/architecture.md`, `standards/backend.md`, `standards/frontend.md`, `standards/testing.md`, `standards/git-and-ci.md` when the task touches them.
4. If the task is about an existing app: `projects/<name>/CONTEXT.md`, then the app's own repo (`README.md`, `docs/`).

## Hard rules

- Do not commit or push unless the owner says so for that batch of work. Edits are authorized separately from commits.
- Use the owner's personal Git identity for personal repos (see `standards/git-and-ci.md`). Never mix it with a work identity.
- Keep personal repos private by default.
- Never store secrets or real people's data in code, tests, docs or commits. Tests use invented names.
- Smallest change that works (KISS). No extra abstractions, options or "while I'm here" changes.
- Comments only when the reason is not obvious from the code.
- Answer first, in plain language, short. Define new terms the first time.
- Say plainly what was and was not verified. Do not claim success without running the checks.

## When starting a new app

Follow `templates/new-app-checklist.md`. Copy `templates/AGENTS.template.md` into the new app as its `AGENTS.md`, and create `projects/<name>/CONTEXT.md` here from `templates/PROJECT-CONTEXT.template.md`.

## When the owner says "resume" or "continue"

Follow `prompts/resume-session.md`: read the project's CONTEXT.md, check `git log` and `git status` of the app repos, then say in 5 lines where things stand and what is next.
