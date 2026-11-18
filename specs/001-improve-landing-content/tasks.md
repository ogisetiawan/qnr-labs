---

description: "Task list for Improve Landing Content homepage messaging"
---

# Tasks: Improve Landing Content

**Input**: Design documents from `specs/001-improve-landing-content/`

**Prerequisites**: [plan.md](./plan.md), [spec.md](./spec.md), [research.md](./research.md), [data-model.md](./data-model.md), [contracts/homepage-sections.md](./contracts/homepage-sections.md), [quickstart.md](./quickstart.md)

**Tests**: No automated tests. Validate with [quickstart.md](./quickstart.md). Run `pnpm exec astro check` and `pnpm build` only when the owner asks.

**Organization**: Phases follow user stories P1 → P2 → P3 from [spec.md](./spec.md).

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Different files, no dependency on incomplete tasks in the same phase
- **[Story]**: Maps to user stories US1, US2, US3
- Every task names an exact file path

## Path Conventions

Single Astro project: `src/pages/`, `src/components/`, `src/data/`.

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Confirm data constraints before copy changes.

- [x] T001 Confirm `src/data/labs.ts` keeps Account Switcher `summary` `[TBD — short description]`, `install` `[TBD]`, `date` `[TBD]`, and `highlight` `100+ installs` only per [data-model.md](./data-model.md)

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Homepage composition and anchor targets for hero actions.

**⚠️ CRITICAL**: Complete before user story implementation.

- [x] T002 Update `src/pages/index.astro` to remove `IdeaPath` from the homepage and reserve slot order: Hero → Process → DigitalLabs → Services → Open Source → Contact → `SiteFooter`
- [x] T003 [P] Set `id="process"` (or `id="how-we-build"`) on Development Approach in `src/components/Process.astro` for "How We Build" targets
- [x] T004 [P] Confirm `id="labs"` on Digital Labs in `src/components/DigitalLabs.astro` for "Explore Digital Labs" `#labs` target
- [x] T005 [P] Confirm `id="services"` on Services in `src/components/Services.astro`
- [x] T006 [P] Confirm `id="contact"` on closing CTA in `src/components/Contact.astro`

**Checkpoint**: Section order and anchor ids are ready for hero CTAs.

---

## Phase 3: User Story 1 - Find the studio and its released work (Priority: P1) 🎯 MVP

**Goal**: Approved hero copy, founder-led positioning, and honest Digital Labs project display.

**Independent Test**: Read hero and Digital Labs only. Match [quickstart.md](./quickstart.md) checks 2–5 for hero and labs.

### Implementation for User Story 1

- [x] T007 [US1] Update default copy in `src/components/Hero.astro`: title "Turning real problems into useful digital products.", lede per FR-001, eyebrow founder-led (not open-source identity)
- [x] T008 [US1] Set hero actions in `src/components/Hero.astro`: primary label "Explore Digital Labs" `href="#labs"`, secondary "How We Build" `href` to Development Approach id from T003
- [x] T009 [US1] Pass hero props from `src/pages/index.astro` and set `BaseLayout` `description` to match approved positioning without contradicting FR-001
- [x] T010 [US1] Remove the blanket "Open source" stat from `src/components/DigitalLabs.astro`; keep released-project count and `100+ installs` only when `installFact` exists
- [x] T011 [P] [US1] Re-read `src/data/labs.ts` after Digital Labs changes; do not add category, stack, license, or second metrics

**Checkpoint**: MVP hero + Digital Labs pass US1 and SC-001, SC-002.

---

## Phase 4: User Story 2 - Ask QNR to build something (Priority: P2)

**Goal**: Services message with unconfirmed examples; single closing contact invitation.

**Independent Test**: Services then closing CTA only. Match [quickstart.md](./quickstart.md) checks 6 and 8–9.

### Implementation for User Story 2

- [x] T012 [US2] Update `src/components/Services.astro` with heading "Turning your ideas into practical digital solutions." and FR-011 description; add four example names with visible "not a confirmed offer" wording; remove generic process-step bullets that duplicate Development Approach
- [x] T013 [US2] Update `src/components/Contact.astro` closing copy for direct contact (no form); keep Email and GitHub as `[TBD]` where unresolved
- [x] T014 [US2] Place `Contact` last inside `main` in `src/pages/index.astro` after Open Source (depends on T015 for full order)

