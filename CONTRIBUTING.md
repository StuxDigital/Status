<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stux.digital/logo-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stux.digital/logo-dark.png"><img src="https://global.media.stux.digital/logo-dark.png" height="80" alt="Stux.Digital Logo"></picture>
</p>

# Contributing to Status

Status is Stux.Digital's status page, [status.stux.digital](https://status.stux.digital), built with
[GitHup](https://githup.stux.group). To report an outage, open an Issue. Bugs or ideas for the
status page software belong in [StuxGroup/GitHup](https://github.com/StuxGroup/GitHup/issues).

## Local setup

You need Python 3.11+ and nothing else.

```bash
./dev-server.sh [--no-dev-mode] [port]   # or dev-server.bat on Windows
```

## Project conventions

- **Monitors live in `.githup.yml`.** Its syntax is documented in the
  [GitHup docs](https://githup.stux.group/docs/). Only add sites Stux.Digital runs.
- **The status page itself is GitHup's**, including the legal pages and 404. Change how it
  looks or works in GitHup, not here.
- **Brand.** Stux.Digital is a two-tone sky blue (`#38bdf8` on dark, `#0369a1` on light). GitHup takes one accent, so `site.accent` is the dark-theme `#38BDF8` and GitHup darkens it on the light theme until it reads; the logo is the bright `logo-light.png`, which reads on both themes.
- **Legal pages.** The `legal:` block in `.githup.yml` drives **Boring Legal Stuff** at `/legal/`.
  Keep it accurate.
- **Don't edit `data/` by hand.** It belongs to GitHup and the workflow.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/version.sh`.
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.
