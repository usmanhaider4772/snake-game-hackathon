# 🐍 Snake Protocol

> A classic Snake game — reinvented for the hackathon era. Playable in any browser, zero dependencies, one file.

[![Play Now](https://img.shields.io/badge/▶%20Play%20Now-Live%20Demo-00ff88?style=for-the-badge&labelColor=070b16)](https://usmanhaider4772.github.io/snake-protocol)
[![License: MIT](https://img.shields.io/badge/License-MIT-00cfff?style=for-the-badge&labelColor=070b16)](#)
[![Single File](https://img.shields.io/badge/Single%20File-68KB-ff88ff?style=for-the-badge&labelColor=070b16)](#)
[![No Dependencies](https://img.shields.io/badge/Dependencies-Zero-ffcc00?style=for-the-badge&labelColor=070b16)](#)

---

## 🎮 Play It

**[→ Open snake-game.html in any browser](https://YOUR_USERNAME.github.io/snake-protocol)**

Or clone and open locally — no server, no install, no build step:

```bash
git clone https://github.com/YOUR_USERNAME/snake-protocol.git
open snake-protocol/snake-game.html
```

Works on desktop and mobile. Supports keyboard, touch d-pad, and swipe gestures.

---

## ✨ What Makes It Different

This started as a hackathon entry under the brief: *"make a classic game interesting — without making it look like a new game."*

### Core Innovations

| Feature | What it does |
|---|---|
| 🌀 **Galaxy Portals** | Spinning vortex portals with TTL timers — enter one, land somewhere random. Exit location is unknown. |
| 🚪 **Level Door System** | A glowing door appears on the map only after you hit the score threshold. Walk through it to level up — zero interruption. |
| ⭐ **Polymorphic Phishing** | A fake star that *looks* identical to the real `⭐ +5` item. Every 3 seconds it glitches to `💀` for 80ms. Eat it and your controls reverse or score halves. |
| 🏠 **Building Obstacles** | 10 named building footprint shapes (U-houses, towers, T-shapes, crosses) — structured, not random scatter. |
| 🌑 **Zero-Day Fog** | Canvas goes pitch black. Only a 3-tile radius glow around the snake's head is visible. |
| 👻 **Ghost Mode** | One free collision pass — through walls, obstacles, and self. |
| ⚡🐢 **Turbo / Slow** | Speed items that override the scheduler in real time with visual effects. |

### Progression System

- **10 levels** — each genuinely harder, not just faster
- **5 snake skins** — unlocked automatically at specific levels (Cobra at Lv2, Viper at Lv4, Phantom at Lv6, Inferno at Lv8)
- **3 difficulty modes** — Easy, Medium, Hard — tune speed, obstacles, portal frequency, poison weight, and fruit TTL
- **Score-gated door** — can't skip levels by rushing the door before you've earned it

### Visual Design

Fake 3D on Canvas 2D — no WebGL, no libraries:
- Beveled floor tiles (light/shadow edge per cell)
- Extruded obstacle blocks with top face + side face
- Specular highlights and rim lighting on every snake segment
- Floor shadow ellipses under the snake
- Smooth interpolated movement between grid steps

---

## 🕹️ Controls

| Platform | Control |
|---|---|
| Desktop | Arrow keys or WASD to steer, SPACE to pause |
| Mobile | On-screen d-pad or swipe anywhere on the canvas |

---

## 🍎 Item Reference

| Item | Score | Effect |
|---|---|---|
| 🍎 Apple | +1 | Grow |
| 🍌 Banana | +2 | Grow |
| 🍒 Cherry | +3 | Grow |
| ⭐ Star | +5 | Grow |
| 💀 Poison | -2 | Shrink by 2 |
| 💣 Bomb | -3 | Shrink by 3 |
| 👻 Ghost | 0 | One free collision pass |
| ⚡ Turbo | +1 | 4s speed boost (×3) |
| 🐢 Slow | 0 | 3s speed reduction |
| 🌑 Fog | +2 | 5s blackout fog |
| ⭐ Phish | 0 | Fake star — reverses controls or halves score |

All items have randomized TTL (6–14s) — they disappear and respawn elsewhere if not eaten.

---

## 🏗️ Architecture

Single HTML file, clean MVC structure, no build tooling:

```
config          — all constants (grid, levels, fruits, skins, difficulty)
SaveManager     — localStorage persistence (scores, unlocks, leaderboard, name)
Snake           — body, direction, ghost/turbo/slow/fog/reversed effects
FoodManager     — weighted random spawn, TTL expiry, level-scaled poison
ObstacleManager — building footprint templates, difficulty-scaled count
PortalManager   — TTL portals, unknown exit, respawn on use/expiry
ScoreManager    — score, level threshold, interval calc, difficulty-aware
Renderer        — Canvas 2D, full 3D illusion techniques, fog, effects
UI              — HUD, overlays, snake selector, game over screen
Game            — game loop, state machine, door/level logic
LandingPage     — animated intro, leaderboard, name input, bg canvas
Sound           — Web Audio API, 12 distinct sounds, pure oscillators
```

**Tech stack:** Vanilla JS ES6+ · HTML5 Canvas · Web Audio API · CSS3 · localStorage

---

## 📊 Analytics

This project uses [Umami](https://umami.is) for privacy-friendly, cookie-free analytics.

To add analytics to your own deployment:

1. Create a free account at [umami.is](https://umami.is) or self-host
2. Add a new website and copy your tracking script
3. Paste it into `snake-game.html` just before `</head>`:

```html
<script async src="https://analytics.umami.is/script.js" data-website-id="YOUR_WEBSITE_ID"></script>
```

Umami is GDPR-compliant, has no cookies, and doesn't share data with third parties. You can see page views, devices, countries, and referrers in a clean dashboard.

**Alternative:** [Plausible](https://plausible.io) works the same way — just swap the script tag.

---

## 🚀 Deploy to GitHub Pages

1. Fork or push to a GitHub repo
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)` folder
4. Your game is live at `https://YOUR_USERNAME.github.io/REPO_NAME`

For a custom domain, add a `CNAME` file with your domain and configure DNS.

---

## 🧑‍💻 Hackathon Context

Built under the constraint: *"make it interesting without making it look like a new game — and keep it small."*

The evaluation criteria were:
- **Recognizable** — must still feel like Snake at its core
- **Interesting** — features that reward skill and attention, not just reflexes
- **Compact** — single file, no framework, ships as a double-click

The phishing fruit was the standout mechanic — it exploits muscle memory and greed, forcing players to actually look at the board instead of playing on autopilot.

---

## 📄 License

MIT — do whatever you want with it.

---

<p align="center">
  <strong>🐍 Snake Protocol</strong> — Built at a hackathon · Open source · Zero dependencies
</p>
