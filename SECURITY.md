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
| `api.pacestreak.com`, when it exists | Findings from automated scanners with no demonstrated impact |
| `status.pacestreak.com` | Missing headers with no exploitable consequence |
| Code in any repository in this organization | Social engineering, physical attacks, denial of service |

## What is already known

These are deliberate, not findings:

- **The auth cookie is scoped `Domain=pacestreak.com`.** The frontend and the
  API are on different subdomains, so it has to be. It is therefore sent to
  every subdomain — which is exactly why nothing untrusted is hosted under this
  domain.
- **`status.pacestreak.com` is served from GitHub Pages** and is intentionally
  public, including full uptime history.
- **The landing page loads no third-party scripts.** Its CSP is
  `default-src 'self'`. If you find something loading from elsewhere, that *is*
  worth reporting.
