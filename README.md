# wavetoday-site

Public marketing site for Wave, a calm check-in app for an older adult and the people around them. Visitors use it at [https://wavetoday.app/](https://wavetoday.app/).

This repository is the site: hand-written HTML, a self-hosted Outfit font, and images. GitHub Pages publishes the `main` branch. The custom domain is the `CNAME` file.

## Page map

GitHub Pages serves each HTML file at the `.html` path and at the same path without the extension. Store materials use the extensionless privacy URL. The sitemap lists the `.html` paths.

| Public URL | File | Role |
|---|---|---|
| `/` | `index.html` | Home: features, Wave Circle, FAQ, Play badge |
| `/download`, `/download.html` | `download.html` | Play badge and a QR code for the same listing |
| `/privacy`, `/privacy.html` | `privacy.html` | Privacy policy. `#delete` is section 07, the Play data-deletion target |
| unknown paths | `404.html` | GitHub Pages 404. `noindex`, and omitted from the sitemap |
| `/sitemap.xml` | `sitemap.xml` | `/`, `/download.html`, `/privacy.html` |
| `/robots.txt` | `robots.txt` | Allows crawlers and points at the sitemap |

Also at the root: `CNAME` (`wavetoday.app`), `_config.yml` (the Pages build), `favicon.ico`, `favicon-32x32.png`, and `apple-touch-icon.png`.

## Sibling repositories

| Repo | Role |
|---|---|
| [`wavetoday-dev`](https://github.com/kikanshathomas/wavetoday-dev) | App source (`app/`, `native/`, `server/`), store notes, and the art scripts |
| [`wavetoday`](https://github.com/kikanshathomas/wavetoday) | Capacitor Android packaging |
| this repo | The public website |

`wavetoday-dev/tools/scripts/make-og.mjs` and `make-store-art.mjs` write into a `site/` directory beside the app tree (`wavetoday-dev/site/`). That folder is not committed in `wavetoday-dev`. Check this repository out at that path before regenerating art. The outputs and the files they must not overwrite are in [docs/architecture.md](docs/architecture.md).

## Edit and preview

Edit the HTML directly. Paths such as `/assets/...` are root-absolute, so preview with a static server started at the repository root. Steps are in [docs/setup.md](docs/setup.md).

## Publish

Pages builds `main` with Jekyll from the repository root and serves [https://wavetoday.app/](https://wavetoday.app/). `_config.yml` keeps `CLAUDE.md`, this README, and `docs/` off the public site, so those files stay on GitHub and do not become new pages. Merging to `main` is the publish step. See [docs/deploy.md](docs/deploy.md).

## Links that have to keep working

- Privacy: `https://wavetoday.app/privacy`, `https://wavetoday.app/privacy.html`, and `https://wavetoday.app/privacy.html#delete`
- Support: `mailto:support@ubersoft.pro` (the site has no `/support` page; that path 404s)
- Play listing, including the QR code: `https://play.google.com/store/apps/details?id=com.wavetoday.app`
- "Support Development": `https://ko-fi.com/ubersoft`

## Docs

| File | Contents |
|---|---|
| [docs/overview.md](docs/overview.md) | What the site is, and which repo does what |
| [docs/architecture.md](docs/architecture.md) | Files, assets, and the art scripts |
| [docs/setup.md](docs/setup.md) | Local preview |
| [docs/deploy.md](docs/deploy.md) | GitHub Pages, the domain, and what a merge publishes |
| [docs/ownership.md](docs/ownership.md) | Who edits what |
| [docs/changelog.md](docs/changelog.md) | Pointer to the app changelog, which QA owns |

This site has no API, so there is no `docs/api.md`.
