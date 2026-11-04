# Privacy and third parties

What the site collects, and which outside services it contacts. Last reviewed: 2026-11-04.

---

## What the site itself collects

Nothing. The pages contain no analytics, advertising, or tracking scripts (checked on the live home page on 2026-11-04). The site sets no cookies of its own (checked on four live pages on 2026-11-04) and has no forms, accounts, or comments.

**One exception to know about:** when the Figma frame on the Teal page loads, Figma sets three cookies from its own domains. The cookie test could not load the YouTube video, so its cookie behavior was not examined.

The footer used to show an email address. It was replaced with a LinkedIn link on 2026-11-03.

---

## Outside services the pages contact

When a visitor opens a page, their browser may request files from these services. Each service can see the visitor's network address and browser details.

| Service | What it provides | Which pages | Address |
|---------|------------------|-------------|---------|
| GitHub Pages | Hosts the site, and logs requests | All | `cblocher.github.io` |
| Google Fonts | The Montserrat and Lora fonts | All pages that use the site layout | `fonts.googleapis.com`, `fonts.gstatic.com` |
| Google Fonts | The "Press Start 2P" font | The two game pages | `fonts.googleapis.com` |
| Tailwind CDN | The Tailwind styling library | The two game pages | `cdn.tailwindcss.com` |
| YouTube | The video | The AI skill page | `youtube-nocookie.com` |
| Figma | The feedback file | The Teal page | `embed.figma.com`, `www.figma.com` |

The video uses YouTube's privacy-friendly address, which is meant to set no tracking cookies until someone plays it. Its cookie behavior was not examined. The video and Figma frames load lazily, as the visitor scrolls near them.

If a visitor's network blocks one of these services, the page still works. Fonts fall back to system fonts, and a blocked frame shows an empty box with a text link below it.

---

## Links that leave the site

| Where | Destination |
|-------|-------------|
| Navigation, footer | `https://www.linkedin.com/in/chrisblocher` |
| About page | Coursera (Google AI Professional), Applysynergies (5 Moments of Need), Pendo Academy, td.org |
| Style guide game page | Firehead's PDF; the game pages on this site |
| AI skill page | `claude.ai`, a Claude support article, GitHub (the skill's README), YouTube |
| Teal page | The Figma file |
| Downloads page | Digital.gov, Microsoft's style guide, a Claude support article, GitHub |

On 2026-11-04 an automated check could not reach most of these hosts from the build environment. They should be clicked through by hand every quarter.

---

## Content and permissions

- The text, images, and case studies are the owner's own work from the UXfolio portfolio.
- The style guide game page uses guidelines from an eight-page PDF published by Firehead. The page states that Firehead gave permission.
- The Content Designer photo on the About page shows app icons that belong to other companies. It is unchanged from UXfolio.
- No license file is in the repo. Without one, all rights are reserved to the owner by default. Add a license only on purpose.

---

## History and the owner's email

The git history is public. It includes the owner's commit email address, as any public repo does. GitHub's account setting "Keep my email addresses private" prevents the real address appearing in future commits. It does not change old ones. Rewriting history to remove it is possible but disruptive, and was not done.
