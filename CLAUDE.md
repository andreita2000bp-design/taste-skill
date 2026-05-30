# Project defaults — taste-skill

This repo ships portable Agent Skills (the `skills/` folder) that turn AI-built
interfaces into modern, responsive, premium frontends. They are installed at
the user level (`~/.claude/skills/`) so every session can invoke them.

## Default behavior for website / UI work

Whenever the user asks for any of:

- a website, landing page, marketing site, portfolio, hero, section, or
  redesign
- HTML / CSS / JS or React / Vue / Svelte / Astro / Next.js frontend code
- "make it look premium", "more modern", "responsive", "fix the UI", "polish
  the design"

**You MUST invoke the matching skill from this repo via the `Skill` tool
before writing any code.** Do not produce frontend code from your own
defaults; let the skill set the design language first. One skill per task is
usually enough — combine only when the task genuinely spans concerns.

### Default routing table

| Brief | Skill to invoke |
| --- | --- |
| General landing page, portfolio, marketing site (greenfield) | `design-taste-frontend` |
| Existing site that needs a quality lift / redesign | `redesign-existing-projects` |
| User asked for "premium / expensive / high-end / agency-y / Apple-like" | `high-end-visual-design` |
| User asked for "minimal / editorial / Notion / Linear vibe" | `minimalist-ui` |
| User asked for "brutalist / Swiss / industrial / terminal" | `industrial-brutalist-ui` |
| User attached or referenced an image and wants it implemented | `image-to-code` |
| Working inside Google Stitch or needs a `DESIGN.md` export | `stitch-design-taste` |
| Output is being truncated / half-finished components | also load `full-output-enforcement` |
| Pre-code reference boards: website comps | `imagegen-frontend-web` |
| Pre-code reference boards: mobile screens | `imagegen-frontend-mobile` |
| Pre-code reference boards: brand identity | `brandkit` |
| Strict GPT/Codex-style rules with aggressive variance | `gpt-taste` |

If the brief is genuinely ambiguous between two skills, ask exactly **one**
clarifying question before picking — never a multi-question dump.

### Three dials (only for `design-taste-frontend`)

When `design-taste-frontend` is active, surface and respect these 1–10 dials
before generating code:

- `DESIGN_VARIANCE` — 1 centered/clean, 10 asymmetric/experimental
- `MOTION_INTENSITY` — 1 static, 10 cinematic / scroll-driven / physics
- `VISUAL_DENSITY` — 1 art-gallery airy, 10 cockpit / packed dashboard

Default for a premium modern landing page: `8 / 6 / 4`.

## Quality bar — non-negotiable for any site we ship

- **Responsive**: mobile-first, fluid type (`clamp()`), tested down to 360 px
  and up to 1920 px. No horizontal scroll, no layout breakage at common
  breakpoints.
- **Modern stack**: semantic HTML5, CSS Grid + Flexbox, container queries
  where they help, `prefers-reduced-motion` respected.
- **Premium typography**: variable fonts, real type scale (1.2–1.333 ratio),
  tight tracking on display sizes, comfortable measure (45–75ch) on body.
- **Premium motion**: GSAP / Framer Motion / native View Transitions, never
  the default "fade-in-up on everything". Motion has intent.
- **Performance**: lazy-load below the fold, no layout shift, no
  unused-bundle bloat.
- **Accessibility**: contrast ≥ WCAG AA, focus rings visible, keyboard
  reachable, semantic landmarks.
- **No AI-slop defaults**: no centered hero over purple mesh gradient, no
  three equal feature cards, no glassmorphism on everything, no Inter +
  slate-900 unless the design read demands it.

## Installation reference

Skills live in `skills/` here and are also installed locally under
`~/.claude/skills/` using their install names (the `name:` field in each
SKILL frontmatter). To install in another machine or repo:

```bash
npx skills add https://github.com/Leonxlnx/taste-skill
# or just one
npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"
```
