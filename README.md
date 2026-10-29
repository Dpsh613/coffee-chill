# Coffee &amp; Chill — Voxel Diorama

A single-file, real-time Three.js voxel diorama of a late-night lounge: a giant
latte, a phone-shaped stage with king-size media keys, a TV console, a poker
table, a cream sofa, a giraffe figurine, plants, candles and drifting fireflies.

**Live:** https://dpsh613.github.io/coffee-chill/

## What's in the box

- `index.html` — the whole experience (markup, CSS, Three.js scene, UI). No build step.
- `references/` — the photo/video references the scene was studied from.

## How it works

- **Voxel batching** — every prop is emitted as voxels into palette buckets
  (`matte`, `fabric`, `wood`, `gloss`, `metal`, `glow`, `glass`) and each bucket is
  drawn as a single `InstancedMesh`, so thousands of cubes cost a handful of draw calls.
- **Procedural everything** — textures (latte art, rug pattern, wood grain, TV logo,
  button glyphs) are painted onto `<canvas>` at runtime; nothing but the CDN module is fetched.
- **Deterministic detail** — a hash/PRNG pair gives stable colour jitter, plank
  variation and speckle across reloads.
- **Lighting** — ACES tone mapping, a warm key with soft shadows, a cool fill, plus
  flickering practical lights (candles, lamp, TV, PS5 LED) feeding an Unreal bloom pass.
- **Interaction** — orbit/zoom/pan, auto-spin stage, sliders for exposure/key/ambient
  glow/bloom/spin, toggles for spin, fireflies, shadows and wireframe, plus snapshot,
  fullscreen and hide-UI. Keys: `H` UI, `R` reset view.

Three.js r166 is loaded from jsDelivr via an import map, so the page is fully static
and can be served from any static host.

## Run locally

```bash
# any static server works
npx serve .
# then open the printed URL
```

Opening `index.html` directly from disk also works in most browsers, but a local
server is recommended for module loading.

## Deploy

Hosted with GitHub Pages from the `main` branch root — pushing to `main` publishes
the site.
