# Contract: Navigation After Product Philosophy Rename

## Primary header (`SiteHeader.astro`)

**Must remove** from default `links`:

| Before | After |
| --- | --- |
| `{ href: '/#how-we-build', label: 'How We Build' }` | Entry deleted |

Remaining default links (unless already changed by owner elsewhere) stay coherent with homepage anchors, e.g. Digital Labs, Services, and Contact — this feature does not redesign the whole nav, only removes How We Build.

## Hero secondary CTA (`Hero.astro`)

| Prop | After |
| --- | --- |
| `secondaryLabel` default | `Product Philosophy` |
| `secondaryHref` default | `#product-philosophy` |

Primary CTA (`Explore Digital Labs` → `#labs`) unchanged.

## In-page consistency check

Before marking nav tasks done, search the homepage surface for leftover `#how-we-build` or the label “How We Build” in header/hero. Section body must not reintroduce that nav label as the section title.
