# Data Model: Section Design Briefs

Design-time entities only. No database or collection changes.

## Section design brief

One record per homepage section (seven total).

| Field | Required | Rules |
| --- | --- | --- |
| sectionId | Yes | Stable anchor: `hero`, `how-we-build`, `labs`, `services`, `open-source`, `contact`, `footer` |
| order | Yes | 1–7; matches content contract |
| componentTarget | Yes | Astro file path for implement phase |
| referenceUrl | No | Required when `SECTION-SUGGESTED.md` has REFRENCEE; otherwise `null` |
| layoutIntent | Yes | Plain-language description of structure adopted from reference or current pattern |
| headingLevel | Yes | `h1` (hero only) or `h2` for section titles; `h3` for sub-blocks |
| eyebrow | No | When used: `--text-caption`, uppercase micro, `--color-muted-gray` |
| cardTreatment | No | Default: white surface, `--radius-cards`, `--shadow-subtle` inset |
| primaryAction | No | Dark pill; at most one per section group |
| secondaryAction | No | Sand pill or text link per token rules |
| responsiveStack | Yes | How columns collapse at `<768` and `≥900` |
| a11yNotes | Yes | Focus order, contrast, `aria-labelledby` pattern |
| approved | Yes | `false` until owner marks brief approved (FR-012) |

## Reference mapping

Child of a brief when `referenceUrl` is set.

| Field | Rules |
| --- | --- |
| adoptedElements | Bullet list: columns, card zones, list density, CTA placement |
| rejectedElements | Gradients, glass, foreign icons, reference hex colors, extra CTAs |
| tokenMapping | How each adopted surface maps to CSS variables |

## Homepage featured project card (Digital Labs, feature184)

Runtime source: `src/data/labs.ts` (`LabProject`). Component: `src/components/DigitalLabs.astro` (not `ProjectCard.astro`). Governs implement task T008 and FR-013.

| UI zone (feature184) | Source | Rule |
| --- | --- | --- |
| Project name (`h3`) | `labs.ts` → `title` | Confirmed |
| Status badge | `labs.ts` → `status` | Confirmed when value is real status (e.g. Released) |
| Verified highlight | `labs.ts` → `highlight` | Confirmed only for stated metrics (Account Switcher: "100+ installs") |
| Product description | `labs.ts` → `summary` | Show stored value; MUST remain `[TBD — short description]` until owner supplies copy |
| Problem | **Not in `labs.ts`** | Fixed row label + explicit `[TBD]` placeholder per feature 001 FR-004; MUST NOT invent prose or derive from `summary` |
| Solution | **Not in `labs.ts`** | Same as Problem |
| Detail: Category | **Not from `labs.ts` `category` on homepage** | Row label + `[TBD]` until owner approves in a content change (feature 001 FR-007) |
| Detail: Technology | **Not in `labs.ts`** | `[TBD]` row only |
| Detail: License | **Not in `labs.ts`** | `[TBD]` row only |
| Install / release | `labs.ts` → `install`, `date` | Show stored placeholders `[TBD]` until confirmed |
| Screenshot | **Not in `labs.ts`** | Neutral `[TBD] Screenshot` block, not stock art |
| Live demo / GitHub | `labs.ts` → `install` (+ repo when confirmed elsewhere) | Link only when URL is confirmed; otherwise static `[TBD]` row |

`LabProject` today (`title`, `category`, `status`, `summary`, `highlight`, `install`, `date`): implement MUST NOT add problem/solution fields in feature 002 without a content feature. Layout rows exist without those keys.

## Relationships

- Each brief links to frozen copy in `specs/001-improve-landing-content/contracts/homepage-sections.md` by `sectionId`.
- Implement tasks MUST cite `componentTarget` and `approved: true` before code changes.
- Homepage feature184 binding MUST satisfy feature 001 `spec.md` FR-004 and FR-007.