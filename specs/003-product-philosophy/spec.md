# Feature Specification: Product Philosophy Section

**Feature Branch**: `003-product-philosophy`

**Created**: 2026-11-28

**Status**: Draft

**Input**: User description: "read TASK.md to generate task to update section 'How We Build'" (source: `TASK.md`)

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Read the Product Philosophy stages (Priority: P1)

A visitor opens the homepage and reaches the former “How We Build” block. They see it titled as Product Philosophy, with a short subheading and four clear stages that explain how QNR turns ideas into products.

**Why this priority**: The section’s job is to communicate the founder’s product philosophy. Without the new heading and four-stage content, the rest of the visual work has nothing accurate to present.

**Independent Test**: Open only this section. Confirm the heading, subheading, and four stage names and descriptions match the approved copy in `TASK.md`, and that the six older Development Approach stages are gone.

**Acceptance Scenarios**:

1. **Given** the homepage, **When** a visitor finds this section, **Then** the section heading reads “PRODUCT PHILOSOPHY” (or the same words with site-consistent casing) and the subheading is “How QNR turns ideas into products.”
2. **Given** the section, **When** a visitor reads the stages in order, **Then** they see exactly four stages: Notice & Capture; Think & Validate; Define; Create & Share—with the body copy from `TASK.md` for each stage.
3. **Given** a visitor who knew the old six-stage “How We Build” content, **When** they re-read the section, **Then** Discover / Define / Design / Build / Validate / Deliver as a six-stage list are no longer present.

---

### User Story 2 - Follow a four-stage visual timeline (Priority: P2)

A visitor scans the section and understands the stages as one continuous path. On a wide viewport they see four stages in a horizontal row with a connecting timeline and stage illustrations that progress from messy ideas to a finished product. On a narrow viewport the same story remains readable without horizontal scrolling.

**Why this priority**: The owner asked for a connected four-stage SVG timeline so the philosophy reads as a flow, not four disconnected cards.

**Independent Test**: Review the section at narrow and wide widths. Confirm four stages, a connecting timeline that does not cover stage text, progressive illustration meaning (messy → structured → defined → finished), and no competing sections changed.

**Acceptance Scenarios**:

1. **Given** a wide viewport, **When** a visitor views the section, **Then** the four stages sit in one horizontal sequence with a connecting line behind the stage indicators.
2. **Given** each stage, **When** a visitor looks at its illustration, **Then** stage 01 suggests messy ideas, 02 structured/validated ideas, 03 defined features / first-version scope, and 04 a finished digital product—without introducing stock photography or invented project metrics.
3. **Given** a 360px-wide viewport, **When** a visitor reads the section, **Then** all stage titles and body copy remain readable without zooming or horizontal page scroll.

---

### User Story 3 - Navigate without a How We Build nav item (Priority: P3)

A visitor uses the primary site navigation and the hero actions. “How We Build” no longer appears as a top-nav item. They can still reach Product Philosophy from the hero secondary action (or an equivalent in-page control), and keyboard users can move through the section’s interactive elements with a visible focus state.

**Why this priority**: `TASK.md` requires removing the How We Build nav item; hero and in-page reachability must stay coherent so the section is not stranded.

**Independent Test**: Inspect the header and hero only. Confirm no “How We Build” nav label; confirm a working path to the Product Philosophy section; confirm focus is visible on interactive controls.

**Acceptance Scenarios**:

1. **Given** the site header, **When** a visitor reads the primary nav labels, **Then** “How We Build” is not listed.
2. **Given** the hero, **When** a visitor activates the secondary action, **Then** they land on the Product Philosophy section (same page anchor).
3. **Given** keyboard-only navigation, **When** a visitor tabs through the section’s links or controls, **Then** focus is always visible and content does not depend on animation to be readable.

---

### Edge Cases

