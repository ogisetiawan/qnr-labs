# Implementation Plan: Product Philosophy Section

**Branch**: `003-product-philosophy` | **Date**: 2026-11-28 | **Spec**: [spec.md](./spec.md)

**Input**: Feature specification from `/specs/003-product-philosophy/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command; its definition describes the execution workflow.

## Summary

Replace the homepage “How We Build” / Development Approach block with **Product Philosophy**: four stages from `TASK.md`, remove the How We Build nav item, retarget the hero secondary CTA to `#product-philosophy`, and present a warm-token timeline with inline SVG illustrations. Motion follows existing HeroArt patterns (CSS transform/opacity + `prefers-reduced-motion`). No new dependencies. Other homepage sections stay unchanged.

## Technical Context

**Language/Version**: TypeScript 6, Astro 7 static site

**Primary Dependencies**: None added. Styling remains Tailwind CSS v4 via existing Vite plugin; section UI in `.astro` + inline SVG + scoped CSS.

**Storage**: N/A — stage copy lives in the section component props/defaults (or a small colocated data module under `src/`); no content-collection change required for this feature.

**Testing**: Owner-led review via [quickstart.md](./quickstart.md) at 360, 768, and 1280 px. Run `pnpm exec astro check` only when the owner asks.

**Target Platform**: Homepage `/` section + `SiteHeader` nav + `Hero` secondary CTA.

**Project Type**: Static marketing site; design-system-constrained Astro components.

**Performance Goals**: No layout shift from late-loading illustrations; SVG inline or same-document; no animation libraries; optional progressive enhancement must leave content visible without JS.

**Constraints**: Tokens from `src/styles/global.css`; motion transform/opacity only; no React/islands for decoration; no invented copy beyond `TASK.md`; do not restyle Digital Labs / Services / Open Source / Contact / Footer; Family font remains `[TBD]` (use `--font-family` / Inter rules as elsewhere).

**Scale/Scope**: One section rewrite, two navigation touchpoints (header + hero), four stage illustrations + timeline connector.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

| Gate | Result |
| --- | --- |
| No new palette/typeface; tokens from stylesheet | Pass — warm direction maps to existing cream/stone/sand tokens |
| Honest copy; no invented metrics/team/prices | Pass — stages from `TASK.md` only |
| No new deps / no decorative client islands required | Pass — CSS (+ optional tiny progressive script only if needed; content works without it) |
| Motion respects reduced-motion | Pass — same gate as HeroArt |
| Scope limited; other sections untouched | Pass |
| `specs/specs.md` not replaced | Pass — feature cites owner `TASK.md`; product-spec process deferral noted as owner-authorized exception (same pattern as features 001–002) |

Gate passes. Phase 0 proceeds.

## Project Structure

### Documentation (this feature)

```text
specs/003-product-philosophy/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── contracts/
│   ├── section-content.md
│   └── navigation.md
└── tasks.md                 # created by /speckit-tasks
```

### Source Code (implementation phase)

```text
src/components/
├── Process.astro            # primary target: retitle → Product Philosophy, 4 stages, timeline
├── Hero.astro               # secondary CTA label + href
├── SiteHeader.astro         # remove How We Build nav item
└── (optional) ProductPhilosophyArt.astro  # colocated stage SVGs if Process grows too large
src/pages/index.astro        # only if import/props need rename; section order unchanged
src/styles/global.css        # read-only unless a missing role truly has no token (prefer reuse)
```

**Structure Decision**: Keep a single homepage Astro section component (evolve `Process.astro` in place or rename file only if tasks require clearer naming). Prefer colocated SVG partials over new packages. Do not touch Digital Labs / Services / Open Source / Contact / Footer components for this feature.

## Complexity Tracking

| Violation | Why Needed | Simpler Alternative Rejected Because |
| --- | --- | --- |
| Process-style marketing section | Owner `TASK.md` + prior shipped homepage process content | Removing the section would leave no Product Philosophy story |
| Optional progressive motion script | TASK mentions IntersectionObserver cleanup if used | Pure CSS-only motion may be enough; prefer CSS first; add script only if scroll-triggered behavior is required and still progressive |

## Constitution Check (after design)

Re-checked after `research.md`, `data-model.md`, contracts, and `quickstart.md`.

Design artifacts introduce no new tokens-as-requirements, no dependencies, and keep content without JS. Gate passes for `/speckit-tasks`.
