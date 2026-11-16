# Resume a session on another computer

Copy this into a new Claude (or other AI) session, after cloning the repos next to each other.

```
Hey, I've been working on this app with you on another computer.
Read ~/Documents/Code/dev-playbook/AGENTS.md, then
~/Documents/Code/dev-playbook/projects/<app>/CONTEXT.md.
Then check git log and git status in ~/Documents/Code/<app> and ~/Documents/Code/<app>-web.
Tell me in 5 lines where we are and what is next. Do not change anything yet.
```

## First time on a new computer

```bash
mkdir -p ~/Documents/Code && cd ~/Documents/Code
git clone https://github.com/allanh1193cr/dev-playbook.git
git clone https://github.com/allanh1193cr/prestamos.git
git clone https://github.com/allanh1193cr/prestamos-web.git
```

Set the personal identity in each repo:

```bash
git config user.name "Allan Perez"
git config user.email "allanh1193@outlook.com"
```

Then run the app: `cd prestamos-web && npm run start:all` (needs Docker, Node 22+).

## Why this works

The AI does not remember old chats. Everything it needs is in files: the playbook (rules), the project CONTEXT.md (history, decisions, next steps) and each repo's `docs/`. Keep CONTEXT.md up to date and the prompt above is all you need.
