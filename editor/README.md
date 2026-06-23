# Foundry Kiosk Editor

A single-file web app for editing the info-pillar copy and exporting **print-ready PDFs**
of each face — or of any individual mounted piece — at its exact real-world size.

## Use it

Open `editor/index.html` in **Chrome or Edge** (no build, no server, no install — just
double-click). Keep the `vendor/` folder (offline QR library + embedded Archivo fonts)
and the sibling `brand/` folder (wordmark + pattern) in place. Then:

1. Pick a face tab (**Side 1 / 2 / 3**), **All faces** (see all three at once), or
   **Shared** (footer hours, socials, address).
2. Edit the text fields on the left. The preview updates live; edits auto-save to your
   browser's local storage.
3. Choose an **Export target** (the whole 26×84″ face, a single piece, or — on the
   All-faces tab — the whole pillar as one wide sheet).
4. (Optional) Tick **Print marks** to add a 0.125″ bleed (on full-bleed pieces like
   posters/plaques) and corner crop marks for a print shop.
5. Click **Print / Save PDF** → in the print dialog choose *Save as PDF*. The page is
   pre-sized to the target's true dimensions, so the output is vector-sharp and to scale.

## Print quality

The exported PDFs are built to be print-ready, not just screenshots:

- **Archivo is embedded** (vendored woff2, `vendor/fonts/`), so type is brand-correct on
  any machine or at the print shop — no font substitution.
- **Backgrounds always print.** Colours, QR codes, and the pattern bands are forced on
  via `print-color-adjust`, so you don't have to fiddle with the browser's "Background
  graphics" setting.
- **Real brand pattern.** The header/footer bands now use crops of
  `brand/Foundry_Pattern.jpg` (not the old SVG reconstruction).
- **Exact sizes.** Every target prints at its true dimension (a plaque is a real 8×8″,
  a poster a real 11×17″, etc.).

## Export targets & sizes

| Target | Size |
|--------|------|
| Whole face | 26 × 84 in (large-format) |
| Header / hero / panels / footer | 23 in wide (cleat-module panels) |
| Weekly calendar | 8.5 × 11 in |
| Event poster 1 / 2 | 11 × 17 in |
| Scout plaque 1 / 2 / 3 | 8 × 8 in |
| All three faces | ~82 × 84 in (one wide sheet) |

## Text formatting

- `*word*` → gold emphasis  ·  `**word**` → bold  ·  line breaks split lines.
- **Calendar events:** one per line as `type:text`, where `type` is `r` reserved (gold),
  `t` class (teal), `s` event (sage), `g` closed (green). e.g. `r:9a Wood hold`.
- **Open Scout cleat:** leave a Scout's *name* blank to render that slot as an empty cleat.

## QR codes

The QR codes are **real and scannable** — generated live from the URLs you type:

- **Side 1** → *Get-started QR* URL  ·  **Side 3** → *Get-trained QR* URL
- **Side 2 posters** each take an optional QR URL (shown in the poster's corner box).

Leave a URL blank to fall back to a decorative placeholder grid. Codes are generated
fully offline by the bundled MIT library in `vendor/qrcode-generator.js` — nothing is
sent over the network, so your URLs stay private. They render as crisp vectors, so they
stay sharp at any print size. Always do a test scan of the final PDF before printing.

## Buttons

- **Export** — download all current copy as `foundry-kiosk-content.json`.
- **Import** — load copy back from a JSON file (good for sharing or versioning content).
- **Reset** — restore the placeholder defaults and clear local edits.

## How it stays true to the renders

Every face/piece is authored at the spec renders' design scale (**1 in = 8.38 px**) and
reuses their component CSS. For print the target is wrapped and scaled with CSS `zoom`
so 8.38 design-px maps to 1 real inch, then `@page` is sized to the measured box. Preview
fits the same markup to the pane. Edit one place, both stay in sync.

> Remaining placeholders before a final run: real Scout photos and event-poster artwork
> (the editor renders generated placeholders), and the content checklist in
> `../docs/CONTENT.md` (hours, handles, QR URLs, Scout names). Always test-scan the final
> PDF's QR codes and proof one face at full size before ordering prints.
