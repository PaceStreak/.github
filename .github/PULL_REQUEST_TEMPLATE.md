## What does this change, and why?

<!-- The diff already says what. Explain why. -->

## Related issue

<!-- Closes #… — for anything non-trivial, an issue should exist first. -->

## How was it verified?

<!-- Commands run, browsers checked, before/after screenshots for visual changes. -->

## Checklist

- [ ] One concern only — no formatting sweeps mixed into a fix
- [ ] No new third-party runtime dependency on the landing page (its CSP is
      `default-src 'self'` and is enforced in production)
- [ ] Asset URLs cache-busted if assets changed (`landing`: run `stamp.py`)
- [ ] Any trap discovered is written down in a comment next to the code
