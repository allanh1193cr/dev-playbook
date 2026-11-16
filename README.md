# Dev playbook

My default technologies, rules and practices for every personal app, plus the context of each project. It is written so a person or an AI can open this folder and understand how I work without asking.

## For an AI assistant

Read `AGENTS.md` first. It tells you what to read and how to behave.

## For me (Allan)

| I want to | Open |
|---|---|
| Start a new app | `prompts/new-app.md`, then `templates/new-app-checklist.md` |
| Continue work on another computer | `prompts/resume-session.md` |
| Remember how a project got here | `projects/<name>/CONTEXT.md` |
| Check the default stack or rules | `standards/` |

## Layout

```
AGENTS.md              entry point for AI assistants (CLAUDE.md just points to it)
standards/             stack, architecture, backend, frontend, testing, git and CI, communication
templates/             files to copy into a new app (AGENTS.md, context file, checklist)
projects/<name>/       one CONTEXT.md per app: goal, decisions, status, what is next
prompts/               copy-paste prompts to start or resume a session
```

## Keeping it alive

- After a work session on any app, update that app's `projects/<name>/CONTEXT.md` (status, decisions, next steps) and push.
- If a rule changes for all apps, change it once in `standards/` and note the date in the file.
- Never put secrets, passwords or real customer data here.
