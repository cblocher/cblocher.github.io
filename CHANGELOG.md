# Changelog

What changed on the site and when. The newest entry is at the top. Entries are never edited after they are written. If one turns out to be wrong, add a correction in a new entry that names the date of the old one.

This file is not published. `_config.yml` excludes it.

---

## 2026-11-04

### Rebuilt (pull request 2)

- New structure: layouts (`default`, `project`), includes, Sass partials built into one stylesheet, and no inline styles.
- Four case studies moved to `projects/` (`ai-skill`, `digital-coach`, `teal-usability`, `style-guide-game`) and brought up to date with the UXfolio portfolio: Overview, Goal, Results, facts, stats, slides, embeds, Learnings, and Next steps.
- Home and About pages rebuilt from UXfolio. The About page gained a new headshot, role photos, a hobbies section, and a testimonials list. The old mentoring widget was removed.
- A "Coming soon..." card added to the home page and the "Read more" lists.
- Clean images: originals kept untouched in `_originals/`, web copies by project, and 4:3 thumbnails.
- Old addresses (`/projects-ai`, `/projects-cabira`, `/projects-teal`, `/projects-onboarding`, in both the folder and `.html` forms) redirect to the new pages.
- Removed the old project pages, the old stylesheets, two unused includes, and 30 unused images. The default theme was turned off.
- Fixed the Tailwind line on the Documentation Quest game page.
- Code blocks now wrap long lines, so the downloads page no longer scrolls sideways on phones.
- Added the Vale heading check, the learning guide, and the decision log.
- Fixed typos and wording: "Captured" (Teal summary), "Claude produce" (AI skill goal), "from planning to promoting," "criteria," "Iterate: Have Claude," "(shown below)," "1 week" (Teal timeline and Capture sentence), "(30 minutes)" (game card), and "embracing opportunities."
- A testimonial now reads "He is [an expert in] his craft," with the edit in brackets.

### Fixed (pull request 3)

- Browser tab titles. The home page title no longer carries the whole site description, and the site title now uses a comma instead of a pipe, which the SEO plugin was dropping.

### Added

- Documentation set in `docs/`, and this changelog.

---

## 2026-11-03

### Accessibility and repair (pull request 1)

- Added a skip link, landmarks, and visible keyboard focus.
- Fixed heading levels on the About and Documentation Quest pages, and removed a second H1 from the site header.
- Fixed phone header overflow and removed a zoom limit.
- Replaced the footer email address with a link to LinkedIn.
- Repaired broken image references on the home and project pages.
- Resized four oversized images.
