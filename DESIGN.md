# Gnomons — Design Guidelines

How gnomons.com looks, reads, and is built. These guidelines are derived from the pages
already live in this repo — [index.html](index.html),
[cyber-resilience-by-design.html](cyber-resilience-by-design.html) and
[conversational-hand-gestures.html](conversational-hand-gestures.html) — and are meant
to keep every new page consistent with them.

---

## 1. Design principles

1. **Engineering-document calm.** The site should feel like a well-kept datasheet, not
   an ad. White paper, slate ink, one green accent, thin hairlines. No gradients, no
   stock imagery, no decorative illustration.
2. **Mono for the machine, sans for the human.** JetBrains Mono marks anything technical
   or structural — labels, part numbers, specs, tags, metadata. Inter carries headlines
   and prose.
3. **Show the mechanism.** Prefer a precise SVG architecture diagram, a stat tile with a
   real number, or a status table over adjectives. Every claim should be checkable.
4. **Honest status.** Distinguish *built*, *in progress* and *planned* visually and
   verbally. Never present roadmap work as shipped.
5. **One path to contact.** Every page ends in the same email CTA
   (`services@gnomons.com`). No forms, no trackers.

---

## 2. Brand assets

| File | Use | Notes |
|---|---|---|
| `logo.png` | Sundial mark (gnomon + sun) | 1130×1131, `#008000`. Shown at 36×36 (`w-9 h-9`) in the header. |
| `wordmark.png` | "gnomons" lettering | 1457×525, `#0f7003`. Shown at 36px tall (`h-9`) next to the mark, `gap-3`. |
| `favicon.ico` | Browser tab icon | Link it from every page. |

- Always pair mark + wordmark in the header; don't use the wordmark alone.
- Never recolor, stretch, outline, or place the logos on green or dark backgrounds.
  The logo greens (`#008000`, `#0f7003`) are **asset colors only** — do not use them in UI.
- In running text the name is written **Gnomons** (capital G). The wordmark's lowercase
  styling is reserved for the image.
- Name origin, when referenced: Greek *γνώμων (gnōmōn)*, "one who knows or examines" —
  the pillar of a sundial. The sundial/shadow metaphor is the brand's only allowed motif.

---

## 3. Color

The palette is Tailwind's **slate** (neutrals) + **green** (brand). The landing page uses
Tailwind classes; subpages use the equivalent CSS custom properties. Use these names
exactly so both systems stay in sync.

### 3.1 Core tokens

| Role | CSS variable | Tailwind | Hex |
|---|---|---|---|
| Page background | `--paper` | `bg-white` | `#ffffff` |
| Panel / quiet surface | `--panel` | `bg-slate-50` | `#f8fafc` |
| Headings, primary ink | `--ink` | `text-slate-900` | `#0f172a` |
| Body text | `--ink-soft` | `text-slate-600` | `#475569` |
| Secondary / metadata | `--ink-mute` | `text-slate-500` | `#64748b` |
| Faint labels, disclaimers | `--ink-faint` | `text-slate-400` | `#94a3b8` |
| Borders | `--line` | `border-slate-200` | `#e2e8f0` |
| Hairlines / section dividers | `--line-soft` | `border-slate-100` | `#f1f5f9` |
| Brand (buttons, dots, strokes) | `--brand` | `brand-600` | `#16a34a` |
| Brand hover, label text | `--brand-dark` | `brand-700` | `#15803d` |
| Brand text on tint | `--brand-darker` | `brand-800` | `#166534` |
| Brand soft fill (badges) | `--brand-soft` | `brand-100` | `#dcfce7` |
| Brand tint (panels, chips) | `--brand-tint` | `brand-50` | `#f0fdf4` |
| Brand border | `--brand-line` | `green-200` | `#bbf7d0` |
| Live indicator dot | — | `brand-500` | `#22c55e` |

Dark band (landing page "Engagement" section only): `bg-slate-900` surface,
`slate-800/60` cards, `slate-700/60` borders, `text-slate-300`/`400` body, `brand-500`
labels.

### 3.2 Semantic / secondary colors

Only introduce these when they carry meaning, and always define the full ramp:

