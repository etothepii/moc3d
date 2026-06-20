# Bermuda parcel 3D terrain — 19284

Interactive 3D render of The Mid Ocean Club and Golf Course (parcel 19284) with a 10.0 m buffer.
Orthophoto-draped DEM with contour lines and parcel boundaries. Pure static site:
no application server, no CDN, works on GitHub Pages from a project sub-path.

## View locally

This folder uses **relative paths only**, so always serve it over HTTP (not
`file://`). To catch GitHub-Pages sub-path bugs, serve the PARENT directory and
open the site under a sub-path:

    cd ..
    python3 -m http.server 8000
    # open http://localhost:8000/docs/

## Deploy to GitHub Pages

The folder IS the Pages site root. Pick one:

  (a) **Repo root** — push these files to the default branch, set Pages source to
      the branch root.
  (b) **/docs** — copy these files into a `docs/` folder, set Pages source to
      `/docs`.
  (c) **gh-pages branch** — push these files to a `gh-pages` branch.

The empty `.nojekyll` file stops Jekyll from mangling the upload. Relative paths
make every option work unchanged at `https://<user>.github.io/<repo>/`.

## Controls

* **Desktop:** drag to orbit, scroll to zoom, right-drag to pan.
* **iPhone / touch:** one finger to rotate, pinch to zoom, two fingers to pan.
* The **☰ menu** (top-left, closed by default) holds the vertical-exaggeration
  slider, layer toggles (imagery / contours / parcels / buildings) and reset view.
  Imagery is on by default; contours and parcels start off.
* Tap/click the terrain to read lon / lat / elevation and the parcel under it.

## Data files (`data/`)

* `dem.bin` / `dem.json` — float32 elevation grid (north-up) + metadata.
* `web_basemap.jpg` / `basemap.json` — 2019 orthophoto cropped to the study bbox.
* `parcels.geojson`, `contours.geojson`, `buildings.geojson` — vector overlays (EPSG:3857).
* `study_area.json` — manifest (parcel ids, names, zoning, acreage, bboxes, scale).

Regenerate with `generate_site.py` (idempotent).

## Copyright & permitted use

© Government of Bermuda. The parcel, contour, elevation and 2019 orthophoto data
shown here are derived from Government of Bermuda planning data and remain the
property of the Government of Bermuda. **This data must not be used for commercial
purposes.** Provided for reference/visualisation only, with no warranty as to
accuracy.
