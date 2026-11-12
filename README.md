# Chrono-Heist: The Glass Vault

**Play it live: https://diorwachira.github.io/ChronoHeist/**

A 3D stealth-puzzle heist that runs in the browser. Every guard, camera, laser, shutter and gondola in the vault follows one 24-second loop. You can rewind, fast-forward and freeze that loop, and leave recordings of yourself behind to hold doors open.

The whole game is one file, `index.html`. Geometry, textures, shaders, animation and sound are all generated in code. The only thing loaded from outside is Three.js, from the jsDelivr CDN.

## The six stages

Steal the crystal from the vault core and reach the extraction pad without filling the detection meter. Each wing has its own colour, floor shader and lighting.

| # | Stage | Wing | What it teaches |
| --- | --- | --- | --- |
| 1 | The Atrium Perimeter | Cool Cyan Atrium | Reading the loop: a timed bulkhead, a sentry, a camera, a rotating laser. |
| 2 | The Prism Chamber | Cool Cyan Atrium | Two Ghost Echoes hold two pressure plates while you slip through the vault door. |
| 3 | The Pendulum Gallery | Emerald Gallery | Gondolas over an abyss. An echo rides one to an island switch that turns a mirror prism, sending a relay beam into a receptor that drops the barrier. |
| 4 | The Chronos Foundry | Amber Foundry | A two-shutter airlock that only slow-mo and Focus can clear, a crossfire room where an echo's body casts a safe shadow, and drones that emit pulse rings. |
| 5 | The Temporal Rift | Violet Chrono-Lab | Amber fields that ignore your rewind. Rewinding shifts the laser core inside against the watchtower outside until a gap opens. |
| 6 | The Grand Glass Sanctum | Crimson Sanctum | A three-node lock that both echoes and you must step on in the same instant, then a Lockdown sprint as laser walls close. |

Every stage can be picked from the Stage Select bar in the inspector. Clearing one awards a rating (Phantom, Master Thief or Operative) based on your run clock and how many echoes you used; the best rating per stage is saved in the browser.

## Core ideas

**Ghost Echoes.** Pressing `R` saves everything you just did, rewinds the loop to 0.00 and replays it as a hologram. Echoes press plates, ride gondolas and cut laser beams, and guards cannot see them. You can keep two; a third replaces the oldest.

**Focus.** In 0.25× slow-mo the world slows more than you do, for as long as the Focus gauge lasts. It refills at normal speed.

**Lasers are lethal.** A red beam fills the meter the moment it touches you. Low beams and pulse rings can be jumped. Beams in the wing's own colour are harmless signal relays.

**Rift phase (Stage 5).** Inside an amber field, time keeps running forward while you rewind everything else. The HUD shows the phase offset, and the timeline shows a second, amber playhead for the field's clock.

## Controls

| Action | Key |
| --- | --- |
| Move | `W` `A` `S` `D` |
| Dash, hold to sprint | `Shift` |
| Jump (low beams, pulse rings, gaps) | `F` |
| Rewind time | hold `Q` or `←` |
| Fast-forward time | hold `E` or `→` |
| Freeze time and orbit the camera | `Space` |
| Slow-mo / normal / freeze | `1` `2` `3` |
| Anchor a Ghost Echo | `R` |
| Restart the stage | `Backspace` |
| Free-orbit camera / wireframes | `O` / `V` |
| Mute / legend | `M` / `H` |
| Scrub the loop | drag the timeline |
| Orbit / zoom | drag / mouse wheel |

The same list is in the game, in the **Director & Shader Inspector** panel at the top right. That panel also holds the stage select bar and switches time scale, camera mode, bloom and audio.

## Reading the timeline

The bar along the bottom shows the 24-second loop.

- **THREAT** marks when the spot you are standing on is covered by a vision cone, a pulse ring or a laser.
- **GATE / NODES** shows when timed doors and shutters are open, or which plates, receptors and locks are live.
- **LIVE** is your current run.
- **ECHO 1 / ECHO 2** show each recording, where it stops and holds position, and a white tick wherever it steps onto a plate or node.

## Run it locally

Open `index.html` in a browser. It needs an internet connection the first time, to fetch Three.js.

## Built with

- [Three.js](https://threejs.org/) r160 (ES modules via CDN), with its bloom and output post-processing passes
- Custom GLSL for the vision cones, laser beams, glass, floor accents, conduits, static fields, Ghost Echo holograms and the time-scrub distortion
- The Web Audio API for all music and sound effects
