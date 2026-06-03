# Whisk & Honey — Product Landing Page

**DESN 368 / P4** | Abigail Nosov

A responsive product landing page for a bakery brand called Whisk & Honey, built from a Figma design using semantic HTML5 and CSS.

---

## Project Description

This landing page promotes a bakery's value proposition — fresh ingredients, bakery-inspired desserts, and quick aesthetic breakfast options. The design follows a warm, playful, and professional tone using a pink (#F2839A) primary palette on a cream (#FAF5EE) background. The page includes a hero section, embedded video, feature cards, a product menu data table, and a contact form.

---

## CSS Transform Used

**Hover lift effect** — Buttons (`.btn-primary`, `.btn-secondary`) and feature cards (`.features-grid article`) lift `4px` on hover/focus using `transform: translateY(-4px)` combined with a `box-shadow` transition for a smooth elevation effect.

---

## CSS Animation Used

**Hero fade-in** — All hero content (tagline, heading, paragraph, buttons, badges) fades in and slides up using the `hero-fade-in` keyframes (`opacity: 0 → 1`, `translateY(30px → 0)`). Each child element has a staggered delay (0.1s–0.7s) for a sequential reveal. Feature cards also use a separate `fade-slide-up` animation with staggered delays (0s, 0.15s, 0.3s).

Both animations are wrapped inside `@media (prefers-reduced-motion: no-preference)` to respect user accessibility preferences.

---

## Table Content Type

The data table (`#data-table`) displays a **product menu** with three columns:

| Column | Content | Source |
|---|---|---|
| **Item** | Menu item name | Figma design copy |
| **Description** | Brief item description | Figma design copy |
| **Price** | USD pricing | Figma design copy |

The table uses `<thead>` with `<th scope="col">` and `<tbody>` with five data rows: Butter Croissant ($4.50), Seasonal Pastry Box ($28.00), Honey Cake Slice ($6.75), Breakfast Cookie Pack ($12.00), and Custom Celebration Cake (From $65).

---

## Challenges Encountered

1. **Figma API image retrieval** — The Figma API returns signed S3 URLs with expiration. Downloaded images had to be re-fetched and saved locally. SVG icons from Figma used `clip-path` URL references that broke when loaded via `<img>` tags in some browsers, requiring manual SVG cleanup.

2. **Mobile navigation** — Implementing a hamburger toggle without JavaScript libraries required a clean, accessible approach using a small vanilla JS toggle with `aria-expanded` attributes.

3. **Design fidelity** — Translating Figma's absolute-positioned artboard layout (939px wide) into a responsive, fluid layout required careful use of `clamp()`, `min()`, and CSS Grid with `auto-fit` to maintain proportions across viewports.

4. **Missing video asset** — The Figma design only contains a video thumbnail image with a play-button overlay and timestamp, not an actual video file. A TODO is left in the HTML for the final MP4 upload.

---

## Key Learnings

- Extracting design tokens (colors, typography, spacing) from a Figma file via the REST API and translating them into CSS custom properties creates a maintainable, single-source-of-truth stylesheet.
- Mobile-first CSS with a single `@media (max-width: 767px)` breakpoint keeps the responsive logic simple and predictable.
- Semantic HTML5 elements (`<article>`, `<section>`, `<nav>`, `<header>`, `<footer>`, `<table>` with `<thead>`/`<tbody>`) provide meaningful structure without extra divs.
- Combining `:focus-visible` with custom `outline` styles ensures accessible keyboard navigation without cluttering mouse users' experience.
- CSS Grid (`grid-template-columns: repeat(auto-fit, minmax(260px, 1fr))`) handles responsive card layouts without media queries, while `overflow-x: auto` on table wrappers solves mobile scrolling cleanly.
