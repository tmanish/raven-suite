# Raven Slides

A presentation editor in a single HTML file — build slide decks, present full‑screen, and import/export real PowerPoint files, all in your browser.

→ Open the app: [`../raven-slides.html`](../raven-slides.html)

---

## Usage

Open `raven-slides.html`, add slides from the thumbnail rail, and build each slide with text boxes, shapes, and images. Press **F5** (or the present control) to run the deck full‑screen. Import an existing `.pptx` with the open control and export your deck as `.pptx`. **Export to keep your work.**

Common workflow:

- Add slides and pick a layout.
- Add text boxes (with formatting), shapes, and images; set backgrounds; adjust stacking order.
- Add speaker notes per slide.
- Reorder slides in the thumbnail rail.
- Present full‑screen with F5.
- Import or export `.pptx`.

## Features

- Slide thumbnail rail with reordering, plus five built‑in layouts.
- Text boxes with formatting, shapes, image insert, slide backgrounds, and z‑order (bring forward / send back).
- Per‑slide speaker notes.
- Undo / redo.
- Full‑screen Present mode (F5).
- Imports real `.pptx` decks and exports standard `.pptx`.
- Light and dark themes.

## Limitations

- **`.pptx` import covers common content** — text, basic shapes, images, and notes. Animations, slide transitions, embedded audio/video, SmartArt, charts, and complex master‑slide effects are not fully supported.
- **Export fidelity is bounded by the export library.** Decks are written through PptxGenJS, so exported files reflect its feature set; very elaborate visual effects may render differently in PowerPoint.
- No real‑time collaboration and no cross‑session autosave (export to save).

## Technology

- **PptxGenJS 3.12.0** — generates `.pptx` files for export.
- **JSZip 3.10.1** — unpacks the Office Open XML (`.pptx`) container on import.
- System font stack (no external fonts loaded).

## Security & privacy

- Fully client‑side. Decks you open are read locally and never uploaded; exports are produced in the browser and downloaded directly.
- No backend, accounts, cookies, telemetry, or analytics.
- The only network activity is loading the two libraries from a public CDN on first open. To run offline, vendor them locally and update the `<script>` tags.
- No `localStorage` is used.

## File support

| | Formats |
|---|---|
| **Open** | `.pptx` |
| **Export** | `.pptx` |

## License & usage clause

Original code: **GPL-3.0** (see the repository [`LICENSE`](../LICENSE)). PptxGenJS is MIT and JSZip is dual MIT/GPL‑3.0 (see the README license table). Provided **as is, without warranty**; verify imported and exported decks and keep backups. Not affiliated with or endorsed by Microsoft; "PowerPoint" is a trademark of Microsoft Corporation, used here only to describe compatibility.
