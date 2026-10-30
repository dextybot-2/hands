# hands-detect-figer-motion

Browser demo: a wireframe figure hovers above your hand and is controlled with gestures.
Runs fully locally — MediaPipe Hand Landmarker + Three.js, no backend.

## Run

```bash
npm install   # also copies the MediaPipe wasm runtime and downloads the hand model into public/
npm run dev
```

Open the printed URL and allow camera access. `/?demo` drives the figure with a synthetic hand (no camera needed).

## Deploy to GitHub Pages

The included GitHub Actions workflow builds and deploys the site when code is pushed to the `main` branch. In the repository settings, set **Pages > Build and deployment > Source** to **GitHub Actions**. The first successful workflow run publishes the site at `https://<owner>.github.io/<repository>/`.

## Controls

- **Instagram** opens [@_akash._t](https://www.instagram.com/_akash._t/).
- **First hand in frame** is the lead: the figure hovers above it and follows it with a springy lag.
- **Number of raised fingers** sets the shape: 0 — cylinder, 1 — line, 2 — flat frame, 3 — triangular prism, 4 — cube, 5 — pentagonal prism.
- **Second hand** is the tool:
  - pinch or close the hand — shrink, open — grow;
  - fast index-finger flick — spin the figure (it keeps spinning by inertia);
  - twist the wrist — roll the figure in the screen plane;
  - quick movement also adds a gentle bank and brighter motion trail.

## Tuning

- Low-spec defaults request 640×480 camera input at 24 fps, cap the renderer at device pixel ratio 1, disable antialiasing, limit hand detection to about 15 updates per second, use five ghost layers, and cap motion blur at 3 px.
- `CFG` in `src/main.js` — follow spring, hover height, scale range, spin, blur.
- Constants at the top of `src/hands.js` — gesture thresholds.
