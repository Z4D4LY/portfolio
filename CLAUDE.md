# CLAUDE.md

Guidance for working with this project.

## Project Overview

A bilingual (English / French) personal portfolio for Amine Sadali, built with Astro and Tailwind CSS v4. All content is centralized in a single configuration file.

## Tech Stack

- **Astro**: Static site generator
- **Tailwind CSS v4**: Utility-first CSS framework using the `@tailwindcss/vite` plugin
- **TypeScript**: For type-safe configuration
- **Tabler Icons**: Icon library

## Development Commands

```bash
npm run dev       # Start development server
npm run build     # Build for production
npm run preview   # Preview production build
```

## Architecture

- **Components** (`src/components/`): Astro components for each section (Hero, About, Projects, Experience, Education, Certifications, Languages, Recommendations, Header, Footer)
- **Main Layout** (`src/pages/index.astro`): Single-page layout that imports all components
- **Configuration** (`src/config.ts`): Single source of truth for all content, with `en` and `fr` variants

## Important Details

- Tailwind CSS v4 with the Vite plugin
- No linting or testing framework configured
- All components use `.astro` format
- IBM Plex Mono font loaded from Google Fonts
- Social links in the config are optional and conditionally render

## Owner

Copyright (c) 2025 Amine Sadali (Z4D4LY). All rights reserved.
