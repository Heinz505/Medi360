# Medi360 — Hospital Rostering SaaS

> Submission for the Two-Part Web Developer Assessment.
> Two builds, one product universe: a marketing landing page and a rostering dashboard.

---

## Live URLs

| Deliverable | URL |
|---|---|
| Challenge 1 — Landing page | https://heinz505.github.io/Medi360/ |
| Challenge 2 — Rostering dashboard | https://heinz505.github.io/Medi360/rostering-dashboard.html |
| GitHub repository | https://github.com/Heinz505/Medi360 |

---

## Running locally

No build step, no dependencies to install. This is a plain HTML/CSS/JS project.

```bash
# Clone the repo
git clone git@github.com:Heinz505/Medi360.git
cd Medi360

# Open in a browser — any of these work:
#   Double-click index.html in your file explorer
#   Or serve with a local server to avoid any path issues:

npx serve .
# → visit http://localhost:3000

# Or with Python:
python -m http.server 8080
# → visit http://localhost:8080
```

Key files:

```
Medi360/
├── index.html                    # Challenge 1 — primary landing page
├── rostering-dashboard.html      # Challenge 2 — weekly rostering dashboard
├── index-landing-concept-2.html  # Alternate landing concept B (for reference)
├── index-landing-concept-3.html  # Alternate landing concept C (for reference)
├── css/
│   ├── styles.css                # Shared style system (landing + dashboard)
│   ├── index-landing-concept-2.css
│   └── index-landing-concept-3.css
└── images/
    ├── hero-roster.jpg
    └── hero-roster-mobile.jpg
```

Tested at 360px, 768px, and 1280px. Mobile menu is functional on all modern browsers.

---

## Stack

| Layer | Choice | Reason |
|---|---|---|
| Markup | Semantic HTML5 | Accessibility-first, no framework overhead |
| Styling | Vanilla CSS (custom properties, clamp, grid, flex) | Full control, no build step |
| Components | Bootstrap 5.3 (CDN) | Responsive grid, offcanvas, accordion, form selects |
| Typography | Manrope via Google Fonts | Clean, clinical weight range, pairs well with data-heavy UI |
| Icons | Inline SVG | No icon font requests, accessible via `aria-label` |
| JS | Vanilla ES2020 (IIFE) | Roster rendering, calendar picker, filter logic — no framework |
| Data | Embedded JSON (`<script type="application/json">`) | Zero API surface, zero backend, self-contained |
| Deployment | GitHub Pages / Vercel | Static output, free tier, no config |

---

## Breakpoints tested

| Width | Target |
|---|---|
| 360px | Mobile — full feature parity, working mobile nav |
| 768px | Tablet — two-column layouts activate |
| 1280px | Desktop — full sidebar + roster grid layout |

---

## AI usage & process write-up

### Tools used

**GitHub Copilot (Claude Sonnet 4.6)** — primary coding assistant throughout the build, used inside VS Code via the chat agent panel.
**VS Code** — editor and debugging environment.
**Photoshop / Illustrator / Inkscape** — used for image and brand asset preparation where needed.
**Gemini / Bing Images** — used for occasional visual reference and comparison during early concept exploration.

### How I integrated AI into the workflow

I worked in a tight prompt → review → edit cycle rather than accepting blocks whole. The typical loop looked like:

1. **Prompt for structure** — describe a section's purpose, layout intent, and content hierarchy. Review the output, then adjust copy and markup to match the real product voice.
2. **Prompt for variants** — for the landing page I asked for two to three visual directions. Copilot generated the Command Center concept (concept B) and the warm editorial concept (concept C). I kept both as reference but submitted the primary index.html after editing it most heavily by hand.
3. **Prompt for interaction logic** — the calendar week-picker, filter row, and shift detail panel were scaffolded by AI and then reworked: the Sunday-first week model required manual data restructuring, and the `buildWeekRoster` template system was rewritten from scratch to produce realistic 10-week scheduling patterns.
4. **Prompt for accessibility** — I asked Copilot to audit the dashboard against WCAG AA. It identified missing `aria-pressed` on shift chips, missing live regions on filter output and week-range labels, and low-contrast muted states. I reviewed each suggestion and applied them with targeted patches rather than a wholesale rewrite.

### What AI got right

- Scaffolding semantic section structure quickly (hero, features, pricing, FAQ) with correct heading hierarchy and landmark roles.
- Producing consistent CSS custom property systems and responsive clamp() scale values.
- Generating realistic placeholder staff data — names, departments, shift notes — far faster than typing it manually.
- Identifying accessibility gaps I would have caught in a later pass but would have taken longer to enumerate manually.

### What I had to fix or rewrite

- **Calendar and week model.** AI initially produced a Monday-first ISO week model. The product required Sunday-first weeks to match clinical handover practice. I rewrote the day-order array, the `buildWeekRoster` function, and the column header renderer manually.
- **Dashboard data realism.** Early AI output produced flat, repetitive shift patterns. I rewrote the staff template system to support two alternating weekly templates per person and per-shift note variations.
- **Copy and brand voice.** AI defaults to safe, generic SaaS language. Every heading and subheading was rewritten to be more specific to the clinical operations context — language like "coverage visibility" and "handover-ready context" rather than "increase efficiency".
- **Hero shape positioning.** Visual decoration like the animated background circles required several manual iterations to feel balanced rather than default.

### The single biggest decision I made myself

Before writing code, I gave Copilot the architecture constraints up front: the languages, libraries, versions, accessibility expectations, brand direction, theme, typography, palette, and the fact that the work needed to stay static and self-contained. That made the output much more focused and reduced the amount of cleanup needed later.

### What I'd do with another day

- Balance the visual design further and add a few more elements to break up any repetition in the layout.
- Build out the staff section in the dashboard side menu with mock data and avatars.

---

## Branch structure

```
main
└── develop
    ├── feature/landing-page
    ├── feature/dashboard
    └── feature/readme        ← this branch
```

---

## Assessment checklist

- [x] Sticky nav with working mobile menu
- [x] Hero with primary CTA
- [x] Features section (3+ features)
- [x] Product showcase section
- [x] Pricing / How it works section
- [x] FAQ with accordion
- [x] Final CTA + footer
- [x] Mobile-first at 360px
- [x] Responsive at 360 / 768 / 1280px
- [x] No horizontal scroll
- [x] No lorem ipsum
- [x] Original brand name, palette, and copy
- [x] Dashboard: sidebar nav, topbar, filters, roster grid, shift detail panel
- [x] Dashboard: 10-week mock data, Sunday-first weekly model
- [x] WCAG accessibility pass (focus states, live regions, aria labels, contrast)
- [x] Live deployment URL — https://heinz505.github.io/Medi360/
- [x] Public GitHub repo URL — https://github.com/Heinz505/Medi360
