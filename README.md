# TerraMech — Catch & Clear

A single-file, dependency-free promotional arcade game for the fictional heavy
equipment brand **TerraMech**. Open `terramech.html` in any modern browser, or
publish it as a Claude Artifact — there is no build step and no external asset.

**The shift:** steer the excavator bucket, salvage falling steel, keep hazards
out of the rig. Streaks raise the multiplier, power-ups bend the rules, and the
site rolls over from Morning Shift to Night Shift, where drops come faster and
every load pays double. The final screen grades the run from Rookie to
TerraMech Master.

| Area | Notes |
| --- | --- |
| Loop | `requestAnimationFrame` with clamped `deltaTime`; all gameplay scales off a 720px reference height |
| Movement | Exponential-damped lerp on the bucket, with residual velocity driving tilt and drag streaks |
| Items | Gravity acceleration, angular velocity, and a mouth-band collision test on the bucket rim |
| Power-ups | Magnetic Field (5s steering pull on materials), Titanium Frame (5s invincibility that smashes hazards) |
| Phases | Morning → Dusk → Night, driven by material salvaged or score, whichever is further along |
| VFX | Particle engine (sparks, debris, shockwaves, dust), decaying screen shake, canvas text popups, three-layer parallax |
| Input | Pointer, touch, and arrow/WASD keys; `P` pauses, `M` toggles sound |

Honours `prefers-reduced-motion`, persists best score and sound preference to
`localStorage`, and lays out for portrait phones as well as desktop.
