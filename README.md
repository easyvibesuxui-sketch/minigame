# TerraMech — Catch & Clear

A single-file, dependency-free promotional arcade game for the fictional heavy
equipment brand **TerraMech**. Open `terramech.html` in any modern browser, or
publish it as a Claude Artifact — there is no build step and no external asset.

**The shift:** you work the bucket at the near end of a floodlit yard. The
gantry throws steel down the deck toward you — scoop every load, keep hazards
out of the rig. Streaks raise the multiplier, power-ups bend the rules, and the
yard rolls over from Morning Shift to Night Shift, where throws come faster and
every load pays double. The final screen grades the run from Rookie to
TerraMech Master.

The playfield is a real 3-D scene rendered by hand into a 2-D canvas: no WebGL,
no library. World coordinates are metres, and the camera is solved from the
composition — you state where the catch line and the far gantry should land on
screen and the view derives the focal length, horizon and camera height, so the
yard frames identically at any aspect ratio.

| Area | Notes |
| --- | --- |
| Loop | `requestAnimationFrame` with clamped `deltaTime`; gameplay in metres, HUD scaled off a 720px reference height |
| Camera | Pin-hole projection solved from screen anchors; ground converges on an off-frame horizon, scale falls off as 1/depth |
| Solids | Every piece is a convex prism (n-gon swept along an axis) with per-face culling, depth sorting and lambert shading |
| Movement | Exponential-damped lerp on the bucket; residual velocity leans the scoop and smears its light pool |
| Items | Accelerating approach down the yard with yaw/pitch tumble, a contact shadow, and a landing marker on the catch line |
| Power-ups | Magnetic Field (5s steering pull on materials), Titanium Frame (5s invincibility that smashes hazards) |
| Phases | Morning → Dusk → Night, driven by material salvaged or score, whichever is further along |
| VFX | Particle engine (sparks, debris, shockwaves, dust), decaying screen shake, canvas text popups, additive neon rails and flood bloom |
| Input | Pointer, touch, and arrow/WASD keys; `P` pauses, `M` toggles sound |

Honours `prefers-reduced-motion`, persists best score and sound preference to
`localStorage`, and lays out for portrait phones as well as desktop.
