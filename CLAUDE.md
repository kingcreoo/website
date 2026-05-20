# Creoo Testing Lab — CLAUDE.md

## Stack
- **Framework:** Astro (static output only — no SSR)
- **Styling:** Single CSS file at `src/styles/global.css`
- **Fonts:** System serif stack — no external fonts loaded
- **Deploy target:** Pi Zero 2W serving static files via nginx

## Commands
- `npm run dev` — local dev server at localhost:4321, use this for all testing
- `npm run build` — builds static output to `dist/`

## File & URL Structure
- `src/pages/articles/` → `/articles/` — main pieces including blog posts, dev logs, idea talks
- `src/styles/global.css` — all styles live here, no inline styles
- `public/images/` — static assets

## Frontmatter
Articles (`title`, `date`, `description`, `tags`):
```markdown
---
title: The Lowtech Loadout
date: 2026-03-10
description: Why a Librebooted ThinkPad and a beater Subaru constitute a deliberate philosophy.
tags: [philosophy, hardware]
---
```
Frontmatter fields should be wired into `<title>` and `<meta name="description">` tags for SEO.

## Design Rules
- **No JS for core functionality** — JS for progressive enhancement only (mobile toolbar, hover previews)
- **No client-side filtering** — tags generate static pages at build time
- **Mobile breakpoint:** `768px` — check layout at this width when touching CSS
- **Color palette:** background `#faefd4`, text `#1C1D21`, muted `#75798a`, hover `#474747`

## Rules
- Always check the mobile breakpoint when touching layout CSS
- Never add npm packages without asking first
- Never add inline styles — keep all styles in `global.css`
- Run `npm run build` and verify no errors before considering a task done

## Art Wall Photo Workflow
When the user asks to process photos for a gallery on the art wall:

1. Ask for the source folder path (e.g., `/home/creoo/Pictures/Wyoming`) and the gallery slug (e.g., `wyoming`) if not given.
2. Ensure `public/images/art/<slug>/` exists — create if not.
3. Copy all image files (`*.jpg *.jpeg *.png`) from source to destination.
4. In the destination folder, run:
   ```
   mogrify -resize 1600x1600\> -quality 82 -auto-orient -strip *.jpg *.jpeg *.png
   ```
   The `\>` flag means shrink only — already-small photos pass through untouched. `-auto-orient` bakes EXIF rotation into the pixels. `-strip` removes metadata.
5. Generate `public/images/art/<slug>/_meta.json` with:
   - `title` — human-readable name (ask user if unclear)
   - `date` — ISO date; use the oldest photo's date if the user doesn't specify
   - `cover` — filename for the folder icon on `/art/`. Prefer landscape or square. Ask if unclear.
   - `images` — array of `{ file, width, height }` in chronological order. Get dimensions with `identify -format "%f %w %h\n" *.jpg`.
6. Report count of images processed, total size, and any errors.
7. The gallery page at `/art/<slug>/` is rendered automatically by `src/pages/art/[slug].astro` — no template changes needed for new galleries.
