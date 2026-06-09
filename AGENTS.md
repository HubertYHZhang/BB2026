# AGENTS.md

This file provides guidance to Codex (Codex.ai/code) when working with code in this repository.

## What this repo is

A course slide deck project for BB2026 (an economics/business course taught in Chinese). Each lecture has three artifacts:

- `markdown/<lecture>-content.md` — source content, authored in Markdown
- `slides/<lecture>-slides.html` — generated HTML slide deck for presenting
- `lecture notes/<lecture>.html` — generated HTML lecture notes for reading

## Workflow

To generate a new slide deck or lecture notes HTML file:

1. Read `TEMPLATE.md` for the full design system (colors, typography, slide types, navigation).
2. Read the relevant `markdown/<lecture>-content.md` for content.
3. Produce a self-contained HTML file following the template exactly.

Use `TEMPLATE.md` as the canonical project spec. Do not add a separate OpenSpec/spec system unless the project starts changing shared behavior, build tooling, or the content format itself.

Prompt shorthand (put in your message):
```
Read TEMPLATE.md for the design system and markdown/<lecture>-content.md for content.
Generate an HTML slide deck following the template's design exactly.
```

## Content markdown conventions

- `---` separates logical sections (becomes a transition point between slide groups)
- `[transition]` inline marker → use a terracotta transition slide
- `[question]` inline or blockquote marker → use the question slide style (left border, large text)
- `> [question] text` → blockquote questions become question slides
- Images referenced as `resources/<filename>` — copy the path as-is into the HTML
- `<iframe>` embeds (Bilibili videos) — preserve verbatim
- `$$...$$` display math, `$...$` inline math → render with KaTeX CDN

## Generation checklist

Before considering generated output complete:

1. Confirm every markdown section has been represented, preserving the lecture's order and emphasis.
2. Keep one main idea per slide and split dense content into multiple slides.
3. Preserve `resources/<filename>` image paths and `<iframe>` embeds exactly as written.
4. Render math with KaTeX CDN when math appears in the source content.
5. Include the template navigation behavior: keyboard, click/touch navigation, and bottom progress bar.
6. Verify the output file name matches the established lecture naming pattern.

## When to write a spec

Write a short design note or proposal only for changes that affect the project structure or repeated workflow, such as:

- Changing the slide visual system in `TEMPLATE.md`
- Changing markdown conventions or required metadata
- Adding automation, build scripts, validation, or shared assets
- Restructuring generated output locations or file naming

For routine lecture generation, follow the checklist above instead of creating a separate spec.

## Template design rules (key points)

- Alternate slide themes for visual rhythm: dark → light → cream → terracotta (transition) → dark …
- One idea per slide maximum; generous whitespace
- Eyebrows: IBM Plex Mono, uppercase, with terracotta/gold colored lecture number
- Large numbers and formulas: centered, EB Garamond italic, gold on dark slides
- Navigation: arrow keys, space, click left/right thirds, touch swipe; progress bar at bottom

## File naming

Follow the pattern already established: `第N讲-<topic>-slides.html` and `第N讲-<topic>-content.md`.
