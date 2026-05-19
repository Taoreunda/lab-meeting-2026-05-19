## Overview

Apple's web presence is a masterclass in **reverent product photography framed by near-invisible UI**. Every page is a stack of edge-to-edge product "tiles" — alternating light and dark canvases, each centered on a hero headline, a one-line tagline, two tiny blue pill CTAs, and an impossibly crisp product render. Nothing competes with the product. Typography is confident but quiet; color is either pure white, an off-white parchment, or a near-black tile; interactive elements are a single, quiet blue.

Density is unusually low even by contemporary SaaS standards. Each tile occupies roughly one viewport, and there is no decorative chrome — no borders, no gradients, no decorative frames, no shadows on headlines. Elevation appears only when a product image rests on a surface (a single soft `rgba(0, 0, 0, 0.22) 3px 5px 30px` drop for visual weight). The result is a catalog that feels more like a museum gallery: the wall disappears and the artifact takes over.

Store and shop surfaces retain the same chassis but switch modes. The product configurator (iPhone 17 Pro, accessories grid) introduces a tight grid of white utility cards at `{rounded.lg}` (18px) radius with a thin border, paired with a persistent thin sub-nav strip. The environment page leans darker and more editorial. Across all five surfaces the typographic system, spacing rhythm, and the single blue accent are consistent — this is one design language expressed at different volumes.

