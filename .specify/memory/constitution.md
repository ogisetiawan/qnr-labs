<!--
Sync Impact Report
- Version change: 1.0.0 → 1.1.0
- Bump rationale: Principle I now records the owner-approved purpose in
  specs/specs.md. The site is an open-source project showcase that starts
  from personal problems and invites a visitor to ask QNR to build. The
  honesty rules are unchanged. MINOR because the principle was expanded,
  not removed.
- Modified principles:
  - [PRINCIPLE_1_NAME] → I. Product Principles
  - [PRINCIPLE_2_NAME] → II. Product Scope and Boundaries
  - [PRINCIPLE_3_NAME] → III. Design Principles
  - [PRINCIPLE_4_NAME] → IV. Technology and Architecture
  - [PRINCIPLE_5_NAME] → V. Coding Standards
- Added principles:
  - VI. Content and Data Management
  - VII. Quality Assurance and Testing
  - VIII. Security and Maintainability
  The request named these topics. The template allows a different principle
  count than the five scaffold slots.
- Added sections: none beyond the template's two named sections and Governance.
- Renamed sections:
  - [SECTION_2_NAME] → Documentation and Specification Governance
  - [SECTION_3_NAME] → Conflicting and Incomplete Requirements
- Removed sections: none.
- Rejected template example: this constitution does not supersede
  specs/specs.md. That file remains the only product specification.
- Intentionally retained marker: [TBD] is the project marker for an
  unresolved required value. It is not a constitution template slot.
  Retained items are listed under Conflicting and Incomplete Requirements.
- Unresolved source conflicts, recorded here and not edited in the sources:
  - Node.js 24 sentence versus the Node.js 26 pin
  - Checklist content-config path versus section 9
  - Checklist robots/sitemap wording versus section 9
  - "pnpm astro check" versus "pnpm exec astro check"
  - Ember-orange button-fill wording versus the text-link rule
  - Suggested substitute typefaces versus the missing Family font file
  - Mascot instruction inside Do's and Don'ts versus the mascot prohibition
  - Light-only style reference versus the light-and-dark requirement
  - Empty checklist item "Addition"
-->

# QNR Digital Labs Constitution

This file records governance already stated in `AGENTS.md`, `specs/specs.md`,
and `specs/design.md` through "Do's and Don'ts". It is not a product
specification. The only authoritative product specification is `specs/specs.md`.

## Core Principles

### I. Product Principles

QNR Digital Labs is a founder-led showcase of open-source projects for
`qnr.my.id`. Each project starts from a problem the founder needed to solve
and is published so other people can use it. A visitor with a problem of
their own can ask QNR to build it. The site MUST stay honest about stage,
ownership, and maturity. It MUST NOT claim a team, a formal company, a client
base, a service menu, a price, or business maturity that `specs/specs.md`
does not state.

Published copy MUST come from `specs/specs.md`. "QNR builds…" and "ask QNR to
build it" are allowed formulations. "Our team" is not. The name QNR MUST NOT
be given a public expansion. Metrics, testimonials, clients, licenses,
repositories, personal-problem stories, and feature claims MUST NOT be
invented. The only Account Switcher install metric the spec states is 100+
installs.

The site MUST prefer real work and plain status over marketing claims. It MUST
stay lightweight and maintainable. Positioning MUST remain accurate while the
founder is working solo.

### II. Product Scope and Boundaries

Work MUST stay inside the pages, fields, and actions named in `specs/specs.md`.
A page the spec marks optional, or conditions on public content or a real
contact route, MUST stay unbuilt until that condition is met in the spec.
Each work detail page includes the privacy policy placement the spec names.

The MVP MUST NOT add a blog, login, CMS backend, database, pricing page,
booking or payment flow, Team page, Careers page, testimonials, client logos,
fabricated metrics, or a multi-language switcher.

A service catalog, prices, a process section, testimonials, and client case
studies are deferred, as `specs/specs.md` states. A short statement of the
three facts — a personal problem, published so other people can use it, and a
visitor can ask QNR to build — is in scope. Deferred and non-goal items MUST
NOT be built. An implementation that already contains one does not amend the
spec.

A new project MUST be one Markdown file. It MUST NOT require a layout change.

### III. Design Principles

