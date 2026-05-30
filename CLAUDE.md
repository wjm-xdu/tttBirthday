# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A single-file birthday webpage (`birthday.html`) for the user's girlfriend. Pure HTML/CSS/JS with no build step, no framework, no dependencies (except optional Google Fonts). Red apple theme with warm, playful style.

## How to run

Open `birthday.html` directly in a browser. No server or build step needed.

## Key files

- `birthday.txt` — Original requirements/prompt
- `prompt.txt` — Additional prompt (currently empty)
- `birthday.html` — The complete webpage
- `birthdaymusic.mp3` — Background music (BGM)
- `bear.jpg` — Cartoon bear image used in the cake tab animation
- `backround(1).jpg` — Background for letter tab and cake tab
- `backround (2).jpg` — Background for love notes tab and candles+gift tab
- `backround (3).jpg` — Background for wish bottle tab

## Color theme

Red apple palette: `#C0392B` (dark red), `#E74C3C` (bright red), `#FF6B6B` (light red), `#27AE60` (green), `#2ECC71` (light green), `#F39C12` (golden), `#8B4513` (brown).

## Configurable variables (in `<script>` at top of `birthday.html`)

| Variable | Purpose |
|---|---|
| `LETTER_CONTENT` | Letter greeting, body paragraphs, signature, date |
| `LOVE_NOTES` | Array of `{icon, title, desc}` cards for the love notes tab |
| `GIFT_POOL` | Array of reward strings for the gift box |

## Architecture

Five tab sections via fixed bottom nav. Each tab has full-cover background image in `contain` mode (shows entire image, cream background fills letterboxed areas), with a light white overlay for readability:

1. **Envelope + Letter** (`#tab-letter`, bg: backround(1).jpg) — Click-to-open envelope with animated flap, sliding letter paper, apple seal wax
2. **Love Notes** (`#tab-notes`, bg: backround (2).jpg) — Card grid with click-to-expand modal. Editable: toggle edit mode to modify title/desc inline, delete cards, changes persist to localStorage
3. **Wish Bottle** (`#tab-bottle`, bg: backround (3).jpg) — Text input → DOM-based bottle float animation → localStorage-persisted collection
4. **Bear Cake** (`#tab-cake`, bg: backround(1).jpg) — Animated scene: bear.jpg image walks in from left carrying a cake emoji, bob animation, click anywhere to spawn hearts/apples, bear jumps on click
5. **Candles + Gift** (`#tab-candles-gift`, bg: backround (2).jpg) — CSS-drawn cake base with Web Audio API mic blow detection (click-to-extinguish fallback) + gift box with random reward draw and confetti particles

Global: falling apple particles (toggleable), BGM with play/pause toggle, opening animation overlay, responsive layout.
