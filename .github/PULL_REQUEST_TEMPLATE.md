## What does this change, and why?

<!-- The diff already says what. Explain why. -->

## Related issue

<!-- Closes #… — for anything non-trivial, an issue should exist first. -->

## How was it verified?

<!-- Commands run, browsers checked, before/after screenshots for visual changes. -->

## Checklist

- [ ] One concern only — no formatting sweeps mixed into a fix
- [ ] No new third-party runtime dependency, and no inline script or style
      (every site ships `default-src 'self'`, enforced in production)
- [ ] Nothing signed-in added to `web` — that belongs in `app`
- [ ] Any trap discovered is written down in a comment next to the code
