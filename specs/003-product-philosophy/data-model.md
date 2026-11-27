# Data Model: Product Philosophy

Design-time / presentational entities. No database or content-collection schema change required.

## Product Philosophy section

| Field | Required | Rules |
| --- | --- | --- |
| sectionId | Yes | `product-philosophy` (anchor `#product-philosophy`) |
| orderOnPage | Yes | After Hero, before Digital Labs (homepage order from feature 001) |
| componentTarget | Yes | `src/components/Process.astro` (or renamed equivalent mounted from `index.astro`) |
| heading | Yes | Product Philosophy (site-consistent casing; TASK headline “PRODUCT PHILOSOPHY”) |
| subheading | Yes | Exactly: `How QNR turns ideas into products` |
| stages | Yes | Ordered list length **4** |
| timeline | Yes | Presentational connector; must not replace text |

## Philosophy stage

| Field | Required | Rules |
| --- | --- | --- |
| order | Yes | `01` … `04` |
| title | Yes | From `TASK.md` only (see contract) |
| description | Yes | From `TASK.md` only; do not invent alternate marketing copy |
| illustrationIntent | Yes | 01 messy ideas; 02 structured/validated; 03 defined first-version scope; 04 finished digital product |
| mark | Yes | Display order marker `01`–`04` |

### Frozen stage rows (from TASK.md)

| order | title | description (preserve wording) |
| --- | --- | --- |
| 01 | Notice & Capture | Find & make feel problems, frustrations, and things that could be better. Write down rough ideas without worrying about perfect solutions. |
| 02 | Think & Validate | Structure ideas using SMART and explore possible solutions. Evaluate feasibility, potential value, and practical limitations. |
| 03 | Define | Research, learn, and adapt relevant insights to the original goals. Shape the solution and prioritize essential features for the first version. |
| 04 | Create & Share | Initialize the project, develop, test, and refine the product. Publish the finished product so others can benefit from it. |

Note: TASK line breaks may be joined into one or two paragraphs per stage without changing words. Do not “fix” informal phrasing (e.g. “Find & make feel”) unless the owner amends `TASK.md`.

## Removed entities (must not appear in this section)

| Entity | Rule |
| --- | --- |
| Six-stage Development Approach | Discover, Define, Design, Build, Validate, Deliver — removed from this section |
| Nav item “How We Build” | Removed from primary header links |
| Anchor `#how-we-build` on homepage controls | Replaced by `#product-philosophy` for hero secondary (and any other in-page targets this feature owns) |

## Navigation bindings

| Control | Field | Value after feature |
| --- | --- | --- |
| SiteHeader default links | — | No How We Build entry |
| Hero secondary | label | Product Philosophy |
| Hero secondary | href | `#product-philosophy` |

## Relationships

- Section owns exactly four stages in fixed order.
- Timeline connector is child presentation of the section; decorative relative to stages.
- Feature 001 content contract for “Development Approach” is superseded for this block by `TASK.md` / this feature’s contracts; other homepage sections remain under feature 001/002 contracts.
