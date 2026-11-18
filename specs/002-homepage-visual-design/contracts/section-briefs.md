# Contract: Section Design Briefs

Copy is frozen per `specs/001-improve-landing-content/contracts/homepage-sections.md`. **Approved** defaults to false until owner sign-off.

## 1. Hero (`hero`) — `src/components/Hero.astro`

- **Reference**: None — current QNR pattern
- **Layout**: Centered column; display headline; body lede; dark + sand pills; optional `HeroArt` flanking at `≥1024px`.
- **Heading**: `h1` display scale (`--text-heading-lg` mobile, `--text-display` desktop).
- **Eyebrow**: Founder-led micro label, not open-source identity.
- **Actions**: Primary `#labs`, secondary `#how-we-build`.
- **Responsive**: Single column; art below copy on small viewports.
- **A11y**: `aria-labelledby="hero-title"`; focus visible on pills.
- **Approved**: false

## 2. Development Approach (`how-we-build`) — `src/components/Process.astro`

- **Reference**: None — current diagram
- **Layout**: `h2` + framework disclaimer; six steps in responsive grid inside stone panel (`--color-stone-surface`, `--radius-3xl`, `--shadow-subtle`).
- **Heading**: `h2` `--text-heading-lg`.
- **Eyebrow**: None.
- **Actions**: None in section (hero covers navigation).
- **Responsive**: 2-col mobile grid → 6-col desktop with optional track line.
- **A11y**: Ordered list semantics for steps; decorative track `aria-hidden`.
- **Approved**: false

## 3. Digital Labs (`labs`) — `src/components/DigitalLabs.astro`

- **Reference**: [feature184](https://www.shadcnblocks.com/block/feature184)
- **Layout**: Eyebrow “Digital Labs”; section title; replace stat-only grid with one featured project card matching SECTION-SUGGESTED field *shape* (placeholders visible). Secondary pill may link to `/labs` for full listing when needed.
- **Data (FR-013)**: From `src/data/labs.ts`, bind only `title`, `status`, `highlight`; show `summary`, `install`, `date` as stored. Problem and Solution are labeled rows with explicit `[TBD]` copy—not from `labs.ts`. Category, Technology, and License detail rows show `[TBD]` only; do not render seed `category` as confirmed. Screenshot block stays `[TBD] Screenshot`.
- **Component**: Feature184 spotlight in `DigitalLabs.astro` (optional colocated partial). Do not restyle `ProjectCard.astro` for the homepage.
- **Heading**: `h2`.
- **Card**: 32px padding, inset hairline; status badge “Released”.
- **Actions**: Install/GitHub only when URLs confirmed; otherwise `[TBD]` text rows.
- **Responsive**: Single column card; full width on 360px.
- **A11y**: Project name as `h3`; placeholder regions `aria-label` from `[TBD]` text.
- **Approved**: true

## 4. Services (`services`) — `src/components/Services.astro`

- **Reference**: [feature101](https://www.shadcnblocks.com/block/feature101)
- **Layout**: Intro column + four example rows; disclaimer visually separated.
- **Heading**: `h2`; categories as `h3` per row.
- **Actions**: None (contact is later section).
- **Responsive**: Stack intro above list below `900px`.
- **A11y**: Disclaimer not only color-dependent; readable at caption size.
- **Approved**: true

## 5. Open Source (`open-source`) — `src/components/OpenSource.astro`

- **Reference**: [feature254](https://www.shadcnblocks.com/block/feature254)
- **Layout**: Compact statement block; optional stone band.
- **Heading**: `h2` with eyebrow.
- **Actions**: None.
- **Responsive**: Single column; comfortable line length.
- **A11y**: Section `aria-labelledby`.
- **Approved**: true

## 6. Contact CTA (`contact`) — `src/components/Contact.astro`

- **Reference**: [feature246](https://www.shadcnblocks.com/block/feature246)
- **Layout**: Invitation copy + channel list; art as decorative secondary column.
- **Heading**: `h2` “Contact QNR Labs”.
- **Actions**: Channels only; no submit control.
- **Responsive**: Copy above art on narrow viewports.
- **A11y**: List of channels; links only when `href` set.
- **Approved**: true

## 7. Footer (`footer`) — `src/components/SiteFooter.astro`

- **Reference**: None — keep current
- **Layout**: No change in this feature.
- **Approved**: true (explicitly frozen by owner note)