| Meaning | Prefix | Main | Dark | Soft | Tint |
|---|---|---|---|---|---|
| **In progress / partial** | `--warn-*` (amber) | `#d97706` | `#b45309` | `#fef3c7` | `#fffbeb` |
| **Second data lane** (e.g. language model vs. vision) | `--accent-*` (sky) | `#0ea5e9` | `#0369a1` | `#e0f2fe` | `#f0f9ff` |

Accent line: `--accent-line: #bae6fd`. Amber border: `#fde68a`.

### 3.3 Rules

- Green is the **only** brand color. Use it for actions, status "built", and key labels —
  not for large backgrounds beyond the 50-tint.
- Body copy is never pure black and never brand green; use `--ink-soft`.
- Emphasis inside prose: `<strong>` in `--ink` (landing) or `--brand-darker` (callouts).
- Text selection: `brand-100` background, `brand-900`/`--brand-darker` text.
- Don't add new hues ad hoc. If a page needs a third category, add a named ramp here first.

---

## 4. Typography

**Fonts** (Google Fonts):
- **Inter** 400/500/600/700/800 — headings, body. Fallback: `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif`.
- **JetBrains Mono** 400/500/600/700 — labels, tags, specs, metadata, code. Fallback: `'Fira Code', Monaco, monospace`.

Enable `antialiased` (Tailwind) and `line-height: 1.6` on body.

### 4.1 Scale

| Element | Landing page (Tailwind) | Subpages (CSS) |
|---|---|---|
| H1 / hero | `text-4xl sm:text-5xl md:text-6xl font-bold tracking-tight leading-[1.1]` | `clamp(32px,4.6vw,48px)`, 800, `-0.02em`, lh 1.1, `text-wrap:balance` |
| Hero lead | `text-lg md:text-xl text-slate-600 leading-relaxed` | 17px, `--ink-soft`, lh 1.65 |
| H2 / section title | `text-3xl font-bold text-slate-900` | 27px, 700, `-0.01em`, `text-wrap:balance` |
| H3 / card title | `text-xl font-bold` | 18px, 700, lh 1.32 |
| Lede / body | `text-base` / `text-sm leading-relaxed text-slate-600` | 15.5px lede, 14px card body |
| Section label (eyebrow) | `text-xs font-mono font-semibold uppercase tracking-wider text-brand-700` | 12px mono 600, `0.08em`, uppercase, `--brand-dark` |
| Tag / chip | `font-mono text-xs font-medium` | 12px mono 500 |
| Badge / pill | — | 10.5px mono 600, `0.03em` |
| Tech note / caption | `text-xs font-mono text-slate-500` | 11–12.5px mono, `--ink-mute` |
| Fine print | `text-[11px] text-slate-400` | 11px, `--ink-faint` |

### 4.2 Rules

- Every section opens with a **mono uppercase section label** followed by an Inter
  heading. This label→heading pair is the site's signature.
- Headlines use sentence case on subpages ("Built with cyber resilience in mind."),
  Title Case on the landing page section titles. Keep each page internally consistent.
- Japanese text is welcome inline (names, vision statement); give Japanese names in
  parentheses in mono, `text-slate-400`: `Jun Sato (佐藤潤)`.
- Use real typographic characters: em dash `—`, middle dot `·`, `×`, `µ`, `²`, `§`, `→`.

---

## 5. Layout & spacing

- **Content width:** `max-w-5xl` (1024px) on the landing page; `.wrap` 1040px on subpages.
  Side gutters: `px-6` / 24px.
- **Section rhythm:** `py-20` (80px) landing; `padding: 52px 0` subpages. Hero gets more
  (`pt-24 pb-20 md:pt-32 md:pb-28`).
- **Section separation:** a 1px `slate-100` / `--line-soft` hairline (`<hr>` or
  `border-bottom`). Alternate surfaces sparingly: `brand-50/40` band with `brand-100/60`
  borders, or the single dark `slate-900` band.
