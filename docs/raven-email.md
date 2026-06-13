# Raven Email

An HTML‑to‑EML email builder in a single HTML file — turn an HTML design into a properly‑formed email file, with inlined CSS and embedded images, entirely in your browser.

→ Open the app: [`../raven-email.html`](../raven-email.html)

---

## Usage

Open `raven-email.html`. The do's and don'ts of email HTML are shown up front (step 1), before you upload — read them, because email clients are far stricter than browsers. Then provide your HTML, set the headers, review the live preview and report, and export an `.eml` file you can open, test, or send from a real mail client.

Common workflow:

- Review the email‑HTML guidance shown before upload.
- Provide your HTML email design.
- Let the app inline your CSS and embed images (see Features).
- Fill in From / To / Subject (Subject auto‑fills from the document `<title>`).
- Check the live preview and the colour‑coded report.
- Optionally mark it as an unsent draft, then export `.eml`.

## Features

- **Real CSS inlining via the CSS Object Model.** Styles are resolved in true cascade order; existing inline styles win, and `@media` queries and pseudo‑classes are preserved in a retained `<style>` block (since they can't be inlined).
- **CID image embedding.** `data:` URI images are converted into inline MIME attachments referenced by Content‑ID — because some clients (notably Outlook) won't render `data:` URIs directly. Relative image paths are matched and fixed by filename.
- **Optional remote‑image download** to embed externally‑hosted images.
- Live preview and a colour‑coded report of what was changed.
- Editable From / To / Subject headers, with Subject auto‑filled from `<title>`.
- An `X‑Unsent` draft toggle (opens as a composable draft in supporting clients).
- Light and dark themes.

## Limitations

- **`.msg` (Outlook) is not supported.** It is a proprietary OLE/binary format that cannot be written reliably in a browser. The app exports `.eml`, which Outlook opens natively — then *Save As → .msg* inside Outlook if you specifically need that format.
- **Remote image download is subject to CORS.** Servers that block cross‑origin requests will prevent their images from being embedded.
- **Email clients vary widely.** Even a correctly built email can render differently across Outlook, Gmail, Apple Mail, and others; always test in your target clients.
- Some CSS that cannot be inlined is moved into a retained `<style>` block, which not every client honours equally.

## Technology

- **No external libraries.** This app uses only native browser APIs.
- The browser's **CSS Object Model (CSSOM)** for accurate cascade resolution, the **DOM** for parsing/transforming the HTML, and standard MIME assembly for the `.eml` output.
- System font stack (no external fonts loaded).

## Security & privacy

- The most self‑contained app in the suite: it loads **no external scripts and no external fonts**.
- Fully client‑side. Your HTML and images are processed locally and never uploaded; the `.eml` is generated in the browser and downloaded directly.
- The **only** time it touches the network is if you explicitly use the optional "download remote images" feature, which fetches the image URLs you referenced in your email.
- No backend, accounts, cookies, telemetry, analytics, or `localStorage`.
- It renders your email HTML in the browser tab for preview; only process content you trust.

## File support

| | Formats |
|---|---|
| **Input** | HTML email (uploaded or pasted) |
| **Export** | `.eml` (RFC 822 / MIME; opens in Outlook, Apple Mail, Thunderbird, etc.) |

## License & usage clause

Original code: **GPL-3.0** (see the repository [`LICENSE`](../LICENSE)). No third‑party runtime libraries are bundled. Provided **as is, without warranty**; always test exported emails in your target clients before sending at scale. Not affiliated with or endorsed by Microsoft; "Outlook" is a trademark of Microsoft Corporation, used here only to describe compatibility.
