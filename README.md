# Byproduct Summary

A phone-friendly PWA for browsing DM nutrient analysis of distillers grains (WDGS) and corn gluten feed (WCGF) samples, aggregated by plant.

## Use

Five filters, applied in order:

1. **Byproduct Type** — WDGS or WCGF (required, no blended view across types)
2. **Year**
3. **Date Range** — narrows within the selected year
4. **State**
5. **Specific Plant**

The table shows sample count and mean of each nutrient (DM basis) for every plant matching the current filters, plus a Grand Total row. Column headers and the Plant column stay fixed in place while scrolling.

Feedyard and Sample ID are never included in the underlying data — not just hidden from view.

## Updating the data

The dataset is a static JSON array embedded directly in `index.html`. There is no backend and no database. To update it:

1. Regenerate the JSON from the source spreadsheet (`Data` sheet), applying the same cleaning steps used previously: canonicalize plant names to `City, ST`, resolve any new naming inconsistencies, exclude Feedyard/Sample ID/Acid Fat, derive State from the Plant field.
2. Replace the `const DATA = [...]` array in `index.html` with the new JSON.

## Files

- `index.html` — the app (markup, styles, logic, and data all in one file)
- `manifest.json` — PWA manifest
- `sw.js` — service worker (offline caching of the app shell)
- `apple-touch-icon.png`, `apple-touch-icon-precomposed.png` — iOS home screen icon (must stay at repo root)
- `favicon.ico` — browser tab icon
- `icons/` — additional icon sizes referenced by the manifest

## Installing on iPhone

Open `index.html` via the GitHub Pages URL in Safari, tap Share, then "Add to Home Screen."

## License

MIT — see `LICENSE`.