- **Grids:** 3 columns for peer items (pillars, steps, team) → `md:grid-cols-3 gap-8/10`;
  2 columns for paired cards → `grid-template-columns:1fr 1fr; gap:18px`; 12-column split
  (5/7) for asymmetric feature panels. Subpage hero: `1.15fr 0.85fr`, gap 44px.
- **Breakpoints:** Tailwind defaults on the landing page (`sm` 640, `md` 768, `lg` 1024).
  Subpages collapse at **760px** (hero) and **680px** (cards, stat strips).
- Inner card padding: 24–32px (`p-6`/`p-8`). Card stack gap: 11px between elements.

---

## 6. Shape, elevation & motion

| Token | Value | Use |
|---|---|---|
| Radius — small | 4–5px (`rounded`) | Chips, tags, number tiles, provision labels |
| Radius — button | 6px | Buttons, translate button |
| Radius — card | 8–10px (`rounded-lg` / 10px) | Cards, panels, diagrams, video, CTA box |
| Radius — pill | 99px (`rounded-full`) | Eyebrow, badges, status pills, dots, avatars |
| Shadow — card | `0 1px 2px rgba(15,23,42,.04), 0 8px 20px -10px rgba(15,23,42,.10)` (`shadow-sm`) | Cards, diagrams |
| Shadow — primary button | `0 8px 20px -8px rgba(22,163,74,.45)` (`shadow-md shadow-brand-600/20`) | Primary CTA only |

- Borders do the work; shadows stay barely visible.
- **Hover:** cards shift border to `brand-300` / `--brand-line` (amber `#fde68a` for
  in-progress cards); links/buttons shift to `brand-700`. Never move or scale elements.
- **Transitions:** `transition-colors` / `.15s ease`. The only animation on the site is
  the `animate-pulse` availability dot in the hero.
- Header: sticky, `h-20`, `bg-white/90 backdrop-blur-md`, bottom hairline.

---

## 7. Components

Copy markup from the referenced page rather than re-inventing it.

### Eyebrow (hero)
Pill with a leading dot, mono uppercase, green on tint.
Landing: `inline-flex gap-2 px-3 py-1 rounded-full bg-brand-50 border border-brand-100 text-xs font-mono text-brand-800` + pulsing `brand-500` dot.
Subpages: `.eyebrow` + `.dot`. Content pattern: `Category · Platform · Detail`
(e.g. `Featured R&D · Renesas RA8P1 · µT-Kernel 3.0`).

### Section label + heading
`.section-label` (or Tailwind `text-xs font-mono font-semibold uppercase tracking-wider text-brand-700`)
directly above the H2. On the dark band, the label is `text-brand-500`.

### Buttons
| Variant | Style | Example |
|---|---|---|
| Primary | `bg-brand-600 hover:bg-brand-700 text-white font-medium rounded px-6 py-3.5 text-sm` + brand shadow + trailing arrow icon | "Email Us About Your Project", `.cta-btn` |
| Secondary (outline) | `text-brand-700 border border-brand-600 hover:bg-brand-50 px-4 py-2 rounded font-semibold text-sm` | Header "Get in Touch" |
| Utility (mono) | `bg-slate-50 border-slate-200 font-mono text-xs`, hover → brand tint | Copy-email button |
| Text / ghost | mono 12px `--ink-mute`, thin border, hover → brand | `.translate-btn`, `.back` link |

Buttons are full-width stacked on mobile (`flex-col sm:flex-row items-stretch`).

### Cards
- **Case study / capability card:** white, `border-slate-200/80`, `rounded-lg`, `p-8`,
  `shadow-sm`, hover border brand. Structure: tag row → H3/H4 → body → hairline →
  mono `Key: value` metadata (`<strong class="text-brand-700">Target:</strong> …`).
- **Subpage `.card`:** optional top-right `.badge`, `.provision` label, H3, body,
  `.why-line` (bold green one-liner above a hairline), `.tech-note` (mono), and
  `.chips-label` + `.chips`. Add `.dev` modifier to switch everything to amber.
- **Quiet panel:** `bg-slate-50/50 border-slate-100 rounded p-6` — capability matrix,
  team cards, offices.
