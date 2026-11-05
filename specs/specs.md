# QNR Labs Website — Project Specs

> Context file for the Cursor agent. Read this fully before writing any code.
> Anything marked **[TBD]** is an open decision: do NOT invent a value. Use a clearly marked placeholder and list it in your final summary.

---

## 1. Project Overview

**Name:** QNR Labs
**Domain:** `qnr.my.id`
**Category:** Independent Digital Product Studio / Digital Solutions Studio 
**Stage:** Founder-led, early-stage concept; currently no confirmed team or formal company structure.
 

### What QNR Labs is

QNR Labs is intended to become the home for digital products, applications, tools, client solutions, and experiments created by the founder. It should start as a simple, credible website that can grow alongside the work. It must not pretend to be a large company or imply a team, customer base, or business maturity that does not yet exist. The name QNR is derived from the initials/name of the founder's child and has personal meaning. Do not invent or publish a different expansion of the acronym.
 

### Relationship to other sites

| Site | Purpose |
|---|---|
| `ogisetiawan.my.id` | Personal portfolio / personal brand (built separately with Next js on Netlify). Out of scope here. |
| `ogisetiawan.github.io` | Old portfolio, to be retired. |
| `qnr.my.id` (this project) | Studio brand: showcase of released apps + entry point for client work. |

---

## 2. Goals

1. **Showcase released work** in one clean place, starting with the **Account Switcher** browser extension (100+ installs).
2. **Establish a credible studio presence** that can later accept client inquiries.
3. Be **simple to extend**: adding a new project should mean adding one content file, not editing layout code.

### Non-goals (do NOT build these now)

- No blog, no login, no CMS backend, no database.
- No pricing page, no booking/payment flow.
- No "Team" page, no "Careers" page (no team exists yet).
- No testimonials, client logos, or fabricated metrics.
- No multi-language switcher in MVP.

---

## 3. Target Audience

| Audience | What they want | What the site must give them |
|---|---|---|
| **Users of released apps** (e.g. Account Switcher users) | Find the official page, install link, updates | Clear project page with install CTA |
| **Potential clients** (small businesses, startups, individuals needing tools/web apps) | Judge credibility fast and know how to reach out | Honest hero, real work shown, one clear contact CTA |
| **Future collaborators** | Understand what the studio is | Short, honest description of what QNR Labs does |

---

## 4. Vision and Direction

### Long-term vision
Build QNR into an independent digital product/solution studio. Initially, the founder builds and releases products independently. Over time, QNR may take on client work, collaborate with friends or external contributors, recruit a team, and potentially develop repeatable solutions into standalone products.

This is a direction, not a claim that QNR is currently a formal company or has a team.

### Near-term purpose
- Present released applications and tools in one place.
- Showcase selected client work only when disclosure is permitted.
- Separate stable/released products from work in progress and experiments.
- Give each project a clear description, status, and relevant destination (live product, store listing, documentation, or repository).
- Establish a consistent identity that can scale without a major redesign.

### Guiding principles
- Build useful things that solve real problems.
- Prefer real work and clear explanations over marketing claims.
- Ship small, learn, improve, and iterate.
- Use technology intentionally.
- Be honest about project status, ownership, availability, and maturity.
- Keep the website lightweight and easy to maintain.

---

## 5. Brand Positioning

### Recommended category
**Independent Digital Product Studio**

Alternative supporting descriptor: **Software, Tools & Experiments**

### Suggested one-liner
“Building useful software, tools, and digital solutions.”

Alternative:
“An independent studio for software, tools, and digital experiments.”

Use wording that remains accurate while the founder is working solo. Avoid copy such as “our team” unless a real team exists. “QNR builds…” is a useful neutral formulation.

### Brand personality
- Minimal
- Modern
- Thoughtful
- Technical
- Independent
- Practical
- Quietly confident, not overhyped

--- 

## 6. MVP Scope

