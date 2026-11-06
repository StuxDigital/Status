# Changelog

All notable changes to Stux.Digital Status are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Date Versioning](https://datevers.ing) since v26.10.23 (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v26.11.06-3

### Added

- CI (`.github/workflows/ci.yml`) runs `tests/version.sh` on pushes to `main` and `test` and on pull requests into `main`, so a pull request has checks to pass

### Changed

- `commit.sh` and `commit.bat` end by telling you to push `test` (with the new tag) and open a pull request from `test` into `main`, instead of pushing `main`
- `CONTRIBUTING.md` says to merge `main` into `test` before starting new work, since GitHup commits monitoring data to `main` every few minutes

## v26.11.06-2

### Added

- Monitors for **Stux.Digital Clients** (in the Stux.Digital group) and a new **Templates** group with **Stux.Digital Clientpage**, **Soonpage** and **Maintenancepage**, now that they all serve. `README.md` lists them, and the "not monitored yet" notes are gone

### Changed

- Work happens on a `test` branch: changes reach `main` only through a pull request from `test`, and release commits and tags are made on `test`. `README.md` and `CONTRIBUTING.md` (a new Branches section) say so

## v26.11.06-1

### Changed

- `README.md` and the `.githup.yml` comment no longer say Stux.Digital Clients, Clientpage, Soonpage and Maintenancepage don't serve yet: they all do, and can now be added as monitors. They also say the first client site, Stux.Group, is monitored by Stux.Group Status
- `CONTRIBUTING.md` uses the full name, Stux.Digital Status, and says the logo and favicon are the page's own badge icon rather than `logo-light.png`

## v26.11.06

### Changed

- The page's logo and favicon are now its own badge icon, the Stux.Digital mark with a heartbeat badge (as on the Stux.Digital Status card at clients.stux.digital), rather than the plain Stux.Digital logo and icon. The README's header too, now titled Stux.Digital Status

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.2
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## [1.0.2] - 2026-10-09

### Changed

- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## [1.0.1] - 2026-10-09

### Changed

- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## [1.0.0] - 2026-10-08

### Added

- Stux.Digital Status (`status.stux.digital`), built with [GitHup](https://githup.stux.group): checks every 5 minutes (catching up when GitHub runs the schedule late), incident Issues, and the status page deployed to GitHub Pages by `.github/workflows/status.yml`
- Monitors for the Stux.Digital site (`stux.digital`) and the Stux.Digital media CDN; Clients, Clientpage, Soonpage and Maintenancepage are listed in `.githup.yml` to add once they serve
- Stux.Digital branding: the bright `logo-light.png` and `icon-light.png`, which read on both themes, and the sky-blue `#38BDF8` accent (GitHup darkens it on the light theme until it reads)
- GitHup's Boring Legal Stuff hub and six legal pages for Stux.Digital, plus its 404, sitemap page, `sitemap.xml` and `robots.txt`
- `dev-server.sh` / `dev-server.bat` (example data, DEV_MODE on by default, `--no-dev-mode` for production rendering), and `commit.sh` / `commit.bat` for tagged releases
