# Duskdot

A dark / light switch with a pixel-dot moon and sun. Tap it, or grab the knob and drag it across: the knob stretches as it moves and settles with a small bounce, the glow runs around the rim, the background follows the knob, and the dots of the icon loosen and regather into the other icon.

- Mouse, touch and pen use the same rules. The switch is also a keyboard control (Space or Enter).
- On a phone the page shows a column centred on the switch.

## Run locally

It is a static site with no build step. Serve the `public/` folder with any static file server, for example:

```
python3 -m http.server 8080 -d public
```

and open http://localhost:8080.

## Structure

```
public/
  index.html      page and the switch element
  credits.html    credits
  js/app.js       input, fixed-step clock (1/240 s), layout
  js/sim.js       simulation: state from input, no DOM
  js/render.js    WebGL2 renderer: background, track, knob, glow and icon dots
  js/core.js      clock, seeded PRNG, spring and low-pass integrators, pointer input
  data/           constants and image tables used by the renderer
```

Rendering is a pure function of the simulation state, and the simulation runs on a fixed step, so the same input always gives the same frames. `index.html?mode=capture` exposes `window.APP.renderAt(frame)` for frame-exact rendering of a given input log.

## Credits

Code, image tables and icon dots: original assets made for this page. No third-party fonts, libraries or sounds. See `public/credits.html`.
