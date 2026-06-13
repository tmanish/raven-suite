# Raven Suite

A family of six self‑contained, single‑file web apps — a privacy‑first, browser‑only office and design toolkit. Each app is one `.html` file with no build step, no server, no account, and no data ever leaving your device.

Every tool is designed as a familiar, capable alternative to a mainstream app, while being honest about the boundaries of what a browser can do with proprietary file formats.

---

## What's inside

| App | What it is | File | Docs |
|-----|------------|------|------|
| **Raven Write** | Rich‑text word processor | [`raven-write.html`](raven-write.html) | [docs](docs/raven-write.md) |
| **Raven PDF** | PDF viewer, editor & annotator | [`raven-pdf.html`](raven-pdf.html) | [docs](docs/raven-pdf.md) |
| **Raven Sheets** | Spreadsheet with a formula engine | [`raven-sheets.html`](raven-sheets.html) | [docs](docs/raven-sheets.md) |
| **Raven Slides** | Presentation editor | [`raven-slides.html`](raven-slides.html) | [docs](docs/raven-slides.md) |
| **Raven Email** | HTML‑to‑EML email builder | [`raven-email.html`](raven-email.html) | [docs](docs/raven-email.md) |
| **Raven Figgy** | Vector / UI design tool | [`raven-figgy.html`](raven-figgy.html) | [docs](docs/raven-figgy.md) |

