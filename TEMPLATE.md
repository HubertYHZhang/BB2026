# Slide Template Reference

## How to use this template
This file describes the design system for the course slide deck.
Point Claude Code at this file + a content markdown file → it generates slides.

## Command for Claude Code
```
Read TEMPLATE.md for the design system and [lecture].md for content.
Generate an HTML slide deck following the template's design exactly.
```

## Design System

### Color Palette
```css
--bg:        #faf8f3;   /* warm off-white */
--bg-warm:   #f4efe2;   /* slightly darker warm */
--bg-cream:  #f7f2e6;   /* cream for alternating slides */
--ink:       #1f1d1a;   /* near-black text */
--ink-soft:  #5a554d;   /* secondary text */
--ink-faint: #a39d8f;   /* tertiary/labels */
--rule:      #ddd6c4;   /* borders/dividers */
--terracotta:#d97757;   /* primary accent */
--blue:      #3b6e8f;   /* secondary accent */
--gold:      #c9a961;   /* tertiary accent, used on dark bg */
--green:     #5a8a6a;   /* interaction/activity accent */
```

### Typography (Google Fonts)
- **Chinese serif (headings):** Noto Serif SC, weight 400–700
- **Chinese sans (body alt):** Noto Sans SC, weight 300–600
- **Latin serif:** Source Serif 4, weight 400–600
- **Latin display (subtitles, accents):** EB Garamond, italic
- **Sans (UI, body):** Work Sans, weight 300–600
- **Mono (labels, counters):** IBM Plex Mono, weight 400–500

### Slide Themes (alternate for rhythm)
- `.dark` — bg: --ink, text: --bg, accent: --gold
- `.light` — bg: --bg, text: --ink, accent: --terracotta
- `.cream` — bg: --bg-cream, text: --ink, accent: --terracotta
- `.terracotta` — bg: --terracotta, text: white (for transition/impact slides)
- `.blue` — bg: --blue, text: white (optional)

### Slide Types

**Title slide** (dark)
- Eyebrow: mono, uppercase, with colored number
- h1: serif-cn, 96px
- Subtitle: EB Garamond italic, terracotta/gold
- Course info: small mono text

**Content slide** (light/cream)
- Eyebrow with part number
- h2 or h3 heading
- Body text, bullet lists, or cards
- Use .accent class for colored keywords

**Question slide** (light)
- Large question text with left border (terracotta)
- Optional small hint text below

**Transition slide** (terracotta)
- Just a large h2, centered or left-aligned
- Minimal — marks a shift in topic

**Data/showcase slide** (dark)
- Two-column layout for stats/examples
- Cards in 2 or 3 column grid
- Large numbers in EB Garamond italic + gold

**Discussion slide** (dark)
- Question in .slide-question style
- Key prompt for students

### Navigation
- Arrow keys (← →), Space, PageUp/PageDown
- Click left third (back) or right third (forward)
- Touch swipe on mobile
- Progress bar at bottom
- Slide counter bottom-right

### Math
- Use KaTeX CDN for math rendering
- Delimiters: $...$ for inline, $$...$$ for display

### Key Design Principles
- Generous whitespace — don't crowd slides
- One idea per slide maximum
- Alternate dark/light/cream for visual rhythm
- Transition slides (terracotta) to mark topic shifts
- Big numbers and formulas centered, with context below
- Questions always have the left-border treatment
- Eyebrows use mono font, uppercase, with colored number

## Lecture Notes PDF Export

Lecture-note HTML files should include a dedicated `@media print` layout instead of relying on the screen layout. Use a restrained LaTeX article-like format: A4 pages, white background, roughly 25mm margins, 10pt serif body text, normal line height, modest heading sizes, and `break-inside: avoid` for goals, notes, questions, quotes, images, and embedded media. Hide decorative web-only UI such as top bars, footers, background grids, and navigation controls in print.

Questions should print as discussion callouts with a terracotta left border. Notes and supplement blocks should print as light boxed callouts. Section dividers and headings should avoid breaking at the bottom of a page.

For high-quality PDF lecture notes, prefer a dedicated LaTeX source over HTML print CSS. Map markdown markers to semantic LaTeX environments: `[question]` → `questionbox`, `[transition]` → `transitionnote`, `[note]` → `notebox`, learning goals → `goalsbox`, and overview/highlight content → `keybox`. Compile Chinese notes with XeLaTeX or LuaLaTeX through `ctexart`.
