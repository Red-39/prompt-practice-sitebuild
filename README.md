# Enterprise System Portal

A multi-stage UI/UX prank disguised as a corporate login portal. Built as a fun experiment in dark patterns and frustrating user flows.

## Demo

The experience walks users through four increasingly absurd stages before revealing the joke:

1. **The Reverse Loading Bar** — A progress bar that fills up to 98%... then reverses back to zero.
2. **The Runaway Button** — A "Click to Continue" button that dodges the cursor on hover and changes its label each time, requiring 7 near-misses before it finally lets you click it.
3. **The Absurdist EULA** — A scrollable terms-of-service agreement full of ridiculous clauses (waiving rights to your Tupperware, acknowledging that "The Cloud" is a server named Steve, etc.) with an honest accept button: *"I didn't read this, but I accept anyway."*
4. **The Hydra Pop-ups** — Shaking system warning dialogs that multiply every time you close one (closing 1 spawns 3 more), until you've closed 5 total and the prank is complete.

A confetti celebration reveals the joke at the end.

## Tech Stack

- Vanilla HTML, CSS, and JavaScript — no build tools required
- [Tailwind CSS](https://tailwindcss.com/) (CDN) for styling
- [canvas-confetti](https://github.com/catdad/canvas-confetti) for the celebration reveal

## Getting Started

No installation needed. Just open `index.html` in a browser.

```bash
# If you have a local server (e.g. VS Code Live Server, Python, etc.)
python3 -m http.server 8080
# Then visit http://localhost:8080
```

Or simply double-click `index.html` — it runs entirely client-side.

## Project Structure

```
/
├── index.html      # Everything: markup, styles, and scripts in one file
└── favicon.png     # (Optional) browser tab icon
```

## Stage Breakdown

| Stage | Mechanic | Key JS |
|-------|----------|--------|
| 1 | Reverse loading bar | `setInterval` incrementing/decrementing a progress value |
| 2 | Runaway button | `mouseenter` repositions the button with `transform: translate()` |
| 3 | Absurdist EULA | Static scrollable text with an honest accept button |
| 4 | Hydra pop-ups | Each `close` handler spawns 3 new popups; exits at 5 total closures |
| 5 | Reveal | `canvas-confetti` burst + congratulations message |

## Customization

- **Loading messages** — Edit the `forwardMsgs` / `backwardMsgs` arrays in the Stage 1 script block.
- **EULA clauses** — Add or edit `<p>` tags inside the scrollable `div` in Stage 3.
- **Pop-up warnings** — Edit the `systemWarnings` array in the Stage 4 script block.
- **Pop-up hydra threshold** — Change the `closedCount >= 5` check to require more or fewer closes before the reveal.
- **Button escape count** — Change the `jumpCount < 7` and `jumpCount >= 7` checks in Stage 2.
