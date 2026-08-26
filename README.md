# SINGLE SHOT — Descent of the Hollow Choir

A complete, self-contained **first-person 3D horror roguelike RPG** in a single HTML file.
No build step, no dependencies, no network requests — open `index.html` in any modern
browser (WebGL2) and play.

> Your revolver holds **one bullet**. The catacombs below are hungry, and the dark is
> not empty. Descend five floors, keep your flame alive, and end the Choir before it
> ends you. Every run is new. Death is final.

## How to run

```
open index.html
```

or

```
python3 -m http.server   # then visit http://localhost:8000
```

Requires a browser with **WebGL2** and pointer-lock support (Chrome, Edge, Firefox, Safari 15+).

## Controls

| Input | Action |
|-------|--------|
| `WASD` | Move |
| Mouse | Look |
| `LMB` | Fire (single shot) |
| `RMB` | Melee |
| `R` | Reload (slow) |
| `Shift` | Sprint (drains stamina) |
| `1 · 2 · 3` | Skills (Adrenaline · Hellfire · Mend) |
| `I` | Inventory |
| `C` | Character |
| `Esc / P` | Pause |

## The loop

- **Roguelike:** each floor is procedurally generated from a seeded RNG. Loot, level,
  descend. On Floor V the Choir waits — kill it to win.
- **RPG:** kills grant XP; level up to pick a **boon**. Equip weapons, armor, and rings
  with rarity tiers (Common → Mythic) and stat bonuses.
- **Horror:** your torch burns fuel. In darkness your **Sanity** erodes and the Choir
  grows bolder. The post pipeline distorts the screen as your mind frays.
- **Single-shot:** the revolver fires one round, then you reload — slowly. Positioning,
  timing, and nerve matter more than spray.

## Under the hood

Everything is hand-rolled in one file:

- **Renderer** — custom WebGL2 pipeline: dynamic point-light lighting (up to 12),
  distance fog, emissive materials, a procedural 8×8 texture atlas, a first-person
  viewmodel, and a post-processing chain (bright-pass → separable blur → composite with
  vignette, color grade, film grain, and sanity distortion).
- **Audio** — fully procedural Web Audio: ambient drone, heartbeat, gunshots, melee,
  enemy grunts, UI, boss roar, and reverb via a convolver. All synthesized at runtime.
- **Math** — a small column-major matrix library (perspective, lookAt, invert, multiply,
  translation, Euler, point transform).
- **RNG** — seeded `mulberry32` for deterministic runs; a separate FX RNG for cosmetics.
- **Noise** — Perlin / fbm2 / hash2 for procedural textures.

## Floors

I. The Threshold · II. The Drowned Halls · III. The Bone Gallery ·
IV. The Choir's Throat · V. The Hollow Choir

## Notes

- Single file, ~2,900 lines. No external assets, fonts, or libraries.
- Deterministic per seed; the seed is shown on the title screen.