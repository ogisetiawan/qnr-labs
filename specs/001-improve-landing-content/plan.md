# Implementation Plan: Improve Landing Content

**Branch**: `001-improve-landing-content` | **Date**: 2026-11-19 | **Spec**: [spec.md](./spec.md)

**Input**: Feature specification from `/specs/001-improve-landing-content/spec.md`

**Note**: This template is filled in by the `/speckit-plan` command; its definition describes the execution workflow.

## Summary

Replace the homepage's repeated process story and blanket open-source wording with the approved section order: Hero, Development Approach, Digital Labs, Services, Open Source, a closing contact call to action, and the current footer. Reuse the existing static page and components. Do not add a dependency, a page, a form, or a new visual system. Unresolved Account Switcher and contact values stay labeled placeholders. Service names stay unconfirmed examples. The product spec is cited and is not edited by this plan.

## Technical Context

**Language/Version**: TypeScript 6, Astro 7 static site, Node.js 26

**Primary Dependencies**: `astro`, `tailwindcss`, `@tailwindcss/vite`, `@astrojs/sitemap`. No package is added.

**Storage**: In-repo content. Homepage projects stay in `src/data/labs.ts`. This feature does not create a content-collection entry.

**Testing**: No test runner is installed. Validation is a content review against [quickstart.md](./quickstart.md). `pnpm exec astro check` and `pnpm build` run only when the owner asks.

**Target Platform**: Static homepage at `/` on `https://qnr.my.id`

**Project Type**: Static website

**Performance Goals**: Keep the page static HTML. Add no client JavaScript. Meet the product spec's Lighthouse target when the owner asks for that check.

**Constraints**: Founder-led copy. No team, price, client, testimonial, or expansion of "QNR". One install metric: "100+ installs". Selective open source. One primary action in the hero. Existing tokens only. Do not invent unresolved project or contact values. Do not restyle from the layout links in `SECTION-SUGGESTED.md`.

**Scale/Scope**: One homepage. Seven content blocks, six of them already have a component. About, FAQ, `/labs`, and `/about` stay out of this change.

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

Reviewed against `.specify/memory/constitution.md` before research.

| Gate | Result |
| --- | --- |
| Founder-led, no team, price, client, testimonial, or expansion of "QNR" | Pass |
| Unresolved Account Switcher and contact values stay placeholders | Pass |
| Static Astro, no new dependency, no island, no form | Pass |
| Existing visual tokens; no new palette, typeface, or reference-site layout | Pass |
| Hero has one primary action and one secondary action | Pass |
| Feature files cite `specs/specs.md` and do not replace it | Pass |
| Deferred process section and service catalog | Exception, justified below |
| Published copy is not yet in `specs/specs.md` | Exception, justified below |

The two exceptions are owner decisions from 2026-11-19. They are not resolved by editing `specs/specs.md` or the constitution in this command. Phase 0 may proceed.

## Project Structure

### Documentation (this feature)

```text
specs/001-improve-landing-content/
├── plan.md
├── research.md
├── data-model.md
├── quickstart.md
├── contracts/
│   └── homepage-sections.md
├── checklists/
│   └── requirements.md
└── tasks.md              # created later by /speckit-tasks
```

### Source Code (repository root)

```text
src/
├── pages/
│   └── index.astro                 # section order only
├── data/
│   └── labs.ts                     # Account Switcher placeholders unchanged
└── components/
    ├── Hero.astro                  # headline, founder-led eyebrow, two actions
    ├── Process.astro               # sole Development Approach
    ├── DigitalLabs.astro           # remove the blanket open-source stat
    ├── Services.astro              # approved message; examples are unconfirmed
    ├── OpenSource.astro            # new section, existing section pattern
    ├── Contact.astro               # closing direct-contact call to action
    └── SiteFooter.astro            # unchanged
```

`src/components/IdeaPath.astro` leaves the homepage. The file stays. `/labs` and `/about` are not part of this feature.

**Structure Decision**: This is the existing single static site. The homepage is `src/pages/index.astro` composed from `.astro` components. No backend, mobile app, or new package is introduced.

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
| --- | --- | --- |
| A six-stage Development Approach, which the constitution defers as a process section | The owner selected `SECTION-SUGGESTED.md` as the homepage and required one approach section | A single three-fact sentence was the constitution's in-scope alternative. The owner replaced the repeated live sections with this six-stage framework and required it to be marked as a recommendation, not a rigid path. |
| Four service names, which the constitution defers as a service catalog | The same owner note includes them, and only as hypotheses | Omitting the names would drop copy the owner supplied. They appear only as unconfirmed examples, with no prices or clients. Contact stays in the closing call to action. |
| Approved homepage sentences are not yet written in `specs/specs.md` | Planning was requested for the approved feature spec | Silently editing the product spec is forbidden. The conflict is recorded here and in the feature assumptions. Implementation still must not invent facts the product spec leaves unresolved. |

## Constitution Check (after design)

Re-checked after `research.md`, `data-model.md`, `contracts/homepage-sections.md`, and `quickstart.md`.

The design does not add a dependency, a form, a page, an About or FAQ block, a second approach sequence, a blanket open-source claim, or a guessed Account Switcher value. The three exceptions above remain, with the same justification. No new violation was introduced. Gate passes for planning.
