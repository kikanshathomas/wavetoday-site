# Overview

Wave's public website introduces the app and links to Google Play. The audience is the person setting things up for an older adult, plus anyone who wants the privacy policy before they install.

The site states the product rule already written on the pages: the person holding the phone initiates, and their circle receives. It describes a calm home screen (tap a face to call, "I'm okay", the day, "I need help"), Wave Circle, and a one-time unlock with no subscription.

## What this repository is

A static site. Four HTML pages, fonts, images, `sitemap.xml`, `robots.txt`, and the GitHub Pages config. Pages are edited by hand. Nothing here is generated at request time.

## Repository roles

| Repo | What it holds |
|---|---|
| `wavetoday-site` (this repo) | wavetoday.app |
| `wavetoday-dev` | The app, the Wave Circle server, store listing copy, and scripts that render some of this site's images |
| `wavetoday` | The Capacitor project that packages the Android app |

The app and the circle server are not deployed from this repository. The privacy policy on `/privacy` describes both, because Play and the App Store send people here.

## Who it is for

Readers of the marketing site, and store reviewers following the privacy and data-deletion links. People who only receive circle messages do not need this site or the app.
