# Quickstart: Homepage Visual Design Review

Validate design briefs before `/speckit-implement`. No build required unless the owner requests `pnpm dev` for side-by-side review.

## Prerequisites

- [section-briefs.md](./contracts/section-briefs.md) and [reference-mapping.md](./contracts/reference-mapping.md) are open.
- Content contract: `specs/001-improve-landing-content/contracts/homepage-sections.md`.
- Tokens: `src/styles/global.css`.

## Review steps

1. **Coverage**: Confirm seven briefs exist and four reference URLs match `SECTION-SUGGESTED.md`.
2. **Per brief**: For each section, verify layout intent, heading level, actions, and responsive stack are filled.
3. **Reference rejection**: For each mapped section, confirm rejected elements (gradients, foreign palette, forms) are listed.
4. **Copy freeze**: Spot-check briefs do not rewrite headlines from feature 001.
5. **TBD**: Digital Labs and Contact briefs require visible placeholders, not invented screenshots or URLs. For Digital Labs, confirm Problem/Solution rows and category/technology/license details show `[TBD]`, while only `title`, `status`, and `100+ installs` read as confirmed from `labs.ts` (see `data-model.md` § Homepage featured project card).
6. **Approval gate**: Owner sets **Approved: true** on briefs 1–6 before implementation tasks run (footer already approved).
7. **Viewport planning**: Note expected behavior at 360, 768, and 1280 px per brief (manual check during implement).

## Optional live check

When the owner runs `pnpm dev`, open `/` and compare each section to its brief. Mismatches are logged back into the brief, not into product specs.

## Out of scope

- Lighthouse scores in this phase.
- `/labs` page layout (content spec conflict documented in feature 001 research).

## Implement notes (feature 002)

Rejected on every mapped section (do not copy from shadcn previews):

- Gradients, glow, glassmorphism, heavy drop shadows
- Foreign hex colors, preview typefaces, icon packs
- Extra marketing CTAs, pricing tables, contact forms, repo grids, contributor avatars, star counts
- Dark-theme chrome from reference screenshots

**T016**: Layout intent implemented in Astro components per briefs. Owner should confirm 360, 768, and 1280 px in the browser when running `pnpm dev`.