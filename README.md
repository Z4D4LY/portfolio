# Amine Sadali — Portfolio & CV

A bilingual (English / French) personal portfolio website and ATS-optimized CV page, built with Astro and Tailwind CSS v4. All content is centralized in a single TypeScript configuration file, shared between the portfolio and CV views.

## Live Site

[https://z4d4ly.github.io/portfolio/](https://z4d4ly.github.io/portfolio/)

## Features

### Portfolio Page
- **Hero** — Animated intro with name, title, and social links (email, LinkedIn, GitHub)
- **About Me** — Professional summary and consulting philosophy
- **Projects** — Featured work with descriptions, links, and tech stacks
- **Experience** — Career timeline with role details and achievements
- **Education** — Academic background
- **Certifications** — Professional certifications with issuers and dates
- **Languages** — Language proficiency levels
- **Recommendations** — Professional endorsements with quotes
- **Contact** — Contact section with direct email link
- **Responsive Design** — Mobile-first layout with smooth scrolling navigation
- **Dark Mode** — Toggle with system preference detection and localStorage persistence
- **Bilingual EN/FR** — Full English/French toggle with all content switching in real-time

### CV Page (`/cv`)
- **ATS-Optimized Layout** — Single-column, semantic HTML (`h1`→`h2`→`h3`), no icons or decorative elements, clean sans-serif font for maximum parser compatibility
- **Professional Header** — Name, title, photo, and full contact info (email, phone, location, nationality, LinkedIn, GitHub, remote status)
- **Professional Summary** — Concise career overview
- **Categorized Skills** — Frontend, Backend, DevOps, AI & ML — displayed in a 2-column grid on screen, inline in print
- **Experience** — Full career history with company, title, dates, and bullet-point achievements
- **Education** — Degrees and institutions
- **Certifications** — Compact list of all certifications
- **Languages** — Proficiency levels
- **Interests** — Professional interests
- **PDF Export** — "Download PDF" button triggers browser print-to-PDF with optimized `@media print` styles (`@page A4`, proper margins, page-break control, hidden UI elements)
- **Dark Mode** — Synced with portfolio page via shared localStorage key
- **Bilingual EN/FR** — Same toggle pattern as portfolio page
- **Profile Photo** — 100px circular image in screen view, 70pt in print PDF

## Tech Stack

- **[Astro](https://astro.build/)** — Static site generator (output: static)
- **[Tailwind CSS v4](https://tailwindcss.com/)** — Utility-first CSS framework via `@tailwindcss/vite` plugin
- **[Tabler Icons](https://tabler.io/icons)** — SVG icon library for social links and UI elements
- **[IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono)** — Monospace font for the entire site
- **TypeScript** — Type-safe configuration and Astro components
- **GitHub Pages** — Deployment via GitHub Actions (`.github/workflows/deploy.yml`)

## Architecture

```
src/
├── components/        # Astro components (Hero, About, Projects, Experience, etc.)
│   ├── Header.astro   # Sticky navigation with CV link
│   ├── Hero.astro     # Landing hero with Download CV button
│   ├── About.astro
│   ├── Projects.astro
│   ├── Experience.astro
│   ├── Education.astro
│   ├── Certifications.astro
│   ├── Languages.astro
│   ├── Recommendations.astro
│   ├── Contact.astro
│   ├── Footer.astro
│   └── Section.astro  # Reusable section wrapper
├── pages/
│   ├── index.astro    # Portfolio homepage
│   └── cv.astro       # ATS-optimized CV page
├── styles/
│   ├── global.css     # Tailwind import + dark mode overrides
│   └── cv.css         # CV screen + print styles
└── config.ts          # Single source of truth (all content, both languages)
```

## Single Source of Truth

All content lives in `src/config.ts` under `en` and `fr` objects:

| Field | Portfolio | CV |
|-------|-----------|-----|
| `name`, `title`, `description` | Header, Hero, SEO | Header |
| `social` | Hero links | Contact section |
| `aboutMe` / `profile` | About section | Professional Summary |
| `skills` / `cvSkills` | Skills tags | Categorized skills grid |
| `experience` | Experience section | Experience section |
| `education` | Education section | Education section |
| `certifications` | Certifications section | Certifications list |
| `languages` | Languages section | Languages section |
| `recommendations` | Recommendations section | — |
| `contact` | — | Contact info |
| `interests` | — | Interests section |
| `ui.*` | Section headings, labels | Section headings, button labels |

CV-specific fields (`contact`, `profile`, `interests`, `cvSkills`, and `ui.cv*` labels) are only used by the CV page.

## Local Development

```bash
# Install dependencies
npm install

# Start development server with hot reload
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

The development server uses polling for file watching (configured in `astro.config.mjs`) for compatibility with WSL and containerized environments.

## Deployment

The site is deployed to GitHub Pages via GitHub Actions. The workflow:
1. Checks out the repository
2. Sets up Node.js
3. Installs dependencies
4. Builds with `npm run build`
5. Deploys to the `gh-pages` environment using `actions/deploy-pages`

The site is served at `https://z4d4ly.github.io/portfolio/` (configured with `base: "/portfolio"` in `astro.config.mjs`).

## Customization

1. Edit `src/config.ts` to update all content (text, skills, projects, experience, etc.)
2. Add a profile photo at `public/profile.jpg` (referenced by the CV page)
3. Change the accent color via `siteConfig.accentColor`
4. Modify styles in `src/styles/global.css` (portfolio) and `src/styles/cv.css` (CV)
5. Add or remove components from `src/pages/index.astro`

## Print / PDF

The CV page includes dedicated `@media print` styles that:
- Set A4 page size with 0.4in margins
- Remove all backgrounds, shadows, and colors
- Hide all interactive controls (PDF button, lang toggle, back link, theme toggle)
- Prevent orphaned section headers with careful `break-inside` control
- Display skills inline with category labels for ATS parsing
- Include the profile photo at 70pt circular
- Reduce font sizes to fit content on a single page

To export: open `/cv`, click "Download PDF", choose "Save as PDF" in the print dialog, and uncheck "Headers and footers" for best results.

## Rights

Copyright (c) 2025 Amine Sadali (Z4D4LY). All rights reserved. See [LICENSE.md](LICENSE.md).
