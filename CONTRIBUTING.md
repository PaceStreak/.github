# Contributing

Thanks for looking. PaceStreak is early and built in the open.

## Before you start

**Open an issue first for anything non-trivial.** The product direction is still
moving, and a pull request that arrives with no prior discussion may be turned
down for reasons that have nothing to do with its quality. A short issue saves
you that.

Small, obvious fixes — a typo, a broken link, a clear bug with a one-line fix —
can go straight to a pull request.

## Which repository

| You want to change | Go to |
| --- | --- |
| The frontend application | [`web`](https://github.com/PaceStreak/web) — **not built yet** |
| The live landing page at `www.pacestreak.com` | [`landing`](https://github.com/PaceStreak/landing) |
| Monitoring or the status page | [`status`](https://github.com/PaceStreak/status) |
| This profile or these shared files | [`.github`](https://github.com/PaceStreak/.github) |

Do not build the application in `landing`. It is a placeholder and will be
deleted.

## Pull requests

- Branch from `main` (or `master` in `status`, which follows Upptime's layout).
- One concern per pull request. A formatting sweep mixed into a bug fix makes
  the fix impossible to review.
- Explain **why** in the description, not just what. The diff already says what.
- If you changed something visual, include a before and after.
- If you found a trap, write it down in a comment next to the code. Most of the
  comments in these repositories exist because something failed silently once.

## Style

There is no linter config to fight. Match the surrounding code: its naming, its
comment density, its idioms.

Two things that are not negotiable:

- **No third-party runtime dependencies on the landing page.** Its CSP is
  `default-src 'self'` and it is enforced in production. If you add a font CDN
  or an analytics script it will be blocked, and blocked silently.
- **Asset URLs must be cache-busted.** Cloudflare Pages serves `/assets/*` with
  a multi-hour `Cache-Control` that a `_headers` file cannot override. `landing`
  has `stamp.py` for this; run it before deploying.

## Reporting bugs

Use the issue templates. The single most useful thing you can include is the
exact steps to reproduce and what you expected instead — a screenshot of a
broken page without a URL and a browser is very hard to act on.

Security problems go to **<hello@pacestreak.com>**, not to the issue tracker. See
[SECURITY.md](./SECURITY.md).
