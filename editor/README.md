# Foundry Kiosk Editor

A single-file web app for editing the info-pillar copy and exporting **print-ready PDFs**
of each face — or of any individual mounted piece — at its exact real-world size.

## Use it

**Hosted:** https://cagedchimp.github.io/Foundry-Kiosk/editor/ (Chrome or Edge).

Or run locally — open `editor/index.html` in **Chrome or Edge** (no build, no server, no
install — just double-click). Keep the `vendor/` folder (offline QR library + embedded
Archivo fonts) and the sibling `brand/` folder (wordmark + pattern) in place. Then:

1. Pick a face tab (**Side 1 / 2 / 3**), **All faces** (see all three at once), or
   **Shared** (footer hours, socials, address).
2. **Click any text on the preview and type** — the sign itself is editable. Hovering
   outlines anything you can change. The fields on the left edit the same copy and the two
   stay in sync; the left panel is still where images, QR links, calendar events and
   adding/reordering sections live. Edits auto-save to your browser's local storage.
3. Choose an **Export target** (the whole 26×84″ face, a single piece, or — on the
   All-faces tab — the whole pillar as one wide sheet).
4. (Optional) Tick **Print marks** to add a 0.125″ bleed (on full-bleed pieces like
   posters/plaques) and corner crop marks for a print shop.
5. Click **Print / Save PDF** → in the print dialog choose *Save as PDF*. The page is
   pre-sized to the target's true dimensions, so the output is vector-sharp and to scale.

## Sections (modular layout)

Each face is a stack of **sections** you can rearrange — the **Sections** panel at the top
of every Side tab lets you:

- **Show / hide** any section with its checkbox (hidden sections drop out of the preview
  *and* the export menu).
- **Reorder** by dragging the ⋮⋮ handle.
- **Add** new sections from the “+ Add a section…” menu: a **Text box** (heading + body)
  or a **Custom QR card** (eyebrow + title + URL → live QR). Added sections are editable
  inline and removable with ✕. You can add as many as you like.
- **Style each section** with two dropdowns: a **Background** (faint wordmark by default,
  plus pattern/mark/motif/stripes/grid/none) and a **Color** colourway (Default, or any
  brand colour — Green, Forest, Paper, Gold, Teal, Sage). Text recolours automatically for
  contrast and the background watermark follows the colour.
- **Align its text** with the **Text** dropdown: *As designed* (the default — leaves the
  section's original alignment alone), or force **Left / Center / Right** for everything in
  that section. Alignment is per-section, saves with your layout, and carries into the PDF.

The **header and footer are fixed brand furniture** (always present); everything between
them is modular. Your layout — order, what's on/off, and any added sections — saves locally
and travels in **Export/Import JSON**.

## Print quality

The exported PDFs are built to be print-ready, not just screenshots:

- **Type: Trade Gothic LT Std** (Babson brand), embedded under the project's web-font
  license, with **Archivo** (woff2) as the fallback for any missing weight. Brand-correct
  on the hosted site and at the print shop — no substitution.
- **Backgrounds always print.** Colours, QR codes, and the pattern bands are forced on
  via `print-color-adjust`, so you don't have to fiddle with the browser's "Background
  graphics" setting.
- **Real brand pattern.** The header/footer bands use crops of
  `brand/Foundry_Pattern.jpg`; several section panels also carry a faint motif drawn
  from the pattern vocabulary (nested squares, chevrons, stripe-fan, triangle, quarter-disc)
  for subtle variety — kept contained, never confetti.
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

## Images

Three places take a real uploaded image (click **Choose…**, then **Replace…** / **Remove**):

- **Scout photos** (Side 3) — fills the plaque photo box; falls back to initials if empty.
- **Poster artwork** (Side 2) — replaces the generated placeholder with your full-bleed
  image; it also extends into the print-marks bleed.
- **Custom capability icons** (Side 1, under the *Custom icons* toggle) — swap any of the
  five built-in line icons for your own.

Uploads are **downscaled in the browser** (photos ~700px, posters ~1600px, icons ~400px)
and stored as data URLs — so they persist locally and travel inside **Export/Import JSON**.
Nothing is uploaded anywhere. If you add many large images and auto-save hits the browser's
storage limit, the save indicator warns you — use **Export** to keep a copy. For premium
edge-to-edge poster printing, prep final artwork at full resolution in a dedicated tool;
the in-app image is best for proofing the pillar and for sleeved/mounted prints.

## The text toolbar

Click into any text on the preview and a small toolbar appears above it:

- **B / Gold / Clear** — formatting. These need you to *select* some text first (they grey
  out until you do); no need to learn the marker syntax below.
- **A− / A+** — size that piece of text, in 5% steps (50%–200%). Handy when a headline
  wraps and you want it on one line — shrink it until it fits. The **%** in the middle
  shows the current size; click it to reset to 100%.
- **◧ ◫ ◨** — align that piece of text left / centre / right. Click the active one again to
  clear it and fall back to the section's alignment.

Size and alignment are per piece of text, save with your content, and carry into the PDF.
A field's own alignment beats its section's **Text** dropdown, so you can centre one line
inside an otherwise left-aligned section.

> Note: some copy has a **deliberate line break** in it (the Side 1 headline ships as
> "Bring your ⏎ idea to life"). Delete the break first if you want it on one line, then use
> **A−** if it still wraps.

## Text formatting
- `*word*` → gold emphasis  ·  `**word**` → bold. While you're editing a piece of text on
  the preview it shows these raw markers; click away and it renders. (The markers never
  reach the PDF.)
- **Line breaks and paragraphs:** press **Enter** for a new line, and **Enter twice** to
  leave a blank line between paragraphs — the way to break longer copy up. This works both
  in the preview and in the boxes on the left, and blank lines carry into the PDF.
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

> Remaining before a final run: the content checklist in `../docs/CONTENT.md` (hours,
> handles, QR URLs, Scout names) and dropping in the real Scout photos / poster artwork /
> icons. Always test-scan the final PDF's QR codes and proof one face at full size before
> ordering prints.
