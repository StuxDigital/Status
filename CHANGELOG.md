# Changelog

All notable changes to Stux.Digital Status are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
