# QNR Labs — Agent Instructions

Static Astro site for `qnr.my.id`. Product and technical truth is `specs/specs.md`. Visual tokens are `specs/design.md`, implemented in `src/styles/global.css`.

## Precedence

1. The user's current request.
2. `specs/specs.md`, then `specs/design.md`.
3. This file.
4. A skill in `.cursor/skills/`, and only where it does not contradict 1–3.

If `specs/` or a required document is missing, stop and say so. If the spec and the repo disagree, follow the pinned repo (`package.json` `engines`, `.nvmrc`) and report the conflict. Do not invent a resolution. The development-environment paragraph still says Node 24; `engines`, `.nvmrc`, and checklist T1 pin Node 26.

## Always

- Read the relevant `specs/` sections before changing the site.
- A required item marked **[TBD]** stays a labeled placeholder. Do not guess it. List every placeholder in the completion summary.
- Do not build anything under Non-goals or Deferred. Do not add behavior the request and the spec do not ask for.
- Do not invent copy, metrics, testimonials, clients, a team, or an expansion of "QNR". The site is founder-led. "QNR builds…" is a safe formulation. "Our team" is not.
- Prefer content-driven rendering. A new project is one Markdown file, not a layout edit. Keep components small and typed. Ship no client JavaScript unless a requirement needs an island.
- Add a dependency only when the allowed-deps table in `specs/specs.md` cannot meet the requirement. Say why first. For the MVP, do not add `react`, `@astrojs/react`, `@astrojs/mdx`, `@astrojs/vercel`, `@astrojs/tailwind`, `gray-matter`, or `react-markdown`.
- Do not run `git commit`, `git push`, `pnpm build`, `pnpm exec astro check`, or any deploy unless the user explicitly asks. A checkout under `htdocs` is only a folder. Do not use Apache, PHP, or MySQL.

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
| `frontend-design/SKILL.md` | Building or restyling a page or component | Not for design review. Do not invent a palette, a font, an aesthetic, or marketing copy. |
| `perf-astro/SKILL.md` | The user asks to optimize this site's performance | Do not install `astro-critters` or `@playform/compress`. Do not run a Lighthouse audit from this skill. |
| `tlc-spec-driven/SKILL.md` | The user asks to specify, discuss, design, task, implement, validate, verify, UAT, or record, pause, or resume a feature | Not for a small direct edit. `.specs/` is the skill's planning workspace, not the product spec. |

### Overrides

- **Astro.** Package manager is pnpm. Scripts are `pnpm dev`, `pnpm build`, and `pnpm preview`. Typecheck is `pnpm exec astro check`. Keep TypeScript on 6; `astro check` does not support TypeScript 7. Content collections follow section 9: `src/content.config.ts`, `astro/zod`, files in `src/content/work/`. The checklist still says `src/content/config.ts`; follow section 9 and mention the mismatch.
- **Frontend.** Use the tokens already in `src/styles/global.css`. Inter is the body face. The display face "Family" has no licensed file in the repo; leave that **[TBD]** placeholder. Change `public/brand/` only when the user asks.
- **Performance.** Meet the section 9 Lighthouse targets inside the current stack: static HTML, no unnecessary client JS, `astro:assets`, explicit width, height, and `alt`, and `font-display: swap`.
- **Spec-driven.** Product requirements stay in `specs/`. On Windows, run the skill scripts with `py -3`, and put `--root` before the subcommand. A local commit is in scope only when the user asked to execute that workflow. One task, one commit. Push and deploy stay out.
