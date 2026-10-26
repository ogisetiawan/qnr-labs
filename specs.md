# QNR Labs Website — Project Specs

> Context file for the Cursor agent. Read this fully before writing any code.
> Anything marked **[TBD]** is an open decision: do NOT invent a value. Use a clearly marked placeholder and list it in your final summary.

---

## 1. Project Overview

**Name:** QNR Labs
**Domain:** `qnr.my.id`
**Category:** Independent Digital Product Studio / Digital Solutions Studio 
**Stage:** Founder-led, early-stage concept; currently no confirmed team or formal company structure.
 

### What QNR Labs is

QNR Labs is intended to become the home for digital products, applications, tools, client solutions, and experiments created by the founder. It should start as a simple, credible website that can grow alongside the work. It must not pretend to be a large company or imply a team, customer base, or business maturity that does not yet exist. The name QNR is derived from the initials/name of the founder's child and has personal meaning. Do not invent or publish a different expansion of the acronym.
 

### Relationship to other sites

| Site | Purpose |
|---|---|
| `ogisetiawan.my.id` | Personal portfolio / personal brand (built separately with Astro on Netlify). Out of scope here. |
| `ogisetiawan.github.io` | Old portfolio, to be retired. |
| `qnr.my.id` (this project) | Studio brand: showcase of released apps + entry point for client work. |

---

## 2. Goals

1. **Showcase released work** in one clean place, starting with the **Account Switcher** browser extension (100+ installs).
2. **Establish a credible studio presence** that can later accept client inquiries.
3. **Capture traffic from the old site.** The old page `ogisetiawan.github.io/account-switcher` still receives links from the extension. This site must become the new destination (see section 8).
4. Be **simple to extend**: adding a new project should mean adding one content file, not editing layout code.

### Non-goals (do NOT build these now)

- No blog, no login, no CMS backend, no database.
- No pricing page, no booking/payment flow.
- No "Team" page, no "Careers" page (no team exists yet).
- No testimonials, client logos, or fabricated metrics.
- No multi-language switcher in MVP.

---

## 3. Target Audience

| Audience | What they want | What the site must give them |
|---|---|---|
| **Users of released apps** (e.g. Account Switcher users) | Find the official page, install link, updates | Clear project page with install CTA |
| **Potential clients** (small businesses, startups, individuals needing tools/web apps) | Judge credibility fast and know how to reach out | Honest hero, real work shown, one clear contact CTA |
| **Future collaborators** | Understand what the studio is | Short, honest description of what QNR Labs does |

---

## 4. Vision and Direction

### Long-term vision
Build QNR into an independent digital product/solution studio. Initially, the founder builds and releases products independently. Over time, QNR may take on client work, collaborate with friends or external contributors, recruit a team, and potentially develop repeatable solutions into standalone products.

This is a direction, not a claim that QNR is currently a formal company or has a team.

### Near-term purpose
- Present released applications and tools in one place.
- Showcase selected client work only when disclosure is permitted.
- Separate stable/released products from work in progress and experiments.
- Give each project a clear description, status, and relevant destination (live product, store listing, documentation, or repository).
- Establish a consistent identity that can scale without a major redesign.

### Guiding principles
- Build useful things that solve real problems.
- Prefer real work and clear explanations over marketing claims.
- Ship small, learn, improve, and iterate.
- Use technology intentionally.
- Be honest about project status, ownership, availability, and maturity.
- Keep the website lightweight and easy to maintain.

---

## 5. Brand Positioning

### Recommended category
**Independent Digital Product Studio**

Alternative supporting descriptor: **Software, Tools & Experiments**

### Suggested one-liner
“Building useful software, tools, and digital solutions.”

Alternative:
“An independent studio for software, tools, and digital experiments.”

Use wording that remains accurate while the founder is working solo. Avoid copy such as “our team” unless a real team exists. “QNR builds…” is a useful neutral formulation.

### Brand personality
- Minimal
- Modern
- Thoughtful
- Technical
- Independent
- Practical
- Quietly confident, not overhyped

--- 

## 6. MVP Scope

### Core pages
1. `/` — Homepage and selected work index.
2. `/work` — Optional listing page for products and selected solutions if the collection warrants a separate page.
3. `/work/[slug]` — Project detail pages for work that needs more explanation.
4. `/labs` — Experiments and work in progress, only if there is enough public content.
5. `/about` — Brief explanation of QNR Labs and its current founder-led stage.
6. `/contact` — Optional if a clear contact route is available; can initially link to a public professional contact channel.

