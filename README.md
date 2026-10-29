# Astrosurf shop catalog

The items sold in the Astrosurf in-game shop. The game downloads `catalog.json`
from this site at startup, so items published here reach players without an
app update.

## Adding an item

1. Add the file:
   - Rocket: `rockets/<name>.png`, pointing right, transparent background,
     cropped tight, at least 96 px on its longest side.
   - Music: `music/<name>.ogg` (Ogg Vorbis, loops), under 16 MB.
2. Add an entry to `items.json`: `id`, `type` (`rocket` or `music`), `name`,
   `price` in points, `file`, and optionally `trail_color` (`"#rrggbb"`) for rockets.
3. Rebuild the catalog and publish:
   ```sh
   python3 ~/orbit-hop/tools/make_catalog.py .
   git add -A && git commit -m "Add <item>" && git push
   ```

**Never rename or reuse an `id`.** Players own items by id. Removing an entry
hides the item from the shop, but players who bought it keep it, so leave its
file here.

`.nojekyll` stops GitHub Pages from processing the files.