**Checkpoint**: Services and contact CTA pass US2 and SC-007 (once US3 inserts Open Source).

---

## Phase 5: User Story 3 - See the approach once, and see what is shared (Priority: P3)

**Goal**: One six-stage Development Approach; selective open-source section; no duplicate process blocks.

**Independent Test**: Count stage lists once; read Open Source and Account Switcher. Match [quickstart.md](./quickstart.md) checks 4, 7, and 10.

### Implementation for User Story 3

- [x] T015 [US3] Rewrite defaults in `src/components/Process.astro`: title "Thoughtful development, from idea to release.", six stages Discover–Deliver per `SECTION-SUGGESTED.md`, plus recommended-framework disclaimer per FR-006
- [x] T016 [P] [US3] Create `src/components/OpenSource.astro` with selective open-source copy per FR-012; use existing section/container pattern; do not label Account Switcher open source
- [x] T017 [US3] Import and render `OpenSource` in `src/pages/index.astro` between Services and Contact; finalize FR-010 order
- [x] T018 [US3] Verify `src/components/IdeaPath.astro` is not imported on `src/pages/index.astro`; file remains in repo

**Checkpoint**: Full homepage section order and US3 acceptance scenarios pass.

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Navigation consistency, validation, optional typecheck.

- [x] T019 Update `src/components/SiteHeader.astro` homepage anchor links if needed (`#labs`, `#services`, approach section) without adding About/FAQ to homepage body
- [x] T020 Run [quickstart.md](./quickstart.md) manual checks 1–10; list every `[TBD]` still visible in completion summary
- [x] T021 [P] When the owner requests validation: run `pnpm exec astro check` after TypeScript or prop changes

---

## Dependencies & Execution Order

### Phase Dependencies

- **Phase 1**: Start immediately
- **Phase 2**: After T001 — blocks all user stories
- **Phase 3 (US1)**: After Phase 2
- **Phase 4 (US2)**: After Phase 2; T014 completes after T017 for final `index.astro` order
- **Phase 5 (US3)**: After Phase 2; T017 before T014 final verification
- **Phase 6**: After Phases 3–5 (or after MVP Phase 3 if stopping early)

### User Story Dependencies

- **US1**: Independent after foundational anchors
- **US2**: Independent of US3 content, but final section order needs Open Source (T017) before contact placement check
- **US3**: Independent; Process can ship before Open Source component exists

### Within Each User Story

- Hero anchors (T007–T008) depend on T003–T004
- `index.astro` final order: T002 → US1/US2 partial → T017 → T014 verify

### Parallel Opportunities

- T003, T004, T005, T006 after T002 (different files)
- T011 parallel with T010 (different files)
- T016 parallel with T015 (new file vs Process.astro) once T015 scope is clear
- T021 independent of copy review

---

## Parallel Example: User Story 1

```text
# After Phase 2:
Task T010: DigitalLabs.astro stat cleanup
Task T011: labs.ts audit (in parallel)
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1–2
2. Complete Phase 3 (T007–T011)
3. Stop and validate with [quickstart.md](./quickstart.md) hero + Digital Labs checks
4. Ship or continue to US2/US3

### Incremental Delivery

1. Foundation → US1 (hero + labs) → demo
2. Add US2 (services + contact) → demo
3. Add US3 (approach + open source + page order) → full quickstart

### Parallel Team Strategy

- Developer A: US1 (`Hero.astro`, `DigitalLabs.astro`)
- Developer B: US3 (`Process.astro`, `OpenSource.astro`) after Phase 2
- Developer C: US2 (`Services.astro`, `Contact.astro`)
- One owner merges `index.astro` (T002, T009, T014, T017)

---

## Notes

- Do not edit `specs/specs.md`, `IMPROVE-CONTENT.md`, or `SECTION-SUGGESTED.md` during implementation
- Do not change `src/pages/labs.astro` in this feature (noted conflict in [research.md](./research.md))
- `SiteFooter.astro` stays unchanged per FR-009
- No new npm dependencies
- Layout reference URLs are out of scope