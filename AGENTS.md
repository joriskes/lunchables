# AGENTS.md

This file provides guidance to AI coding agents (opencode, etc.) when working with code in this repository.

## Commands

```bash
npm run dev          # Start dev server
npm run build        # Production build
npm run lint         # prettier + eslint check
npm run format       # Auto-format with prettier
npm run check        # TypeScript / svelte-check
```

No tests — this is a presentation app.

## What This Is

A SvelteKit presentation app for a "Lunchables" talk on OpenCode — an open-source AI coding agent. Slides are Markdown files compiled via mdsvex, displayed one-per-page with keyboard navigation and View Transition animations.

## Architecture

**Slides** live in `src/slides/` as `.md` files with YAML frontmatter:

```yaml
---
title: 'Slide title'
subtitle: 'Optional subtitle'
type: content | code | demo | ship
order: 1
---
```

**API** (`src/routes/api/slides/+server.ts`) uses `import.meta.glob()` to load all slides dynamically and returns them sorted by `order`.

**Slide routing** (`src/routes/[slug]/+page.svelte`) renders slides by type. Type `ship` shows a `ShipScore` component with browser compatibility ratings (Chrome/Firefox/Safari). Type `demo` renders interactive demo components from `src/lib/demo/`.

**Layout** (`src/routes/+layout.svelte`) handles Arrow/Space keyboard navigation and View Transition API animations between slides.

## Code Style

- Tabs for indentation, single quotes, 100-char line width (`.prettierrc`)
- Strict TypeScript
- Tailwind CSS for styling; custom fonts: Manrope (sans), JetBrains Mono (mono)
- Shiki `github-dark` theme for code blocks in slides
