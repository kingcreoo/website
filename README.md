# Creoo Testing Lab

A public journal / portfolio running on a Raspberry Pi Zero 2W sitting in my office. On here I will be posting blogs, idea explorations, commentary, and documentation of ongoing projects. I will write as things happen. The site's state is subject to change.

The philosophy of the site is to be as simpled as possible. I wish to harbor no load times on my site and the content should not be performative in any way. Content should speak for it's self and inner workings should be open sourced.

My inspiration for this site was sparked by "Low Tech Magazine".

## Navigation of this repository

**Writing** lives under `/articles/` and are displayed currently only on the front page in a simple catalogue.

**Photos** live on the art wall at `/art/`. It is organized into galleries by trip or subject. Currently it just includes photos of my trip to South America, my times in Wyoming, and a few of my motorcycles. The art wall currently features a justified gallery system and when you click on each photo it jumps into priority view.

- **[Astro](https://astro.build)** - The site currently uses astro for simplicity's sake.
- **Single CSS file** - No silly frameworks just a single global css file.
- **No database** - Articles are Markdown files and photo galleries on the art wall are folders with a `_meta.json` index
- **Served by nginx** - No silly subscription fee or service to host. It runs on my own hardware.

## What's coming

- Tons of content
- Mobile formatting
- Content archive (simple list format as opposed to front-page catalogue format)
- Self-hosted video (no YouTube embeds)
- Solar-powered server version