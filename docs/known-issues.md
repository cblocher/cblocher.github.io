# Known issues and open items

What is not finished, not verified, or not ideal. Last reviewed: 2026-11-04.

Each item says who can act on it. Remove an item when it is fixed, and record the fix in `CHANGELOG.md`.

---

## Not yet verified

| Item | Detail | Owner |
|------|--------|-------|
| Figma frame on the Teal page | Could not be displayed in the build environment (Figma refused the requests). Check it in a normal browser. | Site owner |
| YouTube video on the AI skill page | The video host is blocked in the build environment. Check that it plays. | Site owner |
| External links | Most could not be reached by the automated check. See the list in `privacy-and-third-parties.md`. | Site owner |
| Screen reader and keyboard walk-through | Never done by a person. See `accessibility.md`. | Site owner |
| Alt text and slide captions | Written by an AI assistant. Need review. | Site owner |

---

## Site

| Item | Detail | Fix |
|------|--------|-----|
| Redirects are not HTTP 301 | GitHub Pages cannot send real redirects, so old addresses use a page with a meta refresh. Search engines generally follow it, but a 301 is stronger. | Only a different host solves this |
| No `sitemap.xml`, `robots.txt`, or custom 404 page | Each returns GitHub's default "not found" page. | Add the `jekyll-sitemap` plugin to `_config.yml`, add a `robots.txt`, and add a `404.md` page |
| Game pages lack a `main` landmark | The best-practice scan reports `landmark-one-main` and `region`. The pages are standalone HTML. | Wrap each game's content in a `main` element |
| Game pages load Tailwind from a CDN | They depend on `cdn.tailwindcss.com` being reachable | Build the styles into the repo |
| The `doc-quest` page's Tailwind line was broken until 2026-11-04 | Fixed in D26 | None |
| Fonts come from Google | Every page makes a request to Google (see the privacy document) | Self-host the fonts |
| Figma frame sets cookies | Figma sets three cookies on the Teal page when the frame loads | Replace the frame with a screenshot and a link, or add a notice |
| No public accessibility statement | Recommended for a portfolio site | Add a short `accessibility.md` page, with the owner's approval |
| Role photo shows other companies' app icons | The Content Designer photo on About, unchanged from UXfolio | Replace the photo, on UXfolio first |
| The downloads page heading breaks the sentence-case rule | The heading in `assets/downloads/README.md` is "README - Technical Content Design — Claude Skill." The file is not to be changed. | None |

---

## UXfolio items (outside this repo)

The GitHub site follows UXfolio, so these can only be fixed there.

| Item | Detail |
|------|--------|
| Typos and wording | Six fixes listed in the phase 4 review, and four edits made on the GitHub side only (the Teal facts row and Capture sentence, the game card time, and "embracing opportunities") |
| LinkedIn footer link | The footer link reads `linkedin.com/cblocher` without `/in/`, which probably does not open the profile |
| File names turned into links | Five file names on the AI skill page (`practitioners.md` and four more) are links to unrelated websites |

---

## Housekeeping

| Item | Owner |
|------|-------|
| Delete the merged branches: `claude/case-study-fixes` (never merged, now obsolete), `claude/site-restructure`, `claude/site-title-fix`, and this documentation branch after it merges | Site owner |
| Remove the extra domains added to the build environment: `uxfol.io`, `cblocher.github.io`, the Figma hosts, `cdn.tailwindcss.com` | Site owner |
| Turn on "Keep my email addresses private" in GitHub settings | Site owner |
| Review the Claude GitHub App's access to this repo | Site owner |

---

## Optional improvements

| Idea | Why |
|------|-----|
| An interactive carousel for the five prototype slides | Shortens the digital coach page. Build the stacked version as its fallback. |
| A staging preview for branches | See changes at an address before merging |
| Run Vale and the accessibility scan automatically on every pull request | Catches problems before a merge, without relying on memory |
| A local clone of the repo | A second copy of everything |
