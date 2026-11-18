# Research: Homepage Section Visual Design

## Decision: Shape-only reference mapping

**Rationale**: shadcnblocks previews often use neutral gray palettes, shadows, and sans stacks that conflict with QNR parchment tokens. The spec requires adopting column balance, card grouping, and CTA placement—not colors or type from the preview.

**Alternatives considered**: Pixel-matching reference screenshots. Rejected because it would violate `specs/design.md` and the constitution.

## Decision: Authoritative reference list

**Rationale**: Only `SECTION-SUGGESTED.md` `REFRENCEE` lines count for this feature.

| Section | URL |
| --- | --- |
| Digital Labs | https://www.shadcnblocks.com/block/feature184 |
| Services | https://www.shadcnblocks.com/block/feature101 |
| Open Source | https://www.shadcnblocks.com/block/feature254 |
| Contact CTA | https://www.shadcnblocks.com/block/feature246 |

**Alternatives considered**: `REFRENCEE-SECTION.md` (feature245, cta30). Rejected; superseded by owner’s `SECTION-SUGGESTED.md` list.

## Decision: Digital Labs moves from stat tiles to project spotlight

**Rationale**: Current `DigitalLabs.astro` is intro + metric cards. Feature184 implies a featured project panel with structured fields (name, status, narrative zones, metadata rows, actions). Stats alone do not show problem/solution placeholders the content spec allows when `[TBD]`.

**Alternatives considered**: Keep stat grid and add a card below later. Rejected because it duplicates hierarchy and wastes vertical space on a single project.

## Decision: Homepage feature184 data binding

**Rationale**: `LabProject` in `src/data/labs.ts` has no problem or solution fields. Feature 001 requires those stories and metadata to stay unresolved. The feature184 layout shows labeled Problem/Solution and detail rows as explicit `[TBD]` UI; only `title`, `status`, and the verified `highlight` bind from data. Seed `category` must not display as confirmed on the homepage.

**Alternatives considered**: Extend `labs.ts` with problem/solution keys in feature 002, or map `summary` into Problem copy. Rejected—would invent or smuggle narrative; content changes belong in feature 001 scope.

**Alternatives considered**: Reuse `ProjectCard.astro` on the homepage. Rejected—the `/labs` card schema targets listing layout, not feature184 section hierarchy.

## Decision: Services stays two-column intro + list

**Rationale**: Feature101 is typically headline column + stacked feature rows. Current implementation already uses intro + list; the brief tightens disclaimer styling (`--text-micro`, muted color) and row separators (`--color-stone-border`).

**Alternatives considered**: Icon grid. Rejected—would read as a confirmed service menu.

## Decision: Open Source stays a single statement band

**Rationale**: Feature254 is a supporting message layout, not a repo grid. Matches selective-open-source copy.

**Alternatives considered**: Logo wall of OSS projects. Rejected—would imply more public repos than exist.

## Decision: Contact CTA uses split focus layout

**Rationale**: Feature246 pairs a strong invitation with side channel list. Current `Contact.astro` already splits copy and decorative art; brief aligns copy column width and channel rows to reference proportion while keeping no form fields.

**Alternatives considered**: Full-width email capture. Rejected—non-goal.

## Decision: Hero and Development Approach — incremental polish

**Rationale**: No reference URL. Keep centered hero grid with `HeroArt`, pill pair, and process diagram with stage nodes. Adjust only spacing rhythm (80–104px section padding) to match mapped sections below.

**Alternatives considered**: New hero reference from `family.co`. Rejected—out of scope; would be a new aesthetic pick.

## Decision: Footer unchanged

**Rationale**: `SECTION-SUGGESTED.md` says keep current footer. No brief beyond token audit.