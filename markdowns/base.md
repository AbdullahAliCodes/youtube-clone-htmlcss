# YouTube Clone — Project Status (Base)

Summary of what has been built so far in this HTML/CSS YouTube clone.

---

## 1. What’s Done

### 1.1 Structure & layout
- Single-page layout: `index.html` (~968 lines), `style.css` (~475 lines), `responsive.css` (71 lines). No JavaScript.
- Semantic structure: `<nav>`, `<main>`, sidebar sections, scroll area, video grid, `<footer>`.

### 1.2 Top nav
- **Left:** Burger icon, YouTube logo (inline SVG with “YouTube” text), “ZA” region.
- **Center:** Search input + search button, mic button.
- **Right:** Dark/light toggle (checkbox + label), Create button, notifications bell, profile image.
- Sticky top bar (56px), flex layout.

### 1.3 Sidebars

**Large sidebar (240px):**
- Home, Shorts.
- Subscriptions with 8 channel avatars/names (PewDiePie, Mr Feast, Sidemen, Ali-A, Glarses, Linus Tech Tips, Dashy).
- You: History, Playlists, Watch later, Liked videos, Your videos, Downloads, Show more.
- Explore: Music, Gaming, News, Show more.
- More from YouTube: YouTube Studio, YouTube Music, YouTube Kids.
- Settings, Report history, Help, Send feedback.
- Footer: About, Press, Copyright, Contact us, Creators, Advertise, Developers; Terms, Privacy, Policy & Safety, How YouTube works, Test new features; © 2026 Google LLC.

**Small sidebar:**
- Shown only between 791px and 1312px (see responsive).
- Home, Shorts, Subscriptions, You — icon + label each.

### 1.4 Video feed
- Horizontal category strip with “All” (active) and many chips (Gaming, Podcasts, Cars, Toy Story 2, Software Development, AI, etc.), plus left/right arrow containers.
- **20 video cards** in a grid; each has:
  - Thumbnail (local `.avif`),
  - Channel avatar (local `.jpg`),
  - Title, channel name, views/date,
  - Three-dots menu icon.

### 1.5 Responsive breakpoints
- **1991px:** 3 columns; large sidebar.
- **1312px:** 3 columns; large sidebar hidden, small sidebar shown.
- **960px:** 2 columns.
- **791px:** 2 columns; both sidebars hidden.
- **603px:** 1 column (mobile-style).

### 1.6 Assets
- `resources/video-thumbnails/` — yt-thumbnail-1.avif through 20 (and any others present).
- `resources/channel-dps/` — channel-1-dp.jpg through 20, plus my-channel-dp.jpg.
- `resources/symbols/three-dots-vertical.svg`.
- All other UI icons are inline SVGs in the HTML.

### 1.7 Styling
- Fonts: Roboto, Noto.
- Light theme only.
- Search bar: pill-shaped, split input + button.
- Category chips: active (dark) vs inactive (light).
- Video cards: 16:9 thumbnails, rounded corners, two-line title clamp.
- Footer links with hover styling.

---

## 2. Known issues & gaps

### 2.1 Bugs
1. **style.css line 60:** `.search-area-middle { width: ; }` — invalid (empty value). Remove or set a valid value (e.g. `max-width` or a width).
2. **Left arrow SVG (index.html ~line 533):** Path is `d="M13.793 5.293 7.086 12l6.707..."`. Missing **L** (line-to): should be `M13.793 5.293 L7.086 12...` so the left arrow renders correctly.
3. **HTML class typo (index.html ~line 75):** `notifcations-icon` → should be `notifications-icon` to match CSS.
4. **Sidebar typo:** “Pewdipie” → “PewDiePie”.
5. **Video 10 title (index.html ~line 744):** “in time>” → “in time?”.

### 2.2 Dark mode
- `darkMode.css` exists but is **empty** and **not linked** in `index.html`.
- The nav toggle (#switch + label) has no styles and no script — it does nothing.
- To implement: add CSS variables + class on `<body>`, JS to toggle, and link `darkMode.css` (or remove the toggle).

### 2.3 Unused / redundant
- **Material Symbols:** Head includes `Material+Symbols+Outlined` with `icon_names=home`; the page uses only inline SVGs. Remove the link or use the font for icons.
- **Category arrows:** No JavaScript; the strip scrolls natively but the arrow buttons don’t control scroll.

### 2.4 Missing behavior (expected for HTML/CSS-only)
- No search submit or client-side search.
- No burger menu behavior (sidebar open/close).
- No navigation: video cards and footer links have no real `href` (or only `#`).
- No hover/focus styles for video cards or category chips (only footer link hover).

### 2.5 Accessibility & content
- Many thumbnails use the same alt text (“intro to agent skills”); each should describe the video.
- Three-dots icon uses `alt=""`; fine if decorative; add a proper label if it becomes interactive.

---

## 3. File layout

```
youtube-clone-htmlcss/
├── index.html
├── style.css
├── responsive.css
├── darkMode.css          (empty, not linked)
├── markdowns/
│   └── base.md           (this file)
└── resources/
    ├── video-thumbnails/ (e.g. yt-thumbnail-1.avif … 20)
    ├── channel-dps/      (e.g. channel-1-dp.jpg … 20, my-channel-dp.jpg)
    └── symbols/          (e.g. three-dots-vertical.svg)
```

---

## 4. Summary

Static, responsive YouTube home layout is in place: full nav, two sidebar variants, category strip, and 20-video grid with local assets and clear breakpoints. Remaining work: fix the listed CSS/SVG/typos, optionally implement (or remove) dark mode and clean unused assets; if adding JS later: search, burger menu, category-arrow scroll, and links for videos and footer.