The visual system is already chosen. Agents MUST NOT pick a new aesthetic,
palette, or font. Token values MUST be read from `src/styles/global.css`.
Color roles, spacing, radius, elevation, and the do and don't rules MUST be
read from `AGENTS.md` and from `specs/design.md` through "Do's and Don'ts".
When a hex value in `specs/design.md` disagrees with the stylesheet, the
stylesheet MUST be used.

UI text MUST use `--font-inter` at 400, 500, and 600. Display and hero text
MUST use `--font-family` at weight 500, at `--text-heading-lg` and
`--text-display`. The Family font file is [TBD]. Another typeface MUST NOT be
added to fill that gap, including substitutes named in `specs/design.md`.

Page width MUST use `--page-max-width`. Sections sit 80–120px apart. Cards use
32px padding. Related items sit 8–12px apart. Cards MUST be white, use
`--radius-cards`, and use the inset hairline `--shadow-subtle`. A large drop
shadow MUST NOT be used. The page MUST stay flat: no gradient, glass, or glow.

Each action group has one primary action. The primary action is a dark pill
using `--surface-dark-surface`, cream text, and `--radius-buttons`. The
secondary action is a sand pill using `--surface-sand`. A tertiary action is
text only. `--color-ember-orange` is for a text link and the focus ring, not a
filled button. `--color-link-blue` is for an inline link, not a filled button.
Status color marks status only. `--color-alert-red` is for a destructive or
error state only.

The `:focus-visible` outline MUST be kept. Layout MUST be checked at 360, 768,
and 1280. Text contrast MUST meet WCAG AA. Motion, when a requirement needs it,
MUST use transform and opacity and MUST respect `prefers-reduced-motion`.

`public/brand/` MUST be changed only when the user asks. Login, tweets,
mascots, and Ethereum features or words from the reference MUST NOT be added.
Component writeups in `specs/design.md` that name another product are shape
only. They are not QNR requirements.

### IV. Technology and Architecture

The site MUST use Astro with TypeScript `strict` and `output: 'static'`. It
MUST NOT add React, Vue, or Svelte. Pages MUST ship no client JavaScript unless
a requirement needs an island. UI MUST be `.astro` components. An island is
allowed only when a requirement needs browser state.

A later on-demand route MUST stay in this repo: add `@astrojs/vercel` and set
`prerender` to false on that route only. That package MUST NOT be installed
until a route must render on demand. The site MUST NOT switch to
`output: 'server'` and MUST NOT move to Next.js for that route. Login, a
database, a CMS, and payments stay out of scope until a future spec adds them.

Content MUST follow section 9 of `specs/specs.md`: the `work` collection in
`src/content.config.ts`, a schema from `astro/zod`, the `glob` loader, and one
Markdown file per project in `src/content/work/`. A separate `zod` package
MUST NOT be added. The project page is the dynamic route under `src/pages/work/`
built with `getStaticPaths`. `@astrojs/mdx` MUST NOT be added for the MVP.

Styling MUST use Tailwind CSS v4 through `@tailwindcss/vite`. `@astrojs/tailwind`
MUST NOT be installed. Light and dark themes MUST use CSS variables and follow
`prefers-color-scheme`. A manual theme toggle is an island only if the design
requires a switch. Dark palette values that the stylesheet does not define
MUST NOT be invented. The style reference through "Do's and Don'ts" documents
a light theme only.

Images MUST use `astro:assets`. Every content image MUST have `alt` text and
explicit width and height. `site` MUST be `https://qnr.my.id`. Each page MUST
set a unique title, meta description, Open Graph tags, and a canonical URL on
that host. `@astrojs/sitemap` writes `sitemap-index.xml` during `pnpm build`.
`public/robots.txt` MUST point at that index.

The package manager MUST be pnpm. `package-lock.json` and `yarn.lock` MUST NOT
be committed. Node.js MUST be 26, as pinned by `AGENTS.md`, `package.json`
`engines`, `.nvmrc`, and the Scaffold checklist item. TypeScript MUST stay on
6. `astro check` does not support TypeScript 7. The typecheck command is
`pnpm exec astro check`. Scripts are `pnpm dev`, `pnpm build`, and
`pnpm preview`. Do not use `npx`.

