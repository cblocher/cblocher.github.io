# Content guide

How to add or change content. Last reviewed: 2026-11-04.

For the folder map, see `README.md`. For how a page is built, see `architecture.md`.

---

## The source of truth

UXfolio (https://uxfol.io/5a5a1147) is the latest version of the portfolio (D23). When the GitHub site and UXfolio differ, UXfolio wins. When you fix a typo or change wording on the GitHub side, make the same change on UXfolio, or the next sync will undo it.

---

## Change a case study

Each case study is one file in `projects/`. The settings at the top (between the two `---` lines) control the title, images, and facts. The text below them is Markdown.

### Settings

| Key | What it does | Required? |
|-----|--------------|-----------|
| `title` | The page title and the H1 | Yes |
| `summary` | The italic line under the title | Yes |
| `card_title` | The title on the home page card, if different from `title` | No |
| `card_summary` | The text on the home page card, if different from `summary` | No |
| `order` | The position of the card (1 comes first) | Yes |
| `thumbnail` | The 800 by 600 card image | Yes |
| `hero` | The top image: `src`, `alt`, and optionally `shape: portrait` for a tall image | No |
| `overview`, `goal`, `results` | The three columns under the hero. Markdown links work. | No |
| `facts` | Team, role, timeline, tools, as `Label: "value"` lines | No |
| `stats` | Big numbers: a list of `value` and `label` | No |
| `slides` | A numbered series of images: `src`, `alt`, `caption` | No |
| `redirect_from` | Old addresses that should redirect here | No |

### Body

- Start sections at `##`. The layout already writes the H1.
- Use sentence case for headings: "Why I built one," not "Why I Built One." Vale checks this.
- Add an image: `{% include figure.html src="/assets/images/projects/<project>/<file>" alt="What the picture shows" caption="Optional caption" %}`
- Add an embed: `{% include embed.html src="https://embed..." link="https://..." title="What the embed shows" caption="Optional caption" %}`
- Add the slides: `{% include slides.html label="Prototype slides" %}` (the slides themselves are in the settings).
- Add the stats: `{% include stats.html %}` (the numbers are in the settings).

---

## Add a new case study

1. Put the full-size images in `_originals/<project>/` exactly as they were exported. Never edit them.
2. Make web copies in `assets/images/projects/<project>/`. Resize anything wider than 2000 px to 2000 px wide. Save as WebP, or keep PNG for logos and diagrams.
3. Make a thumbnail named `thumbnail.webp`, 800 by 600 pixels. Fit the whole screen inside the frame on the page background color (`#F3F4F6`) with about 6 percent of margin. Do not crop. The 1px border comes from the stylesheet.
4. Copy an existing file in `projects/` to a new name, such as `projects/new-project.md`, and edit the settings.
5. Add rows for the new images to `_originals/manifest.md`.
6. Run Vale, build the site, and check the page (see `workflow-and-maintenance.md`).
7. Add an entry to `docs/decision-log.md` if you made a choice worth remembering.

The home page and the "Read more" list pick the project up on their own, sorted by `order`.

---

## Change the home page or the About page

- **Home page:** `index.md`. The cards come from the case study files. The "Coming soon" card comes from `_data/coming_soon.yml`. Delete that file to remove the card.
- **About page:** `about.md`. The four role cards, the five testimonials, and the four certifications are lists in the settings at the top. The intro text, the "When not untying content knots..." section, and the photos are in the body.

---

## Alt text

| Image type | Alt text |
|------------|----------|
| A screenshot or photo that carries information | Describe what a person would learn by seeing it. Include any text that matters. |
| A diagram or chart | State the main point and the key data. |
| A decorative image whose meaning is in nearby text (role photos, certification badges, card thumbnails) | `alt=""` |
| A comic | Give the panels' dialogue |

Write alt text in plain sentences. Do not start with "Image of" or "Picture of."

---

## Writing rules

- Headings in sentence case. Vale enforces this (`vale projects/`).
- Link text says where the link goes. Never "click here."
- American English.
- When copying text from UXfolio, fix obvious typos and tell the owner so UXfolio can be fixed too.
- Direct quotes keep their wording. Where a word must change, put the edit in square brackets, as in "He is [an expert in] his craft."

---

## Syncing from UXfolio

1. Open the UXfolio page and read the whole page, including captions.
2. Compare it with the matching file in `projects/` or `about.md`.
3. Copy new or changed text. Do not reword it.
4. Download any new images at full size into `_originals/`, then make web copies.
5. Record the change in `CHANGELOG.md` and, if it was a decision, in `docs/decision-log.md`.

---

## Things not to change

- `assets/downloads/`. It holds the README for the published skill, and UXfolio links to it.
- `_originals/` files. Add to it, but never edit an original.
- The addresses of the two game pages. UXfolio links to them.
- Old redirects. Once an address is published, keep its `redirect_from` entry.
