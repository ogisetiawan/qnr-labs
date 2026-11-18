---

description: "Task list for homepage section visual design implementation"
---

# Tasks: Homepage Section Visual Design

**Input**: Design documents from `specs/002-homepage-visual-design/`

**Prerequisites**: [plan.md](./plan.md), [spec.md](./spec.md), [research.md](./research.md), [data-model.md](./data-model.md), [contracts/section-briefs.md](./contracts/section-briefs.md), [contracts/reference-mapping.md](./contracts/reference-mapping.md), [quickstart.md](./quickstart.md)

**Tests**: No automated tests. Validate with [quickstart.md](./quickstart.md). Run `pnpm exec astro check` only when the owner asks.

**Organization**: User stories P1 → P3 from [spec.md](./spec.md). Copy stays frozen per `specs/001-improve-landing-content/`.

## Format: `[ID] [P?] [Story] Description`

## Path Conventions

Single Astro project: `src/components/`, `src/pages/index.astro`, `src/styles/global.css`.

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Gate implementation on approved briefs and frozen content.

- [x] T001 Confirm owner set **Approved: true** on briefs 1–6 in `specs/002-homepage-visual-design/contracts/section-briefs.md` before changing component markup (FR-012)
- [x] T002 Re-read `specs/001-improve-landing-content/contracts/homepage-sections.md` and `specs/002-homepage-visual-design/contracts/reference-mapping.md`; list rejected reference treatments (gradients, glass, foreign hex) in implement notes

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Shared section rhythm before per-story restyling.

**⚠️ CRITICAL**: Complete before user story implementation.

- [x] T003 Align default `padding-block` (80px mobile, 104px desktop) and `scroll-margin-top` across homepage section components in `src/components/Hero.astro`, `Process.astro`, `DigitalLabs.astro`, `Services.astro`, `OpenSource.astro`, `Contact.astro`
- [x] T004 [P] Verify section components use token-backed colors only (`src/styles/global.css`); remove any hard-coded hex added during prior edits if found in those six files

**Checkpoint**: Section chrome is consistent before reference-mapped layouts.

---

## Phase 3: User Story 1 - Review the full homepage rhythm (Priority: P1) 🎯 MVP

**Goal**: Hero and Development Approach match briefs; page hierarchy feels like one system.

**Independent Test**: [quickstart.md](./quickstart.md) steps 1–2 for Hero and `#how-we-build`; spacing and typography only.

### Implementation for User Story 1

- [x] T005 [US1] Polish `src/components/Hero.astro` layout per `contracts/section-briefs.md` §1: display scale, founder-led eyebrow, pill pair, art breakpoints—no copy changes beyond what feature 001 already set
- [x] T006 [US1] Polish `src/components/Process.astro` per §2: stone diagram panel tokens (`--color-stone-surface`, `--radius-3xl`, `--shadow-subtle`), ordered step semantics, desktop track `aria-hidden`
- [x] T007 [US1] Confirm `src/pages/index.astro` keeps Hero then Process order without altering frozen strings

**Checkpoint**: Hero + Development Approach pass US1 acceptance scenarios.

---

## Phase 4: User Story 2 - Understand released work and services (Priority: P2)

**Goal**: Digital Labs feature184 spotlight and Services feature101 list layout.

**Independent Test**: [quickstart.md](./quickstart.md) Digital Labs + Services checks; `[TBD]` placeholders visible.

### Implementation for User Story 2