- A visitor has `prefers-reduced-motion: reduce`. Timeline and illustration motion MUST NOT be required to understand the four stages; static content remains complete.
- JavaScript fails or is disabled. Stage titles, body copy, and illustrations MUST still appear in a sensible order.
- Existing bookmarks or links to `#how-we-build` may break if the section id changes; this feature updates in-page targets (hero secondary and any remaining anchors) to the new section id so current homepage controls stay consistent.
- Narrow layouts that stack stages MUST NOT leave a horizontal connecting line crossing body text in a confusing way; adapt the connector to the stacked layout or omit the decorative connector when it cannot stay clear.
- Color direction in `TASK.md` says warm minimalist accents “following template.” Fills, borders, and text MUST map to existing site design tokens; new one-off hex values MUST NOT be introduced solely for this section when an equivalent token already exists.
- Other homepage sections (Hero copy beyond the secondary CTA target/label, Digital Labs, Services, Open Source, Contact, Footer) MUST NOT be redesigned by this feature.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: The homepage section that currently presents Development Approach / “How We Build” MUST be retitled to Product Philosophy, with subheading “How QNR turns ideas into products.”
- **FR-002**: The section MUST present exactly four stages in this order, using the stage titles and descriptions from `TASK.md`: (1) Notice & Capture, (2) Think & Validate, (3) Define, (4) Create & Share.
- **FR-003**: The six-stage list Discover, Define, Design, Build, Validate, Deliver MUST be removed from this section.
- **FR-004**: The primary site navigation MUST NOT include a “How We Build” item.
- **FR-005**: The hero secondary action MUST remain a path to this section. Its label and target MUST align with Product Philosophy (not the removed “How We Build” nav wording alone).
- **FR-006**: Wide layouts MUST show four stages in a horizontal sequence with a connecting timeline behind stage indicators; each stage MUST include an illustration that matches the progressive meaning in `TASK.md` section 4.
- **FR-007**: Narrow layouts MUST keep the four stages readable and ordered without horizontal page scroll; the connector MUST adapt or hide rather than cross content confusingly.
- **FR-008**: Any motion MUST be limited to transform and opacity, MUST respect `prefers-reduced-motion`, and MUST NOT be required to reveal the stage content. Content MUST remain visible without client scripting.
- **FR-009**: Visual styling MUST follow the warm minimalist direction while using the established site palette and type rules (template / design tokens). Reference or task hex values MUST NOT override the site’s token source of truth when a token already covers the role.
- **FR-010**: This feature MUST NOT change Digital Labs, Services, Open Source, Contact, or Footer layout or copy, and MUST NOT add a contact form, pricing, team claims, or invented metrics.
- **FR-011**: Approved Product Philosophy copy from `TASK.md` MUST NOT be rewritten for marketing tone; unresolved product facts elsewhere on the site MUST stay `[TBD]`.

### Key Entities

- **Product Philosophy section**: One homepage block. Fields: section id/anchor, heading, subheading, ordered list of four stages.
- **Philosophy stage**: One step. Fields: order (01–04), title, description, illustration intent (messy ideas → structured/validated → defined first version → finished product).
- **Timeline connector**: Decorative connection among stages; presentational only; must not replace text content.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: A reviewer finds the Product Philosophy heading, the exact subheading from `TASK.md`, and exactly four named stages—zero of the old six Development Approach stage names remaining in that section.
- **SC-002**: A reviewer finds no “How We Build” label in the primary site navigation.
- **SC-003**: From the hero secondary action, a visitor reaches the Product Philosophy section in one activation on the same page.
- **SC-004**: At 360px width, a visitor can read every stage title and description without horizontal scrolling or zooming.
- **SC-005**: With reduced motion preferred (or scripting unavailable), a reviewer can still identify all four stages and their meanings from static content alone.
- **SC-006**: A side-by-side check of Digital Labs, Services, Open Source, Contact, and Footer shows no unintended copy or layout changes from this feature.

## Assumptions

- Source of truth for this feature’s section copy and visual direction is `TASK.md`. Older notes in `TASK-SECTION-HOW-WE-BUILD.md` (six steps, connecting line only) are superseded where they disagree.
- Homepage section order from feature 001 remains: Hero → this section → Digital Labs → Services → Open Source → Contact → Footer.
- Section anchor becomes `#product-philosophy` (or equivalent stable id matching Product Philosophy). Hero secondary href and any leftover `#how-we-build` homepage targets are updated in the same feature so navigation stays consistent.
- Hero secondary label becomes “Product Philosophy” (or short equivalent that matches the new section name), since the How We Build nav item is removed.
- “Warm Minimalist + Muted Accent Colors” and “following template” mean reuse of existing QNR design tokens and warmth; not a new brand palette file.
- Illustrations are custom inline SVG (or equivalent light assets already allowed by the site), not third-party icon kits or stock photos.
- Animation may use progressive enhancement (for example scroll-aware behavior) only if content remains complete without it; no new UI framework or animation library is required by this specification.
- Feature 002 visual rhythm for other sections stays intact; this feature only replaces the How We Build / Process block’s content and its own presentation.
- Product specification conflicts: `specs/specs.md` still lists a process-style block as deferred in places; owner-approved `TASK.md` and prior shipped homepage process content authorize this Product Philosophy update. The feature cites that owner request and does not rewrite `specs/specs.md` unless the owner asks separately.
