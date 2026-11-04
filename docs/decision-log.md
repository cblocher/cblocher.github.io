# Decision log

A running record of decisions made while rebuilding this site, with the reasoning, so the finished documentation can be accurate. Entries are added as decisions are settled. Old entries are not edited. If a decision changes, a new entry says so and points to the old one by its ID.

This file is not published. `_config.yml` excludes the `docs` folder.

**Format:** each entry gives the status, the context, the decision, what else was considered, and the reasons. "Chris" is the site owner. "Claude" is the AI assistant doing the build work.

---

## Project and process

### D01: Rebuild the site and match the UXfolio portfolio

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** The GitHub site had four case study pages that were an out-of-date first draft. They showed raw Markdown, used screen captures with clipped carousel pieces and a blue glow, and lacked sections that the UXfolio portfolio (https://uxfol.io/5a5a1147) has: Overview, Goal, Results, Team, Timeline, Tools, stats, Learnings, and Next steps.
- **Decision:** Rebuild the site on a clean structure and make the four case studies match the UXfolio versions in content.
- **Alternatives considered:** Swap in clean images on the old pages and leave the rest for the planned portfolio build. Stop and merge the earlier fixes.
- **Reasons:** Chris chose the full rebuild. Fixing images alone would have left outdated text, and the old pages were about to be replaced anyway.
- **Consequences:** A larger piece of work, split into five phases with an approval gate after each one.

### D02: Work in phases, with approval before each one

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** Five phases: inventory (read-only), skeleton, images, content, verify. Each ends with Chris's approval. Anything that overwrites or deletes a file gets its own confirmation message first.
- **Reasons:** Chris has little coding experience and wants to check each result. Originals stay recoverable, and nothing changes the live site until Chris merges.

### D03: Build on a new branch from `main` and leave the earlier branch unmerged

- **Date:** 2026-11-04
- **Status:** Decided; the old branch has not been closed yet
- **Context:** The branch `claude/case-study-fixes` holds crops and fixes made before the rebuild decision.
- **Decision:** Start the rebuild on `claude/site-restructure`, branched from `main`.
- **Reasons:** The rebuild replaces those fixes with clean originals, so merging the old branch would bring in work that is about to be replaced.
- **Consequences:** `claude/case-study-fixes` can be deleted once Chris decides it is not needed.

### D04: Back up the originals as a zip and rely on git history

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** Chris wanted the original images safe before any merge.
- **Decision:** A zip of all 30 original images from `main` (commit `eccaa6d`), plus git history. No tag or backup branch.
- **Alternatives considered:** A git tag (the push was refused in this environment), a backup branch, a tag created on the GitHub website. Chris chose to skip the marker.
- **Reasons:** A merge adds new versions and does not erase old ones. The commit `eccaa6d` is the site before the rebuild.

---

## Structure and hosting

### D05: Keep Jekyll on GitHub Pages

- **Date:** 2026-11-04
- **Status:** Decided; not re-evaluated against other tools
- **Context:** The site already ran on Jekyll through GitHub Pages, publishing from `main`.
- **Decision:** Keep it.
- **Reasons:** It needs no extra hosting, it builds Markdown into HTML, and the existing content and redirects work with it. Other static site generators were not compared in this session.
- **Consequences:** Only the plugins on GitHub's approved list can be used. Previews use the `github-pages` gem (Jekyll 3.10) so builds here match what GitHub runs.

### D06: Follow the folder structure Chris specified

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** `_layouts` (default and project), `_includes`, `_sass`, `projects/`, `assets/images/projects/<project>/`, and `_originals/`, as in the guidelines Chris supplied from another thread.
- **Additions:** `_vale/` and `.vale.ini` for the writing check, and `docs/` for documentation. All three are kept out of the published site.

### D07: Case studies live in `projects/` with clean addresses, and old addresses redirect

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** `/projects/ai-skill/`, `/projects/digital-coach/`, `/projects/teal-usability/`, and `/projects/style-guide-game/`. The old addresses (`/projects-ai/`, `/projects-cabira/`, `/projects-teal/`, `/projects-onboarding/`) redirect with the `jekyll-redirect-from` plugin.
- **Reasons:** Chris's structure called for `projects/`. Redirects keep old links working.
- **Open item:** The redirects for the `.html` forms of the old addresses are added in phase 5, when the old pages are removed. Until then the old files would collide with them.

### D08: Keep the two game pages at their current addresses

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** The UXfolio onboarding page links to `/projects-ai-headline-hero.html` and `/projects-doc-quest.html`.
- **Decision:** Leave both at the top level, unchanged.
- **Alternatives considered:** Move them to `/games/` or `/projects/` with redirects.
- **Reasons:** UXfolio can't be edited from this project, and this choice keeps those links working with no changes there.

### D09: Drop the Primer theme setting

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** `_config.yml` set `theme: jekyll-theme-primer`, but the site used its own layout and stylesheet.
- **Decision:** Remove the setting. The old `style.scss`, which imported the theme, is excluded from the build until phase 5 removes it.
- **Reasons:** An unused theme setting adds confusion. Keeping `style.scss` would have broken the build once the theme was gone.

---

## Styles and accessibility

### D10: One stylesheet built from Sass partials, with no inline styles

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** Styles live in `_sass/` and are built by `assets/css/main.scss` into `main.css`. Layouts, includes, and pages carry no `style="..."` attributes.
- **Reasons:** One place to change the design. Inline styles on the old pages were the reason layout changes needed edits to many files.
- **Detail:** The output is named `main.css`, not `style.css`, so it cannot collide with the old static file before the old one is removed.

### D11: Accessibility built in from the start

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** A skip link, landmarks, one H1 per page, visible keyboard focus, a reduced-motion setting, alt text on every image, titles on every embed, and the current page marked in the navigation. Automated scans use axe against WCAG 2.1 A and AA.
- **Result so far:** 0 violations on the home page, the skeleton, and the four project pages.
- **Not done:** No screen reader testing. The old About page still has one scan failure (a scrolling quote carousel), which the rebuild removes.

### D12: Darker link color and underlined links

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** The old link blue (`#3B82F6`) had about 3.4 to 1 contrast against the page background, below the 4.5 to 1 minimum for text.
- **Decision:** Links use `#1D4ED8` (about 6.1 to 1) and are underlined. Secondary text uses `#595959`.
- **Consequences:** A visible change from the old design. It was flagged to Chris for review.

### D13: Headings in sentence case, typed in the source and checked by Vale

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** Chris wanted capitalization handled in CSS so it would not depend on what was typed in the Markdown.
- **Decision:** Headings are typed in sentence case, as they are on UXfolio. A Vale rule checks them. A single CSS value, `--heading-case` in `_sass/_tokens.scss`, is set to `none` and can be changed later.
- **Alternatives considered:** CSS `text-transform: capitalize` on every heading. A Liquid snippet to apply Title Case at build time.
- **Reasons:** CSS changes only how text looks. Screen readers, the browser tab, search results, and link previews use the typed text, so the same heading would show two ways. CSS has no true Title Case, because `capitalize` also capitalizes small words such as "of," and no safe sentence case, because lowercasing would break names such as Claude and Figma. The Liquid option covers only page settings and adds code to maintain.
- **Limits of the check:** It does not read `title:` lines in page settings, headings in layouts, or catch a single stray capital in the middle of a heading.

### D14: Build Vale from its official source

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** GitHub release downloads were blocked in the build environment. PyPI offered a third-party wrapper.
- **Decision:** Build Vale from its official module path, `github.com/vale-cli/vale/v3` (the project moved from `errata-ai`), using Go's module proxy.
- **Reasons:** A third-party wrapper would add a link in the supply chain that the project does not control.

---

## Images and media

### D15: Use the UXfolio originals, and never edit the full-size copies

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** The repo's case study images were screen captures of the UXfolio pages, with carousel step bars cut off and a blue focus glow. Cropping them made them worse, because the missing content was not in the files.
- **Decision:** Download the originals from the portfolio's image host, keep them unchanged in `_originals/<project>/`, and make web copies in `assets/images/projects/<project>/`. Copies wider than 2000 pixels are resized to 2000. Narrower ones are copied byte for byte. `_originals/manifest.md` maps each original to its source and its web copy.
- **Reasons:** Edits to a degraded copy cannot restore what is missing. Originals are the only safe starting point for any later change.

### D16: Thumbnails fit the whole screen at 4:3

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** Each thumbnail is 800 by 600 pixels, with the whole screen fitted on the page background color and the 1px border drawn by the stylesheet.
- **Alternatives considered:** Crop to fill, which cut text mid-word on three of the four. UXfolio's device-frame tiles, which can't be downloaded and use a gray tile Chris did not want.
- **Reasons:** Nothing is cut off, and all four are exactly the same size.

### D17: Embeds use UXfolio's Figma file, a 16:9 frame, and YouTube's no-cookie address

- **Date:** 2026-11-04
- **Status:** Decided; display not verified
- **Decision:** The Teal page embeds the same Figma file as UXfolio, in a 16:9 frame with no border, wider than the text column. The AI skill page embeds the video from `youtube-nocookie.com`. Each embed has a title and an "Open in a new tab" link.
- **Reasons:** The same Figma file keeps the content matched. The no-cookie address sets no tracking cookies until someone plays the video. The title and the link serve screen readers and visitors whose browsers block frames.
- **Not verified:** Figma refuses requests from the build environment, and the YouTube domain is blocked there, so neither displayed in any screenshot. Check both after merging.

### D18: Stack the prototype slides, and use a plain list for the testimonials

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** The five prototype slides are stacked in order with "Slide 1 of 5" labels. The five testimonials are a plain list, not a scrolling carousel.
- **Alternatives considered:** An interactive carousel. Chris asked about the effort and chose to build the stacked version first.
- **Reasons:** No script, works with a keyboard and a screen reader, and is easy to maintain. Carousels often hide content and fail accessibility checks. The stacked markup also serves as the fallback if a carousel is added later.
- **Open item:** A carousel for the slides can be added later as an optional enhancement.

---

## Content

### D19: Fix obvious typos and a few wording problems when copying from UXfolio

- **Date:** 2026-11-04
- **Status:** Decided
- **Decision:** Text is copied from UXfolio, with obvious typos fixed. The six fixes are listed in the phase 4 review sheet. Chris should make the same fixes on UXfolio so the two stay in sync.

### D20: Content edits made by Chris

- **Date:** 2026-11-04
- **Status:** Decided
- **Decisions:** The Teal timeline is "1 week" (it said 3 months). The style guide game card says "(30 minutes)" (it said 3 days). The phrase "embracing innovative opportunities" became "embracing opportunities," to remove a repeated word.
- **Open item:** The Teal Capture section still says feedback was collected "over the course of three months." Chris has not decided what to do with it.

### D21: Alt text, slide captions, and the video title

- **Date:** 2026-11-04
- **Status:** Decided; alt text awaiting Chris's review
- **Decision:** UXfolio's images mostly have no alt text, so Claude wrote it, along with the five slide captions. Chris supplied the video title, "Multi-Modal Video Generation Process."

### D22: A quote is edited in square brackets

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** A testimonial says "He is a master of his craft." Chris's language standard avoids "master."
- **Decision:** The quote will read "He is [an expert in] his craft and genuinely a pleasure to work alongside." The brackets show readers the wording was edited.
- **Alternatives considered:** Leave the quote as written. Cut the sentence with an ellipsis.

### D23: UXfolio is always the latest version

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** The UXfolio portfolio is newer than the GitHub site on the About page and the home page. UXfolio has newer text, new images, a new section, and a "Coming soon..." tile.
- **Decision:** When the two differ, UXfolio wins, and its newest information is added to the GitHub site. Chris keeps UXfolio current, and the GitHub site follows it.
- **Consequences:** Edits made on the GitHub side only (the typo fixes in D19) must also be made on UXfolio, or the next sync will undo them.

### D24: Mentoring items are not carried over

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** The old GitHub About page ended with an ADPList booking widget, a "Let's talk!" paragraph about mentoring, and a CareerVillage line. UXfolio has none of them.
- **Decision:** Leave them out of the new About page. They stay in git history (the About page as of commit `eccaa6d`).
- **Alternatives considered:** Keep the whole section, or keep the text and link without the embedded widget.
- **Reasons:** Under D23, UXfolio is the latest version.

### D25: Decorative images get empty alt text; the "Coming soon..." tile is included

- **Date:** 2026-11-04
- **Status:** Decided; the alt text is awaiting Chris's review
- **Decision:** The four role photos and the four certification badges use empty alt text, because the heading or title next to each one says what it is. The headshot and the Meta Quest photo get written descriptions. The UXfolio "Coming soon..." tile appears on the home page and in the "Read more" list, as a card with no link.
- **Reasons:** A screen reader should not repeat the same name twice. The placeholder tile is part of the UXfolio page, so under D23 it comes across.

### D26: Fix the Tailwind line on the doc-quest game page

- **Date:** 2026-11-04
- **Status:** Decided; applied on the branch
- **Context:** `projects-doc-quest.html` line 7 read `<script>"https://cdn.tailwindcss.com"></script>`. The address was text inside the script, not the tag's `src`, so Tailwind never loaded. The page uses 25 Tailwind classes and scrolled sideways on a 390-pixel screen. The sibling page, `projects-ai-headline-hero.html`, has the correct tag.
- **Decision:** Change line 7 to `<script src="https://cdn.tailwindcss.com"></script>`. No other line changed.
- **Verification:** Tested on a scratch copy before the repo changed. Tailwind loaded, the sideways scroll went away, and the accessibility scan found 0 violations.
- **Consequences:** The page now looks the way its author intended, which is a visible change. Both game pages still depend on Tailwind's CDN, which loads the library from the internet on every visit. Self-hosting a built stylesheet would remove that dependency. It is not done.

### D27: Code blocks wrap long lines

- **Date:** 2026-11-04
- **Status:** Decided
- **Context:** A folder-tree code block in the published downloads README made that page scroll sideways on phones. The README must not be changed.
- **Decision:** Style `pre` blocks in `_sass/_base.scss` to wrap long lines. A scrolling code block would need to be keyboard-focusable, which cannot be added to HTML that Jekyll generates from a README.

### D28: Remove the old files, and turn the default theme off

- **Date:** 2026-11-04
- **Status:** Decided; applied on the branch
- **Context:** Four groups of old files were left after the rebuild: the four old project pages, the old stylesheets, two unused includes, and 30 unused images (2.6 MB).
- **Decision:** Delete all four groups, each after Chris's confirmation. The old project pages are replaced by redirects for their `.html` and folder-form addresses. Set `theme: null` in `_config.yml`.
- **Why `theme: null`:** The GitHub Pages toolchain adds its default theme (Primer) when none is set, and published its 136 KB stylesheet at `/assets/css/style.css` once the old file was deleted. Nothing uses it. Setting the theme to null leaves `main.css` as the only stylesheet.
- **Checks after removal:** 140 internal references and none broken, 0 accessibility violations on all 10 pages, no sideways scrolling at 390 pixels, and Vale clean on all 11 of the site's own Markdown files.
- **Recovery:** Everything removed stays on `main` and in git history (commit `eccaa6d`), and the 30 images are in the zip Chris downloaded.
- **Kept:** `_originals/` (full-size images and the manifest), and `assets/downloads/`, which was not touched.

### D29: The Teal Capture sentence says "one week"

- **Date:** 2026-11-04
- **Status:** Decided; applied on the branch
- **Context:** After D20 set the Teal timeline to "1 week," the Capture section still said feedback was collected "over the course of three months."
- **Decision:** Change the phrase to "over the course of one week," as Chris directed, so the page agrees with itself. Chris's wording is lowercase mid-sentence here ("over the course of one week").
- **Consequences:** UXfolio still says "3 months" in the facts row and "three months" in this sentence, and UXfolio is the source of truth under D23. Chris needs to make both edits there, or the next sync would undo them.

---

## Open decisions

| Item | State |
|------|-------|
| Add a carousel for the prototype slides | Optional, after the content is done |
| Self-host the Google Fonts instead of loading them from Google | Not decided. The fonts are requested from a third party on every page |
| A public accessibility statement page | Planned for the documentation phase |
| Whether to delete the branch `claude/case-study-fixes` | Waiting for Chris |
| Check the Figma embed and the YouTube video in a real browser | After merge |
| Make the same typo and wording fixes on UXfolio (the six in the phase 4 review sheet, and the four Chris made: the Teal facts row and Capture sentence, the game card time, and "embracing opportunities") | Waiting for Chris |
| Fix the likely broken LinkedIn address in UXfolio's footer (`linkedin.com/cblocher` has no `/in/`) | Waiting for Chris |
| Fix the five `.md` file names that UXfolio turned into web links on the AI skill page | Waiting for Chris |
| Remove the allowed domains added for this work (`uxfol.io`, `cblocher.github.io`, the Figma hosts, `cdn.tailwindcss.com`) | Waiting for Chris, after the site is merged |