**Key Characteristics:**
- Photography-first presentation; UI recedes so the product can speak.
- Alternating full-bleed tile sections: white/parchment ↔ near-black, with the color change itself acting as the section divider.
- Single blue accent (`{colors.primary}` — #0066cc) carries every interactive element. No second brand color exists.
- Two button grammars: tiny blue pill CTAs (`{rounded.pill}`) and compact utility rects (`{rounded.sm}`).
- SF Pro Display + SF Pro Text — negative letter-spacing at display sizes for the signature "Apple tight" headline feel.
- Whisper-soft elevation used only when a product image needs to breathe — exactly one drop-shadow in the entire system.
- Tight two-row nav: slim `{component.global-nav}` + product-specific `{component.sub-nav-frosted}` with persistent right-aligned primary CTA.
- Section rhythm across multiple pages: light hero → dark product tile → light utility tile → dark tile → parchment footer — a predictable pulse.

## Colors

### Brand & Accent
- **Action Blue** (`{colors.primary}` — #0066cc): All text links, all blue pill CTAs, focus ring root.
- **Focus Blue** (`{colors.primary-focus}` — #0071e3): Keyboard focus ring on buttons.
- **Sky Link Blue** (`{colors.primary-on-dark}` — #2997ff): Brighter blue used on dark surfaces.

### Surface
- **Pure White** (`{colors.canvas}` — #ffffff)
- **Parchment** (`{colors.canvas-parchment}` — #f5f5f7)
- **Pearl Button** (`{colors.surface-pearl}` — #fafafc)
- **Near-Black Tile 1** (`{colors.surface-tile-1}` — #272729)
- **Near-Black Tile 2** (`{colors.surface-tile-2}` — #2a2a2c)
- **Near-Black Tile 3** (`{colors.surface-tile-3}` — #252527)
- **Pure Black** (`{colors.surface-black}` — #000000): video, global nav.
- **Translucent Chip Gray** (`{colors.surface-chip-translucent}` — #d2d2d7) at ~64% alpha.

### Text
- **Near-Black Ink** (`{colors.ink}` — #1d1d1f): All headlines, paragraphs, dark utility button fill.
- **Body On Dark** (#ffffff)
- **Body Muted** (#cccccc) on dark tiles
- **Ink Muted 80** (#333333) on Pearl Button surface
- **Ink Muted 48** (#7a7a7a) disabled / fine-print

### Hairlines
- **Divider Soft** (#f0f0f0 / `rgba(0,0,0,0.04)`)
- **Hairline** (#e0e0e0)

**No decorative gradients.** Depth comes from photography, not CSS gradients.

## Typography

### Font Family
- **Display**: `SF Pro Display, system-ui, -apple-system, sans-serif` (≥ 19px)
- **Body / UI**: `SF Pro Text, system-ui, -apple-system, sans-serif` (< 20px)

### Hierarchy

| Token | Size | Weight | Line Height | Letter Spacing |
|---|---|---|---|---|
| hero-display | 56px | 600 | 1.07 | -0.28px |
| display-lg | 40px | 600 | 1.10 | 0 |
| display-md | 34px | 600 | 1.47 | -0.374px |
| lead | 28px | 400 | 1.14 | 0.196px |
| lead-airy | 24px | 300 | 1.5 | 0 |
| tagline | 21px | 600 | 1.19 | 0.231px |
| body-strong | 17px | 600 | 1.24 | -0.374px |
| body | 17px | 400 | 1.47 | -0.374px |
| dense-link | 17px | 400 | 2.41 | 0 |
| caption | 14px | 400 | 1.43 | -0.224px |
| caption-strong | 14px | 600 | 1.29 | -0.224px |
| button-large | 18px | 300 | 1.0 | 0 |
| button-utility | 14px | 400 | 1.29 | -0.224px |
| fine-print | 12px | 400 | 1.0 | -0.12px |
| nav-link | 12px | 400 | 1.0 | -0.12px |

### Principles
- Negative letter-spacing at display sizes (-0.12 → -0.374px).
- Body copy at **17px, not 16px**.
- Weight ladder: 300 / 400 / 600 / 700. **500 is absent.**
- Headlines at weight 600 (not 700).
- Line-height: 1.07–1.19 (display) / 1.47 (body) / 2.41 (dense link lists).

## Layout

### Spacing System
- Base unit 8px. xxs 4 · xs 8 · sm 12 · md 17 · lg 24 · xl 32 · xxl 48 · section 80.
- Section vertical padding 80px; tiles stack edge-to-edge with 0 gap.
- Card padding 24px; button padding 8–11px × 15–22px.

### Grid & Container
- Text-heavy sections max ~980px; product grids max 1440px; product tiles full-bleed.
- Utility grids: 3–5 columns; tile heroes single column centered.
- Gutters 20–24px.

### Whitespace
Every tile begins with at least 64px of air above its headline and 48–64px below. Product renders are never crowded; ≥40px from nearest content.

## Elevation & Depth

| Level | Treatment | Use |
|---|---|---|
| Flat | No shadow, no border | Tiles, nav, footer |
| Soft hairline | 1px `rgba(0,0,0,0.08)` border | Utility cards, sub-nav |
| Backdrop blur | `backdrop-filter: blur(N)` | Sub-nav, floating sticky bar |
| Product shadow | `rgba(0,0,0,0.22) 3px 5px 30px` | **Product renders only** |

**Apple uses exactly ONE drop-shadow** — applied to product imagery, never to cards, buttons, or text.

## Shapes

| Token | Value | Use |
|---|---|---|
| none | 0 | Full-bleed tiles |
| xs | 5px | Inline chips (rare) |
| sm | 8px | Dark utility buttons, inline card imagery |
| md | 11px | White Pearl Button capsules |
| lg | 18px | Store utility cards, accessories grid |
| pill | 9999px | Primary blue pill CTAs, search input, sticky bar CTA |
| full | 50% / 9999px | Circular control chips |

## Components

### Top Navigation
- **global-nav** — 44px black bar pinned top; nav-link (12/400/-0.12) edge-to-edge.
- **sub-nav-frosted** — parchment 80% with backdrop-blur; height 52px; tagline (21/600) left; utility links + primary CTA right.

### Buttons
- **button-primary** — Action Blue bg, white text, pill, 11×22 padding; active = `transform: scale(0.95)`.
- **button-secondary-pill** — transparent bg, Action Blue text+border, pill.
- **button-dark-utility** — ink (#1d1d1f) bg, white text, 8px radius, 8×15 padding.
- **button-pearl-capsule** — Pearl bg, Ink Muted 80 text, 11px radius, 3px Divider Soft border.
- **button-store-hero** — Action Blue with button-large (18/300).
- **button-icon-circular** — 44×44, translucent chip bg ~64% alpha, ink icon.
- **text-link** — Action Blue inline links.
- **text-link-on-dark** — Sky Link Blue (#2997ff) for dark surfaces.

### Cards & Containers
- **product-tile-light** — white bg, ink text, 0 radius, 80px vertical padding; centered stack: name → tagline → 2 pill CTAs → product render with system shadow.
- **product-tile-parchment** — same on #f5f5f7.
- **product-tile-dark** — #272729 bg, white text, Sky Link Blue inline.
- **store-utility-card** — white bg, 1px Hairline border, 18px radius, 24px padding.
- **configurator-option-chip** — white bg, pill, 12×16 padding; selected = 2px Focus Blue border.
- **floating-sticky-bar** — parchment 80% + backdrop-blur, 64px height.

### Inputs
- **search-input** — white bg, ink text, body (17/400), 1px `rgba(0,0,0,0.08)` border, pill, 12×20 padding, 44px height.

### Footer
- parchment bg, Ink Muted 80 text; columns in dense-link (17/400/2.41); headings caption-strong (14/600); legal row fine-print (12/400) with Ink Muted 48.

## Do's and Don'ts

### Do
- Use Action Blue #0066cc for every interactive element. Single accent.
- Display sizes with negative letter-spacing (-0.28 → -0.374px).
- Body copy at 17px / 400 / 1.47 / -0.374px.
- Alternate light/parchment ↔ near-black tiles for section rhythm.
- Reserve pill for action-grammar elements (CTAs, search, chips).
- Apply product-shadow only on product renders.
- `transform: scale(0.95)` active state on all buttons.
- Keep global nav pure black.

### Don't
- Don't add a second accent color.
- Don't shadow cards, buttons, or text.
- Don't use decorative gradients.
- Don't use weight 500 anywhere.
- Don't round full-bleed tiles.
- Don't tighten body line-height below 1.47.
- Don't mix radii grammars.
- Don't use Sky Link Blue on light surfaces.

## Responsive Breakpoints
- ≤419 small phone · 420–640 phone · 641–735 large phone · 736–833 tablet portrait · 834–1023 tablet landscape · 1024–1068 small desktop · 1069–1440 desktop · ≥1441 wide desktop (locked at 1440).

## Iteration Notes
1. Focus on one component at a time.
2. Variants live as `-active`, `-focus`, `-2`, `-3`.
3. Always token refs; never inline hex.
4. Default + Active/Pressed only — no hover doc.
5. Display = SF Pro Display 600 with negative spacing. Body = SF Pro Text 400 / 17px. Unbreakable.
6. Single drop-shadow reserved for product photography only.
7. When in doubt about emphasis: alternate surface before adding chrome.
