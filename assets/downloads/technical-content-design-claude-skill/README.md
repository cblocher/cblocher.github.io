# README - Technical Content Design — Claude Skill

A Claude skill for technical writers and content designers working across SaaS, software, and mobile app products. It produces high-quality, accessible content that reads as human-written — and adapts to your client's voice, tools, and style guide.

## Disclaimer
This skill is provided as-is and shouldn't be used to create production-ready content. It is merely the result of me learning how to build Claude skills and use reference files. Use at your own risk.

## What this skill does

When active, Claude acts as an experienced technical writer and content designer. It handles the full range of software content deliverables, including:

- Help articles and user guides
- UI copy, microcopy, and error messages
- API references and SDK documentation
- Blog posts, emails, and social content
- PRDs, feature specs, and UX flows
- Video scripts, captions, and subtitles
- Style guides, glossaries, and word lists
- Compliance documentation (SOC2, ISO)

## What makes it different

Most AI writing defaults to generic, textbook-style output. This skill is built to avoid that. Key behaviors:

- **Infers before asking.** It reads context from your conversation first and only asks what it genuinely can't determine — batched into one message, three questions max.
- **Mirrors your language.** It picks up your product names, feature labels, industry terminology, and audience descriptions and uses them throughout the draft.
- **Enforces accessibility from the start.** WCAG 2.1 AA standards (plain language, heading hierarchy, alt text, inclusive language) are active while writing, not checked afterward.
- **Actively avoids AI-sounding writing.** Flagged phrases, em dashes, uniform paragraph rhythm, and over-hedging are blocked during drafting — not reviewed at the end.
- **Surfaces style guide rules before writing.** When you provide a style guide, it lists the rules it extracted and confirms them with you before producing a single word.

## Content lifecycle coverage

The skill organizes deliverables across six lifecycle phases:

| Phase | Deliverables |
|-------|-------------|
| 1: Discovery & Strategy | Content strategy, style guides, glossaries |
| 2: Planning & Definition | PRDs, feature specs, user stories, acceptance criteria |
| 3: Design & Prototyping | UX flows, microcopy, error messages, onboarding |
| 4: Build & Document | API references, help articles, compliance docs |
| 5: Launch & Announce | Release notes, blog posts, emails, social, video scripts |
| 6: Operate & Maintain | FAQs, knowledgebase, troubleshooting |

## Installation

### Download the technical-content-design.skill file
1. Right-click technical-content-design.skill > Save link as > and save it to desktop.

### Claude (web — claude.ai)

1. Go to **Settings > Capabilities** and enable **Code execution and file creation**
2. Go to **Customize > Skills**
3. Click **+** then **Upload a skill**
4. Upload `technical-content-design.skill`
5. Toggle the skill on

Full instructions: [support.claude.com](https://support.claude.com/en/articles/12512180-use-skills-in-claude)

### Claude Code (terminal)

1. In Claude Code, enter `mkdir -p ~/.claude/skills`
2. Then enter `unzip technical-content-design.skill -d ~/.claude/skills/`
3. Restart Claude Code to pick it up.
4. Once you're restarted Claude Code, enter `/skills`. The technical-content-design.skill should be listed.

Full instructions: [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills)

## File structure

```
technical-content-design/
├── SKILL.md                          # Main skill instructions
└── references/
    ├── accessibility-checklist.md    # WCAG 2.1 AA checklist with examples
    ├── content-type-catalog.md       # Structure and format guide per content type
    ├── drafting-guidance.md          # DITA patterns, reuse, and visual guidance
    ├── practitioners.md              # Practitioner influences and principles
    └── writing-quality-reference.md  # Anti-AI writing guide with examples
```

## Defaults

When no style guide is provided, the skill defaults to:
- **Voice and tone:** [Federal Plain Language Guidelines](https://digital.gov/guides/plain-language)
- **Grammar and usage:** [Microsoft Writing Style Guide](https://learn.microsoft.com/en-us/style-guide/welcome/)

These can be overridden at any time by uploading or pasting your own style guide.

## License

MIT — use it, adapt it, share it.
