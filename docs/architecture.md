# Architecture

The published site is the files in this repository. GitHub Pages copies them as static files. Each page carries its own `<style>` block. The only shared CSS file is `assets/css/fonts.css`.

```
wavetoday.app
  index.html          home
  download.html       Play badge + QR
  privacy.html        policy, #delete
  404.html            unknown paths
  assets/css/fonts.css
  assets/fonts/       Outfit, two unicode-range files
  assets/img/         mark, screenshots, og image, icons, Play badge
  assets/js/qrcode.min.js   download page only
```

`download.html` builds the QR in the browser with vendored qrcodejs 1.0.0 (`assets/js/qrcode.min.js`). The script is minified third-party code; leave it intact. If the library fails to load, the page shows the Play URL as text.

Every page counts visits with GoatCounter (`https://wavetoday.goatcounter.com/count`, loaded from `gc.zgo.at`). The privacy policy, section 03, is the public description of that counter. A different analytics host means a policy edit in the same change.

Outfit is self-hosted. `outfit-2.woff2` is the latin subset and is preloaded. `outfit-1.woff2` is latin-ext, pulled in by `fonts.css` when a character needs it. Both files are the same faces the app ships. `fonts.css` records the unicode ranges.

## Pages and contracts

| File | Contract |
|---|---|
| `index.html` | `og:image` is `assets/img/og.png`. The `og:image:width` / `height` meta tags are 1024 and 500, matching the file `make-og.mjs` writes. |
| `download.html` | QR text and the badge href are the Play listing `id=com.wavetoday.app`. |
| `privacy.html` | Keep the filename. Extensionless `/privacy` and `/privacy.html` both serve it. Keep `id="delete"` on section 07. |
| `404.html` | Filename GitHub Pages looks up for a missing path. `noindex`. |
| `sitemap.xml` | The three public URLs above. 404 is absent. |
| `CNAME` | `wavetoday.app`. Pages reads this for the custom domain. |

Support on every page is `mailto:support@ubersoft.pro`. "Support Development" is `https://ko-fi.com/ubersoft`.

## Images

| File | Size | How it is used |
|---|---|---|
| `assets/img/og.png` | 1024×500 | Share card on the home and download pages. Same file is the Play listing graphic. |
| `assets/img/app-icon.png` | 256×256 | Download page icon. |
| `assets/img/mark.png` | 512×512 | Nav, footer, and home mark. The drawn hand, separate from the launcher icon. |
| `assets/img/favicon-master.png` | 1024×1024 | Not linked from any page. Source image for the small favicons. |
| `favicon-32x32.png` | 32×32 | Browser icon. |
| `favicon.ico` | 16, 32, and 48 | Browser icon. Linked from the privacy page and the 404. |
| `apple-touch-icon.png` | 180×180 | Home-screen icon. |
| `assets/img/google-play-badge.png` | 478×142 | Official Play badge on the home and download pages. |
| `assets/img/shot-*.png` | 460×818 | Screenshot fallbacks on the home page. |
| `assets/img/shot-*.webp` | 920×1636 | `srcset` and the lightbox (`data-full`) for the same four shots. |

The four shots are `shot-home`, `shot-home-sent`, `shot-calling`, and `shot-emergency`. Each pair is referenced. Keep both the PNG and the WebP.

## Art scripts in wavetoday-dev

The scripts live in `wavetoday-dev/tools/scripts/` and resolve `site/` as `wavetoday-dev/site/` (two directories up from `tools/scripts/`). `wavetoday-dev` does not commit a `site/` folder. Put a checkout of this repository at `wavetoday-dev/site` so the scripts write into it, then commit the changed images here.

`make-og.mjs` reads `store/icon/og-master.png` and the app's Outfit files, and writes:

- `site/assets/img/og.png` at 1024×500, no alpha

`make-store-art.mjs` reads `store/icon/icon-master.png` for the large icons and `site/assets/img/favicon-master.png` for the small ones. It writes:

| Output | Source | Size |
|---|---|---|
| `store/icon/playstore-icon-512.png` (in wavetoday-dev) | icon master | 512 |
| `site/assets/img/app-icon.png` | icon master | 256 |
| `site/apple-touch-icon.png` | icon master | 180 |
| `site/favicon-32x32.png` | favicon master | 32 |
| `site/favicon.ico` | favicon master | 16, 32, 48 |

Regenerate those files by re-running the script. Hand-editing the outputs drifts from the master.

These scripts do not write `mark.png`, the Play badge, or the four screenshot pairs. `tools/scripts/capture-shots.mjs` writes store screenshots under `wavetoday-dev/store/screenshots/` and does not update `assets/img/shot-*`.

## Scripts on the pages

Home: the footer year, an `IntersectionObserver` that adds `in` to `.reveal`, and a lightbox that opens `data-full`.

Download: QR generation, with a text link if `QRCode` is missing, and the footer year.

Privacy: the footer year stays "2026" until the calendar year passes it, then shows a range. The effective date in the header is hand-edited and is independent of that script.

404: GoatCounter only.
