---

description: "Task list for Product Philosophy section implementation"
---

# Tasks: Product Philosophy Section

**Input**: Design documents from `specs/003-product-philosophy/`

**Prerequisites**: [plan.md](./plan.md), [spec.md](./spec.md), [research.md](./research.md), [data-model.md](./data-model.md), [contracts/section-content.md](./contracts/section-content.md), [contracts/navigation.md](./contracts/navigation.md), [quickstart.md](./quickstart.md)

**Tests**: No automated tests. Validate with [quickstart.md](./quickstart.md). Run `pnpm exec astro check` only when the owner asks.

**Organization**: User stories P1 → P3 from [spec.md](./spec.md). Copy from `TASK.md` / section-content contract only.

## Format: `[ID] [P?] [Story] Description`

## Path Conventions

Single Astro project: `src/components/`, `src/pages/index.astro`, `src/styles/global.css`.

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Align implementers on contracts and frozen copy before markup changes.

- [x] T001 Re-read `TASK.md`, `specs/003-product-philosophy/contracts/section-content.md`, and `contracts/navigation.md`; confirm four-stage titles/descriptions and nav rules before editing components
- [x] T002 [P] Confirm `src/pages/index.astro` still mounts Process after Hero and before Digital Labs; note only import/props may change later—no section-order reorder

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Stable section id and token constraints shared by all stories.

**⚠️ CRITICAL**: Complete before user story implementation.

- [x] T003 Set default section `id` to `product-philosophy` (anchor `#product-philosophy`) in `src/components/Process.astro` per `data-model.md` field `sectionId`
- [x] T004 [P] Verify Product Philosophy styling will use only tokens from `src/styles/global.css` (cream/stone/sand/muted); do not add foreign hex for roles already covered

**Checkpoint**: Anchor and token rules locked.

---

## Phase 3: User Story 1 - Read the Product Philosophy stages (Priority: P1) 🎯 MVP

**Goal**: Section shows Product Philosophy heading, exact subheading, and exactly four TASK.md stages; six-stage Development Approach content is gone.

**Independent Test**: [quickstart.md](./quickstart.md) steps 1–2; open section only.

### Implementation for User Story 1

- [x] T005 [US1] Update defaults in `src/components/Process.astro`: heading “Product Philosophy”, subheading exactly “How QNR turns ideas into products” per `contracts/section-content.md`
- [x] T006 [US1] Replace six-stage defaults in `src/components/Process.astro` with exactly four stages from `data-model.md` / `contracts/section-content.md`: (01) Notice & Capture, (02) Think & Validate, (03) Define, (04) Create & Share—preserve TASK wording including “Find & make feel…”
- [x] T007 [US1] Remove Discover / Design / Build / Validate / Deliver (and old six-node diagram markup) from `src/components/Process.astro` so SC-001 can pass
- [x] T008 [US1] Keep semantic ordered-list (or equivalent) structure for stages in `src/components/Process.astro` with `aria-labelledby` on the section

**Checkpoint**: Copy-only MVP: four stages + new titles readable without timeline polish.

---

## Phase 4: User Story 2 - Follow a four-stage visual timeline (Priority: P2)

**Goal**: Horizontal timeline + progressive SVG illustrations on wide viewports; readable stack on narrow; warm tokens; CSS motion only.

**Independent Test**: [quickstart.md](./quickstart.md) steps 5–7, 9.

### Implementation for User Story 2

