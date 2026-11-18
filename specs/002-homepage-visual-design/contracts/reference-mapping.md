# Contract: Reference Mapping

Bindings between `SECTION-SUGGESTED.md` REFRENCEE URLs and QNR layout intent. Colors and fonts always come from `src/styles/global.css`.

## Digital Labs → feature184

- **URL**: https://www.shadcnblocks.com/block/feature184
- **Adopt**: Section eyebrow + `h2`; featured project card as primary surface; status chip; labeled Problem and Solution rows with explicit `[TBD]` placeholders (not data-driven prose); product description from `labs.ts` `summary` when still a placeholder; metadata list rows for category, technology, license each showing `[TBD]` until owner-approved (do not bind `labs.ts` `category` on homepage); action row for Live demo / GitHub only when URLs are confirmed in data.
- **Reject**: Dark theme preview, drop shadows, icon sets from preview, implying multiple products in a carousel.
- **Tokens**: Card `--surface-pure-white`, borders `--shadow-subtle`, status pill `--surface-sand` or mint for released, text `--color-body-brown`.

## Services → feature101

- **URL**: https://www.shadcnblocks.com/block/feature101
- **Adopt**: Two-column layout at `≥900px` (intro left, stacked category rows right); hairline row dividers; disclaimer below list full width.
- **Reject**: Pricing columns, checkmark icon grids, “Get started” duplicate CTA in section body.
- **Tokens**: Dividers `--color-stone-border`; disclaimer `--color-muted-gray`, `--text-caption`.

## Open Source → feature254

- **URL**: https://www.shadcnblocks.com/block/feature254
- **Adopt**: Narrow supporting band (`max-width` ~38rem); eyebrow + `h2` + single lede; optional subtle stone band background (`--color-stone-surface`) if contrast still AA.
- **Reject**: Repo cards, star counts, contributor avatars.
- **Tokens**: Background optional stone surface; text as body scale.

## Contact CTA → feature246

- **URL**: https://www.shadcnblocks.com/block/feature246
- **Adopt**: Split layout: invitation + channel list primary; decorative art secondary; channels as tappable rows when `href` exists, static rows when `[TBD]`.
- **Reject**: Form fields, social icon strip, secondary marketing copy.
- **Tokens**: Links `--color-link-blue`; focus ring `--color-ember-orange`; no orange filled buttons.

## Sections without reference

| Section | Pattern |
| --- | --- |
| Hero | Current centered copy + dual pills + flanking art |
| Development Approach | Six-node diagram in stone surface container |
| Footer | Existing two-column footer; no layout change |