### Suggested homepage sequence
1. Header: QNR Labs wordmark and minimal navigation.
2. Hero: concise positioning statement and a “Explore work” link/action.
3. Selected work: a few real projects with title, one-line description, category, status, and destination.
4. Labs / experiments: optional; show only meaningful public experiments.
5. Short About section: explain the independent, founder-led studio without overclaiming.
6. Contact / footer: relevant links and copyright.

### Deliberately deferred (add only after the first real client project exists)

- Capabilities / services section
- Process section
- Testimonials

---

## 8. Project Detail Page Template

Each project is a content entry with:

| Field | Type | Notes |
|---|---|---|
| `title` | string | e.g. "Account Switcher" |
| `slug` | string | URL segment |
| `summary` | string | One sentence for cards |
| `description` | markdown | Body of the detail page |
| `category` | enum | `extension` · `web-app` · `tool` · `client` . `ai-agent` etc  |
| `status` | enum | `released` · `in-progress` |
| `links` | array | e.g. `{ label: "Install", url }` |
| `highlights` | string[] | Short bullets (only verified facts) |
| `date` | date | Release date **[TBD]** |
| `featured` | boolean | Show on home |
 

### Seed content: Account Switcher

- Category: `extension`, status: `released`
- Verified fact: **100+ installs**
- Install link (Chrome Web Store URL): **[TBD]**
- Short description / feature bullets: **[TBD — ask owner; do not invent features]**
- Screenshots: **[TBD]** (use a neutral placeholder block until provided)

---

## 8. Design Direction 
- TBD

### Reference sites (for feel, do NOT copy layout or content)

- https://cirqle.studio/
- https://dexon-react.vercel.app/
- https://unifato.com/agnova/project-details.html
- https://jtrlabs.com/
- https://px7.digital/

---

## 8. Technical Requirements

### Stack (Optional TBD)

- **Framework:** Astro (static output)
- **Content:** Astro Content Collections (Markdown/MDX + typed schema via Zod) for projects
- **Styling:** Tailwind CSS (or plain CSS variables if simpler); no heavy UI libraries
- **Hosting:** Vercel, custom domain `qnr.my.id`
- **Package manager:** pnpm (unless the repo already uses another)
- **JS:** ship zero JS by default; add islands only if truly needed

### Quality targets

- Lighthouse (mobile) ≥ 95 for Performance, Accessibility, Best Practices, SEO
- Semantic HTML, keyboard navigable, visible focus states, WCAG AA contrast
- Images optimized via Astro image tooling, with `alt` text and explicit dimensions
- Each page has unique `<title>`, meta description, Open Graph tags, canonical URL
- Generate `sitemap.xml` and `robots.txt`
- Favicon + simple OG image (text-based wordmark acceptable)

---

## 9. Agent Working Rules

1. Read this file first. If something required is marked **[TBD]**, use a labeled placeholder and continue; collect all placeholders in your final summary.
2. Do not add features from the Non-goals or Deferred lists.
3. Do not invent copy that makes factual claims (see section 4).
4. Keep components small and typed; prefer content-driven rendering over hard-coded project markup.
5. Work in small steps, run `pnpm run build` after each milestone, and fix errors before continuing.
6. Do not install dependencies that are not needed for this scope. State the reason for any added dependency.
7. At the end, report: what was built, what is placeholder, what the owner must do manually.

---

## 10. Task Checklist (execute in order)

- [ ] **T1 — Scaffold:** Init Astro project, TypeScript strict, Tailwind (or CSS tokens), base layout with SEO head component.
- [ ] **T2 — Design tokens:** Colors, typography scale, spacing, light/dark theme.
- [ ] **T3 — Content collection:** `work` schema + seed `account-switcher.md` with placeholders for TBD fields.
- [ ] **T4 — Home page:** Hero, Selected Work (single-item-safe layout), Contact CTA, Footer.
- [ ] **T5 — Project detail template:** `/work/[slug]` rendering all schema fields; Account Switcher is the first entry.
- [ ] **T6 — Utility pages:** 404, sitemap, robots, favicon, OG image.
- [ ] **T7 — Quality pass:** Lighthouse, accessibility check, responsive check at 360px / 768px / 1280px.
- [ ] **T8 — Deploy config:** `vercel` (build command, publish dir) and notes for connecting `qnr.my.id`.

### Definition of Done (MVP)

- Builds cleanly with no warnings that affect output.
- Home page and Account Switcher page render correctly on mobile and desktop, light and dark.
- Adding a second project requires only adding one Markdown file.
- No fabricated claims anywhere on the site.
- All **[TBD]** items are listed in the final report.