<img src="src/assets/images/logo.png" width="96" alt="Oomio logo" />

# OOMIO

A modern, online home for the traditional Sinhala card game **Oomi**.

![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-Build-646CFF?logo=vite&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-Realtime%20DB-FFCA28?logo=firebase&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green)

---

## ✨ Features

- 🎮 **Play with AI** or with friends
- 👥 **Live multiplayer lobbies** — 2v2 teams, host controls (add bots, move/kick players), shareable room codes
- 🌐 **Sinhala & English** support, switchable anytime
- 📱 Responsive design — desktop and mobile
- ⚡ **Real-time sync** for lobbies and live gameplay, powered by Firebase
- 🃏 Faithful Oomi rules — 32-card deck, trump suits, trick-taking, team play

---

## 🃏 About the Game

Oomio is played with a 32-card deck — only **7, 8, 9, 10, Jack, Queen, King, and Ace** from each suit. Four players split into two teams of two, with partners seated across from each other.

Each round, one player picks the **trump suit** — the suit that beats all others for that round — and leads the first card. Every other player must follow the suit that was led if they're able to; if they can't, they may play any card, including a trump.

The highest card wins the trick: a trump always beats a non-trump, regardless of rank. If multiple trumps are played in the same trick, the higher trump wins. Whoever wins a trick leads the next one. Trump stays the same for the whole round, and the right to pick it rotates to the next player once a new round begins.

---

## 🛠 Tech Stack

| Layer | Tool |
|---|---|
| Frontend | React + Vite |
| Realtime data / multiplayer | Firebase Realtime Database |
| Hosting | Vercel |
| Backend | *None* — Firebase's client SDK talks directly to the database, no custom server |

---

## 📁 Project Structure

```text
oomio/
├── public/
│   ├── card-assets/        # Card back, suit art
│   └── sounds/              # SFX + background music
│
├── src/
│   ├── pages/                # Route-level screens (Home, Lobby, Game, ...)
│   ├── components/
│   │   ├── common/           # Button, Modal, Toggle, LanguageSwitcher, ...
│   │   ├── lobby/             # Team panels, player slots, lobby modals
│   │   └── game/              # Table, hand, cards, trump picker, ...
│   │
│   ├── game/                  # Pure game logic - no React, no Firebase
│   │   ├── engine/             # Game state + reducer
│   │   ├── rules/               # Legal moves, trick resolution, scoring
│   │   ├── cards/                # Deck building, shuffling, dealing
│   │   └── ai/                    # Bot decision-making
│   │
│   ├── firebase/               # Realtime Database service layer
│   │   ├── config.js
│   │   ├── lobbyService.js
│   │   ├── gameService.js
│   │   └── presenceService.js
│   │
│   ├── context/                # Language + other app-wide providers
│   ├── locales/                 # en.js / si.js translation strings
│   └── utils/                    # Small helpers (ids, room codes, storage)
│
├── firebase/
│   └── database.rules.json
├── .env.example
└── firebase.json
```

---

## 🚀 Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) 18+
- npm
- A [Firebase](https://console.firebase.google.com/) project with **Realtime Database** enabled

### Installation

```bash
git clone https://github.com/<your-username>/oomio.git
cd oomio
npm install
```

### Environment Variables

Copy `.env.example` to `.env` and fill in your Firebase project's web config (found in Firebase Console → Project Settings → your web app):

```bash
cp .env.example .env
```

```env
VITE_FIREBASE_API_KEY=
VITE_FIREBASE_AUTH_DOMAIN=
VITE_FIREBASE_DATABASE_URL=
VITE_FIREBASE_PROJECT_ID=
VITE_FIREBASE_STORAGE_BUCKET=
VITE_FIREBASE_MESSAGING_SENDER_ID=
VITE_FIREBASE_APP_ID=
```

> Firebase web API keys are meant to be public and safe to ship in client code — the real security boundary is the database rules below, not secrecy of this key.

### Run locally

```bash
npm run dev
```

---

## 🔥 Firebase Setup

1. Enable **Realtime Database** in your Firebase project.
2. Deploy the rules in `firebase/database.rules.json` — either via the Firebase CLI (`firebase deploy --only database`) or by pasting them into the console's Rules tab.
3. That's it — no Cloud Functions or additional backend required for the core game to run.

---

## 🌍 Deployment

The frontend deploys to **Vercel** like any Vite app — connect the repo and it builds automatically. Add the same `VITE_FIREBASE_*` variables in your Vercel project's Environment Variables settings. No separate backend deployment is needed; Firebase is the only other piece, and it's already hosted by Google.

---

## 🗺 Roadmap / Known Limitations

This project is under active development. A few things to know before relying on it:

- **AI bots** don't yet make live moves in an actual game — the decision logic exists, but isn't wired into gameplay yet.
- **Turn timer** can be configured per-lobby but isn't enforced yet (no auto-play on timeout).
- **Round/match win conditions** are a provisional default (most tricks wins the round) pending final confirmation of official Oomi scoring rules.
- **Database rules are currently open** (no authentication) — fine for development and testing, but should be hardened (e.g. with Firebase Anonymous Auth) before a public launch.
- Stale lobbies/games aren't automatically cleaned up yet.

---

## 🤝 Contributing

This is currently a solo project, but issues and pull requests are welcome if you'd like to help out — especially around the AI logic, additional language support, or UI polish.

---

## 📄 License

This project is licensed under the MIT License — see the `LICENSE` file for details. *(Replace this section if you choose a different license.)*

---

## 👤 Author

**Kavinda Hasaranga**
📧 kavindahasaranga2003@gmail.com
