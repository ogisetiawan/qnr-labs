# Implementation Plan: Homepage Section Visual Design

**Branch**: `002-homepage-visual-design` | **Date**: 2026-11-19 | **Spec**: [spec.md](./spec.md)

**Input**: Feature specification from `/specs/002-homepage-visual-design/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command. This phase produces design artifacts only; homepage UI code changes belong in `/speckit-tasks` and `/speckit-implement`.

## Summary

Document visual and UX direction for all seven homepage sections before restyling components. Four sections map to shadcn block references from `SECTION-SUGGESTED.md` (feature184, feature101, feature254, feature246). Three sections (Hero, Development Approach, Footer) refine the existing QNR patterns. Copy stays frozen under `specs/001-improve-landing-content/`. Tokens stay in `src/styles/global.css`. Deliverables are section briefs and a design review checklist, not new dependencies or pages.

## Technical Context

**Language/Version**: TypeScript 6, Astro 7 static site (implementation phase only)

**Primary Dependencies**: None added. Styling remains Tailwind CSS v4 via existing Vite plugin.

**Storage**: Design artifacts in `specs/002-homepage-visual-design/`; runtime content unchanged in `src/data/labs.ts`.

**Testing**: Owner-led visual review using [quickstart.md](./quickstart.md) at 360, 768, and 1280 px. No automated UI test suite.

**Target Platform**: Homepage `/` only. Header anchors may align but are a secondary touch.

**Project Type**: Static marketing site; design-system-constrained Astro components.

**Performance Goals**: No new client JavaScript for layout. Static HTML and CSS only.

**Constraints**: Warm parchment tokens, hairline borders, one primary action per group, no gradients/glass/glow from references, no new fonts, no `[TBD]` values filled with guessed visuals, content contract from feature 001.

**Scale/Scope**: Seven section briefs, four reference mappings, polish pass on rhythm across the page.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

| Gate | Result |
| --- | --- |
| No new palette, typeface, or mascot from references | Pass (shape-only mapping) |
| Content from feature 001 not rewritten in briefs | Pass |
| No dependency, form, or login added by design work | Pass |
| `[TBD]` placeholders stay visible in Digital Labs/contact | Pass |
| `specs/specs.md` not replaced | Pass |
| Process section styling (deferred in product spec) | Exception — owner approved in feature 001; brief documents existing diagram only |

Gate passes. Phase 0 proceeds.

## Project Structure

### Documentation (this feature)

```text
specs/002-homepage-visual-design/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── contracts/
│   ├── reference-mapping.md
│   └── section-briefs.md
└── tasks.md                 # created by /speckit-tasks
```

### Source Code (implementation phase — not edited in this command)

```text
src/components/
├── Hero.astro
├── Process.astro            # Development Approach
├── DigitalLabs.astro
├── Services.astro
├── OpenSource.astro
├── Contact.astro
├── SiteFooter.astro
└── SiteHeader.astro
src/pages/index.astro
```

**Structure Decision**: Single static site. Each brief names the target component file for the later implement phase.

## Complexity Tracking

| Violation | Why Needed | Simpler Alternative Rejected Because |
| --- | --- | --- |
| External reference layouts | Owner required REFRENCEE mapping in `SECTION-SUGGESTED.md` | Keeping current stat-only Digital Labs layout would not meet feature184 hierarchy for problem/solution and detail rows |
| Process section visual weight | Constitution defers “process” marketing | Feature 001 already shipped the six-stage copy; this plan only tunes rhythm to match mapped sections |

## Constitution Check (after design)

Re-checked after `research.md`, `data-model.md`, contracts, and `quickstart.md`.

Briefs introduce no new tokens, dependencies, or copy changes. Reference mapping is structure-only. Gate passes for `/speckit-tasks`.