# SpinOut Prototype (SPINA)

Minimal demo of a retro-styled "crash" multiplier racing game built as a single HTML file for local development and experimentation.

## Overview
- Single-file prototype: `spin_a_ver4.html`
- Canvas-based visuals, mock players, deterministic round outcomes (provably-fair demo with server seed + client seed).
- Simple UI: lock bets, auto-cashout, double-down, manual cashout, background music and engine sound stubs.

## Features
- Deterministic crash multiplier per round using SHA-256 (serverSeed + clientSeed + nonce).
- Mock players with varied risk profiles placing bets and auto-cashing out.
- Player controls: Lock Bet, Cash Out, Double Down, Auto Cashout toggle, Music controls.
- Simple background-music support (place an MP3 in `assets/bg_music.mp3`).
- Leaderboard & session log; demo bankrolls for mock players and the local player.

## Files
- `spin_a_ver4.html` — main prototype (UI, game logic, rendering).
- `assets/bg_music.mp3` — optional background music (create `assets/` folder).

## Quick start (local)
1. Ensure you are in project folder:
   - c:\Users\user-pc\Desktop\SPINA
2. Serve the directory (recommended to avoid some browser audio restrictions):
   - Windows / PowerShell: `python -m http.server 8000`
   - or with Node: `npx serve .`
3. Open browser to: `http://localhost:8000/spin_a_ver4.html`

Alternatively, open `spin_a_ver4.html` directly in the browser (some audio features may require a local server / user gesture).

## Important UI IDs (for quick dev)
- `betInput`, `placeBetBtn` — lock/unlock a bet
- `startRoundBtn` — shows countdown / start
- `cashoutBtn` — cash out during running round
- `doubleDownBtn` — double the bet pre-round
- `autoCashoutToggle`, `autoInput` — auto cashout toggle and target
- `musicToggle`, `musicVol` — background music controls
- `multiplierDisplay`, `roundId`, `state`, `balance`, `currentBet`
- `serverSeedHash`, `clientSeedInput`, `nonce` — provably-fair display
- `log` — session log
- `racersContainer` — mock racers list

## Configuration & Constants
- Starting player balance: `state.balance` (default R10,000).
- Max demo rounds: `state.maxMockRounds`.
- Round countdown: `state.roundStartDelay` (ms).
- Music file path: `BG_MUSIC_SRC` in the script — change if needed.

## Troubleshooting
- Audio autoplay: browsers block audio until a user gesture. Click any UI button (Music toggle or Lock Bet) to enable music/AudioContext.
- If cashout or buttons appear disabled, ensure a bet is locked (`Lock Bet`) before the round starts.
- To debug, open DevTools Console — the game writes helpful logs into the in-page session log as well.

## Dev notes
- Core functions: `startRoundImpl()`, `finalizeRound()`, `cashout()`, `computeRoundHash()`.
- Seed generation uses `crypto.subtle.digest('SHA-256')` — supported in modern browsers.
- Replace the simple audio stubs with a WebAudio graph if you need richer mixing or multiple tracks.

## License
MIT — feel free to reuse or modify for learning and prototyping.
