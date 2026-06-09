---
name: slides-maker
description: Convert lecture notes into clear, concise, lecture-ready single-file HTML slide decks for this course on institutions. Use when Codex is asked to make slides, HTML slides, lecture decks, academic teaching slides, or convert notes into a visual classroom sequence; prefer this for HTML decks rather than PPTX/PowerPoint output.
---

# Slides Maker

## Core Principles
1. Follow the instructions in the `.tex` file given by the user on different roles of specific contents. Use these different roles to assemble a full story chain for the slides deck.
2. Be concise when possible, unless the user asks you not to.
3. Add guiding slides when needed, such as when something new is to be introduced. You can create a separate page just to ask a question or to raise an example from the given materials.
4. It is better to build the skeleton without content than hallucinating something. For example, you think we should have a question slide here, but the user did not specify that. You should add an empty slide there to remind the user instead of hallucinating something by yourself.
5. Keep the reasoning logic as in the lecture notes instead of just giving the keywords. Whenever the user writes with logical deduction, you should try to represent those logical relations in the slides.
6. For Chinese academic decks, use precise, restrained Chinese with occasional light humor only when it serves the teaching.

## Workflow
### From markdown to html
Before making the html, you should create a `.md` file on what you are going to write in each page. The description should be as detailed as possible, including the visualization, font style and size (you can stipulate different relative sizes for different levels of contents and just specify the levels in the md), all the bullet points or table or pictures, etc. 

When converting the md into html, you should NOT write a mechanical script to make it. Instead, you should read the `.md` and make the `.html` based on your understanding. There is something that rules cannot include.

### Planning multiple visual versions

A single slide-plan `.md` can drive more than one HTML visual treatment. When the user asks for both the original slides plan and a recolored plan, keep the intellectual sequence, page list, examples, images, math, embeds, and interaction behavior identical, then create two sibling HTML decks:

* the normal BB2026 warm academic version;
* the alternate recolor version, using the palette and theme rules requested by the user.

Do not duplicate or fork the content plan unless the content itself changes. The second version should be a visual variant of the same teaching sequence, not a separate lecture.

## Recommended Slide Types

### 1. Title Slide

Use for lecture opening.

Style:

* dark background;
* large Chinese title;
* small English subtitle or course label;
* small course/date line.

Example:

```html
<section class="slide dark active">
  <div class="slide-inner">
    <div class="eyebrow">
      <span class="num">01</span>
      <span class="dash"></span>
      <span>Day 1</span>
    </div>
    <h1>关于市场</h1>
    <div class="subtitle">What is a market — and where does it end?</div>
    <p class="small">日常制度的经济学</p>
  </div>
</section>
```

### 2. Puzzle Slide

Use when the notes begin from an example, contradiction, or intuition.

Good puzzle slides often ask:

```text
为什么 A 很正常，B 却让人不安？
为什么同样是双方自愿，有些交易仍然不合适？
为什么有些东西可以定价，有些不可以？
```

### 3. Contrast Slide

Use for paired cases.

Examples:

* 买模拟题 vs 买考试名次；
* 外卖时间 vs 陪伴时间；
* 市场 vs 排队；
* 价格分配 vs 抽签分配.

Use a two-column layout. Each column should contain:

* small label;
* main sentence;
* one short explanatory line.

### 4. Question Slide

Use a large question card with a left border.

Example:

```html
<div class="slide-question">
  如果不用价格，资源还能怎样分配？
</div>
```

Use this for classroom pauses.

### 5. Transition Slide

Use for section changes.

Good transition slide titles:

```text
如果不用市场，还能怎么分配？
市场为什么显得有效？
何为“有效”？
市场的边界在哪里？
```

Use terracotta or dark background.

### 6. Concept Slide

Use when introducing a definition.

Structure:

```text
概念名
一句定义
一个例子或对比
```

Do not overload with academic literature.

### 7. Mechanism Slide

Use when explaining how an outcome is generated.

Preferred structure:

```text
条件 → 行动 → 相互影响 → 结果
```

Or:

```text
谁在行动？
他们知道什么？
他们想要什么？
他们如何相互影响？
结果如何出现？
```

### 8. Table Slide

Use only when comparison is central.

Rules:

* no more than 6 rows;
* preferably 3 columns;
* each cell should be short;
* each row should have one clear point.

Good table structure:

