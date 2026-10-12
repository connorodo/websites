# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Astro 7 site (from the "minimal" starter) with Tailwind CSS v4. Requires Node >= 22.12.0. There is no test suite, linter, or formatter configured.

## Commands

```
npm install
npm run build      # production build to ./dist/
npm run preview    # serve the built site
npx astro ...      # other Astro CLI commands, e.g. `npx astro add <integration>`
```

## Development

When starting the dev server, use background mode (via `npx` if `astro` isn't on PATH):

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`. The dev server runs at `localhost:4321`.

## Architecture

- Routing is file-based: each `.astro` or `.md` file in `src/pages/` becomes a route. Static assets go in `public/` and are served from `/`.
- Tailwind v4 is wired in as a Vite plugin in `astro.config.mjs` (not the `@astrojs/tailwind` integration), and there is no `tailwind.config.js`. Configuration lives in CSS: `src/styles/global.css` holds `@import "tailwindcss";`, so theme customization goes there via `@theme`.
- `global.css` is not imported anywhere yet. Tailwind classes have no effect on a page until that page (or a shared layout) imports it, e.g. `import '../styles/global.css';` in the frontmatter.
- There are no layouts or components yet. `src/pages/index.astro` contains a full `<html>` document directly.
- TypeScript uses `astro/tsconfigs/strict`.

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Using React, Vue, Svelte, or other framework components](https://docs.astro.build/en/guides/framework-components/)
- [Adding or managing content](https://docs.astro.build/en/guides/content-collections/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
- [Supporting multiple languages](https://docs.astro.build/en/guides/internationalization/)
