# Chrono-Heist: The Glass Vault

**Play it live: https://diorwachira.github.io/ChronoHeist/**

A 3D stealth-puzzle heist that runs in the browser. Every guard, camera, laser and bulkhead in the vault follows one 24-second loop. You can rewind, fast-forward and freeze that loop, and leave recordings of yourself behind to hold doors open.

The whole game is one file, `index.html`. Geometry, textures, shaders, animation and sound are all generated in code. The only thing loaded from outside is Three.js, from the jsDelivr CDN.

## How to play

Steal the crystal from the vault core and reach the extraction pad without filling the detection meter.

- **Stage 1 · The Atrium Perimeter.** Learn the loop: a patrolling sentry, a sweeping camera, a rotating laser and a bulkhead that only opens in two windows of the loop.
- **Stage 2 · The Prism Chamber.** The vault door needs two pressure plates held at once. Walk to a plate, anchor that run as a Ghost Echo, do the same for the other plate, then slip through while both echoes hold the door.

**Ghost Echoes.** Pressing `R` saves everything you just did, rewinds the loop to 0.00 and replays it as a hologram. Echoes press plates and cut laser beams, and guards cannot see them. You can keep two; a third replaces the oldest.

## Controls

| Action | Key |
| --- | --- |
| Move | `W` `A` `S` `D` |
| Dash, hold to sprint | `Shift` |
| Jump (clears low beams) | `F` |
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

The same list is in the game, in the **Director & Shader Inspector** panel at the top right. That panel also switches stage, time scale, camera mode, bloom and audio.

## Reading the timeline

The bar along the bottom shows the 24-second loop.

- **THREAT** marks when the spot you are standing on is covered by a vision cone or a laser.
- **GATE** shows when the timed bulkhead is open (Stage 1). In Stage 2 this row shows which plates are held.
- **LIVE** is your current run.
- **ECHO 1 / ECHO 2** show each recording and where it stops and holds position.

## Run it locally

Open `index.html` in a browser. It needs an internet connection the first time, to fetch Three.js.

## Built with

- [Three.js](https://threejs.org/) r160 (ES modules via CDN), with its bloom and output post-processing passes
- Custom GLSL for the vision cones, laser beams, Ghost Echo holograms and the rewind effect
- The Web Audio API for all music and sound effects