- [x] T008 [US2] Refactor `src/components/DigitalLabs.astro` from stat grid to featured project layout per `contracts/reference-mapping.md` feature184 and FR-013: eyebrow, `h2`, project `h3`; bind from `src/data/labs.ts` only `title`, `status`, and `highlight`, plus `summary`/`install`/`date` as stored placeholders; render labeled Problem and Solution rows as explicit `[TBD]` copy (not bound from `labs.ts`); render Category, Technology, and License detail rows as `[TBD]`—do not display `LabProject.category` or sample stack/license as confirmed
- [x] T009 [P] [US2] Implement the feature184 spotlight markup inside `src/components/DigitalLabs.astro` (or a colocated `DigitalLabsProjectSpotlight.astro` imported only by Digital Labs); do not change `src/components/ProjectCard.astro` for homepage layout—reuse `--radius-cards`, `--shadow-subtle`, 32px padding per brief §3
- [x] T010 [US2] Restyle `src/components/Services.astro` per feature101: two-column `≥900px`, hairline row dividers, disclaimer at `--text-caption` / `--color-muted-gray`—no new CTAs in section body
- [x] T011 [US2] Wire `src/pages/index.astro` to pass `labProjects` into `DigitalLabs.astro` after layout change; consumption MUST follow FR-013 (no new fields in `labs.ts` in this feature unless owner opens a content change)

**Checkpoint**: Digital Labs and Services match reference shapes and content contract.

---

## Phase 5: User Story 3 - Reach contact with clear trust cues (Priority: P3)

**Goal**: Open Source feature254 band and Contact feature246 split layout.

**Independent Test**: Open Source + Contact only; no form controls; keyboard focus visible.

### Implementation for User Story 3

- [x] T012 [US3] Restyle `src/components/OpenSource.astro` per `contracts/reference-mapping.md` feature254: optional stone band background, max-width ~38rem, eyebrow + `h2` + lede—no repo grid or metrics
- [x] T013 [US3] Restyle `src/components/Contact.astro` per feature246: invitation + channel list primary column, decorative art secondary, links only when `href` exists, `[TBD]` rows static
- [x] T014 [US3] Confirm `src/pages/index.astro` order: Open Source then Contact; footer unchanged via `SiteFooter.astro`

**Checkpoint**: US3 acceptance scenarios and SC-006 focus/a11y pass at review widths.

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Navigation alignment and design sign-off.

- [x] T015 Align `src/components/SiteHeader.astro` anchor targets with section ids (`#labs`, `#how-we-build`, `#services`, `#contact`) if markup ids changed in T008–T013
- [x] T016 Run `specs/002-homepage-visual-design/quickstart.md` review at 360, 768, and 1280 px; record any brief amendments back into `contracts/section-briefs.md` without editing product copy
- [ ] T017 [P] When the owner requests validation: run `pnpm exec astro check` after Astro component prop/type edits

---

## Dependencies & Execution Order

### Phase Dependencies

- Phase 1 blocks all implementation (approval gate)
- Phase 2 blocks user stories
- US2 T008 depends on T003 spacing tokens
- US3 after US2 recommended for full-page rhythm check, but Open Source and Contact files can be edited in parallel with US2 after Phase 2

### User Story Dependencies

- **US1**: Independent after Phase 2
- **US2**: Independent; largest change is Digital Labs T008–T009
- **US3**: Independent file set; T014 assumes prior sections exist

### Parallel Opportunities

- T004 with T003 (different concern, same files—run T003 before T004 or sequentially)
- T009 parallel with T010 after T008 structure is clear
- T012 parallel with T013
- T017 anytime after implement

---

## Parallel Example: User Story 2

```text
After T008 structure is drafted:
Task T009: DigitalLabs.astro (or colocated spotlight component) feature184 markup
Task T010: Services.astro feature101 layout (parallel)
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Phases 1–2
2. Phase 3 (T005–T007)
3. Stop and review Hero + Development Approach

### Incremental Delivery

1. Foundation → US1 → US2 (Digital Labs is the main visual shift) → US3 → Polish

### Notes

- Do not change approved copy in feature 001 specs
- Do not add npm dependencies or client JS islands
- `SiteFooter.astro` is explicitly out of scope (brief already approved)
- Reference URLs are shape guides only; do not import shadcn assets
- Digital Labs data: see FR-013 and `data-model.md` § Homepage featured project card; `ProjectCard.astro` remains for `/labs` listing shape only