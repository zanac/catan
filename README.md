# 🎲 Catan Web

A full web-based multiplayer implementation of Settlers of Catan, playable from any browser — no app required.

![Catan Web Screenshot](screenshot.png)

## Features

- **2–4 players** — each player joins from their own device
- **Admin view** — full board on desktop, manages the game
- **📱 Mobile** — each player scans a QR code and plays from their phone
- **💻 Web player** — join via link on PC or tablet, with turn management
- **📺 Spectator mode** — TV/projector view via `/spectator?pin=XXXXX`
- **Skin system** — Classic Catan skin with illustrated hex tiles and custom robber
- **Undo** — available during setup and main game
- **Languages** — EN, IT, FR, DE (auto-detected from browser)
- **PWA** — installable on mobile as a full-screen app

## Setup

```bash
npm install
node server/index.js
```

Open `http://localhost:3000` in your browser.

## How to play

1. Open the game on a desktop browser — this is the **Admin** view
2. Set player names and colors, choose skin and rules
3. Click **Start Game** — a PIN is generated
4. Each player scans the **QR code** (phone) or copies the **Web link** (PC/tablet)
5. Play!

## Skins

Place skin folders inside `skins/` — each with a `skin.json` manifest:

```
skins/
└── myskin/
    ├── skin.json
    ├── preview.png
    └── hex/
        ├── wood.png
        ├── brick.png
        ├── sheep.png
        ├── wheat.png
        ├── ore.png
        └── desert.png
```

`skin.json` example:
```json
{
  "id": "myskin",
  "name": "My Skin",
  "version": "1.0",
  "preview": "preview.png",
  "provides": ["hex", "robber"],
  "hex": {
    "wood":   "hex/wood.png",
    "brick":  "hex/brick.png",
    "sheep":  "hex/sheep.png",
    "wheat":  "hex/wheat.png",
    "ore":    "hex/ore.png",
    "desert": "hex/desert.png"
  },
  "robber": "robber.png"
}
```

## Debug mode

Open `/?debug=1` to show a debug panel in the setup screen.

Select which dev card type should always be the **first one drawn**:

| Button | Card |
|--------|------|
| 👑 Monopolio | Monopoly — steal all of one resource from everyone |
| ⚔️ Cavaliere | Knight — move robber |
| 🛤 Strade | Road Building — place 2 free roads |
| 🌻 Abbondanza | Year of Plenty — take any 2 resources |
| ⭐ Vittoria | Victory Point — instant +1 point |

A red banner `🐛 DEBUG: prima carta = ...` appears at the top of the admin screen confirming debug is active.

> Debug mode is invisible in normal play (`/?` without `debug=1`).

## Deploy

Tested on [Render](https://render.com) — set start command to `node server/index.js`.

Demo: [https://catan-vk1j.onrender.com](https://catan-vk1j.onrender.com)
