# Deploy

GitHub Pages hosts the site. The Pages project for `kikanshathomas/wavetoday-site` is a legacy build from branch `main`, path `/`, with the custom domain `wavetoday.app` and HTTPS enforced. There is no GitHub Actions workflow in this repository. Pushing or merging to `main` is what publishes.

`CNAME` contains `wavetoday.app`. Leave that file in place. Pages will not keep the custom domain if it disappears.

## What Jekyll does

`_config.yml` sets `theme: null` so Pages does not add its default theme stylesheet. No HTML file has front matter, so Jekyll copies page and asset bytes through unchanged.

The exclude list keeps repository files off the public site:

- `CLAUDE.md` and `.claude` (agent rules)
- `README.md` and `docs/` (these docs)

`require_front_matter` is set in `_config.yml` beside a comment that Markdown without front matter should stay unrendered. Publishing still excludes the Markdown outright, so a future change to that key cannot put this README on wavetoday.app by itself.

## Review before merge

A merge to `main` updates the live site. Company practice is a DevOps security check, then QA review, then a clearance line in `kikanshathomas/ubersoft-company` at `company/audit/cleared.md`, then Thomas's go. The CEO merges. Do not push to `main` directly.

After a merge, Pages and its cache can take a few minutes. Confirm the served HTML matches the commit (the query string avoids a cached copy):

```sh
curl -sI "https://wavetoday.app/privacy.html?v=$(date +%s)"
curl -s "https://wavetoday.app/privacy.html?v=$(date +%s)" | cmp - privacy.html && echo identical
curl -sI "https://wavetoday.app/privacy?v=$(date +%s)"
```

The extensionless privacy URL must stay on the same document as `privacy.html`. Also confirm `/download.html` and a nonsense path (the 404) still respond.

## What a docs-only change publishes

Comments inside HTML are part of the file Pages copies, so they ship, and they do not change what a visitor sees. Files under `docs/` and `README.md` are excluded. They show up on GitHub and stay off wavetoday.app.
