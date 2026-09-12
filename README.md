# keema-data

Food database releases for the Keema iPhone app. The app checks
`releases/latest/download/manifest.json` about once a week over Wi-Fi and
downloads `keema.db.sealed` when the manifest's `dataVersion` is newer than
the file it has. Nothing is uploaded; nothing about the phone is recorded
here beyond what GitHub logs for any download.

## What is in the file

- **USDA FoodData Central** — Foundation, SR Legacy, FNDDS and the Branded
  tier. Public domain (CC0). https://fdc.nal.usda.gov
- **Restaurant figures** copied from each chain's own published nutrition
  document. Every such row carries the document's URL. Figures are checked
  against each other (4·protein + 4·carb + 9·fat against printed calories,
  parts not exceeding wholes) before they are included; rows that fail are
  left out.

No Open Food Facts data is included; the app queries it live instead.

## Files per release

| File | What |
|---|---|
| `keema.db.sealed` | SQLite database with an FTS5 index, gzipped and sealed for the app |
| `manifest.json` | `dataVersion`, `schemaVersion`, SHA-256, size, food count |

The build scripts live with the app's source.

## Terms

For the app's use only. The file is sealed and opens only inside the app. See LICENSE.md. The USDA portion is public domain; the
compilation is not.
