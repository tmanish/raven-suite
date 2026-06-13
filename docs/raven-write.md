# Raven Write

A rich‑text word processor in a single HTML file — write, format, open, and export documents entirely in your browser.

→ Open the app: [`../raven-write.html`](../raven-write.html)

---

## Usage

Open `raven-write.html` in a browser and start typing on the page. Use the toolbar for formatting, the **File / Open** control to load an existing document, and **Export** to save your work in the format you need. Because nothing is stored permanently (see Security), **export before closing the tab** to keep your document.

Common workflow:

- Type or paste content directly onto the page.
- Format with the toolbar or standard shortcuts (⌘/Ctrl+B, I, U).
- Press ⌘/Ctrl+F for find & replace.
- Set the paper size and margins in **Page setup** before printing or exporting to PDF.
- Export to `.docx`‑friendly HTML, Markdown, plain text, or PDF, or print directly.

## Features

- Familiar formatting: bold, italic, underline, strikethrough, superscript/subscript, text colour, and highlight.
- Paragraph control: alignment (left/centre/right/justify), ordered and unordered lists, indent/outdent, line spacing, and paragraph styles (headings, quotes, body).
- Insert links, images, tables (with a grid picker), horizontal rules, page breaks, and the current date.
- Find & replace (⌘/Ctrl+F).
- Undo / redo, zoom (50–200%), and a live word / character / reading‑time count.
- Page setup: Letter, A4, Legal, A5, and Tabloid; portrait or landscape; adjustable margins — reflected live on the page and in print/PDF output.
- Smart paste (cleans up pasted formatting) and a spellcheck toggle.
- Light and dark themes.

## Limitations

- **`.docx` import is best‑effort.** Text, basic formatting, lists, tables, and images come through; tracked changes, comments, footnotes/endnotes, headers/footers, complex multi‑column layouts, and embedded objects may not.
- **`.doc` export is not the legacy binary format.** It produces HTML packaged so Microsoft Word opens it; it is not a true binary `.doc` file.
- **PDF export is render‑based.** Output is generated from the on‑screen layout, so very large documents export more slowly and pagination may differ slightly from the browser's own print dialog.
- Document layout is HTML‑based and will not be byte‑identical to Microsoft Word's layout engine.
- No real‑time collaboration and no cross‑session autosave (export to save).

## Technology

- Editing via the browser's native `contenteditable` rich‑text surface.
- **mammoth.js 1.6.0** — converts uploaded `.docx` files to HTML for editing.
- **html2pdf.js 0.10.1** — renders the document to PDF for export.
- Web fonts (Google Fonts): Roboto, Open Sans, DM Sans.

## Security & privacy

- Fully client‑side. Documents you open are read locally and never uploaded; exports are produced in the browser and downloaded directly.
- No backend, accounts, cookies, telemetry, or analytics.
- The only network activity is loading the two libraries and the fonts from public CDNs on first open. To run offline, vendor those files locally and update the `<script>`/`<link>` tags.
- No `localStorage` is used — closing the tab discards unsaved work.
- Pasted or imported HTML is rendered in your browser tab; only open content you trust.

## File support

| | Formats |
|---|---|
| **Open** | `.docx`, `.doc`*, `.html`, `.txt`, `.md` |
| **Export** | `.doc`* (Word‑compatible HTML), `.html`, `.md`, `.txt`, PDF, Print |

\* `.doc` here means HTML packaged for Word compatibility, not the legacy binary format.

## License & usage clause

Original code: **GPL-3.0** (see the repository [`LICENSE`](../LICENSE)). Bundled libraries and fonts keep their own licenses (see the README license table). Provided **as is, without warranty**; verify important output and keep backups. Not affiliated with or endorsed by Microsoft; "Word" and "Office" are trademarks of Microsoft Corporation, used here only to describe compatibility.
