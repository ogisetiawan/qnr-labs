# Research: Product Philosophy Section

## Decision: Source of truth is TASK.md (not the six-step refine note)

**Rationale**: Owner input for `/speckit-specify` was `TASK.md`: Product Philosophy title, four stages, remove How We Build nav, SVG timeline. `TASK-SECTION-HOW-WE-BUILD.md` still describes six Discover→Deliver steps and a refine-only scope.

**Alternatives considered**: Merge both documents. Rejected — conflicting stage counts and copy would make acceptance untestable.

## Decision: Evolve Process.astro in place

**Rationale**: Homepage already mounts `Process.astro` with `id="how-we-build"`. Replacing defaults, markup, and styles there (optionally renaming the file later) minimizes churn in `index.astro` and avoids a dead component.

**Alternatives considered**: New `ProductPhilosophy.astro` beside an unused `Process.astro`. Rejected for this feature unless implement finds rename cleaner; either way only one section ships on `/`.

## Decision: Anchor `#product-philosophy`; update hero + drop nav item

**Rationale**: Spec assumptions require removing “How We Build” from `SiteHeader` and aligning hero secondary label/href with Product Philosophy. Keeping `#how-we-build` would contradict the rename and confuse future content.

**Alternatives considered**: Keep `#how-we-build` for bookmark compatibility. Rejected for homepage consistency; external bookmarks are rare for an unpublished/local site and can be noted as a known break.

## Decision: Map warm palette to existing tokens

**Rationale**: Constitution and `AGENTS.md` require `src/styles/global.css` as token source. Cream canvas, stone surface, sand, stone border, body brown, and muted gray already cover warm minimalist roles. Saturated per-step “tone” fills in the current Process component should be dialed back toward stone/sand/muted accents.

**Alternatives considered**: Paste hexes from older task notes (`#FAF9F7`, etc.). Rejected when an existing token covers the role.

## Decision: CSS-first SVG motion, HeroArt-style

**Rationale**: `HeroArt.astro` already uses inline SVG + `@media (prefers-reduced-motion: no-preference)` with transform/opacity keyframes. That pattern satisfies TASK animation guidance without new libraries and keeps content visible without JS.

**Alternatives considered**:

- IntersectionObserver scroll-reveal as the primary reveal mechanism. Deferred — only add if CSS entrance is insufficient; must leave static content visible and clean up observers if used.
- SMIL/`<animate>` as sole approach. Optional for tiny accent motion; prefer CSS for reduced-motion gating consistency with HeroArt.
- GSAP/Framer/Lottie. Rejected — new dependency, against MVP allowed-deps table.

## Decision: Four illustrations as abstract process glyphs

**Rationale**: Spec forbids stock photos and invented metrics. Each stage gets a small custom SVG that reads as: messy notes → structured blocks → scoped features → finished product frame. Decorative; titles and body copy carry meaning for a11y (`aria-hidden` on decorative SVG when text is adjacent).

**Alternatives considered**: Reuse HeroArt assets as stage art. Rejected — hero art is brand decoration, not process meaning.

## Decision: Mobile connector adapts or hides

**Rationale**: Spec FR-007 — a forced horizontal line on a stacked grid confuses reading. Desktop: horizontal SVG/CSS line behind indicators. Narrow: vertical spine if stages stack cleanly, otherwise omit decorative connector.

**Alternatives considered**: Always show horizontal line. Rejected — fails 360px readability edge case.
