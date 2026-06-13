# Raven Sheets

A spreadsheet in a single HTML file — enter data, write formulas, style cells, and open/export real spreadsheet files, all in your browser.

→ Open the app: [`../raven-sheets.html`](../raven-sheets.html)

---

## Usage

Open `raven-sheets.html` and work in the grid. Type values or `=formulas` into cells, use the toolbar to style and structure, and add sheets with the tabs at the bottom. Open existing spreadsheets with the open control and export with the export control. **Export to keep your work**, since nothing is stored permanently.

Common workflow:

- Enter data or formulas (start a formula with `=`).
- Insert/delete rows and columns, resize columns, and sort ranges.
- Style cells (fonts, colours, alignment, number presentation).
- Use multiple sheets via the tabs.
- Copy/paste to and from other apps as TSV.
- Open `.xlsx`/`.csv`, or export `.xlsx`/`.csv`.

## Features

- Grid of 60 rows × 26 columns per sheet, with multi‑sheet tabs.
- A formula engine with roughly 35 functions, a recursive‑descent parser, and circular‑reference detection.
- Cell styling, insert/delete of rows and columns (with reference remapping), column resizing, and range sort.
- Undo / redo and TSV copy/paste (interoperates with Excel, Google Sheets, etc.).
- Open and export common spreadsheet formats.
- Light and dark themes.

## Limitations

- **A practical subset of Excel's functions** (~35 common ones), not the full library.
- **No charts and no pivot tables.**
- Advanced features such as array/spill formulas, named ranges, data validation, and conditional formatting are limited or unavailable.
- On import, values and supported formulas come through; complex workbook formatting, macros (VBA), and unusual function calls may not survive the round trip.
- The grid is a fixed size per sheet and is intended for everyday spreadsheets rather than very large datasets.

## Technology

- **SheetJS (xlsx) 0.18.5** — reads and writes `.xlsx`/`.xls`/`.csv`/`.tsv`.
- A custom in‑app formula parser/evaluator (recursive descent, with dependency and cycle handling).
- System font stack (no external fonts loaded).

## Security & privacy

- Fully client‑side. Spreadsheets you open are read locally and never uploaded; exports are produced in the browser and downloaded directly.
- No backend, accounts, cookies, telemetry, or analytics.
- The only network activity is loading the SheetJS library from a public CDN on first open. To run offline, vendor it locally and update the `<script>` tag.
- No `localStorage` is used.

## File support

| | Formats |
|---|---|
| **Open** | `.xlsx`, `.xls`, `.csv`, `.tsv` |
| **Export** | `.xlsx`, `.csv` |

## License & usage clause

Original code: **GPL-3.0** (see the repository [`LICENSE`](../LICENSE)). SheetJS (community edition) is distributed under Apache‑2.0 (see the README license table). Provided **as is, without warranty**; verify calculations and keep backups before relying on any spreadsheet for decisions. Not affiliated with or endorsed by Microsoft; "Excel" is a trademark of Microsoft Corporation, used here only to describe compatibility.
