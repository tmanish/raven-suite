# Contributing to Raven Suite

Thanks for being here. Raven Suite is a free, open‑source project built as a service, and contributions of every size are welcome — fixing a typo in the docs counts just as much as adding a feature.

You don't need to be an experienced programmer to help. This guide explains the simplest ways in.

## Ways to help

- **Report a bug** — something broke or behaves oddly. Open an issue using the *Bug report* template.
- **Suggest a feature** — an idea to make a tool more useful. Use the *Feature request* template.
- **Improve the docs** — clearer wording, fixed links, better examples.
- **Contribute code** — fix a bug or build something new.

To report a bug or request a feature, go to the **Issues** tab and click **New issue** — the templates will guide you.

## Principles to keep

These are what make the suite what it is. Please preserve them:

- **One file per app.** Each tool is a single, self‑contained `.html` file with its CSS and JavaScript inline. No splitting into many files.
- **Runs in the browser, nothing uploaded.** All work happens on the user's device. No backend, no accounts, no tracking, no analytics.
- **No build step and no frameworks.** Plain HTML, CSS, and JavaScript. Libraries are loaded from a CDN only when a tool genuinely needs one.
- **Honest about limits.** Where a proprietary format can't be supported properly, the app should say so plainly rather than pretend.

## Making a code change

No command line is required — you can do everything on github.com:

1. **Fork** this repository (top‑right **Fork** button) so you have your own copy.
2. Open the file you want to change and click the **pencil (Edit)** icon.
3. Make your edit. To test it, download your edited file and open it in a browser (see *Testing* below).
4. Scroll down, describe your change, and **commit**.
5. Open a **Pull request** back to this repository. Describe what you changed and why.

If you're comfortable with Git, the usual fork → branch → commit → pull‑request flow is perfect too.

## Testing

Because each app is a single file, testing is just opening it:

- Open the `.html` file in a browser and try the thing you changed.
- Check it still works in both **light and dark** themes.
- Try a couple of different files/inputs if your change touches importing or exporting.
- If you can, check it in more than one browser (Chrome/Edge, Firefox, Safari).

## Style

- Match the patterns already in the file you're editing — naming, spacing, and structure.
- Keep it vanilla: no frameworks, no new build tooling.
- Add a new third‑party library only if it's truly necessary, and prefer well‑known, permissively‑licensed ones loaded from a public CDN.
- Keep the interface consistent with the rest of the suite (the frosted‑glass look, the shared accent colors, light/dark support).

## License of contributions

By contributing, you agree that your contribution is licensed under the project's **GPL‑3.0** license, the same terms as the rest of the suite. In short: your work stays open for everyone, and so does anyone else's improvement on top of it.

## Be kind

Please keep discussion respectful and constructive. Assume good intent, be patient with newcomers, and focus on the work. That's the whole code of conduct.
