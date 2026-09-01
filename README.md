# TerraMech

**Live: https://easyvibesuxui-sketch.github.io/minigame/**

Served by GitHub Pages from the root of `main`, so pushing `index.html` to
`main` updates the live site — there is no build step and no deploy workflow.
(Pages on this repository uses the legacy branch source; the Actions token is
not permitted to change that, so an Actions-based deploy would need the source
switched to "GitHub Actions" under Settings → Pages by hand.)

A single-file, dependency-free brand site for a **fictional** heavy equipment
company, built around a playable operator trial. The whole site is `index.html` —
open it in any modern browser, or let the Pages workflow serve it. No build step,
no external asset, no network call beyond the Google Fonts stylesheet.

TerraMech does not exist. Its history, machines, people and contact details were
invented for this concept.

## The idea

The site's progression *is* the company's history. Six pages of the TerraMech
record sit in the archive, sealed and redacted. Each one unseals at a salvage
total you can only reach by working the yard, so the brand story is earned
rather than scrolled past. Your best run persists in `localStorage`, so the
record stays open on the next visit.

## The trial

Steer the excavator bucket at the near end of a floodlit yard. The gantry throws
steel down the deck toward you — scoop every load, keep hazards out of the rig,
and hold the line into Night Shift, where the yard pays double.

| Area | Notes |
| --- | --- |
| Loop | `requestAnimationFrame` with clamped `deltaTime`; gameplay in metres, HUD scaled off a 720px reference height |
| Camera | Pin-hole projection solved from screen anchors, so the yard frames identically at any aspect ratio; the horizon sits far above the frame |
| Solids | Convex prisms with per-face culling, depth sorting, lambert shading, gradient faces and per-face warning striping |
| Grounding | Planar cast shadows projected down the light ray and collapsed to a convex-hull silhouette, plus contact darkening |
| Movement | Exponential-damped lerp on the bucket; residual velocity leans the scoop and smears its light pool |
| Waves | Sweepable z-staggered salvage runs, and hazard walls abreast with one gap holding a reward |
| Power-ups | Magnetic Field (5s steering pull), Titanium Frame (5s invincibility that smashes hazards) |
| Phases | Morning → Dusk → Night, driven by material salvaged or score, whichever leads |
| Post | Threshold-and-blur bloom refreshed on alternate frames, with a frame-budget watchdog that drops it on slow devices |

## Assets

The TM-7 elevation in the machine section is a generated flat-vector
illustration, cropped to the machine, remapped so its background is exactly the
page's black, quantised to a 48-colour palette and inlined as a data URI —
external image hosts are blocked by the Artifact CSP, so the page carries it.
`tm7-source.png` is the untouched render it came from; `tm7.png` is the
processed asset.

## Design system

Red, black, and the black-to-white ramp between them. Payload is brand red, the
rig wears it, hazards are black drums in white warning stripes, and the deck
runs graphite at the far end down to near-black under the bucket. Chakra Petch
for display and the in-canvas HUD, Barlow Condensed for stencil labels, Barlow
for running text.

Honours `prefers-reduced-motion`, holds the game when it scrolls out of view,
and lays out for portrait phones as well as desktop.