- **Brand panel:** `bg-brand-50/60 border-brand-100` (landing) / `.why-band`, `.define`,
  `.cta` (subpages) — for definitions, "why it matters", and the contact block.

### Tags & chips
Mono, 12px, `px-2.5 py-1`, `rounded`, `bg-brand-50 text-brand-800 border-brand-200/60`.
`.chip.dim` (transparent, slate border, `--ink-mute`) marks items not yet delivered.

### Status pills & badges
| Status | Fill | Text |
|---|---|---|
| Built / strong | `--brand-soft` | `--brand-darker` |
| In progress / partial | `--warn-soft` | `--warn-dark` |
| Planned / open | `--panel` + `--line` border | `--ink-mute` |

Labels are lowercase in badges (`built`, `in progress`) and Title Case in table pills
(`Built`, `Planned`). Pair status with a legend whenever color carries meaning.

### Numbered items
- Pillars: 40×40 `rounded` tile, `bg-brand-50 border-brand-100 text-brand-700 font-mono font-bold`, text `01`/`02`/`03`.
- Steps: mono `STEP 01` label in brand above an H5.
- Bullet lists in the capability matrix: 6px `rounded-full bg-brand-500` dot + mono text.

### Stat tile
`.stat-strip` of 3 tiles, brand tint, centered. Number in mono 700 26px `--brand-darker`
with unit (`17.1 MB`, `2.61 tok/s`); a short 12.5px plain-language label below.
Only use measured numbers; put comparisons/caveats in a `.tech-note` beneath.

### Data rows
`.map-row` (status pill + description) and `.task-row` (mono name + description + pill)
for lists that need scanning. Hairline between rows, no zebra striping except one
de-emphasized row (`.lowest` → `--panel`).

### Progress meter
`.meter` of equal 9px segments, 4px gap, radius 3: brand = built, amber = in progress,
`--line-soft` = planned. Always followed by a `.meter-legend` with counts.

### Avatars
48px `rounded-full`, brand tint, mono initials. No photos.

### Contact CTA (required on every page)
Centered brand-tint box: section label "Start a conversation" → H2 question → one
paragraph → primary button with `services@gnomons.com` and an arrow. The `mailto:` link
carries a page-specific subject, e.g. `?subject=Cyber%20Resilience%20Engineering%20Inquiry`.

### Footer & utilities
Landing footer: copyright line, two mono brand taglines, trademark disclaimer at 11px,
and the `日本語で読む` translate link. Subpages: top bar with `← gnomons.com` back link
(left) and `日本語で読む` button (right). Both use the same `translateToJapanese()`
helper (Google Translate, opens in a new tab with `noopener`).

### Video
16:9 `.video-wrap`, 10px radius, border + card shadow, `youtube-nocookie.com` embed,
`loading="lazy"`, `referrerpolicy="strict-origin-when-cross-origin"`.

---

## 8. Diagrams (inline SVG)

Diagrams are the site's main visual. Draw them by hand as inline SVG, styled by CSS
classes so they inherit the tokens.

- **Container:** `.diagram-box` (hero, ~300×180 viewBox) or `figure.arch-wrap` (full
  width, ~860 wide, `min-width:700–720px` with horizontal scroll on phones).
  Always include a `<figcaption>` in plain language.
- **Hero diagram:** two boxes (brand-tint "protected/input" left, panel "other/output"
  right), mono uppercase labels above, one connecting arrow; caption in mono with `·`
  separators.
- **Structure:** lanes/bands (`.band`: no fill, `--line` stroke, `rx=10`) with a mono
  uppercase `.band-label`; blocks inside (`rx=8`) with a bold Inter `.blk-title` and an
  8.5–9px `.blk-sub`. Hardware blocks use `.blk-hw` (panel fill) with mono titles.
- **Block states:** built `.blk-built` (brand soft + brand stroke), in progress
  `.blk-progress` (amber), extending `.blk-dim` (no fill, `#cbd5e1` stroke), planned
  `.blk-planned` (dashed `4 3`). Gates/shared resources: `.gate-fill` brand tint, mono
  uppercase label.
- **Flows:** 1.3px `#94a3b8` lines with the shared `#arrow` marker; small mono
  `.flow-label`s.