```text
机制 | 关键词 | 核心问题
排队 | 时间 | 等待时间不等于真实需要
抽签 | 随机 | 随机不保证资源流向最重视者
审核 | 信息 | 中心判断难以掌握真实情况
考试 | 指标 | 指标会被训练和扭曲
关系 | 身份 | 关系分配排斥外人
```

### 9. Card Grid Slide

Use three cards for conceptual triads.

Good for:

```text
效率 / 分配 / 边界
功能 / 维持 / 起源
信息 / 激励 / 执行
```

Use six mini-cards only when the content is compact.

### 10. Case Card Slide

Use for examples or news-like cases.

Each card should contain:

* case label;
* short title;
* one-sentence problem.

Example:

```text
案例 A：口罩二级市场
价格上涨是配置信号，还是危机中的剥夺？
```

### 11. Quote Slide

Use sparingly.

A quote slide should contain:

* short quote;
* author;
* one sentence explaining why the quote matters.

Avoid long quotes.

### 12. Recap Slide

Use after dense sections.

Structure:

```text
到目前为止，我们得到三点：
1. ...
2. ...
3. ...
```

### 13. Final Slide

Every deck should end with a clear final slide.

Possible endings:

```text
研究制度，不是问它好不好这么简单。

我们要问：
1. 它处理什么问题？
2. 它如何稳定下来？
3. 它把成本转移给了谁？
```

## Visual Template

Use the user’s existing HTML deck style as the default visual grammar, while adapting when the lecture requires another layout.

### Canvas

Use a fixed 16:9 canvas:

```css
.deck {
  width: 1280px;
  height: 720px;
  position: relative;
  transform-origin: center center;
}
```

Scale the deck to viewport with JavaScript while preserving 16:9.

Include:

* keyboard navigation;
* click navigation;
* touch navigation if easy;
* bottom progress bar;
* slide counter.

### Color Palette

Use a warm academic palette.

The default BB2026 palette is warm, terracotta-forward, and lecture-like. It remains the standard style unless the user asks for another visual treatment.

Recommended default:

```css
:root {
  --bg:        #FAF7F0;
  --bg-cream:  #F3EBDD;
  --bg-warm:   #EFE4D0;

  --ink:       #1E1B18;
  --ink-soft:  #5F5A52;
  --ink-faint: #A79F91;
  --rule:      #D8CEBC;

  --accent:    #B85C38;
  --accent-2:  #527F99;
  --accent-3:  #A8873A;

  --dark:      #1E1B18;
  --dark-soft: #2B2722;
}
```

Use colors semantically:

```text
bg / cream      ordinary explanation
warm            examples, discussion, cases
dark            opening, major emphasis, closing
accent          main questions, contrasts, section markers
accent-2        mechanisms, frameworks, market-level structure, comparison
accent-3        small emphasis on dark slides
```

Avoid using many accent colors on the same slide.

For BB2026 lecture decks, use this blue-slide convention unless the user asks for another style:

```css
:root {
  --blue: #527f99;
}

.blue {
  background: var(--blue);
  color: #fff;
}

.blue .card,
.blue .mini-card {
  background: rgba(25,54,70,.24);
  border: 1px solid rgba(250,248,243,.18);
  box-shadow: 0 18px 36px rgba(31,29,26,.10);
}

.blue .card-label,
.blue .mc-label {
  color: #F4B27B;
}

.blue .card h4,
.blue .mini-card h4 {
  color: #fff;
}

.blue .card p,
.blue .mini-card p {
  color: rgba(250,248,243,.76);
}
```

Use blue slides for mechanism, framework, or market-structure pages. Keep card surfaces in the same blue family rather than switching to white cards.

### NBER-style recolor palette

When the user asks for an NBER-style recolor, Digest-style recolor, or explicitly references `slides/market_nber_recolor_v3.html`, preserve the same slide plan and generate a second HTML deck using this palette. This recolor should feel like a clean policy/research digest: white paper background, strong NBER blue, restrained Digest red, pale blue section surfaces, square frames, and minimal shadows.

Use these tokens:

```css
:root {
  --bg: #FFFFFF;
  --bg-cream: #F3F7FB;
  --bg-warm: #EAF2FA;

  --ink: #161616;
  --ink-soft: #555B64;
  --ink-faint: #8A9099;
  --rule: #CBD7E6;

  --terracotta: #A1192A; /* Digest red in this variant */
  --blue: #1C67B1;
  --green: #4D7B93;
  --gold: #A1192A;

  --nber-blue: #1C67B1;
  --nber-blue-dark: #123A63;
  --nber-blue-soft: #EAF2FA;
  --digest-red: #A1192A;
  --paper: #FFFFFF;

  --serif-cn: "Noto Serif SC", "Source Serif 4", "Songti SC", serif;
  --sans: "Work Sans", "Noto Sans SC", system-ui, sans-serif;
  --mono: "IBM Plex Mono", ui-monospace, monospace;
  --display: "Source Serif 4", "EB Garamond", "Noto Serif SC", serif;
}
```