### Core pages
1. `/` — Homepage and selected work index.
2. `/work` — Optional listing page for products and selected solutions if the collection warrants a separate page.
3. `/work/[slug]` — Project detail pages for work that needs more explanation.
4. `/labs` — Experiments and work in progress, only if there is enough public content.
5. `/about` — Brief explanation of QNR Labs and its current founder-led stage.
6. `/contact` — Optional if a clear contact route is available; can initially link to a public professional contact channel.
7. `privacy-policy` - placed within the detail page of each work project

### Suggested homepage sequence
1. Header: QNR Labs wordmark and minimal navigation.
2. Hero: concise positioning statement and a “Explore work” link/action.
3. Selected work: a few real projects with title, one-line description, category, status, and destination.
4. Labs / experiments: optional; show only meaningful public experiments.
5. Short About section: explain the independent, founder-led studio without overclaiming.
6. Contact / footer: relevant links and copyright.

### Deliberately deferred (add only after the first real client project exists)

- Capabilities / services section
- Process section
- Testimonials

---

## 7. Project Detail Page Template

Each project is a content entry with:

| Field | Type | Notes |
|---|---|---|
| `title` | string | e.g. "Account Switcher" |
| `slug` | string | URL segment |
| `summary` | string | One sentence for cards |
| `description` | markdown | Body of the detail page |
| `category` | enum | `extension` · `web-app` · `tool` · `client` . `ai-agent` etc  |
| `status` | enum | `released` · `in-progress` |
| `links` | array | e.g. `{ label: "Install", url }` |
| `highlights` | string[] | Short bullets (only verified facts) |
| `date` | date | Release date **[TBD]** |
| `featured` | boolean | Show on home |
 

### Seed content: Account Switcher

- Category: `extension`, status: `released`
- Verified fact: **100+ installs**
- Install link (Chrome Web Store URL): **[TBD]**
- Short description / feature bullets: **[TBD — ask owner; do not invent features]**
- Screenshots: **[TBD]** (use a neutral placeholder block until provided)

---

## 8. Design Direction 
- read `design.md` for design tokens

### Reference sites (same content or product )

- https://unifato.com/agnova/project-details.html
- https://cirqle.studio/
- https://px7.digital/
- https://dexon-react.vercel.app/

### Reference sites ( for refrencee design and layout )
- https://family.co/


### Ignore
- https://styles.refero.design/style/1bcae895-2245-4d33-aa43-1c1e80719554
- https://styles.refero.design/style/2b49d4b2-8461-4985-b7ee-cf9517e19803
- https://styles.refero.design/style/41af8353-6a8f-416d-947b-57932f591497
- https://styles.refero.design/style/1329b661-39d8-4f0b-a12a-11ed13671ccb
- https://styles.refero.design/style/7976704d-549b-4ba6-9a0f-c792766a9df3

---

## 9. Technical Requirements

### Stack

**Decision:** Astro, static output, on Vercel. The owner chose Astro. A later on-demand route stays in this repo: add `@astrojs/vercel` and set `export const prerender = false` on that route only. Do not switch the site to `output: 'server'`, and do not move the site to Next.js for that route. Login, a database, a CMS, and payments stay out of scope until a future spec adds them.

- **Framework:** Astro, TypeScript `strict`, default `output: 'static'`. No UI framework (no React, Vue, or Svelte integration). Pages ship no client-side JavaScript unless a requirement needs an island.
- **Server features:** None in the MVP. Do not install `@astrojs/vercel` until a route must render on demand.
- **Content:** Astro Content Collections. One Markdown file per project in `src/content/work/`. Define the `work` collection in `src/content.config.ts` with the `glob` loader and a Zod schema imported from `astro/zod`. Do not add a separate `zod` package. Render the body with the collection entry's rendered content. The project page is `src/pages/work/[slug].astro`, built with `getStaticPaths`. Add `@astrojs/mdx` only when a project page must embed a component.
- **UI:** `.astro` components only. Add an island only when a requirement needs browser state.
- **Styling:** Tailwind CSS v4 through `@tailwindcss/vite`. Do not install `@astrojs/tailwind` (deprecated for Tailwind 4). No component library. Light and dark themes use CSS variables and follow `prefers-color-scheme`. A manual theme toggle is an island only if the design requires a switch.
- **Images:** `astro:assets` (`Image`). Optimize at build time. Every content image has `alt` text and explicit width and height.
- **SEO:** Each page sets a unique `<title>`, meta description, Open Graph tags, and a canonical URL on `https://qnr.my.id`. Set `site` to `https://qnr.my.id` in `astro.config`. `@astrojs/sitemap` writes `sitemap-index.xml` during `pnpm build`. `public/robots.txt` points at that index.
- **Hosting:** Vercel. Custom domain `qnr.my.id`. Framework preset: Astro. Build command: `pnpm build`. Output directory: `dist`.
- **Package manager:** pnpm.

