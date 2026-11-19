# Setup

No install step and no package manager. The pages are the source.

Paths are root-absolute (`/assets/css/fonts.css`, `/favicon-32x32.png`). Opening an HTML file from disk does not load those assets. Start a static server at the repository root:

```sh
python3 -m http.server 8000
```

Then check:

| URL | What you should see |
|---|---|
| http://127.0.0.1:8000/ | Home, mark, four screenshots, Play badge |
| http://127.0.0.1:8000/download.html | Icon, QR, Play badge |
| http://127.0.0.1:8000/privacy.html#delete | Privacy policy, scrolled to section 07 |
| http://127.0.0.1:8000/404.html | The not-found page |

Python's server uses its own 404 for an unknown path. GitHub Pages uses `404.html` for that case, so preview the not-found layout at `/404.html`.

Jekyll is what GitHub Pages runs. It is not required for a local preview. A local `jekyll serve` also works and applies `_config.yml`, including the exclude list, so `README.md` and `docs/` stay out of that preview.

## Regenerating icons and the share image

Do this from `wavetoday-dev`, with this repo checked out at `wavetoday-dev/site`:

```sh
node tools/scripts/make-og.mjs
node tools/scripts/make-store-art.mjs
```

Those commands need the toolchain already used in `wavetoday-dev` (Node, `sharp`, and for the OG image a local Chrome via Puppeteer). Commit the updated files in this repository afterwards. `favicon-master.png` is an input: replace that file first when the small-icon drawing changes, then re-run `make-store-art.mjs`.
