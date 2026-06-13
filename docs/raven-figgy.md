# Raven Figgy

A vector and UI design tool in a single HTML file — an infinite canvas with frames, components, auto layout, boolean operations, and clickable prototypes, all running in your browser.

→ Open the app: [`../raven-figgy.html`](../raven-figgy.html)

---

## Usage

Open `raven-figgy.html`. It launches with a small demo (two linked phone screens) so you can explore immediately. Pick a tool from the top toolbar, draw on the canvas, and edit properties in the right‑hand panel. Use the left panel for pages and the layer tree. **Save a `.figgy` file to keep your work** — closing the tab discards unsaved state.

Common workflow:

- Draw frames (screens) and shapes; add text and images.
- Arrange with move/resize/rotate, snapping, alignment, and auto layout.
- Organise in the layers tree; group, create components, reuse instances.
- Link frames with click → navigate interactions.
- Press **Present** to click through your flows, or export a self‑contained prototype.
- Save/open the native `.figgy` format; export SVG or PNG.

## Features

**Canvas & tools**
- Infinite, pannable, zoomable canvas with fit‑to‑content.
- Tools: frame, rectangle, ellipse, line, polygon, star, pen, text, image, plus move and hand.
- Select, multi‑select, and marquee; move, resize, and rotate with snapping and smart guides.
- Drag a layer into a frame to re‑parent it automatically.

**Layers & structure**
- Layer tree with reorder, show/hide, lock, rename, and group/ungroup.
- Multiple pages.

**Styling (design panel)**
- Position, size, rotation, and corner radius.
- Fills (solid and linear gradient), strokes, opacity.
- Effects: drop shadow, inner shadow, and layer blur.
- Full text properties (family, size, weight, line height, letter spacing, alignment, colour).

**Layout & composition**
- **Auto layout** — see below.
- Alignment, distribution, and "tidy up" grid arrangement.
- Constraints (pin/scale on frame resize) for layers in non‑auto‑layout frames.
- Components and instances, with detach.
- Boolean operations: union, subtract, intersect, exclude (and flatten).

**Prototyping**
- Click → navigate interactions between frames, with instant or dissolve transitions.
- Present mode to click through flows in‑app.
- Export a **self‑contained interactive prototype** as a standalone `.html` file.

**Files & general**
- Save / open the native **`.figgy`** format (JSON; round‑trips perfectly).
- Export SVG and PNG.
- Undo / redo, copy / paste / duplicate, and a full set of keyboard shortcuts.
- Light and dark themes.

### Auto layout

Auto layout behaves like the equivalent feature in mainstream design tools:

- **Direction** — horizontal or vertical, and it nests (an auto‑layout frame inside another lays out its own children too).
- **Alignment** — a 3×3 grid controls packing along the flow (start / centre / end) and alignment across it; the grid re‑maps correctly when you flip direction.
- **Space between** — distribute items edge‑to‑edge (toggle it, or type `auto` in the gap field).
- **Padding** — independent vertical and horizontal values.
- **Frame sizing** — each axis can be Fixed or **Hug contents** (the frame shrink‑wraps its children).
- **Child resizing** — a layer inside an auto‑layout frame can be Fixed or **Fill container** per axis (fill along the flow shares leftover space; fill across stretches to the frame).
- **Drag to reorder** — drag a child within its frame and the others part to show an insertion line; drag it fully out to drop it back on the canvas.
- **Smart add** — adding auto layout (button or **⇧A**) infers direction, gap, and padding from how the children are already arranged.

### Keyboard shortcuts (selection)

| Action | Shortcut |
|---|---|
| Tools | `V` move · `F` frame · `R` rectangle · `O` ellipse · `L` line · `P` pen · `T` text · `H` hand |
| Toggle auto layout | `⇧A` |
| Group / ungroup | `⌘/Ctrl+G` · `⌘/Ctrl+⇧G` |
| Duplicate | `⌘/Ctrl+D` |
| Undo / redo | `⌘/Ctrl+Z` · `⌘/Ctrl+⇧Z` |
| Save `.figgy` | `⌘/Ctrl+S` |
| Present | toolbar **Present** button |

## Limitations

- **`.fig` (Figma) import/export is not supported.** The `.fig` format is a proprietary, undocumented binary container that cannot be decoded or written reliably in a browser. Opening a `.fig` extracts and shows any embedded preview image and explains the situation. **SVG is the bridge** to and from Figma: export SVG from Figma and open it here, or export SVG here and place it into Figma. The native **`.figgy`** (JSON) format round‑trips perfectly.
- **SVG import places the artwork as an image layer**, rendered faithfully but not converted into individually editable vector nodes.
- **The pen tool draws straight segments** (no Bézier curve handles).
- **Components snapshot their contents when created** — editing the main component does not retroactively update existing instances in this version.
- **Boolean operations** support rectangles, ellipses, polygons, stars, and simple paths.
- Scaling a multi‑selection that contains rotated children is approximate.
- Prototype transitions are limited to instant and dissolve.
- No real‑time collaboration; no cross‑session autosave (save a `.figgy` to keep work).

## Technology

- Rendering with **SVG** (the same path used for on‑screen display and for export, so what you see is what you export).
- **polygon‑clipping 0.15.7** — powers the boolean operations.
- **JSZip 3.10.1** — unpacks the `.fig` archive to recover an embedded preview.
- PNG export rasterises the SVG via an offscreen Canvas at 2× scale.
- Exported prototypes are a single self‑contained HTML file with inline screens, transparent navigation hotspots, and a small embedded script.
- Web fonts (Google Fonts): Inter and Roboto.

## Security & privacy

- Fully client‑side. Files you open are read locally and never uploaded; SVG/PNG/`.figgy`/prototype exports are generated in the browser and downloaded directly.
- No backend, accounts, cookies, telemetry, or analytics.
- The only network activity is loading the two libraries (and the fonts) from public CDNs on first open. Opening a `.fig` does **not** make any network request — it unzips the local file. To run offline, vendor the libraries and fonts locally and update the `<script>`/`<link>` tags.
- No `localStorage` is used.
- Imported SVG is rendered in your browser tab; only open content you trust.

## File support

| | Formats |
|---|---|
| **Open** | `.figgy` (native, full round‑trip), `.svg` (placed as image), `.fig` (embedded preview only) |
| **Export** | `.figgy`, `.svg`, `.png`, interactive prototype `.html` |

## License & usage clause

Original code: **GPL-3.0** (see the repository [`LICENSE`](../LICENSE)). polygon‑clipping is MIT and JSZip is dual MIT/GPL‑3.0 (see the README license table). Provided **as is, without warranty**; save `.figgy` files regularly and keep backups. Not affiliated with, endorsed by, or connected to Figma Inc.; "Figma" and "FigJam" are trademarks of Figma Inc., used here only descriptively to indicate interoperability intent and scope.
