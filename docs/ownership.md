# Ownership

Ubersoft departments, for this repository:

| Area | Department |
|---|---|
| Public sentences on the HTML pages | Marketing |
| Claims that have to match the shipping app (what Wave stores, what a purchase unlocks) | Product, checked against `wavetoday-dev` `docs/` and `store/data-safety.md` |
| Layout, comments, and the page structure | Engineering |
| `CNAME`, the Pages project, and the domain | DevOps |
| App and store release notes | QA & Security, in `wavetoday-dev/changelog.txt` |
| Mark, screenshot pairs, `favicon-master.png`, and review of generated icons | Design |

## Leave these alone unless the change is the point

- `privacy.html`, the `/privacy` URL, and `id="delete"`. Store listings and the Play data-deletion link land here.
- `mailto:support@ubersoft.pro` and the Play listing URL `id=com.wavetoday.app`, including the QR payload on the download page.
- The GoatCounter snippet, unless section 03 of the privacy policy changes with it.
- Generated pixels: `og.png`, `app-icon.png`, `apple-touch-icon.png`, `favicon-32x32.png`, and `favicon.ico`. Change the master and re-run the script in `wavetoday-dev`.
- `favicon-master.png` is an input to that script. Deleting it because no page links it breaks the next favicon build.
- `CNAME` and the `_config.yml` exclude list.

`CLAUDE.md` is the agent working rules. It is not the human overview; this `docs/` folder is.
