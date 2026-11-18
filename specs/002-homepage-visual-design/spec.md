# Feature Specification: Homepage Section Visual Design

**Feature Branch**: `002-homepage-visual-design`

**Created**: 2026-11-19

**Status**: Draft

**Input**: User description: "Finalize the visual design and UI/UX direction of every homepage section before frontend implementation, reference mapping based on SECTION-SUGGESTED.md — apply only sections that have REFRENCEE."

This feature defines how each homepage section should look and behave. It does not change approved copy in `specs/001-improve-landing-content/`. It does not replace `specs/specs.md` or `specs/design.md`. It does not approve frontend code in this step.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Review the full homepage rhythm (Priority: P1)

A visitor scrolls the homepage and reads each section in order. Spacing, hierarchy, and actions feel consistent with the warm parchment system. No section looks like a different brand.

**Why this priority**: Without a shared rhythm, reference-mapped sections would clash with Hero and Development Approach.

**Independent Test**: Walk the page top to bottom. Confirm seven sections match the order in `specs/001-improve-landing-content/contracts/homepage-sections.md`, with clear heading levels and one primary action per group.

**Acceptance Scenarios**:

1. **Given** the homepage, **When** a visitor moves from Hero through footer, **Then** vertical spacing between sections falls in the 80–120px band and page width respects the established max width.
2. **Given** any section, **When** a visitor scans it, **Then** typography uses the existing Inter scale and display rules from the product design system, and no new typeface is introduced.
3. **Given** Hero and Development Approach, **When** a visitor compares them with mapped sections, **Then** cards still use white surfaces, 10px radius, and inset hairline borders—no heavy drop shadow or glass.

---

### User Story 2 - Understand released work and services (Priority: P2)

A visitor reads Digital Labs and Services. Layout helps them scan projects and example service categories without mistaking hypotheses for a price list.

**Why this priority**: Digital Labs and Services carry the reference links the owner chose in `SECTION-SUGGESTED.md`.

**Independent Test**: Open only Digital Labs and Services. Confirm the Digital Labs layout follows the feature184 reference shape, the Services layout follows feature101, and disclaimers stay visible.

**Acceptance Scenarios**:

1. **Given** Digital Labs, **When** a visitor views Account Switcher, **Then** the block shows `title`, `status`, and the verified `highlight` ("100+ installs") from `src/data/labs.ts`, shows Problem and Solution rows as explicit unresolved placeholders (not prose from data), shows product description / install / release date only when `labs.ts` values are confirmed or already marked `[TBD]`, never presents category, stack, or license from sample or seed data as confirmed, and the layout follows the reference mapping for feature184 (project spotlight, not a dense catalog).
2. **Given** Services, **When** a visitor reads example categories, **Then** the list is scannable (title + short line per row) and the unconfirmed-offer note is visually distinct from body copy.
3. **Given** a reference block, **When** a visitor inspects color, **Then** every fill and border maps to tokens in `src/styles/global.css`, not to hex values copied from the reference site.

---

### User Story 3 - Reach contact with clear trust cues (Priority: P3)

A visitor finishes at Open Source and the closing contact block. Selective sharing and the contact invitation are easy to find. Keyboard and screen-reader users can operate actions.

**Why this priority**: Open Source and the contact call to action complete the page and carry the remaining reference URLs.

**Independent Test**: Review Open Source and contact only. Confirm feature254 and feature246 shapes, selective-open-source message, and contact channels without a form.

**Acceptance Scenarios**:

1. **Given** Open Source, **When** a visitor reads it, **Then** the section uses the feature254 reference shape (supporting message block, not a product grid).
2. **Given** the closing contact block, **When** a visitor wants to reach out, **Then** the layout follows feature246 (focused invitation + channel list), with one primary path and no form fields.
3. **Given** any interactive control, **When** a visitor uses keyboard only, **Then** focus is visible and contrast meets WCAG AA on the cream canvas.

---

### Edge Cases

- A reference layout includes gradients, glow, or dark-glass chrome. Those treatments MUST NOT be copied. Shape only.
- A reference shows more projects than exist. Digital Labs MUST NOT imply a larger catalog.
- Account Switcher has no confirmed screenshot or repository. Placeholders stay neutral blocks, not stock imagery.
- `src/data/labs.ts` defines `LabProject` but has no problem or solution fields. The feature184 layout MUST still show labeled Problem and Solution rows with `[TBD]` copy only; implement MUST NOT invent descriptions or bind those rows from `category`, `summary`, or other fields.
- The seed `category` value in `labs.ts` is not owner-confirmed for homepage display per `specs/001-improve-landing-content/spec.md` (FR-004, FR-007). Category, technology, and license appear only as `[TBD]` detail rows until a separate content change approves them.
- Viewport at 360, 768, and 1280. Each mapped section MUST remain readable without horizontal scroll.
- `REFRENCEE-SECTION.md` lists different block IDs (for example feature245, cta30). This feature uses only `REFRENCEE` lines in `SECTION-SUGGESTED.md`.
- Hero and Development Approach have no reference URL. They MUST evolve from current components, not from an external block.
- Footer is unchanged. No reference mapping applies.

### Edge Cases — Reference coverage

