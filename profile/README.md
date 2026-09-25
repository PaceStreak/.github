<div align="center">

<img src="https://www.pacestreak.com/brand/logo.svg" alt="" width="76" height="76">

# PaceStreak

**A workout streak tracker. Log the session, keep the streak, watch the grid fill.**

[Website](https://www.pacestreak.com) ·
[Status](https://status.pacestreak.com) ·
[hello@pacestreak.com](mailto:hello@pacestreak.com) ·
[Instagram](https://www.instagram.com/pacestreak/)

</div>

---

Motivation is unreliable. Streaks aren't.

PaceStreak makes consistency the number you actually chase. Log a session in ten
seconds, keep the run alive, and watch six months of work fill in one square at
a time — because a grid you have spent a year building is a much harder thing to
abandon than a to-do list.

## What makes it different

- **Streaks that respect rest.** Streaks count kept weeks against a target you
  set, so rest days are free. Freezes are earned, one missed week a month can be
  repaired, and an injury pause holds the streak while you recover.
- **Ten-second logging.** The fastest log wins. Anything slower gets skipped when
  you are tired, and skipped logs are what actually kill streaks.
- **Any discipline.** Barbell, trail, tarmac or wall — one chain across
  everything, or a separate chain per discipline.
- **Rewards for showing up, never for lifting more.** XP, badges, challenges and
  opt-in leaderboards count attendance. Nothing rewards load, volume or body
  weight.
- **Works offline.** Logs save on the phone first and sync later.
- **Your data, exportable.** JSON, CSV and calendar export, import from a watch
  (GPX, FIT, CSV), and deletion that deletes.

## Status

The product (API and app) is built and tested but not launched yet; where the
API is hosted is the open decision. The [blog](https://blog.pacestreak.com)
covers how each part was built. Early access goes out in batches — mail
[hello@pacestreak.com](mailto:hello@pacestreak.com) to be in the next one.

## Repositories

| Repo | What it is |
| --- | --- |
| [`web`](https://github.com/PaceStreak/web) | The public site at `www.pacestreak.com`. Astro, static, no login. |
| [`app`](https://github.com/PaceStreak/app) | The product itself, at `app.pacestreak.com`. React PWA, built, not yet deployed. |
| [`status`](https://github.com/PaceStreak/status) | Uptime monitoring and the public status page. Powered by Upptime — GitHub Actions, Issues and Pages. |
| [`api`](https://github.com/PaceStreak/api) | The backend, at `api.pacestreak.com`. FastAPI, built, not yet deployed. |
| [`blog`](https://github.com/PaceStreak/blog) | The blog at `blog.pacestreak.com`. Astro, deployed on Cloudflare Pages. |
| [`infra`](https://github.com/PaceStreak/infra) | DNS, Cloudflare, deployment topology and the runbook. Documentation, not automation. |
| [`.github`](https://github.com/PaceStreak/.github) | This profile, and the org-wide community health files. |

## Infrastructure notes

Worth knowing before touching anything, because each of these has already
caused a real outage or a silent breakage:

- **`www.pacestreak.com` is canonical.** The apex `pacestreak.com` 301-redirects
  to it via a Cloudflare Redirect Rule. A proxied DNS record with no rule and no
  route behind it returns 522, which is worse than no record at all.
- **Cloudflare Pages issues a separate certificate per custom domain.** The apex
  and `www` certificates have different SAN lists and different expiry dates —
  one check cannot cover both, so both are monitored.
- **Pages serves `/assets/*` with a multi-hour `Cache-Control` that a `_headers`
  file cannot override.** Ship unhashed asset filenames and a deploy will render
  new markup against a stale stylesheet, silently, for hours.

## Contributing

See [CONTRIBUTING.md](https://github.com/PaceStreak/.github/blob/main/CONTRIBUTING.md)
and the [Code of Conduct](https://github.com/PaceStreak/.github/blob/main/CODE_OF_CONDUCT.md).
Security issues: [SECURITY.md](https://github.com/PaceStreak/.github/blob/main/SECURITY.md).
