<div align="center">

<img src="https://www.pacestreak.com/brand/logo.svg" alt="" width="76" height="76">

# PaceStreak

**A habit and streak tracker for training and everything else worth doing regularly.**

[Open the app](https://app.pacestreak.com) ·
[Website](https://www.pacestreak.com) ·
[Blog](https://blog.pacestreak.com) ·
[Status](https://status.pacestreak.com) ·
[hello@pacestreak.com](mailto:hello@pacestreak.com)

</div>

---

Motivation is unreliable. Streaks aren't.

PaceStreak makes consistency the number you chase: for training, a language, an
instrument, sleep, reading, calm, or a habit you're breaking. Each one keeps a
weekly streak against a target you set, so rest days never break it, and a year
of filled squares is a much harder thing to abandon than a to-do list.

## What it does

- **Habits and streaks that respect rest.** Kept weeks against your own target.
  Earned freezes, a monthly repair, pauses for injury or travel (for everything
  or one habit), habits planned for chosen weekdays, and an optional
  whole-life streak. Habits can be ticked, counted or timed, or broken with clean
  days where a slip is logged, never punished.
- **Training, when you want detail.** Ten-second logging for 11 disciplines, or
  sets, reps and RPE against 283 exercises, with 24 starter routines, 22 plans, race build-ups,
  training blocks, a two-way plate calculator and personal records. Import from
  Strong, Hevy and FitNotes.
- **Food, without the diet app.** Meals, macros, recipes and barcode lookup, and
  an energy-burn estimate from your own food log and weigh-ins.
- **Insights without AI.** Patterns across sleep, mood, habits, training and food,
  shown only when a statistical test says they aren't chance. Nothing you log goes
  to an AI company.
- **Fast every day.** A command palette and keyboard shortcuts, swipe-to-complete,
  routines you step through, reminders with Done and Snooze buttons, search, a
  one-day view, and Undo with a 30-day trash.
- **Private by design.** Habits, food, body and journal are visible to nobody else,
  ever. Social features (follows, preset reactions, groups, coaching, challenges,
  opt-in leaderboards) rank
  turning up, never which habit or how much.
- **Yours to take.** Works offline, installs as an app, exports to JSON, CSV and
  calendar, imports from watches and other habit apps, and deletes for real.

No ads, no analytics, no third-party scripts: every site ships
`default-src 'self'`, enforced. And every line of it is public, under AGPL-3.0.

## Repositories

| Repo | What it is |
| --- | --- |
| [`app`](https://github.com/PaceStreak/app) | The product at `app.pacestreak.com`. React PWA, offline-first, Cloudflare Pages. |
| [`api`](https://github.com/PaceStreak/api) | The backend at `api.pacestreak.com`. FastAPI, Postgres, Redis and a worker. |
| [`web`](https://github.com/PaceStreak/web) | The public site at `www.pacestreak.com`. Astro, static, no login by design. |
| [`blog`](https://github.com/PaceStreak/blog) | How each part was built, mistakes included, at `blog.pacestreak.com`. |
| [`status`](https://github.com/PaceStreak/status) | Uptime monitoring and the public status page, powered by Upptime. |
| [`infra`](https://github.com/PaceStreak/infra) | Topology, decisions and the runbook. Documentation, not automation. |
| [`.github`](https://github.com/PaceStreak/.github) | This profile and the organisation's community health files. |

## How it fits together

```text
www.pacestreak.com    web     static marketing site    Cloudflare Pages
blog.pacestreak.com   blog    static blog              Cloudflare Pages
app.pacestreak.com    app     the product (PWA)        Cloudflare Pages
api.pacestreak.com    api     FastAPI + worker         a VM behind a Cloudflare Tunnel
status.pacestreak.com status  uptime history           GitHub Pages
```

A push to `main` deploys every site. The API deploys itself: CI publishes an
image, and the server rolls it out with no inbound access for a deploy at all.

`web` never touches the API, so a product outage can't take down the page
explaining the product. The [blog](https://blog.pacestreak.com) covers each
decision, including the ones that went wrong in production.

## Contributing

See [CONTRIBUTING.md](https://github.com/PaceStreak/.github/blob/main/CONTRIBUTING.md)
and the [Code of Conduct](https://github.com/PaceStreak/.github/blob/main/CODE_OF_CONDUCT.md).
Security issues go to [hello@pacestreak.com](mailto:hello@pacestreak.com), never
a public issue: see [SECURITY.md](https://github.com/PaceStreak/.github/blob/main/SECURITY.md).
