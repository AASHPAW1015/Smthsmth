# Area Calculator

A personal, phone-friendly web app: look at satellite imagery, drop points, get the area.

- **Tap the map** to add corner points (point 1 is green). Drag a point to move it, tap a point to delete it.
- **📍 Add GPS pt** drops a point where you're standing, so you can walk a field's boundary.
- **🎯 Find me** centres the map on your location.
- **✋ / 🔒** stops taps from adding points so you can pan around safely.
- **Tap the big number** to switch units: acres, hectares, m², ft², km². Perimeter is shown too.
- A warning appears if lines cross, because the area would be wrong.
- Your points and map position are saved on the phone automatically.

Satellite imagery: Esri World Imagery (free, no API key). Map library: Leaflet 1.9.4 (bundled in `vendor/`).
Area is computed on the WGS84 sphere (same method as Leaflet.draw / OpenLayers), accurate to well under 1% for fields and lots.

## Put it on your phone

1. On GitHub: **Settings → Pages → Build and deployment → Source: Deploy from a branch**, choose this branch and `/ (root)`, then Save.
2. After a minute it's live at `https://<your-username>.github.io/<repo-name>/`.
3. Open that link in Chrome on Android, then **⋮ menu → Add to Home screen** (or **Install app**).
4. Allow location access when asked. GPS only works over https, which GitHub Pages provides.

## Run locally

Any static server works, e.g. `python3 -m http.server`, then open http://localhost:8000.
