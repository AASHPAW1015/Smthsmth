# Area Calculator

A personal, phone-friendly web app: look at satellite imagery, drop points, get the area.

- **Tap the map** to add corner points (point 1 is green). Drag a point to move it, tap a point to delete it.
- **🚶 Walk** tracks you with GPS while you walk around a parcel, recording a point every few metres.
  When you get back near where you started, the loop closes by itself and shows the area (or tap **⏹️ Stop**).
  GPS jitter is cleaned up into a few corner points you can drag to fine-tune.
  Keep the screen on and the app open while walking: browsers pause GPS when the screen is off.
- **📍 GPS pt** drops a single point where you're standing.
- Each side's **length is shown along the line** (feet with acres/ft², metres otherwise).
- When zoomed in close, an **overview map** appears top-right with a red box showing where you are. Tap it to jump.
- **🎯 Find me** centres the map on your location.
- **✋ / 🔒** stops taps from adding points so you can pan around safely.
- **Tap the big number** to switch units: acres, hectares, m², ft², km². Perimeter is shown too.
- A warning appears if lines cross, because the area would be wrong.
- Your points and map position are saved on the phone automatically.

Satellite imagery: Esri World Imagery (free, no API key). Map library: Leaflet 1.9.4 (bundled in `vendor/`).
Area is computed with the WGS84 ellipsoid's local radius (spherical excess), matching the exact ellipsoidal area to ~0.01% for field- and farm-sized shapes. In practice your accuracy is limited by how precisely you place points, not the math.

## Put it on your phone

1. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, choose this branch and `/ (root)`, then Save.
2. After a minute it's live at `https://<your-username>.github.io/<repo-name>/`.
3. Open that link in Chrome on Android, then **⋮ menu → Add to Home screen** (or **Install app**).
4. Allow location access when asked. GPS only works over https, which GitHub Pages provides.

## Run locally

Any static server works, e.g. `python3 -m http.server`, then open http://localhost:8000.