Dependencies MUST stay inside the allowed-deps table in `specs/specs.md`:
`tailwindcss`, `@tailwindcss/vite`, and `@astrojs/sitemap`. For the MVP, do
not add `react`, `@astrojs/react`, `@astrojs/mdx`, `@astrojs/vercel`,
`@astrojs/tailwind`, `gray-matter`, or `react-markdown`. Any other package
requires a spec requirement the table cannot meet, a stated reason, and owner
approval. ESLint MUST NOT be added unless a later spec requires it.
`astro-critters` and `@playform/compress` MUST NOT be installed.

The hosting target in the spec is Vercel, with build command `pnpm build` and
output directory `dist`. A checkout under `htdocs` is only a folder. Apache,
PHP, and MySQL MUST NOT be used to serve this site. When an Astro 7 API is
unclear, current docs MUST be checked instead of guessing.

### V. Coding Standards

The relevant `specs/` sections MUST be read before the site is changed. A
change MUST NOT add behavior that the current request and `specs/specs.md` do
not both allow. Components MUST stay small and typed.

Skills under `.cursor/skills/` apply only where they do not contradict the
user's request, `specs/specs.md`, the stylesheet, the design rules in
Principle III, and `AGENTS.md`. The frontend-design skill MUST NOT choose a
new brand. The performance skill MUST meet the section 9 targets inside the
current stack, including `font-display: swap`, and MUST NOT run a Lighthouse
audit from that skill.

A completion summary MUST list what changed, every [TBD] left in place, what
the owner must configure or finish, and known limitations.

Agents MUST NOT run `git commit`, `git push`, `pnpm build`, `pnpm dev`,
`pnpm exec astro check`, or any deploy unless the user explicitly asks.
Product-requirement planning files are not a reason to do so.

### VI. Content and Data Management

Project content MUST be data in `src/content/work/`, rendered by the collection.
The fields MUST be those defined in `specs/specs.md` section 7: `title`,
`slug`, `summary`, `description`, `category`, `status`, `links`, `highlights`,
`license`, `repository`, `date`, and `featured`. The body MUST be the
collection entry's rendered content. A public project is open source, started
from a personal problem, and usable by other people. A client case study MUST
NOT be added unless the owner supplies it and permits disclosure.

The Account Switcher seed MUST use only facts the spec states, plus labeled
placeholders. These values stay unresolved and MUST NOT be guessed:

- Release `date` is [TBD].
- The Chrome Web Store install URL is [TBD].
- The short description and feature bullets are [TBD — ask owner; do not invent features].
- The personal problem it started from is [TBD — ask owner; do not invent it].
- The license is [TBD]. Do not guess a license name.
- The repository URL is [TBD].
- Screenshots are [TBD]. A neutral placeholder block is used until they exist.

There are no MVP secrets. API keys and a `.env` file MUST NOT be invented.
Copy that is not in `specs/specs.md` MUST NOT be written into content.

### VII. Quality Assurance and Testing

When a milestone check is requested, `pnpm build` MUST succeed and
`pnpm exec astro check` MUST pass after type or content-schema changes. The
spec's quality bar is Lighthouse mobile at or above 95 for Performance,
Accessibility, Best Practices, and SEO. Pages MUST use semantic HTML, keyboard
access, a visible focus state, and WCAG AA contrast.

The MVP definition of done is the one in `specs/specs.md`: a clean build, the
home page and the Account Switcher page correct on mobile and desktop in light
and dark, a second project added by one Markdown file only, no fabricated
claims, and every [TBD] listed in the report. Missing owner-supplied values
MUST remain placeholders. They are not test failures to paper over.

### VIII. Security and Maintainability

The MVP MUST NOT add login, a database, a CMS, payments, server-rendered
output, or environment secrets. Server features stay none until a future spec
adds an on-demand route.

The site MUST remain a static Astro build that is small enough to maintain.
Client JavaScript, adapters, UI frameworks, and dependencies MUST NOT be added
for convenience. An alternative stack or package MUST NOT be introduced without
a spec amendment and owner approval.

## Documentation and Specification Governance

`specs/specs.md` is the only product specification. Scope, copy, pages, content
fields, stack, allowed dependencies, non-goals, deferred work, and the
definition of done MUST be read from that file.

`specs/design.md` through "Do's and Don'ts" is the visual reference for how
tokens are used. It is not a second product specification. Text after
"Do's and Don'ts" MUST NOT be used as requirements. `src/styles/global.css`
holds token values. `AGENTS.md` holds agent operating rules and the UI rules
in Principle III.