- **Accessibility:** `role="img"` and a full-sentence `aria-label` describing the flow.
- Always ship a legend when fills encode meaning.

---

## 9. Iconography

- Inline Heroicons-style outline SVGs: `viewBox="0 0 24 24"`, `fill="none"`,
  `stroke="currentColor"`, `stroke-width="2"`, round caps/joins. Sizes `w-4 h-4` in
  buttons, `w-5 h-5` in tiles, `w-6 h-6` for the menu toggle.
- Icons are functional (arrow, mail, copy, check, menu) — never decorative.
- Emoji are acceptable only as literal content (e.g. hand-gesture chips), with
  `aria-hidden="true"`.

---

## 10. Voice & content

- **Audience:** hardware product teams, Renesas partners and distributors, mostly in
  Japan and the wider APAC region. Write plain English that survives machine translation.
- **Tone:** precise, calm, confident without hype. Specific part numbers
  (`EK-RA8P1`, `Cortex-M85`, `Ethos-U55`) beat adjectives.
- **Structure each subpage as:** eyebrow → claim headline → one-paragraph hero →
  definition or "why it matters" → architecture → evidence (stats, status) → closing
  thought → CTA.
- Headings state the outcome ("Firmware that verifies itself before it ever runs");
  a `.why-line` or `.tech-note` carries the technical proof.
- **Confidentiality:** never name clients or products; keep the NDA note
  (`Client and product names are withheld…`) wherever case studies appear.
- **Trademarks:** keep the Renesas trademark disclaimer in the landing footer when
  Renesas is referenced.
- Recurring brand phrases: *Hardware-Aware Intelligence*, *Constrained-Silicon
  Specialists*, *Built with Cyber Resilience in Mind*, *Human-Centric*.

---

## 11. Accessibility

- Body text contrast: slate-600 on white (7.5:1) or better. Don't put `slate-400` on
  anything but fine print.
- Never encode status by color alone — pair with a text pill or legend label.
- Meaningful `alt` on logos; `aria-label` on icon-only buttons (menu, translate).
- Diagrams: `role="img"` + descriptive `aria-label`, plus a visible caption.
- Keep `html lang` accurate (`en`); mark Japanese passages with `lang="ja"` where practical.
- Respect the existing focus behavior of native links/buttons; don't remove outlines.

---

## 12. Page template & build conventions

- Plain static HTML, no build step. One self-contained file per page at the repo root,
  kebab-case name (`cyber-resilience-by-design.html`). Assets are referenced relatively.
- **Landing page** uses the Tailwind Play CDN with the `brand` color and font config in
  `<head>`. **Subpages** use a single `<style>` block with the `:root` tokens above.
  Reuse the token block verbatim when creating a new subpage.
- Every page must start with a complete document head:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Page Title — Gnomons</title>
  <meta name="description" content="One-sentence summary.">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
  <style>/* :root tokens + components */</style>
</head>
<body>
  <!-- back link + translate button, .wrap content, CTA -->
</body>
</html>
```

- Link new subpages from the landing page (e.g. from the matching case-study card) and
  list them in [README.md](README.md).
- Third-party requests are limited to Google Fonts, the Tailwind CDN, YouTube
  (nocookie) embeds, and Google Translate on demand. Don't add analytics or other
  scripts without a deliberate decision.

---

## 13. Known gaps (current pages vs. these guidelines)

None open. Resolved in the last pass:

- All subpages now start with the §12 document head (doctype, `lang`, viewport,
  description, favicon), so the 760px/680px breakpoints apply on phones.
- Radii converged on 6px buttons (`rounded-md`) and 10px cards/panels (`rounded-[10px]`).
- The landing vision panel uses `brand-700` with white text instead of off-palette
  emerald (`brand-700` rather than `brand-600` so 12px text clears 4.5:1 contrast);
  Inter 800 and JetBrains Mono 600/700 are now loaded.
- Landing eyebrows are `<p>` with the visible title as `<h2>`; `brand-200`/`brand-300`
  are defined in the Tailwind config so tag borders and card hover borders render.
- README lists every subpage.
