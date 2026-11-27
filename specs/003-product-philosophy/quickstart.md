# Quickstart: Product Philosophy Review

Owner-led validation after `/speckit-implement`. Do not start or stop the dev server from the agent unless the owner asks. When the owner already runs `pnpm dev`, open `/`.

## Prerequisites

- [section-content.md](./contracts/section-content.md)
- [navigation.md](./contracts/navigation.md)
- [data-model.md](./data-model.md)
- Copy source: `TASK.md`
- Tokens: `src/styles/global.css`

## Review steps

1. **Heading & subheading**: Section shows Product Philosophy and “How QNR turns ideas into products.”
2. **Four stages only**: Notice & Capture; Think & Validate; Define; Create & Share — with TASK wording. No Discover / Design / Build / Validate / Deliver six-pack.
3. **Nav**: Header has no “How We Build” item.
4. **Hero**: Secondary control labeled for Product Philosophy; activating it scrolls to `#product-philosophy`.
5. **Wide layout (~1280)**: Four stages in one horizontal sequence; connector behind indicators, not over body copy.
6. **Narrow layout (~360)**: All titles and descriptions readable; no horizontal page scroll; connector not confusing.
7. **Motion**: With reduced motion (OS setting) or JS disabled, all four stages remain fully readable.
8. **Isolation**: Digital Labs, Services, Open Source, Contact, Footer unchanged in copy and layout.
9. **Tokens**: No obvious foreign hex/gradient/glass on the section chrome.

## Optional typecheck

When the owner asks: `pnpm exec astro check`

## Implement notes (feature 003)

- Section lives in `src/components/Process.astro` with `id="product-philosophy"`.
- Illustrations: `src/components/ProductPhilosophyArt.astro`.
- Nav: How We Build removed from `SiteHeader.astro`; Hero secondary → Product Philosophy / `#product-philosophy`.
- Motion is CSS-only (`prefers-reduced-motion`); no IntersectionObserver.

## Out of scope

- Rewriting `specs/specs.md` product deferrals
- `/labs` page
- Lighthouse runs unless the owner asks
