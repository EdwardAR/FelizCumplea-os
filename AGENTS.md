# AGENTS.md

Static single-page HTML birthday greeting. No build system, no dependencies, no tests.

## Key files

- `index.html` — single HTML file with inline CSS and JS. This is the only source file.
- `vercel.json` — static deployment config (`cleanUrls: true`).
- `assets/images/Barbie.ico` — favicon / decorative image.
- `assets/images/fotoJhoy.png` — background portrait (overlaid via `body::before`) and card thumbnail.
- `assets/audio/happyBirthday.mp3` — background music (loop, starts on button click, volume 0.4).

## How to run

Open `index.html` in a browser directly. Deploy to Vercel with `vercel --prod` (no build step).

## Audio behavior

Audio does **not** autoplay. User clicks "🎵 Activar música" button (top-right) to start. Volume set to 0.4.

## Notable inline JS (in `index.html`)

- **Confetti**: 80 random pieces generated on load with CSS `confettiFall` animation (infinite loop).
- **Text bubbles**: `messages[]` array + `setInterval(createTextBubble, 500)` — uses `vw`/`vh` positioning with runtime bounds correction.
- **Fireworks**: Canvas-based particle system. Auto-fires 3 bursts on load, then random rockets on a timer.
- **Cake + candles**: Pure CSS cake with 5 candles. Click a candle to blow it out (smoke puff animation). When all 5 are out, a celebration message appears.
- **Mic blow detection**: Uses `getUserMedia` + `AnalyserNode` to detect blowing sounds. When loud noise (>55 avg) is detected, all candles blow out automatically. Gracefully degrades if mic permission is denied.
- **Audio toggle**: Button toggles play/pause instead of hiding — user can restart music after stopping.
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
