# AGENTS.md

Static single-page HTML birthday greeting. No build system, no dependencies, no tests.

## Key files

- `index.html` — single HTML file with inline CSS and JS. This is the only source file.
- `vercel.json` — static deployment config (`cleanUrls: true`).
- `Barbie.ico` — favicon / decorative image.
- `fotoJhoy.png` — background portrait (overlaid via `body::before`) and card thumbnail.
- `happyBirthday.mp3` — background music (loop, starts on button click, volume 0.4).

## How to run

Open `index.html` in a browser directly. Deploy to Vercel with `vercel --prod` (no build step).

## Audio behavior

Audio does **not** autoplay. User clicks "🎵 Activar música" button (top-right) to start. Volume set to 0.4.

## Notable inline JS (in `index.html`)

- **Confetti**: 80 random pieces generated on load with CSS `confettiFall` animation (infinite loop).
- **Text bubbles**: `messages[]` array + `setInterval(createTextBubble, 500)` — uses `vw`/`vh` positioning with runtime bounds correction.
- All JS is inline; no external JS files.

## Styling

- Google Fonts: Dancing Script (headings) + Poppins (body).
- Glassmorphism card (`backdrop-filter: blur(16px)`) with entrance animation.
- Background: pink hearts from Freepik CDN, overlaid with `fotoJhoy.png` at 65% opacity + zoom animation.
- Bootstrap 5.3.6 CSS from CDN (jsdelivr).
- Responsive breakpoints at 768px, 480px, and 360px.
- `.barbie-icon` spins 360° continuously; `.photo-thumb` is a circular crop of `fotoJhoy.png`.
- Photo overlay switches to `background-size: cover` on mobile for better framing.
- `body` allows vertical scroll (`overflow-y: auto`) so content is reachable on short screens.
- iOS Safari `background-attachment: fixed` quirk handled via `@supports (-webkit-touch-callout: none)`.
- Confetti count halves on mobile (<480px: 40 pieces); bubble interval slows (900ms vs 500ms) to reduce clutter.
