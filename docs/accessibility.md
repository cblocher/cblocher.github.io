# Accessibility

What is built in, what has been tested, and what has not. Last reviewed: 2026-11-04.

**Target:** WCAG 2.1 level AA.

---

## What is built in

| Feature | Where |
|---------|-------|
| A skip link to the main content | `_layouts/default.html`, `_sass/_accessibility.scss` |
| Landmarks: header, navigation (Main and Footer), main, footer | Layouts and includes |
| One H1 per page, headings in order | Layouts and page files |
| Visible keyboard focus on every link, button, and frame | `_sass/_accessibility.scss` |
| The current page marked in the navigation (`aria-current`) | `_includes/nav.html` |
| Text colors that meet 4.5 to 1 contrast | `_sass/_tokens.scss`; ratios in `design-system.md` |
| Links underlined in body text, so color is not the only cue | `_sass/_base.scss` |
| Alt text on every image, and empty alt text on decorative ones | Page files and includes |
| Titles on every embedded frame, and a text link as a fallback | `_includes/embed.html` |
| A "reduce motion" setting respected | `_sass/_accessibility.scss` |
| External links that open a new tab say so, for screen readers | Navigation, footer, certification cards, embed links |
| A phone layout that does not scroll sideways | Checked at 390 px |
| A video address that sets no tracking cookies until played | `youtube-nocookie.com` |
| No carousel to operate: slides are stacked and testimonials are a list | `_includes/slides.html`, `_includes/quotes.html` |

---

## What has been tested

| Test | Result | Date |
|------|--------|------|
| axe-core, WCAG 2.0 and 2.1 A and AA rules, nine live pages at desktop width | 0 violations | 2026-11-04 |
| axe-core best-practice rules, the same nine pages | 0 issues on seven pages. The two game pages report one missing `main` landmark and unlabeled regions (`landmark-one-main`, `region`). | 2026-11-04 |
| axe-core WCAG A and AA plus best-practice rules on the new 404 page, built locally | 0 violations | 2026-11-04 |
| Sideways scrolling at 390 px, nine live pages, and the 404 page | None | 2026-11-04 |
| Every image has an `alt` attribute, nine live pages | Yes | 2026-11-04 |
| Contrast ratios computed for every text and background pair | All pass (see `design-system.md`) | 2026-11-04 |

The nine pages are the home page, About, the four case studies, the two game pages, and the downloads page.

Automated tools find only a part of the possible problems. A clean scan does not mean the site is accessible.

---

## What has not been tested

- **Screen readers.** No testing with NVDA, JAWS, VoiceOver, or TalkBack.
- **Keyboard-only use by a person.** The focus ring and tab order exist in the code. No one has walked through every page with only a keyboard.
- **Zoom and reflow.** Not checked at 200 percent and 400 percent zoom.
- **Voice control, switch devices, and screen magnifiers.**
- **Color blindness simulation.** Color is never the only cue, but this was not simulated.
- **The Figma and YouTube embeds.** They could not be loaded in the build environment, so their keyboard behavior was not checked.
- **The game pages' own interaction.** Only the automated rules were run.

---

## Known gaps

| Gap | Detail |
|-----|--------|
| Game pages have no `main` landmark and unlabeled regions | They are separate HTML files written outside the site's layout |
| Alt text and slide captions were written by an AI assistant | They need the owner's review |
| The Content Designer photo shows other companies' app icons | Marked decorative, and unchanged from UXfolio |
| No public accessibility statement | Recommended; see "Next steps" |

---

## Checklist before merging a change

1. Build the site and run an automated scan on every page you touched.
2. Tab through the page. The focus ring is visible on every stop, and the order matches the reading order.
3. Check that every new image has alt text (or an empty alt for a decorative one).
4. Check headings: one H1, then H2, with no skipped levels.
5. Check any new color pair for 4.5 to 1 contrast.
6. View the page at 390 px wide. Nothing scrolls sideways.
7. Run Vale on the Markdown files.

---

## Next steps

1. Walk through each page with the keyboard only, and note any problem.
2. Test with at least one screen reader (VoiceOver and NVDA are free or built in).
3. Check zoom at 200 and 400 percent.
4. Publish a short accessibility statement: the target standard, what was tested, known gaps, and how to report a problem. This would be a public page, so it needs the owner's approval.
