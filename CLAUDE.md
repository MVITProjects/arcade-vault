# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Arcade Vault: a platform to play online games and compete for the highest score. Built with spec-driven development (`/spec` and `/spec-impl` workflow, skills from `Klerith/fernando-skills`). The project is at an early stage: `app/` is still the Create Next App scaffold (`layout.tsx`, `page.tsx`, `globals.css`).

## Commands

- `npm run dev` — dev server
- `npm run build` / `npm start` — production build / serve
- `npm run lint` — ESLint (flat config, `eslint.config.mjs`)
- No test runner is configured yet.

## Next.js version warning

Next 16.4.6 / React 19.3 with breaking changes versus common training data (see `AGENTS.md`). Before writing Next code, read the relevant guide in `node_modules/next/dist/docs/` (`01-app`, `02-pages`, `03-architecture`, `04-community`). Heed deprecation notices.

`next.config.ts` enables `cacheComponents`, `partialPrefetching` and `experimental.agentFeedback`, so caching/prefetching behavior follows the Cache Components model, not the older implicit caching.

## Architecture notes

- App Router only (`app/` at repo root, no `src/`). Path alias `@/*` maps to the repo root.
- Tailwind CSS 4 is wired through Turbopack: `next.config.ts` has a `turbopack.rules` entry running `@tailwindcss/turbopack` on `*.css` (no PostCSS config).
- `resources/` (currently untracked) holds design templates as reference prototypes, not app code: `resources/templates/` contains `Arcade Vault.html` plus JSX/CSS mockups (`nav`, `salon`, `biblioteca`, `detalle`, `reproductor`, `auth`, `data`, `app`, `styles.css`). Spanish-named screens: salon (hall/leaderboard), biblioteca (library), detalle (game detail), reproductor (player). Port these into `app/` rather than importing them.
