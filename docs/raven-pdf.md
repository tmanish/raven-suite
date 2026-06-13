# Raven PDF

A PDF studio in a single HTML file — view, reorganise, annotate, and export PDFs entirely in your browser.

→ Open the app: [`../raven-pdf.html`](../raven-pdf.html)

---

## Usage

Open `raven-pdf.html`, then drag a PDF in or use the open control. Pages appear as thumbnails on one side and a full view on the other. Pick a tool from the toolbar to annotate, use the thumbnail rail to reorganise pages, and export a new PDF with your changes baked in.

Common workflow:

- Open one or more PDFs (open a second to merge it in).
- Reorder, rotate, delete, or extract pages from the thumbnail rail (drag to reorder).
- Annotate: highlight, draw, add shapes, text, or images, or white‑out regions.
- Search text, and zoom to read (50–300% plus fit‑to‑width).
- Export a flattened PDF — annotations are written into the file.

## Features

- Open, merge, split, and save PDFs.
- Page operations: reorder (drag), rotate, delete, and extract, with a live thumbnail rail.
- Annotation tools: select, highlight, pen/freehand, rectangle, text, image, white‑out / redact, and eraser, each with a colour palette.
- Annotations are positioned in true PDF page coordinates, so they stay correct through rotation.
- Text search, zoom (50–300%) and fit‑to‑width, lazy page rendering for responsiveness, and undo.
- Export bakes all annotations into a standard PDF.
- Light and dark themes.

## Limitations

- **"Edit text" is white‑out‑and‑overlay, not true content editing.** You cover existing text and place new text on top; the original text stream is not re‑flowed or replaced.
- **No OCR.** Scanned/image‑only PDFs display as images; their text is not made searchable or selectable.
- **No interactive form filling** (AcroForm field editing) and no digital‑signature workflow.
- Very large or high‑resolution PDFs are bounded by your browser's available memory.
- Exported annotations are flattened into the page content.

## Technology

- **pdf.js 3.11.174** — parses and renders PDF pages to the screen.
- **pdf‑lib 1.17.1** — modifies the document and writes annotations into the exported PDF.
- Rendering uses HTML Canvas with annotation overlays in native PDF coordinate space.
- System font stack (no external fonts loaded).

## Security & privacy

- Fully client‑side. PDFs are read locally and never uploaded; the exported PDF is generated in the browser and downloaded directly.
- No backend, accounts, cookies, telemetry, or analytics.
- The only network activity is loading the two libraries from a public CDN on first open. To run offline, vendor them locally and update the `<script>` tags.
- No `localStorage` is used.

## File support

| | Formats |
|---|---|
| **Open / merge** | `.pdf` |
| **Export** | `.pdf` (with annotations flattened in); single‑page extract to `.pdf` |

## License & usage clause

Original code: **GPL-3.0** (see the repository [`LICENSE`](../LICENSE)). Bundled libraries keep their own licenses — pdf.js is Apache‑2.0, pdf‑lib is MIT (see the README license table). Provided **as is, without warranty**; verify important output and keep backups, especially before redacting or flattening. Not affiliated with or endorsed by Adobe; "PDF" is an open ISO 32000 standard and "Acrobat" is a trademark of Adobe Inc.
