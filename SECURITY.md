# Security Policy

## Reporting a vulnerability

**Do not open a public issue for a security problem.**

Email **<hello@pacestreak.com>** with the details. Include what you found, the
steps to reproduce it, and what an attacker could do with it. If you have a
proof of concept, attach it.

You will get an acknowledgement within **72 hours** and a substantive reply once
the issue has been assessed. PaceStreak is a small project — there is no
bug bounty, and no formal SLA beyond that acknowledgement. What you will get is
a straight answer about whether it is a real issue and when it will be fixed.

Please give a reasonable window to fix before disclosing publicly. If a fix is
taking too long, say so — an agreed date is better than a surprise.

## Scope

| In scope | Out of scope |
| --- | --- |
| `pacestreak.com` and `www.pacestreak.com` | Third-party services (GitHub, Cloudflare, Zoho) — report to them |
| `app.pacestreak.com` and `api.pacestreak.com` | Findings from automated scanners with no demonstrated impact |
| `status.pacestreak.com` and `blog.pacestreak.com` | Missing headers with no exploitable consequence |
| Code in any repository in this organization | Social engineering, physical attacks, denial of service |
| | Third-party providers named on the [privacy page](https://www.pacestreak.com/privacy) — report to them |

## What is already known

These are deliberate, not findings:

- **The auth cookie is scoped `Domain=pacestreak.com`.** The frontend and the
  API are on different subdomains, so it has to be. It is therefore sent to
  every subdomain — which is exactly why nothing untrusted is hosted under this
  domain.
- **`status.pacestreak.com` is served from GitHub Pages** and is intentionally
  public, including full uptime history.
- **The sites load no third-party scripts.** Every CSP is `default-src 'self'`.
  The one exception is Cloudflare Turnstile on the app's sign-up, sign-in and
  password-reset forms. Anything else loading from elsewhere *is* worth
  reporting.
- **Inline stylesheets are allowed by hash.** `www` inlines its stylesheet and
  lists its SHA-256 in `style-src`; there is no `'unsafe-inline'` for scripts
  anywhere. The blog allows inline styles (syntax highlighting needs them) but
  not inline scripts.
- **Some links work without a session, by design, and are signed.** One-click
  email unsubscribe, and the Done and Snooze buttons on habit reminders, carry
  an HMAC scoped to one user, one action and (for reminders) one habit and day,
  with an expiry. A forged or altered link is a 403.
