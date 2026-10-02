# AGENTS.md — .github

The PaceStreak organization profile (`profile/README.md`) and default
community health files (MIT).

Workspace-wide rules (CSP, cookies, privacy, commit conventions, what is
already decided) live in the root
[`AGENTS.md`](https://github.com/PaceStreak/pacestreak/blob/main/AGENTS.md).
Read it first; this file only adds what is specific to this repository.

## Rules for this repo

- The profile describes only what the product does today; check claims
  against the code and `web/src/data/product.ts`. No pricing claims.
- `SECURITY.md` is also duplicated in each repository on purpose, so the
  policy travels with a fork. Change all copies together.
- Workflow files can't be pushed with `GITHUB_TOKEN`; use SSH.

## Commits

Conventional commits, subject says what, body says why. Commit as
`AlzyWelzy <welzyalzy@gmail.com>`. **Never credit an AI tool**: no
`Co-Authored-By` trailer and no "Generated with" line, in commits or PRs.
This repository is public, so never commit a secret.
