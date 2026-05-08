---
layout: ../../layouts/ArticleLayout.astro
title: Article Template & Feature Reference
date: 2026-04-03
author: Collin DeSantis
description: A living reference for every feature available in an article. Each element is demonstrated and explained in place.
lede: This template demonstrates every frontmatter field and content element supported by the site.
tags: [meta, reference]
image: /images/rune-1.png
hidden: true
---

This document is both a showcase and a manual. Every element below is an example of a feature you can use in any article on this site. The source file for this page lives at `src/pages/articles/template.md` — open it alongside this page and you will see exactly how each feature is written.

## Frontmatter

Every article starts with a frontmatter block between the `---` fences. It is not visible on the page, but it drives the title, byline, opener, tags, and image. The full set of fields:

```markdown
---
layout: ../../layouts/ArticleLayout.astro
title: Your Article Title
date: 2026-04-03
author: Collin DeSantis
description: One sentence. Used for SEO and as the homepage preview on pinned articles.
lede: One sentence. Appears as the opener under the title on the article page itself.
tags: [tag-one, tag-two]
image: /images/something.jpg
pinned: false
draft: false
hidden: false
---
```

- `layout` — required. Points to the shared article shell.
- `title` — required. Renders as the H1 and in the browser tab.
- `date` — required. ISO format (`YYYY-MM-DD`).
- `author` — optional. Renders as "Written by [name]" with a link to `/authors/<slug>` (slug auto-derived from name).
- `description` — optional. Used as `<meta name="description">` for search engines, and as the preview text on the homepage for pinned articles. Not shown on the article page.
- `lede` — optional. The opening sentence shown beneath the title on the article page. Different from `description` because the audiences are different — `description` is for someone deciding whether to click; `lede` is for someone who already clicked.
- `tags` — optional. Each tag links to `/tags/<tag>`, a grid of all articles with that tag.
- `image` — optional. Used as the thumbnail on homepage cards, tag pages, and author pages. Falls back to `/images/rune-1.png`.
- `pinned: true` — optional. Pins the article to the featured slot on the homepage page 1 (max two pinned at a time).
- `draft: true` — optional. Hides the article from listings in production builds, but it still shows in `npm run dev`. The page itself still builds at its URL — drafts are list-hidden, not entirely absent.
- `hidden: true` — optional. Permanently excluded from all listings (homepage, tags, authors). The page still builds at its URL. Used for things like the about page, which has a dedicated entry point in the header.

---

## Headings

Use `##` for a section heading and `###` for a sub-heading within that section. Never use `#` — the article title already is the h1.

```markdown
## Section Title
### Sub-section
```

Headings are uppercase automatically by CSS. Keep them short and declarative — they are navigation aids, not sentences.

### This Is a Sub-heading

Sub-headings have no border, just heavier weight. Use them sparingly, only when a section genuinely splits into distinct parts.

---

## Paragraphs

Just write. A blank line between blocks creates a new paragraph. No special markup needed.

This is a second paragraph. Line length is constrained by the column width so you do not need to think about it. Write at whatever line width your editor gives you.

---

## Bold and Italic

**Bold** is `**like this**`. Use it for terms being defined, or critical warnings — not for emphasis you could convey with word choice.

*Italic* is `*like this*`. Use it for titles of things (books, films, products), foreign words, or genuine tonal stress.

Avoid using both in the same sentence. If something needs both, the sentence probably needs rewriting.

---

## Blockquotes

> The best tool is the one you already own and understand. Buying a new tool to solve a problem the old tool could handle is just consumption dressed as problem-solving.

Written as:

```markdown
> The best tool is the one you already own and understand.
```

Use blockquotes for direct quotations — things someone actually said or wrote. Not for your own asides; that is what parentheses are for.

---

## Lists

Unordered list — use when order does not matter:

- Penetrating oil
- Wire brush
- 10mm socket (obviously)
- A flashlight you can hold in your mouth

Ordered list — use when sequence matters:

1. Disconnect the battery negative terminal first.
2. Let the capacitors discharge for two minutes.
3. Only then touch anything on the board.

```markdown
- item
- item

1. first
2. second
```

Do not mix list types within a single thought. Do not nest lists more than one level deep — if you need sub-bullets, you probably need a sub-heading instead.

---

## Code

Inline code for commands, file paths, config keys, and anything the reader should type literally: `npm run build`, `src/pages/articles/`, `overflow: hidden`.

Wrap it in backticks: `` `like this` ``

For multi-line code, use a fenced block with the language name:

````markdown
```bash
rsync -avz --delete dist/ pi@creoo.local:/var/www/html/
```
````

Which renders as:

```bash
rsync -avz --delete dist/ pi@creoo.local:/var/www/html/
```

Language identifiers the site uses: `bash`, `markdown`, `css`, `js`, `html`. If you do not know the language, leave the identifier blank — it will still render in monospace without syntax highlighting.

---

## Images

Images go in `public/images/`. A bare image in markdown:

```markdown
![A descriptive alt text](/images/rune-1.png)
```

For an image with a caption, use a `figure` block written in HTML directly inside the markdown file — Astro supports this:

```html
<figure>
  <img src="/images/rune-1.png" alt="The rune mark used throughout the site" />
  <figcaption>The rune mark. Pulled from a public domain woodcut, redrawn at 32×32.</figcaption>
</figure>
```

Which renders as:

<figure>
  <img src="/images/rune-1.png" alt="The rune mark used throughout the site" />
  <figcaption>The rune mark. Pulled from a public domain woodcut, redrawn at 32×32.</figcaption>
</figure>

Always write alt text. It is read by screen readers and displayed if the image fails to load. Describe what is in the image, not what it means.

Photos go in `public/images/` alongside everything else. Name them clearly: `subaru-head-gasket-before.jpg`, not `IMG_4823.jpg`. The Pi is serving these directly — no image CDN, no resizing pipeline. Keep file sizes reasonable. A photo exported at 80% JPEG quality and 1200px wide is enough for any screen that will visit this site.

---

## Tables

Good for gear comparisons, spec lists, anything with rows and columns of related data.

| Tool | Cost | Verdict |
|---|---|---|
| Harbor Freight torque wrench | $30 | Good enough for most fasteners |
| Snap-on equivalent | $280 | Not 9× better |
| Beam-style torque wrench | $18 | No batteries, never needs calibration |

```markdown
| Tool | Cost | Verdict |
|---|---|---|
| Harbor Freight torque wrench | $30 | Good enough |
```

Tables are readable but tedious to write by hand. If a table has more than four columns, consider whether a list serves better.

---

## Horizontal Rules

A `---` on its own line creates a section break — a thin horizontal line. Use it to separate major shifts in topic within an article, or before a closing section. Do not use it decoratively between every paragraph.

---

## Links

External link: [Low-Tech Magazine](https://www.lowtechmagazine.com) — written as `[text](url)`.

Internal link to another article: [About This Site](/articles/about-this-site) — same syntax, just use the path from the root.

Link text should describe the destination, not say "click here." If the URL itself is the point, write the URL.

---

## The See Also Block

At the end of an article, you can add a "see also" section linking to related pieces. It uses a plain HTML div with the class `see-also` directly in the markdown:

```html
<div class="see-also">

**See also**

- [Raw Milk and First Principles](/articles/raw-milk) — the same logic applied to food
- [Hosting on a Pi Zero](/logs/pi-zero-hosting) — the machine serving this page

</div>
```

<div class="see-also">

**See also**

- [Raw Milk and First Principles](#) — the same logic applied to food
- [Hosting on a Pi Zero](#) — the machine serving this page

</div>
