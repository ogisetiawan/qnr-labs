# QNR Labs — Agent Instructions

Static Astro site for `qnr.my.id`. Product and technical truth is `specs/specs.md`. Token values live in `src/styles/global.css`. How to use them is in the UI section below and in `specs/design.md`.

## Precedence

1. The user's current request.
2. `specs/specs.md` for scope and copy. `src/styles/global.css` for token values. `specs/design.md` for how those tokens are used.
3. This file.
4. A skill in `.cursor/skills/`, and only where it does not contradict 1–3.

When a hex value in `specs/design.md` disagrees with `src/styles/global.css`, use the stylesheet.

If `specs/` or a required document is missing, stop and say so. If the spec and the repo disagree, follow the pinned repo (`package.json` `engines`, `.nvmrc`) and report the conflict. Do not invent a resolution. The development-environment paragraph still says Node 24; `engines`, `.nvmrc`, and checklist T1 pin Node 26.

## Always

- Read the relevant `specs/` sections before changing the site.
- A required item marked **[TBD]** stays a labeled placeholder. Do not guess it. List every placeholder in the completion summary.
- Do not build anything under Non-goals or Deferred. Do not add behavior the request and the spec do not ask for.
- Do not invent copy, metrics, testimonials, clients, a team, or an expansion of "QNR". The site is founder-led. "QNR builds…" is a safe formulation. "Our team" is not.
- Prefer content-driven rendering. A new project is one Markdown file, not a layout edit. Keep components small and typed. Ship no client JavaScript unless a requirement needs an island.
- Add a dependency only when the allowed-deps table in `specs/specs.md` cannot meet the requirement. Say why first. For the MVP, do not add `react`, `@astrojs/react`, `@astrojs/mdx`, `@astrojs/vercel`, `@astrojs/tailwind`, `gray-matter`, or `react-markdown`.
- Do not run `git commit`, `git push`, `pnpm build`, `pnpm dev`, `pnpm exec astro check`, or any deploy unless the user explicitly asks. A checkout under `htdocs` is only a folder. Do not use Apache, PHP, or MySQL.

## Completion summary

- What changed.
- Placeholders and **[TBD]** left in place.
- What the owner must configure, provide, or finish.
- Known limitations.

## Skills

Read the skill file to the end before following it. Paths are under `.cursor/skills/`.

| Skill | Load when | Stop |
| --- | --- | --- |
| `astro/SKILL.md` | `.astro` files, content collections, `astro.config`, routes, images, or deploy | Do not use `npx`. Do not add an adapter, island, or UI framework the spec does not require. When an Astro 7 API is unclear, check current docs instead of guessing. |
| `frontend-design/SKILL.md` | Building or restyling a page or component. Follow the UI section below. | Not a design audit. Do not follow the skill's lines that say to pick a new aesthetic, palette, or font. |
| `perf-astro/SKILL.md` | The user asks to optimize this site's performance | Do not install `astro-critters` or `@playform/compress`. Do not run a Lighthouse audit from this skill. |
| `tlc-spec-driven/SKILL.md` | The user asks to specify, discuss, design, task, implement, validate, verify, UAT, or record, pause, or resume a feature | Not for a small direct edit. `.specs/` is the skill's planning workspace, not the product spec. |

### Overrides

- **Astro.** Package manager is pnpm. Scripts are `pnpm dev`, `pnpm build`, and `pnpm preview`. Typecheck is `pnpm exec astro check`. Keep TypeScript on 6; `astro check` does not support TypeScript 7. Content collections follow section 9: `src/content.config.ts`, `astro/zod`, files in `src/content/work/`. The checklist still says `src/content/config.ts`; follow section 9 and mention the mismatch.
- **UI.** The look is already chosen. Use the skill for craft, and the UI section for the system. Change `public/brand/` only when the user asks.
- **Performance.** Meet the section 9 Lighthouse targets inside the current stack: static HTML, no unnecessary client JS, `astro:assets`, explicit width, height, and `alt`, and `font-display: swap`.
- **Spec-driven.** Product requirements stay in `specs/`. On Windows, run the skill scripts with `py -3`, and put `--root` before the subcommand. A local commit is in scope only when the user asked to execute that workflow. One task, one commit. Push and deploy stay out.

## UI

Read `frontend-design/SKILL.md` when building or restyling, then apply this system. The skill's job here is hierarchy, rhythm, interaction, responsive behavior, motion, and clear labels. It does not choose a new brand.

**Direction.** Warm parchment, quiet chrome, flat color, hairline borders. Saturated color is a small accent. One primary action in each group.

| Question | Read |
| --- | --- |
| Token values | `src/styles/global.css` |
| Color roles, spacing, radius, elevation, do and don't | `specs/design.md`, through "Do's and Don'ts" |
| How to compose | `frontend-design/references/` — spatial, typography, interaction, responsive, motion, ux-writing, and color-and-contrast |

Text in `specs/design.md` after "Do's and Don'ts" shows another product (log in, tweets, mascots, Ethereum). Use it only to see a shape. Do not add those features or those words.

**Use the tokens this way**

- UI text uses `--font-inter` at 400, 500, and 600. Sizes run from `--text-micro` to `--text-display`.
- Display and hero use `--font-family` at weight 500, at `--text-heading-lg` and `--text-display`. The Family font file is **[TBD]**. Do not add another typeface to fill that gap.
- Page width is `--page-max-width`. Sections sit 80–120px apart. Cards use 32px padding. Related items sit 8–12px apart. Vary the space so groups are tight and sections can breathe.
- Cards are white, `--radius-cards` (10px), with the inset hairline `--shadow-subtle`. Do not lift them with a large drop shadow.
- Primary action: dark pill, `--surface-dark-surface`, cream text, `--radius-buttons`. Secondary: sand pill, `--surface-sand`. Tertiary: text only. `--color-ember-orange` is for a text link and the focus ring, not a filled button. `--color-link-blue` is for an inline link, not a filled button.
- Status color marks status only. `--color-alert-red` is for a destructive or error state only.
- Keep the `:focus-visible` outline. Check 360, 768, and 1280. Text contrast meets WCAG AA.
- Motion, when needed, uses transform and opacity and respects `prefers-reduced-motion`. No gradient, glass, or glow.

**Leave these skill lines unused**

- "Pick a tone, a palette, or a font pairing." Inter stays.
- "Vary the aesthetic between generations."
- A new OKLCH palette, gradient text, or dark glow.
- New claims, metrics, testimonials, or a team. The skill's UX writing applies to labels, buttons, and empty states, using words `specs/specs.md` already allows.