- [x] T009 [US2] Restyle stage layout in `src/components/Process.astro` for wide viewports: four stages in one horizontal sequence with connecting timeline behind indicators (not over body copy) per FR-006
- [x] T010 [US2] Adapt or omit the connector in `src/components/Process.astro` for narrow viewports so 360px reading has no horizontal page scroll and no confusing line across text (FR-007)
- [x] T011 [P] [US2] Add four decorative inline SVG illustrations (in `src/components/Process.astro` or colocated `src/components/ProductPhilosophyArt.astro`) with intents: messy ideas → structured/validated → defined first-version scope → finished product; `aria-hidden` when adjacent text carries meaning
- [x] T012 [US2] Apply warm minimalist chrome in `src/components/Process.astro` using stone/sand/cream tokens; remove highly saturated per-step tone fills that fight FR-009
- [x] T013 [US2] Add optional transform/opacity motion in `src/components/Process.astro` (HeroArt-style) gated by `prefers-reduced-motion: no-preference`; content remains visible without JavaScript (FR-008)

**Checkpoint**: Timeline + illustrations match quickstart wide/narrow checks.

---

## Phase 5: User Story 3 - Navigate without a How We Build nav item (Priority: P3)

**Goal**: Header drops How We Build; hero secondary reaches `#product-philosophy` with Product Philosophy label.

**Independent Test**: [quickstart.md](./quickstart.md) steps 3–4.

### Implementation for User Story 3

- [x] T014 [P] [US3] Remove `{ href: '/#how-we-build', label: 'How We Build' }` from default `links` in `src/components/SiteHeader.astro` per `contracts/navigation.md`
- [x] T015 [P] [US3] Set `Hero.astro` defaults: `secondaryLabel` = `Product Philosophy`, `secondaryHref` = `#product-philosophy` in `src/components/Hero.astro`
- [x] T016 [US3] Grep homepage components for leftover `#how-we-build` / “How We Build” nav wording in `src/components/SiteHeader.astro`, `src/components/Hero.astro`, and `src/components/Process.astro`; fix any owned leftovers

**Checkpoint**: SC-002 and SC-003 pass.

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Isolation check and owner validation notes.

- [x] T017 Confirm `src/pages/index.astro` still orders Hero → Process → Digital Labs → Services → Open Source → Contact without editing Digital Labs / Services / Open Source / Contact / Footer components
- [x] T018 Run `specs/003-product-philosophy/quickstart.md` review checklist; record any brief/contract amendments under `specs/003-product-philosophy/contracts/` without rewriting frozen TASK stage prose
- [ ] T019 [P] When the owner requests validation: run `pnpm exec astro check` after Astro prop/type edits

---

## Dependencies & Execution Order

### Phase Dependencies

- Phase 1 → Phase 2 → US1 → US2 → US3 → Polish
- US3 can start after T003 (anchor exists) even before US2 polish, but hero target requires T003 first
- US2 builds on US1 stage data in the same file (`Process.astro`)—do not parallelize T006–T013 on conflicting edits

### User Story Dependencies

- **US1**: After Phase 2; delivers readable four-stage content
- **US2**: After US1 stage data exists in `Process.astro`
- **US3**: Needs `#product-philosophy` (T003); can parallelize T014 ∥ T015 after T003

### Parallel Opportunities

- T001 then T002 (T002 is [P] after contracts read)
- T004 with T003
- T011 illustrations while T009/T010 layout settles (coordinate on `Process.astro` / split file)
- T014 ∥ T015 after T003
- T019 anytime owner asks

---

## Parallel Example: User Story 3

```text
After T003 sets id="product-philosophy":
Task T014: SiteHeader.astro remove How We Build
Task T015: Hero.astro secondary label + href (parallel)
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Phases 1–2 (T001–T004)
2. Phase 3 (T005–T008)
3. Stop and review heading + four stages

### Incremental Delivery

1. Foundation → US1 (copy) → US2 (timeline/SVG) → US3 (nav/hero) → Polish

### Notes

- Do not invent stage copy; use `TASK.md` / `contracts/section-content.md`
- Do not add npm dependencies or animation libraries
- Do not restyle Digital Labs, Services, Open Source, Contact, or Footer
- Prefer CSS-only motion; IntersectionObserver only if progressive and cleaned up
- `IdeaPath.astro` stays off the homepage unless the owner asks otherwise
