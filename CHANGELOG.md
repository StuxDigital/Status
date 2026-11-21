# Changelog

All notable changes to Stux.Digital Status are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Date Versioning](https://datevers.ing) since v26.10.23 (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## v26.11.21

### Fixed

- The deploy no longer fails when GitHub briefly can't find the page it just uploaded ("Fetching artifact metadata failed", then "No artifacts named github-pages were found"). This happened in short bursts on GitHub's side across every brand's status page on 20 and 21 November 2026. If the first deploy attempt fails, the workflow now waits 30 seconds and tries once more, and fails only if the retry fails too.

## v26.11.15-2

### Changed

- The comment on the `*/5` schedule in `.github/workflows/status.yml` now says it asks GitHub for a check every 5 minutes on a best-effort basis, and that GitHub often runs it less often, instead of "may run it a little late". The schedule itself is unchanged

## v26.11.15-1

### Changed

- Changes now go live through `test` → `staging` → `main`, with a pull request at each step: `staging` only changes by a merged pull request from `test`, and `main` (live) only by one from `staging`. `commit.sh` / `commit.bat` refuse to run on `staging` or `main`, and after tagging they print the push command and both `gh pr create` commands. CI also runs on `staging`; deploys stay on `main`. `CONTRIBUTING.md` has a new "Branches and going live" section, and the `README.md` Versioning section describes the flow

## v26.11.15

### Added

- `dev-server.sh` / `dev-server.bat` take `--lan`: the server listens on all interfaces instead of `127.0.0.1` only, so phones and other devices on the local network can open it, and it prints the address to open for each of the machine's IPv4 addresses, with a hint that it's usually the `192.168.x.x` one and to allow Python through the firewall if asked. Without it, the server stays on `127.0.0.1`. `README.md` and `CONTRIBUTING.md` document it

## v26.11.13-1

### Fixed

- The registered office address now ends "England, United Kingdom": 124 City Road, London, EC1V 2NX, England, United Kingdom

## v26.11.13

### Changed

- Stux Group Ltd's registered office is now 124 City Road, London, EC1V 2NX, England (was 82a James Carter Road, Mildenhall, England, IP28 7DE), in the company line in `.githup.yml` that GitHup puts on the status page's Imprint. The company number and "registered in England and Wales" are unchanged

## v26.11.08

### Changed

- The site description says "checked regularly" instead of "checked every 5 minutes". GitHub runs the `*/5` schedule best-effort, often much less often, and GitHup now shows the real measured check rhythm on the page ("checked about every … (last 24 h)"). The `.githup.yml` comment and `README.md` say the 5-minute schedule is a request GitHub may run less often. The cron itself is unchanged

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
