# Endless Runner 3D 🏃‍♂️

A browser-based, Temple Run–style endless runner built with **Flask**, **Three.js**, and **Bootstrap 5**. The player automatically sprints down a three-lane path, dodging rocks, trees, and bars while collecting coins — all rendered with Three.js primitives, no external 3D models required.

![Tech](https://img.shields.io/badge/Python-Flask-000000)
![Tech](https://img.shields.io/badge/3D-Three.js-black)
![Tech](https://img.shields.io/badge/UI-Bootstrap%205-7952B3)

## Features

- **3D endless world** — auto-scrolling ground tiles that recycle infinitely, with decorative roadside trees
- **Three-lane movement** — smooth lane switching with A/D or ←/→
- **Jumping** — gravity-based arc (W, ↑, or Space) to clear rocks and gaps
- **Sliding** — duck under low bars (S or ↓)
- **Obstacles** — rocks (jump), trees (must lane-change), bars (must slide), gaps (must jump); spawn patterns always leave one safe lane
- **Collectible coins** — spinning tori that add to score and coin count
- **Score system** — combines distance traveled and coins collected
- **Difficulty progression** — speed and obstacle spawn rate increase the further you run
- **Lives / health** — 3 lives, brief flashing invulnerability after a hit
- **High score** — persisted locally via `localStorage`
- **Dynamic environment** — sky, fog, and ground colors gradually cycle through four stages as you progress
- **Particle effects** — bursts on coin pickup and collisions
- **Third-person camera** — smoothly follows and leans with the player
- **Bootstrap HUD** — Score, Coins, Speed, High Score, Lives, Start/Pause/Restart, and on-screen mobile controls (Left, Right, Jump, Slide)
- **Fully responsive** — playable with keyboard on desktop or buttons on mobile/touch devices

## Project Structure

```
session2/
├── app.py                 # Flask server — serves the game
└── templates/
    └── index.html          # Game UI, HUD, and all Three.js game logic
```

## Requirements

- Python 3.7+
- Flask
- A modern browser with WebGL support (Chrome, Firefox, Edge, Safari)
- Internet connection (Bootstrap and Three.js are loaded via CDN)

## Installation & Setup

1. Clone or download the project folder so you have the structure shown above.
2. Navigate into the project directory:
   ```bash
   cd session2
   ```
3. Install Flask:
   ```bash
   pip install flask
   ```
4. Run the app:
   ```bash
   python app.py
   ```
5. Open your browser and go to:
   ```
   http://127.0.0.1:5000
   ```

## How to Play

| Action | Keyboard | On-Screen Button |
|---|---|---|
| Move Left | `A` or `←` | Left |
| Move Right | `D` or `→` | Right |
| Jump | `W`, `↑`, or `Space` | Jump |
| Slide | `S` or `↓` | Slide |

**Obstacle guide:**

| Obstacle | How to Avoid |
|---|---|
| 🪨 Rock | Jump over it |
| 🌲 Tree | Too tall to jump — switch lanes |
| 🟥 Bar | Slide underneath |
| ⬛ Gap | Jump across |

Click **Start Game** to begin, **Pause** to freeze the action, and **Restart** to reset your run at any time. When you run out of lives, the Game Over screen shows your final score, coins collected, and high score, with a **Play Again** button to go again.

## Tech Stack

- **Flask** — lightweight Python web server that renders `index.html` and serves static routes
- **Three.js (r128, via CDN)** — 3D scene, camera, lighting, geometries, materials, shadows, and animation loop
- **Bootstrap 5 (via CDN)** — HUD cards, buttons, overlays, and responsive layout (no custom CSS or `<style>` tags used)
- **Vanilla JavaScript** — all game logic (movement, collision detection, spawning, scoring, difficulty scaling) lives inline in `index.html`

## Customization Ideas

- Adjust `BASE_SPEED`, `MAX_SPEED`, and `SPAWN_Z` in the script to tune pacing and difficulty
- Add new obstacle types by extending the `spawnObstacle()` function
- Swap in different primitive shapes/colors for the player, coins, or scenery
- Add a `/highscores` API route in `app.py` if you want to persist scores server-side instead of (or alongside) `localStorage`

## Notes

- All 3D assets (player, obstacles, coins, trees, terrain) are built entirely from Three.js primitive geometries — no external `.glb`/`.fbx` model files are used.
- This is an original endless-runner implementation inspired by the general genre of "lane-based runner" games. It does not use any characters, artwork, logos, sounds, or other assets from Temple Run or any other copyrighted property.

## License

Free to use, modify, and extend for personal or educational purposes.
