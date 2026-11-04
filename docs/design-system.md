# Design system

The colors, type, spacing, and components of the site. Last reviewed: 2026-11-04.

All values live in `_sass/_tokens.scss` as CSS custom properties. Change a value there and it changes everywhere. Do not type a color or size directly into a page or a component file when a token exists.

---

## Colors

| Token | Value | Used for |
|-------|-------|----------|
| `--bg-primary` | `#F3F4F6` | Page background |
| `--bg-secondary` | `#FFFFFF` | Certification cards, code blocks, the embed frame |
| `--border` | `#D1D5DB` | Thumbnail, hero, and figure borders; dividers |
| `--text-primary` | `#1A1A1A` | Headings and main text |
| `--text-secondary` | `#595959` | Paragraphs, captions, secondary text |
| `--accent-color` | `#D32F2F` | The red logo box |
| `--accent-hover` | `#B71C1C` | The logo box on hover |
| `--link-color` | `#1D4ED8` | Links |
| `--link-hover` | `#1E3A8A` | Links on hover |

### Contrast

WCAG 2.1 AA needs 4.5 to 1 for normal text. Ratios were computed on 2026-11-04.

| Pair | Ratio |
|------|-------|
| Body text on the page background | 15.81 |
| Body text on white | 17.40 |
| Secondary text on the page background | 6.36 |
| Secondary text on white | 7.00 |
| Link on the page background | 6.09 |
| Link on white | 6.70 |
| Link on hover on the page background | 9.41 |
| White on the logo red | 4.98 |
| White on the logo red, hover | 6.57 |
| Border on the page background | 1.34 (decoration only, not text) |

The old link blue (`#3B82F6`) measured about 3.4 to 1 and failed. It was darkened (D12).

---

## Type

| Token or rule | Value |
|---------------|-------|
| `--font-heading` | Montserrat (weights 600 and 700), then system fonts |
| `--font-body` | Lora (regular, medium, italic), then Georgia |
| Body text | 1.125 rem, line height 1.8 |
| H1 | `clamp(2rem, 9vw, 3.5rem)`, so it shrinks on phones |
| H2 | 2.5 rem, centered. Inside a case study body: 2 rem, left-aligned |
| H3 | 1.5 rem |
| H4 | 1.25 rem |
| `--heading-case` | `none`. Headings display as typed. See `tech-stack.md` for why. |

---

## Spacing and width

| Token | Value |
|-------|-------|
| `--space-sm` | 0.5 rem |
| `--space-md` | 1 rem |
| `--space-lg` | 2 rem |
| `--space-xl` | 4 rem |
| `--space-xxl` | 8 rem |
| `--container-width` | 1000 px (page container) |
| `--container-width-narrow` | 800 px (reading column) |

On a case study page, text stays in the 800 px column. The hero, facts, and embeds use the full 1000 px container.

### Breakpoints

| Width | What changes |
|-------|--------------|
| 768 px and below | The About page's headshot stacks above the intro text |
| 480 px and below | The header wraps and centers, page side padding shrinks, testimonial text gets smaller, and the embed frame gets taller |

---

## Components

| Component | Where it lives | Notes |
|-----------|----------------|-------|
| Skip link | `_sass/_accessibility.scss` | Hidden until it takes keyboard focus |
| Keyboard focus ring | `_sass/_accessibility.scss` | A 3 px dark outline with a white halo, on every link, button, frame, and focusable item |
| Header and navigation | `_sass/_layout.scss`, `_includes/nav.html` | The current page is underlined and marked `aria-current` |
| Hero | `_sass/_cards.scss` | The home page intro |
| Case study card | `_sass/_cards.scss`, `_includes/project-cards.html` | A 4:3 thumbnail with a 1px border, a title, and a summary. The "Coming soon" card is the same card without a link. |
| Case study page | `_sass/_project.scss`, `_layouts/project.html` | Title, summary, hero, Overview, Goal, Results, facts, body |
| Figure | `_sass/_project.scss`, `_includes/figure.html` | Image with a 1px border and a centered italic caption |
| Embed | `_sass/_project.scss`, `_includes/embed.html` | 16:9 frame (4:5 on phones) and an "Open in a new tab" link |
| Slides | `_sass/_project.scss`, `_includes/slides.html` | Stacked, with "Slide 1 of 5" labels |
| Stats | `_sass/_project.scss`, `_includes/stats.html` | Large numbers with labels |
| Role cards, quotes, certification cards | `_sass/_about.scss` and the matching includes | About page |
| Code blocks | `_sass/_base.scss` | Long lines wrap instead of scrolling sideways |
| Footer | `_sass/_layout.scss`, `_includes/footer.html` | "Let's talk!" link and navigation |

---

## Rules

1. **No inline styles.** Never write `style="..."` in a page, layout, or include. Add a class and style it in `_sass/`.
2. **Use tokens.** Colors, fonts, and spacing come from `_tokens.scss`.
3. **Check contrast.** A new text color must reach 4.5 to 1 against the background it sits on. Compute it before using it.
4. **Keep focus visible.** Never remove the focus ring.
5. **Respect reduced motion.** New animations must be switched off by the existing `prefers-reduced-motion` rule.
6. **Alt text.** Every image has an `alt` attribute. Decorative images use `alt=""`.
7. **Add a component in four steps:** write the markup as an include, style it in a `_sass/` file, import that file in `assets/css/main.scss`, and document it in the table above.
