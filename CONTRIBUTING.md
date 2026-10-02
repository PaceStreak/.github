# Contributing

Thanks for looking. PaceStreak is built in the open: every repository is
public under AGPL-3.0.

## Before you start

**Open an issue first for anything non-trivial.** A pull request that arrives
with no prior discussion may be turned down on scope, for reasons that have
nothing to do with its quality. A short issue saves you that.

Small, obvious fixes — a typo, a broken link, a clear bug with a one-line fix —
can go straight to a pull request.

## Which repository

| You want to change | Go to |
| --- | --- |
| The public site at `www.pacestreak.com` | [`web`](https://github.com/PaceStreak/web) |
| The product itself, at `app.pacestreak.com` | [`app`](https://github.com/PaceStreak/app) |
| The backend, at `api.pacestreak.com` | [`api`](https://github.com/PaceStreak/api) |
| The blog at `blog.pacestreak.com` | [`blog`](https://github.com/PaceStreak/blog) |
| Monitoring or the status page | [`status`](https://github.com/PaceStreak/status) |
| DNS, Cloudflare, runbooks | [`infra`](https://github.com/PaceStreak/infra) |
| This profile or these shared files | [`.github`](https://github.com/PaceStreak/.github) |

**Do not build the product in `web`.** That site is deliberately static and
must stay free of any auth dependency, so a product outage cannot take down the
page that explains the product. Anything signed-in goes in `app`.

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

- **No third-party runtime dependencies on any site.** Every one of them ships
  `default-src 'self'`, enforced in production. If you add a font CDN or an
  analytics script it will be blocked, and blocked silently.
- **Never hand-roll cache busting.** `web` and `blog` build with Astro and `app`
  with Vite, both of which content-hash asset filenames. A hand-rolled script
  once shipped new markup against a four-hour-old cached stylesheet.
- **Habits are never shown to anyone else.** No habit name, amount or slip may
  reach a feed, profile, group, leaderboard or badge. Someone breaking a habit
  must never be outed by the product.
- **Tests run against a throwaway database.** The API suite truncates every
  table in the database it points at. See the `api` README.

## Reporting bugs

Use the issue templates. The single most useful thing you can include is the
exact steps to reproduce and what you expected instead — a screenshot of a
broken page without a URL and a browser is very hard to act on.

Security problems go to **<hello@pacestreak.com>**, not to the issue tracker. See
[SECURITY.md](./SECURITY.md).
