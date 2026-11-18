# AGENTS.md

## Project Context

Static Astro site for **QNR Digital Labs** at `qnr.my.id`: an open-source project showcase. Projects start from the founder's own problems and are published for other people to use. Visitors with their own problem can ask QNR to build it.

**Stack:** Astro (static), TypeScript strict, Tailwind CSS v4 via `@tailwindcss/vite`, pnpm, Node 26.

**Source of truth**

| Topic | File |
| --- | --- |
| Scope, copy, stack, allowed deps | `specs/specs.md` |
| Token values | `src/styles/global.css` |
| How tokens are used | `specs/design.md` (through "Do's and Don'ts") and the UI notes under Code Guidelines below |

**Precedence:** (1) the user's current request → (2) `specs/specs.md`, `src/styles/global.css`, `specs/design.md` → (3) this file → (4) skills in `.cursor/skills/` only when they do not contradict 1–3.

If a hex in `specs/design.md` disagrees with `src/styles/global.css`, use the stylesheet. If `specs/` or a required document is missing, stop and report it. If the spec and the repo disagree, follow `package.json` `engines` and `.nvmrc` and report the conflict (do not invent a resolution). The development-environment paragraph in the spec still says Node 24; the repo pins Node 26.

---

## Development Rules

- Read the relevant `specs/` sections before changing the site.
- Do only what the current request asks. Do not build Non-goals, Deferred items, or extra behavior the request and spec do not ask for.
- Prefer content-driven rendering: a new project is one Markdown file in `src/content/work/`, not a layout edit.
- Keep components small, typed, and consistent with existing patterns. Ship no client JavaScript unless a requirement needs an island.
- Add a dependency only when the allowed-deps table in `specs/specs.md` cannot meet the requirement; say why first. For the MVP do not add `react`, `@astrojs/react`, `@astrojs/mdx`, `@astrojs/vercel`, `@astrojs/tailwind`, `gray-matter`, or `react-markdown`.
- Change `public/brand/` only when the user asks.
- When building or restyling UI, read `frontend-design/SKILL.md` for craft (hierarchy, rhythm, interaction, responsive, motion, labels). Do not follow that skill's lines that pick a new aesthetic, palette, or font.

---

## Commands

Run these only when the **current message explicitly asks**. The owner validates the work; do not run commands to prove a result on your own.

| Action | Command |
| --- | --- |
| Install | `pnpm install` |
| Development | `pnpm dev` |
| Build | `pnpm build` |
| Preview production build | `pnpm preview` |
| Typecheck | `pnpm exec astro check` |

Do not use `npx` for Astro. TypeScript stays on 6 (`astro check` does not support TypeScript 7). Content collections: `src/content.config.ts`, `astro/zod`, `src/content/work/` (if the checklist says `src/content/config.ts`, follow section 9 of the spec and report the mismatch).

---

## Code Guidelines

- Use clear names and small `.astro` modules; match imports and layout patterns already in the repo.
- Use CSS variables from `src/styles/global.css`; do not hard-code alternate brand colors.
- **[TBD]** stays a labeled placeholder. Do not guess release dates, URLs, licenses, repositories, personal-problem stories, or feature bullets. List every placeholder in the completion summary.
- Copy must stay honest: no invented metrics, testimonials, clients, team, service menu, prices, or public expansion of "QNR". Safe: "QNR builds…", "ask QNR to build it". Not safe: "our team".
- Semantic HTML, keyboard navigation, visible `:focus-visible`, WCAG AA contrast. Layout is written for 360, 768, and 1280 px without opening a browser to verify.

### UI system

**Direction:** Warm parchment, quiet chrome, flat color, hairline borders. One primary action per group.

| Question | Read |
| --- | --- |
| Token values | `src/styles/global.css` |
| Roles, spacing, radius, elevation, do/don't | `specs/design.md`, through "Do's and Don'ts" |
| Composition patterns | `frontend-design/references/` |

Text in `specs/design.md` after "Do's and Don'ts" is another product (log in, tweets, mascots, Ethereum). Use only as shape; do not add those features or words.

- UI text: `--font-inter` at 400, 500, 600; scale `--text-micro` … `--text-display`.
- Display/hero: `--font-family` weight 500 at `--text-heading-lg` / `--text-display`. Family font file is **[TBD]**; do not substitute another typeface.
- Page `--page-max-width`; sections 80–120px apart; cards 32px padding, white, `--radius-cards`, inset `--shadow-subtle` (no heavy drop shadow).
- Primary: dark pill (`--surface-dark-surface`, cream text, `--radius-buttons`). Secondary: sand pill (`--surface-sand`). Tertiary: text only. `--color-ember-orange` for text links and focus ring, not filled buttons. `--color-link-blue` for inline links. `--color-alert-red` for destructive/error only.
- Motion: transform and opacity only; respect `prefers-reduced-motion`. No gradient, glass, or glow on the site chrome.

---

## Important Constraints

- Do not delete files or change critical config (`astro.config.mjs`, `package.json` engines, `.nvmrc`) without a clear request and scope.
- Do not invent `.env`, API keys, or credentials.
- Do not check whether the dev server is running; do not start or stop it or call `localhost`.
- Do not take screenshots or launch Edge, Chrome, or headless browsers.
- Do not run `git commit`, `git push`, `pnpm build`, `pnpm dev`, `pnpm preview`, `pnpm exec astro check`, Lighthouse, or deploy unless the current message asks.
- This checkout under `htdocs` is only a folder. Do not use Apache, PHP, or MySQL to serve the site.
- Performance bar (Lighthouse, etc.) is in `specs/specs.md`; do not install `astro-critters` or `@playform/compress`. Do not run Lighthouse from the perf skill unless asked.

---

## CHANGELOG (owner prompts)

Use skill `git-workflow-and-versioning` when the owner asks:

- **Generate changelog + bump version:** Review commits since the last release tag, pick the right SemVer bump, update `CHANGELOG.md`.
- **Changelog from a commit range:** Same skill; scope to the range the owner gives.
- **Cut a release:** Bump project version, write `CHANGELOG.md`, prepare the `git tag` command (commit/tag only when the owner asks).