Use these semantic mappings:

```text
paper / white       ordinary explanation and section dividers
pale blue           examples, discussion, cases, low-emphasis structure
NBER blue           opening, major emphasis, mechanisms, framework pages
Digest red          eyebrows, progress bar, links, table headers, small accents
dark blue           subtle grid overlays or deep-blue supporting structure
```

Theme rules for the recolor variant:

* `.light` uses white paper, `.cream` uses near-white blue, and `.warm` uses pale blue;
* `.dark` and `.blue` both use `--nber-blue` with white text;
* `.terracotta` should not become a red full-slide block; use it as a white section divider with blue heading text and thin pale-blue rules;
* question borders, bullets, formulas, and stats use NBER blue on light slides and white on dark/blue slides;
* Digest red is for small navigational or editorial accents, not large backgrounds;
* cards, mini-cards, quote cards, image frames, and video frames should use square corners and little or no shadow;
* the progress bar uses Digest red; navigation and counters should stay quiet.

For dark/blue recolor slides, an understated grid texture is acceptable:

```css
.dark::before,
.blue::before {
  content: "";
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
  background:
    linear-gradient(rgba(255,255,255,.10) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,.07) 1px, transparent 1px),
    linear-gradient(90deg, rgba(18,58,99,.20) 0 34px, transparent 34px 92px);
  background-size: 100% 78px, 118px 100%, 180px 100%;
  opacity: .28;
}
```

When producing both versions, name the recolored output clearly with an NBER/recolor suffix, while keeping the original deck name for the warm BB2026 version unless the user specifies filenames.

### Typography

Use serif Chinese for main content and sans/mono fonts for labels.

Recommended font stack:

```css
--serif: "Source Serif 4", "Noto Serif SC", Georgia, serif;
--sans:  "Work Sans", "Noto Sans SC", system-ui, sans-serif;
--mono:  "IBM Plex Mono", ui-monospace, monospace;
--display: "EB Garamond", "Noto Serif SC", serif;
```

Use:

* serif Chinese for main titles and body;
* mono uppercase for section labels / eyebrows;
* muted small text for secondary remarks;
* display serif for occasional English subtitles or large numbers.

### Slide Themes

Define these slide classes:

```css
.slide.light { background: var(--bg); color: var(--ink); }
.slide.cream { background: var(--bg-cream); color: var(--ink); }
.slide.warm  { background: var(--bg-warm); color: var(--ink); }
.slide.dark  { background: var(--dark); color: var(--bg); }
.slide.accent { background: var(--accent); color: #fff; }
.slide.blue  { background: var(--accent-2); color: #fff; }
```

Use transition slides with `.accent` or `.dark`.

### Eyebrow Labels

Use an `eyebrow` line at the top of many slides:

```html
<div class="eyebrow">
  <span class="num">Part 2</span>
  <span class="dash"></span>
  <span>分配机制</span>
</div>
```

This helps students track structure.

### Question Card

Use a large question card for discussion prompts:

```css
.slide-question {
  font-family: var(--serif);
  font-weight: 500;
  font-size: 48px;
  line-height: 1.4;
  padding-left: 32px;
  border-left: 5px solid var(--accent);
  margin: 32px 0;
}
```

### Big Section Marker

Use a large faint number or Roman numeral for section slides:

```css
.big-num {
  font-family: var(--display);
  font-style: italic;
  font-size: 200px;
  line-height: 0.85;
  color: var(--accent);
  opacity: 0.12;
  position: absolute;
  right: -20px;
  top: -30px;
}
```

Use sparingly.

## HTML Structure

Default structure:

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Lecture Title</title>
<style>
  /* CSS here */
</style>
</head>
<body>
<div class="stage">
  <div class="deck" id="deck">
    <section class="slide dark active">
      <div class="slide-inner">
        ...
      </div>
    </section>
  </div>
</div>

<div class="progress" id="progress"></div>
<div class="counter" id="counter"></div>

<script>
  /* navigation and scaling */
</script>
</body>
</html>
```

Use `<section class="slide ...">` or `<div class="slide ...">`, but be consistent.
