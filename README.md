# RelSim — Relativistic Universe Simulators

[![Deploy to GitHub Pages](https://github.com/tomusdrw/relsim/actions/workflows/deploy.yml/badge.svg)](https://github.com/tomusdrw/relsim/actions/workflows/deploy.yml)
[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-brightgreen)](https://todr.me/relsim/)

A collection of interactive WebGL simulations of space and relativity.

**👉 Live:** [https://todr.me/relsim/](https://todr.me/relsim/) — game-style launcher dispatching to the simulations below.

| Simulation | Page | Description |
|---|---|---|
| **Milky Way 3D** | [`milkyway.html`](https://todr.me/relsim/milkyway.html) | Interactive scale model of the Milky Way: spiral arms, bar, bulge, dust lanes, globular clusters, satellite galaxies and the Sun's neighborhood, with orbit/pan/zoom camera and a searchable catalog of ~60 known objects (with distances from Sol, fly-to locating, short descriptions and Wikipedia links). Selecting an object also shows a relativistic travel-time estimate (ship proper time vs. Earth time) with a max-speed slider (including a no-limit option) and configurable acceleration, flyby/landing mode, coasting fraction and ship mass (kinetic-energy estimate). |
| **Twin Paradox** | [`twin-paradox.html`](https://todr.me/relsim/twin-paradox.html) | Special relativity round-trip simulator demonstrating the twin paradox with light-signal propagation. |

## Twin Paradox — Special Relativity Simulator

An interactive WebGL visualization of special relativity, demonstrating the twin paradox with light-signal propagation.

- **Earth** (observer) at x=0 and a destination **Asteroid** at configurable distance (default: 10 light-years)
- Spaceship travels at constant speed (default 0.9c) to the asteroid and back
- **Two separate routes** (outbound and return) shown slightly offset for clarity
- **Four relativistic clocks**:
  - **Above Earth**: 
    - Earth local time (when the signal arrives)
    - Observed ship proper time (via light signals traveling at c)
  - **Above Spaceship**:
    - Ship proper time (local)
    - Observed Earth time (via light signals)
- **Click or drag** anywhere on the route lines to instantly place the spaceship at that event and update all clocks
- Real-time animation with play/pause
- Configurable distance and speed (with live γ factor)
- Clean cartoon-style graphics

## Controls

| Action              | Effect                              |
|---------------------|-------------------------------------|
| Click / Drag route  | Place ship at that position         |
| ▶ Play / ⏸ Pause    | Animate the round trip              |
| **Space**           | Toggle play/pause                   |
| **R**               | Reset to start                      |
| Distance slider     | Change trip length (1–100 ly)       |
| Speed slider        | Change velocity (0.05c – 0.999c)    |
| Turnaround / End    | Jump to key points in the journey   |

## Physics

All calculations use units where **c = 1** (distances in light-years, times in years).

- Coordinate time `t` is measured in the Earth rest frame.
- Ship proper time: `τ = t / γ`
- Light delay for observations:
  - Signal from ship at event `(t, x)` arrives at Earth at time `t + x`
  - Earth signal observed by ship at event `(t, x)` was emitted at time `t − x`

The visualization includes a **shadow spacecraft** showing the apparent position of the ship from Earth's perspective due to the finite speed of light.

## Running Locally

You can run the simulator in any modern browser:

```bash
# Option 1: Just open the file
open index.html

# Option 2: Use a local server (recommended)
python3 -m http.server 8000
# Then visit http://localhost:8000
```

No build step is required — each simulation is a single self-contained HTML file (Three.js is loaded from a CDN).

## Tech Stack

- Pure HTML + CSS + JavaScript
- [Three.js](https://threejs.org/) (r134) for WebGL rendering
- Canvas-generated cartoon-style sprites (no external image assets)
- GitHub Actions for automatic deployment to GitHub Pages

## Deployment

This project is automatically deployed to GitHub Pages using GitHub Actions whenever changes are pushed to `main`.

**Live site:** [https://todr.me/relsim/](https://todr.me/relsim/)

### Enabling GitHub Pages (for forks)

If you fork this repository:

1. Go to your fork → **Settings → Pages**
2. Under "Build and deployment", set **Source** to **GitHub Actions**
3. The included workflow (`.github/workflows/deploy.yml`) will handle the rest.

## Development

To contribute or experiment:

1. Clone the repo
2. Make changes to `index.html` (launcher), `twin-paradox.html` (relativity sim) or `milkyway.html` (galaxy sim)
3. Open locally or use a live server

Pull requests are welcome!

## License

MIT

---

Made to explore and visualize the beautiful counter-intuitive effects of special relativity. Enjoy the twin paradox! 🚀🌍