| Homepage section | REFRENCEE in SECTION-SUGGESTED.md | Design direction source |
| --- | --- | --- |
| Hero | None | Current QNR hero pattern + content contract |
| Development Approach | None | Current process diagram pattern + content contract |
| Digital Labs | https://www.shadcnblocks.com/block/feature184 | Reference shape + QNR tokens |
| Services | https://www.shadcnblocks.com/block/feature101 | Reference shape + QNR tokens |
| Open Source | https://www.shadcnblocks.com/block/feature254 | Reference shape + QNR tokens |
| Contact (CTA) | https://www.shadcnblocks.com/block/feature246 | Reference shape + QNR tokens |
| Footer | None (keep current) | Existing footer |

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: A design brief MUST exist for every homepage section in the content contract order, before implementation starts on that section.
- **FR-002**: Sections with a `REFRENCEE` line in `SECTION-SUGGESTED.md` MUST document which reference URL applies and which layout elements are adopted (for example: column balance, card grouping, CTA placement).
- **FR-003**: Sections without `REFRENCEE` MUST document continuation of the current QNR section pattern. No external block URL is required or invented.
- **FR-004**: Every section brief MUST state heading level, eyebrow usage, body width, card treatment, primary and secondary actions, and mobile versus desktop stacking.
- **FR-005**: Digital Labs visual design MUST follow reference feature184 for information hierarchy (project identity, status, problem/solution fields when shown, detail rows, external actions) while keeping only confirmed Account Switcher data.
- **FR-013**: Homepage Digital Labs (feature184) MUST bind runtime fields from `src/data/labs.ts` as follows: **confirmed** — `title`, `status`, `highlight` (verified metric only); **display as stored** — `summary`, `install`, `date` when values are already `[TBD]` placeholders or owner-supplied confirmed copy; **layout-only, not from `labs.ts`** — Problem and Solution rows MUST use explicit `[TBD]` labels per feature 001 (FR-004); Category, Technology, and License detail rows MUST use `[TBD]` until the owner approves values in a content change. Implement MUST NOT render `LabProject.category` as confirmed category on the homepage while feature 001 treats category as unresolved. Live demo / GitHub actions appear only when install/repository URLs are confirmed, not as guessed links.
- **FR-006**: Services visual design MUST follow reference feature101 for a readable category list paired with the intro column, and MUST keep the unconfirmed-offer disclaimer visually secondary.
- **FR-007**: Open Source visual design MUST follow reference feature254 for a concise statement block, not a repository grid.
- **FR-008**: The closing contact block MUST follow reference feature246 for a single invitation and channel list, with no form UI.
- **FR-009**: Color, radius, elevation, and typography MUST use `src/styles/global.css` and `specs/design.md` through "Do's and Don'ts". Reference screenshots MUST NOT introduce new brand colors or fonts.
- **FR-010**: Motion, when used, MUST be limited to transform and opacity, MUST respect `prefers-reduced-motion`, and MUST NOT add client JavaScript for decoration.
- **FR-011**: Approved copy from `specs/001-improve-landing-content/spec.md` MUST NOT change during visual design work unless the owner opens a separate content change.
- **FR-012**: Implementation MUST NOT start on a section until its design brief is marked approved in the design checklist for this feature.

### Key Entities

- **Section design brief**: One homepage block. Fields: section name, reference URL or "current pattern", layout intent, token notes, responsive behavior, accessibility notes, and open questions.
- **Reference mapping**: A declared subset of a reference block—structure and hierarchy only, not third-party copy, icons, or colors.
- **Homepage featured project card**: The feature184 spotlight for `/`. Maps structure from reference mapping; data binding rules in FR-013. Implemented in `src/components/DigitalLabs.astro` (not the `/labs` `ProjectCard.astro` catalog card).

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: A reviewer can open one document and see a complete brief for all seven homepage sections before any section UI build begins.
- **SC-002**: Exactly four sections list a `SECTION-SUGGESTED.md` reference URL; three sections explicitly state "no reference—current QNR pattern."
- **SC-003**: A reviewer comparing the live homepage to the briefs finds no section using a reference treatment that is not listed in its brief.
- **SC-004**: A reviewer finds zero new hex colors, fonts, or gradient backgrounds introduced solely to match reference blocks.
- **SC-005**: At 360px width, a visitor can read each section heading and primary action without zooming or horizontal scrolling.
- **SC-006**: A keyboard-only reviewer can reach every action and every in-page anchor target named in the content contract.

## Assumptions

- Homepage content and order are frozen by `specs/001-improve-landing-content/` until a separate content feature says otherwise.
- `SECTION-SUGGESTED.md` is the only authoritative list of reference URLs for this feature. Older notes in `REFRENCEE-SECTION.md` are superseded where they disagree (for example feature245 versus feature184 for Digital Labs).
- Reference URLs name layout families on shadcnblocks.com. The team interprets them manually; this spec does not require embedding third-party assets or scripts.
- Hero and Development Approach keep decorative art already in the repo where it does not violate mascot prohibitions in the constitution.
- Digital Labs may gain a project card layout on the homepage in implementation; this feature only requires the design direction, not the code.
- Design approval is owner sign-off on briefs and checklist items, not Lighthouse scores in this phase.