Spec Kit feature files and a `.specs/` planning workspace MUST NOT be treated
as the product specification. They may plan work only by citing `specs/specs.md`.
They MUST NOT restate it as a competing spec.

Product requirements change only by an owner-approved edit to `specs/specs.md`.
This constitution MUST NOT be used to add, drop, or rewrite them. If this
constitution and `specs/specs.md` disagree on scope or copy, `specs/specs.md`
wins, and the disagreement MUST be reported. If this constitution and
`AGENTS.md` disagree on an agent convention, `AGENTS.md` wins until this file
is amended.

If `specs/` or another required document is missing, work MUST stop. The gap
MUST be reported. It MUST NOT be filled by guessing.

## Conflicting and Incomplete Requirements

A conflict MUST be recorded and reported. It MUST NOT be resolved by silently
editing `specs/specs.md`, `specs/design.md`, or source code, and it MUST NOT
be resolved by inventing a value.

When sources disagree, use this order:

1. The user's current request directs the task. It does not amend
   `specs/specs.md` unless the user asks to change that file.
2. `specs/specs.md` governs scope and copy. Inside that file, section 9
   governs the Astro configuration when the checklist disagrees. The mismatch
   MUST be mentioned.
3. `src/styles/global.css` governs token values.
4. `AGENTS.md`, then `specs/design.md` through "Do's and Don'ts", governs how
   tokens are used.
5. If the spec and the pinned repo disagree, follow `package.json` `engines`
   and `.nvmrc`, and report the conflict. Do not invent a resolution.
6. Skills apply only after the items above.

These inconsistencies are unresolved in the source documents:

- The development-environment paragraph in `specs/specs.md` still says
  Node.js 24. `AGENTS.md`, `package.json` `engines`, `.nvmrc`, and the
  Scaffold checklist item pin Node.js 26. Node.js 26 stands. The Node.js 24
  sentence is an unresolved documentation inconsistency.
- Section 9 requires `src/content.config.ts`. The checklist still says
  `src/content/config.ts`. Follow section 9 and report the mismatch.
- Section 9 requires `@astrojs/sitemap` and `public/robots.txt`. The checklist
  also allows `@astrojs/robots-txt` or a sitemap file in `public/`. Follow
  section 9.
- Section 9 says `pnpm astro check`. `AGENTS.md` says the typecheck command is
  `pnpm exec astro check`. Use the `AGENTS.md` command.
- The color table in `specs/design.md` describes ember orange as a button fill.
  `AGENTS.md` and the "Do's and Don'ts" section say it is not a filled button.
  Follow `AGENTS.md`.
- `specs/design.md` names substitute display typefaces. The Family font file
  is [TBD], and `AGENTS.md` forbids adding a typeface to fill that gap.
- A "Do" bullet tells the reader to use cartoon mascot clusters. `AGENTS.md`
  forbids adding mascots. Follow `AGENTS.md`.
- `specs/design.md` records a light theme. Section 9 and the definition of
  done require light and dark through `prefers-color-scheme`. Do not invent
  the missing dark values.
- The checklist item "Addition" has no requirement text. Its meaning MUST NOT
  be invented.

Unresolved required values stay written as [TBD]. They are the Account Switcher
date, install URL, short description, feature bullets, personal problem,
license, repository, and screenshots, and the Family font file. A completion
summary MUST list each one still in place.

## Governance

This constitution is the governance summary for Spec Kit work on this repo.
It does not replace `specs/specs.md` or `AGENTS.md`.

Amendments MUST be owner-approved. A product change belongs in `specs/specs.md`.
A governance change belongs in this file and MUST NOT add a product requirement.
Each amendment MUST include a sync impact report, a semantic version bump, and
the amendment date. The report is review material and is removed before the
amended file is committed.

Version bumps follow these rules. MAJOR means a principle was removed or
redefined in a way older guidance cannot survive. MINOR means a principle or
section was added or materially expanded. PATCH means wording changed without
a change in meaning.

Compliance review MUST check that the change cites `specs/specs.md`, leaves
[TBD] values unresolved, builds nothing under Non-goals or Deferred, adds no
dependency outside the allowed table, and does not create a second product
specification. Extra complexity MUST be justified by a requirement already in
the spec. Day-to-day agent guidance remains `AGENTS.md`.

**Version**: 1.1.0 | **Ratified**: 2026-11-14 | **Last Amended**: 2026-11-14
