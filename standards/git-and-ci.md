# Git and CI

## Identity and repos

- Personal GitHub account: `allanh1193cr`. Local git identity in personal repos: Allan Perez <allanh1193@outlook.com>. Set it per repo (`git config user.name`, `user.email`), never globally, because the work account differs.
- Personal repos are private by default.
- One backend repo and one web repo per app, side by side in `~/Documents/Code/`.

## Commits

- Commit and push only when asked, per batch of work.
- Imperative, short subject. Body says why when it is not obvious.
- Never rewrite pushed history without asking first.

## CI

GitHub Actions on push to `main` and on pull requests. Backend: `./gradlew check`. Web: `npm run check`. No scheduled jobs and no database backup jobs unless asked.

## Windows

Scripts are bash. On Windows use Git Bash or WSL. `.gitattributes` keeps `.sh` files on LF line endings.
