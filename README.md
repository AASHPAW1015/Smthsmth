# Area Calculator

A personal, phone-friendly web app: look at satellite imagery, drop points, get the area.

- **Tap the map** to add corner points (point 1 is green). Drag a point to move it, tap a point to delete it.
- **🚶 Walk** tracks you with GPS while you walk around a parcel, recording a point every few metres.
  When you get back near where you started, the loop closes by itself and shows the area (or tap **⏹️ Stop**).
  GPS jitter is cleaned up into a few corner points you can drag to fine-tune. Built for long walks (30 min+):
  the screen is kept awake, GPS restarts itself if it goes quiet, the walk is saved after every point, and if the
  page gets closed you're asked to continue where you left off.
  Keep the app open on screen: browsers pause GPS when the screen is off or you switch apps.
- **📌 Mark** puts a point exactly where you stand, instantly. During a walk, tap it at every corner:
  marked corners are always kept, so straight sides come out perfectly straight.
- **Hold 📌 for a Precise Mark**: stand still while GPS is averaged for up to 30 s (readings that disagree are
  dropped). Typically improves a corner from about ±3–5 m to ±1–2 m. During a walk, recording pauses meanwhile.
- While walking, **GPS jumps** (readings that would mean moving faster than 4 m/s) are ignored and counted.
- Under the area you get a **± likely range** (95%), worked out from how precisely each corner is known.
- **☰ More → 📚 My places** keeps your parcels inside the app: open, rename, delete, update. Every finished
  walk is saved there automatically. The app asks Chrome to protect its storage (granted once it's on your home
  screen), and **Back up all places to a file** makes one file you can open here to restore everything.
- **☰ More → Save as a file** writes a `.geojson` file to Downloads (8-decimal lat/lng ≈ 1 mm, plus each point's
  GPS accuracy and marks). **Open a saved file** loads it back exactly. Also saves `.kml` for Google Earth, and
  opens `.gpx` tracks from GPS logger apps.
- **☰ More → ✂️ Divide into parts**: draw dividing lines across the parcel by tapping, with 📌 Mark (GPS), or by
  walking them with 🚶 Walk. Lines snap onto the boundary or onto another line (so you can make a "T").
  Each part gets a colour, a letter, its area and % of the total, and every side of every part shows its length.
  Parts and lines are saved in the .geojson/.kml files too.
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