Allowed dependencies beyond the Astro scaffold, each for a stated reason:

| Package | Reason |
| --- | --- |
| `tailwindcss` | Utility styling for the design tokens |
| `@tailwindcss/vite` | Official Tailwind 4 integration for Astro |
| `@astrojs/sitemap` | Build the sitemap required by the quality targets |

Do not add a package that this table does not list unless the spec gains a requirement it cannot meet. In particular, do not add `react`, `@astrojs/react`, `@astrojs/mdx`, `@astrojs/vercel`, `@astrojs/tailwind`, `gray-matter`, or `react-markdown` for the MVP.

### Development environment

- **Node.js:** 26 LTS (Active LTS). Pin it in `package.json` `engines` and in `.nvmrc`. Node.js 26 becomes LTS on 2026-10-28; stay on 24 until this spec says otherwise.
- **pnpm:** the only package manager. Do not commit `package-lock.json` or `yarn.lock`.
- **Git:** required. This site is not served by XAMPP, Apache, PHP, or MySQL. A checkout under `htdocs` is only a folder location.
- **Scaffold:** `pnpm create astro@latest` with TypeScript strict, an empty project (no UI framework), and static output.
- **Local commands:** `pnpm dev` for the dev server. `pnpm build` must succeed after each milestone in section 11. `pnpm astro check` must pass after type or content-schema changes.
- **Lint:** do not add ESLint unless a later spec requires it. Type checking is `astro check`.
- **Secrets:** no environment variables in the MVP. Do not invent API keys or a `.env` file.

### Quality targets

- Lighthouse (mobile) ≥ 95 for Performance, Accessibility, Best Practices, SEO
- Semantic HTML, keyboard navigable, visible focus states, WCAG AA contrast
- Images optimized at build time with `astro:assets`, with `alt` text and explicit dimensions
- Each page has unique `<title>`, meta description, Open Graph tags, canonical URL
- Generate a sitemap (`sitemap-index.xml` via `@astrojs/sitemap`) and `robots.txt`
- Favicon + simple OG image (text-based wordmark acceptable)

---

## 10. Task Checklist (execute in order)

- [x] **Scaffold:** Init Astro with `pnpm create astro@latest`, TypeScript strict, empty (no UI framework), static output, Tailwind via `@tailwindcss/vite`, Node 26, pnpm. Base layout sets the SEO head. Do not install `@astrojs/vercel`.
- [x] **Base Configuration**
  - `astro.config.mjs`: Set `site: 'https://qnr.my.id'`.
  - `tsconfig.json`: Pastikan strict mode aktif, tambahkan path aliases (`@components/*`, `@content/*`, `@assets/*`).
  - `tailwind.config.mjs`: Siapkan struktur dasar (akan diisi detail di Phase 2).
- [x] **SEO Head Component**
  - Buat `src/components/SEOHead.astro`.
  - Terima props: `title`, `description`, `image` (optional), `canonical` (optional).
  - Render: `<title>`, `<meta name="description">`, Open Graph tags, Twitter Card tags, canonical link.
- [x] **Design Tokens (Tailwind Config)**
  - read `specs/design.md` implementation configuration for the theme
