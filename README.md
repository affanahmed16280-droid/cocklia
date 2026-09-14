# Cochlea Cap — Marketing Website

Premium, cinematic, scroll-driven marketing website for **Cochlea Cap** — a directional haptic alert device giving deaf and hard-of-hearing individuals 360° situational awareness on the street, without surgery.

---

## Running Locally

```bash
# Any static file server works. Simplest options:

# Python (no install needed)
python -m http.server 8080

# Node.js (npx, no install needed)
npx serve .

# Then open:
# http://localhost:8080
```

> **Note:** The video background (`assets/video/hero-loop.mp4`) requires a server — `file://` URLs block video autoplay in most browsers. Always use a local server.

---

## File Structure

```
cocklia/
├── index.html          # Main marketing page (complete rewrite — dark theme)
├── login.html          # Auth page — Firebase login/signup (JS intact, dark restyled)
├── dashboard.html      # Live location + SOS dashboard (Firebase/Leaflet, unchanged)
│
├── css/
│   ├── marketing.css   # Dark design system for index.html
│   ├── auth-dark.css   # Dark overrides for login.html
│   └── style.css       # Original light theme (used only by dashboard.html)
│
├── assets/
│   ├── favicon.svg
│   ├── armband_device.png
│   ├── accessibility_gap.png
│   ├── sound_chart.png
│   └── video/
│       └── hero-loop.mp4   # Hero background video loop (3 MB)
```

---

## Tech Stack

| Concern | Technology |
|---|---|
| HTML/CSS/JS | Vanilla — no framework, no bundler |
| Smooth scroll | [Lenis v1.0.42](https://github.com/studio-freight/lenis) (CDN) |
| Scroll animation | [GSAP 3.12.5 + ScrollTrigger](https://greensock.com/scrolltrigger/) (CDN) |
| Typography | [Inter](https://fonts.google.com/specimen/Inter) (Google Fonts) |
| Auth backend | Firebase Auth + Firestore |
| Maps | Leaflet.js + OpenStreetMap |
| Hosting | Cloudflare Pages |

---

## Deploying to Cloudflare Pages

The project deploys automatically on every push to `main`:

```bash
git add .
git commit -m "your message"
git push origin main
```

Cloudflare Pages is connected to `https://github.com/affanahmed16280-droid/cocklia` and deploys from the repository root with **no build command** (pure static files). The live URL is:

👉 **[https://cochlecap.pages.dev](https://cochlecap.pages.dev)**

---

## Design System

| Token | Value |
|---|---|
| Background | `#0D0E11` (near-black charcoal) |
| Surface | `#141519` |
| Card | `#1C1D23` |
| **Accent (Amber)** | `#E8A04A` — used ONLY on CTAs, directional indicators, and stat highlights |
| Text primary | `#F0EDE8` |
| Text secondary | `#9B9A96` |

Accent amber appears exclusively on: CTA buttons, the active compass direction, stat numbers, the 95 dB threshold line on the chart, and the roadmap card underline on hover.

---

## Accessibility

- Full keyboard navigability with visible `outline: 2px solid #E8A04A` focus states
- Semantic HTML landmarks: `<nav>`, `<main>`, `<section>`, `<footer>` with `aria-label`
- Skip-to-content link at top of page
- WCAG AA contrast on all text/background combinations
- `prefers-reduced-motion`: all GSAP animations become instant; video is hidden
- All images have descriptive `alt` text
- No content conveyed by colour alone
- `aria-live="polite"` on the How It Works step panel

---

## Key Sections

1. **Hero** — Full-viewport, video background loop, headline + dual CTAs
2. **The Problem** — Animated stat counters (70M / 1 crore 23 lakh / 80%) on scroll-enter
3. **How It Works** — Pinned scroll sequence (desktop): 4 steps animate in sync with scroll, directional compass shows which vibrator fires
4. **Research** — SVG line chart that draws itself on scroll-enter; 3 research findings
5. **Progress** — 3 animated counters (3 models / 10 awards / 1 paper) + device gallery
6. **Roadmap** — 3 forward-looking cards (Companion App, Cap 4.0, Cap 5.0)
7. **Closing CTA** — Mission statement + dashboard link
8. **Footer** — Navigation anchors + copyright