**▶ Use them online.** Once GitHub Pages is enabled (see [Quick start](#quick-start)), the whole suite is live at **<https://tmanish.github.io/raven-suite/>**, and each tool opens directly in the browser:

| App | Open in your browser |
|-----|----------------------|
| Raven Write | https://tmanish.github.io/raven-suite/raven-write.html |
| Raven PDF | https://tmanish.github.io/raven-suite/raven-pdf.html |
| Raven Sheets | https://tmanish.github.io/raven-suite/raven-sheets.html |
| Raven Slides | https://tmanish.github.io/raven-suite/raven-slides.html |
| Raven Email | https://tmanish.github.io/raven-suite/raven-email.html |
| Raven Figgy | https://tmanish.github.io/raven-suite/raven-figgy.html |

*(These links assume the repository is named `raven-suite`. If you name it something else, change that part of the URL.)*

---

## Quick start

There is nothing to install.

1. Download the `.html` file for the tool you want.
2. Double‑click it, or open it in any modern browser (Chrome, Edge, Firefox, Safari).

To publish the whole suite as a website, drop the files onto any static host — GitHub Pages, Netlify, Vercel, Cloudflare Pages, or an S3 bucket. No server‑side code is required. When you enable GitHub Pages, the included `index.html` becomes the home page, with the six tools sitting alongside it.

> **First load needs internet.** Most apps pull their libraries (and, in two cases, web fonts) from public CDNs the first time they open. After that the browser caches them. For fully offline or air‑gapped use, see [Offline & self‑hosting](#offline--self-hosting).

---

## Design principles

- **Client‑side only.** All parsing, editing, rendering, and exporting happens in your browser. Your documents are never uploaded anywhere.
- **One file each.** Every app is a single HTML document with its CSS and JavaScript inline. Easy to read, audit, fork, host, or email to a colleague.
- **Familiar by design.** Keyboard shortcuts, panels, and toolbars follow the conventions of the apps people already know.
- **Honest about limits.** Where a proprietary binary format (`.fig`, `.msg`, true binary `.doc`) cannot be round‑tripped in a browser, the app says so plainly and offers the best open‑format path instead, rather than pretending.

---

## Technology (shared)

- Plain HTML, CSS, and JavaScript. No framework, no bundler, no build step.
- Rendering uses native browser primitives (`contenteditable`, Canvas, SVG, the DOM, and the CSS Object Model) plus a small number of well‑known open‑source libraries, loaded at runtime from public CDNs.
- Apple‑inspired "frosted glass" interface with a light and dark theme.

Per‑app libraries (all open source — see [License](#license)):

| App | Libraries (version) | CDN |
|-----|---------------------|-----|
| Raven Write | mammoth.js 1.6.0, html2pdf.js 0.10.1 | cdnjs |
| Raven PDF | pdf.js 3.11.174, pdf‑lib 1.17.1 | cdnjs |
| Raven Sheets | SheetJS (xlsx) 0.18.5 | cdnjs |
| Raven Slides | JSZip 3.10.1, PptxGenJS 3.12.0 | cdnjs |
| Raven Email | *(none — pure browser APIs)* | — |
| Raven Figgy | JSZip 3.10.1, polygon‑clipping 0.15.7 | cdnjs / jsDelivr |

Web fonts (Google Fonts): Raven Write loads Roboto, Open Sans, and DM Sans; Raven Figgy loads Inter and Roboto. The other apps use the system font stack.

---

## Security & privacy

This is the part that matters most for a tool people trust with their files.

- **No backend.** There is no server that receives your data. There are no accounts, no logins, no cookies, and no analytics or telemetry of any kind.
- **Your files stay on your machine.** Opening a document reads it locally through the browser's File API. Exports are generated in the browser and saved with a normal download. Nothing is transmitted.
- **The only network traffic is loading code.** On first open, the apps fetch their JavaScript libraries (and, for Write and Figgy, fonts) from public CDNs. Those CDNs see your IP address and which library you requested — exactly as they would for any website that uses a CDN — but never anything about your documents.
- **Raven Email is the most self‑contained:** it loads **no** external scripts or fonts at all. It only ever touches the network if you explicitly use its optional "download remote images" feature, which fetches the image URLs that you yourself put in the email.
- **No persistent local storage.** None of the apps write to `localStorage` or `IndexedDB`. Closing the tab clears in‑memory state, so **export your work to keep it.**
- **Treat untrusted documents with care.** Raven Write, Raven Email, and Raven Figgy render content you give them (HTML, email markup, SVG) inside your browser tab. As with any tool, only open files from sources you trust.

If you need a hard guarantee of zero outbound requests, self‑host the libraries (next section) and use the apps from `file://` or an offline host.

---

## Offline & self‑hosting

To run any app with no external dependencies:

1. Download the library files listed in [Technology](#technology-shared) (and the font CSS, if you want the exact typefaces).
2. Place them alongside the `.html` file.
3. Edit the `<script src="…">` and `<link href="…">` tags near the top of the HTML to point at your local copies instead of the CDN URLs.

Raven Email already works fully offline out of the box (apart from its optional remote‑image fetch).

---

## Compatibility & limitations (overview)

Each tool's docs list its specifics. The recurring theme is open vs. proprietary formats:

- **Open, well‑documented formats round‑trip well:** `.docx`, `.xlsx`, `.csv`, `.pptx`, `.svg`, `.eml`, `.pdf`, and each app's own native format.
- **Closed, undocumented binary formats are not faithfully supported**, by design and honesty:
  - **`.fig`** (Figma) — proprietary binary; Raven Figgy reads any embedded preview and uses **SVG** as the bridge to and from Figma. Its native `.figgy` (JSON) round‑trips perfectly.
  - **`.msg`** (Outlook) — proprietary binary; Raven Email produces `.eml`, which Outlook opens natively (then *Save As → .msg* inside Outlook).
  - **True binary `.doc`** — Raven Write's `.doc` export is HTML wrapped for Word compatibility, not the legacy binary format.

See each app's **Limitations** section for full detail.

---

## Repository layout

```
.
├── README.md            ← this file
├── LICENSE              ← GPL-3.0 (your code)
├── CONTRIBUTING.md      ← how to help
├── index.html           ← landing page (the home page on GitHub Pages)
├── raven-write.html
├── raven-pdf.html
├── raven-sheets.html
├── raven-slides.html
├── raven-email.html
├── raven-figgy.html
├── .github/
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.md
│       └── feature_request.md
└── docs/
    ├── raven-write.md
    ├── raven-pdf.md
    ├── raven-sheets.md
    ├── raven-slides.md
    ├── raven-email.md
    └── raven-figgy.md
```

You can keep the apps at the repo root (as above) or move them into an `apps/` folder — just update the links in this README and in `docs/` accordingly.

---

## Usage clause & disclaimer

- The software is provided **"as is", without warranty of any kind**, express or implied. See [LICENSE](LICENSE).
- **Verify important output.** These tools are convenient, not infallible. For anything that matters — legal documents, financial spreadsheets, client deliverables — check the result and keep your own backups. The authors are not liable for data loss or for errors in generated files.
- **You are responsible for the content you process** and for complying with the licenses and terms of any files, images, or fonts you import or distribute.
- **Trademarks.** Raven Suite is independent software and is **not affiliated with, authorized by, endorsed by, or connected to** Microsoft Corporation, Adobe Inc., Figma Inc., or Google LLC. "Word", "Excel", "PowerPoint", "Outlook", "Figma", and other product names are trademarks of their respective owners and are used here only descriptively, to indicate file‑format compatibility and feature intent.

---

## License

The original Raven Suite code is released under the **GNU General Public License v3.0 (GPL-3.0)** — see [LICENSE](LICENSE). You are free to use, modify, host, and redistribute it, but **any copy or modified version you distribute must also be released as open source under the GPL-3.0**. This is deliberate: it keeps every improvement available to the next person, so the tools stay free and open for everyone.

Copyright © 2026 \ Manish Todkari. *(Replace with your name. For GPL projects the copyright line lives here in the README; the `LICENSE` file holds the standard, unmodified license text.)*

The third‑party libraries and fonts the apps load remain under **their own licenses**. All of them (MIT, BSD, and Apache‑2.0) are compatible with the GPL-3.0, so there is no conflict in distributing the suite under GPL-3.0:

| Component | License (as commonly distributed) |
|-----------|-----------------------------------|
| pdf.js | Apache‑2.0 |
| pdf‑lib | MIT |
| mammoth.js | BSD‑2‑Clause |
| html2pdf.js | MIT |
| SheetJS (xlsx, community edition) | Apache‑2.0 |
| PptxGenJS | MIT |
| JSZip | MIT or GPL‑3.0 (dual) |
| polygon‑clipping | MIT |
| Inter | SIL Open Font License 1.1 |
| Roboto | Apache‑2.0 |
| Open Sans | SIL Open Font License 1.1 |
| DM Sans | SIL Open Font License 1.1 |

> These are the licenses at the time of writing. **Verify the current license of each dependency before redistributing**, as upstream projects and versions can change. If you self‑host the libraries, include their license files as required.

---

## Contributing

Issues and pull requests are welcome. Because each app is a single file, the workflow is simple: edit the HTML, open it in a browser to test, and submit. Please keep the "one file, client‑side only, honest about limits" principles intact.