- [ ] **Content Collection Setup**
  - Buat `src/content/config.ts`.
  - Definisikan schema `work` menggunakan Zod (title, slug, summary, description, category, status, links, highlights, date, featured).
  - Buat file seed: `src/content/work/account-switcher.md`. Isi dengan data yang ada, gunakan placeholder `[TBD]` untuk URL, screenshot, dan tanggal.
- [ ] **Homepage (`src/pages/index.astro`)**
  - **Header:** Wordmark "QNR Labs" + Nav (Work, About, Contact). Sticky, minimal.
  - **Hero:** Headline "Building useful software, tools, and digital solutions." + Subheadline + CTA "Explore work".
  - **Selected Work:** Query content collection (filter `featured: true`). Render menggunakan `<ProjectCard>`. Pastikan layout aman jika hanya ada 1 project (single-item-safe).
  - **Short About:** 1 paragraf jujur tentang studio (founder-led, independent).
  - **Footer:** Copyright "© [Tahun] QNR Labs", links (GitHub, Email).
- [ ] **Base Components**
  - Buat base component yang diperlukan di `src/components/ui/`:
- [ ] **Project Detail Template (`src/pages/work/[slug].astro`)**
  - Gunakan Astro `getStaticPaths` dan `getEntry`.
  - Layout: Breadcrumb, Title, Status Badge, Meta info.
  - Render `description` (Markdown).
  - Render `highlights` (jika ada).
  - Render `links` (Tombol Install, GitHub, dll).
- [ ] **Other Pages**
  - `src/pages/work/index.astro`: Listing semua project (grid layout).
  - `src/pages/about.astro`: Penjelasan singkat QNR Labs, visi, dan status founder-led.
  - `src/pages/contact.astro`: Link ke email profesional atau channel kontak publik.
- [ ] **Utility Pages & Assets**
  - `src/pages/404.astro`: Custom 404 page dengan link kembali ke Home.
  - Install `@astrojs/sitemap` dan `@astrojs/robots-txt` (jika diperlukan, atau buat manual `robots.txt` dan `sitemap.xml` di `public/`).
- [ ] **Performance & Accessibility**
  - Pastikan semua gambar menggunakan `<Image />` dari Astro atau memiliki `width`/`height` eksplisit.
  - Cek kontras warna (WCAG AA).
  - Pastikan navigasi keyboard (tab order) dan focus states terlihat jelas.
  - Semantic HTML: Gunakan `<header>`, `<main>`, `<section>`, `<footer>`, `<article>`.
- [ ] **Responsive & Lighthouse Testing**
  - Test visual di 360px (Mobile), 768px (Tablet), 1280px (Desktop).
  - Jalankan Lighthouse di Chrome DevTools. Target: ≥95 untuk Performance, Accessibility, Best Practices, SEO.
- [ ] **Vercel Setup**
  - Push kode ke GitHub.
  - Import repo ke Vercel.
  - Framework Preset: Astro.
  - Build Command: `pnpm build` (default).
  - Output Directory: `dist` (default).
- [ ] **Domain Configuration**
  - Tambah custom domain `qnr.my.id` di Vercel Dashboard.
  - Update DNS records di registrar domain (A Record / CNAME sesuai instruksi Vercel).
  - Tunggu propagasi dan pastikan HTTPS aktif otomatis.
- [ ] **Final Manual Checks**
  - Cek semua link internal dan eksternal.
  - Pastikan tidak ada teks "Lorem ipsum" atau placeholder yang tidak disengaja.
  - Verifikasi redirect dari `ogisetiawan.github.io` (jika dikonfigurasi di level DNS/Vercel).
- [ ] **Addition**

  
### Definition of Done (MVP)

- Builds cleanly with no warnings that affect output.
- Home page and Account Switcher page render correctly on mobile and desktop, light and dark.
- Adding a second project requires only adding one Markdown file.
- No fabricated claims anywhere on the site.
- All **[TBD]** items are listed in the final report.