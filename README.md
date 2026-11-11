# Six Impossible Things

A ten-minute live show in six acts. Each act is one self-contained web page: no libraries, no images, no video, no build step. Everything on screen and everything you hear is computed in the browser tab as it runs.

| Act | Page | What it is |
|---|---|---|
| I. Crowd | `demos/crowd.html` | 100,000 particles that form any word, emoji or picture |
| II. Fluid | `demos/fluid.html` | Real-time fluid dynamics you stir by hand, in three looks |
| III. World | `demos/world.html` | A flight through procedural mountains, water and weather |
| IV. Galaxy | `demos/galaxy.html` | A million stars under gravity; collide two galaxies, then rewind time |
| V. Mind | `demos/mind.html` | 200 neural networks learn to drive a track you draw, then race you |
| VI. Sound | `demos/sound.html` | Music composed and synthesised live, that you can play along with |

`index.html` is the presenter hub: the programme, a ten-minute show clock, and a stage that runs one act at a time.

## Deploy on Vercel

It is a static site with nothing to install or build.

1. Import this repository in Vercel.
2. Leave **Framework Preset** as *Other* and the build, install and output settings empty (`vercel.json` already sets this).
3. Deploy. The hub is served at `/`, the acts at `/demos/<name>.html`.

Any other static host works the same way: serve the repository root.

## Run locally

```bash
python3 -m http.server 4173
```

Then open http://localhost:4173.

## Running the show

- **Begin the show** starts Act I and the clock. The clock counts down from 10:00; the acts are budgeted at 9:40.
- **Shift + →** next act, **Shift + ←** previous act, **Esc** back to the programme. A clicker's **Page Down** / **Page Up** also work.
- The small bar at the top of the stage does the same by mouse, and has a full-screen button.
- **presenter cues** on the programme page shows what to do in each act.
- A link ending in `#crowd`, `#fluid`, `#world`, `#galaxy`, `#mind` or `#sound` opens straight into that act.

## Requirements

- A current desktop browser with WebGL 2 (Chrome, Edge, Safari or Firefox). Acts II, III and IV also need floating-point render targets, which every recent desktop GPU provides.
- Act VI plays sound, and browsers only allow that after a click, so it starts with a "tap to begin" button.
- The hub loads one web font (Instrument Serif) from Google Fonts and falls back to a system serif offline. The acts load nothing external.
- Act III adjusts its rendering resolution to the machine to keep the frame rate up. Act IV halves its star count on machines that cannot keep up, and starts with 300,000 stars on phones.
