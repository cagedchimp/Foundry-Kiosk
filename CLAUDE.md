# CLAUDE.md — Working notes for the Foundry Kiosk project

This file orients an AI assistant (or a new collaborator) picking up this repo. Read it first.

## What this is

A design project for a **freestanding, three-sided plywood info pillar** for the
**Weissman Foundry** — an open-door prototyping hub / makerspace shared by Babson,
Olin, and Wellesley colleges (9 Map Hill Drive, Wellesley MA 02482).

The pillar is a physical object: three plywood faces joined by 3D-printed corner
joints, roughly **7 ft tall × 26 in wide per face**. Printed panels, document
holders, a whiteboard, and Scout plaques mount onto the raw plywood on **French
cleats** so pieces can be swapped without tools.

The HTML files in `renders/` are **scale mockups / spec drawings**, not the
production artwork. They exist to communicate layout, proportion, and the cleat
system to whoever fabricates and prints the real thing (likely via Canva templates).

## The three faces

- **Side 1 — The Foundry (evergreen):** identity face. Wordmark header, "Bring your
  idea to life" hero, condensed about-copy, a 5-icon capability strip (Woodshop,
  Digital Fabrication, Fashion & Textiles, 3D Printing & Electronics, Kitchen), a
  concept→product 3-step, and a get-started QR.
- **Side 2 — What's Happening (live, weekly):** mostly holders. A US-Letter weekly
  calendar (printed from Google Calendar) in a paper holder, a real **24×18 in**
  whiteboard, a reserve/drop-in panel, and two 11×17 event posters.
- **Side 3 — Need Help? (Scouts & training):** "Find a Scout" intro, a row of three
  **8×8 in** Scout plaques on a shared cleat (2 filled + 1 open), and a get-trained QR.

All three share fixed **header** and **footer** "furniture"; only the middle content
field changes. See `docs/DESIGN_SPEC.md` for the anatomy and exact decisions.

## Repo layout

```
renders/   HTML scale mockups (open in a browser)
brand/     wordmark (orig + recolored), geometric pattern, Scout plaque reference
docs/      DESIGN_SPEC.md, BRAND.md, BUILD.md, CONTENT.md
```

## How the mockups are built (important technical notes)

- Pure HTML/CSS, no build step. Open any file in `renders/` directly in a browser.
- **Scale:** `pillar_all_sides_measured.html` uses a fixed scale of **1 inch = 8.38 px**
  (so the 84 in face = 704 px tall, 26 in face = 218 px wide). The left ruler and the
  right-hand measurement brackets are keyed to this and measure the **sign only**.
- The **wordmark** is the real vector (`brand/wordmark.svg`), recolored per context:
  green (`wordmark_green.svg`) on light, white (`wordmark_white.svg`) on green/dark.
  It's injected via a small `<script>` block at the bottom of the measured render.
- The **geometric pattern** in the mockups is an **SVG reconstruction** of the motif
  vocabulary (triangles, circles, nested squares, stripe fans) in the brand palette,
  built from square tiles using `preserveAspectRatio="xMidYMid slice"` so tiles never
  distort. For production, swap these for crops of the real `brand/Foundry_Pattern.jpg`.
- **Pattern rule:** tiles are always true squares, never stretched. Keep it contained
  (header strip + footer strip), not sprinkled like confetti — this is a brand rule.
- QR codes are **decorative placeholders** (CSS grids), not scannable. Replace with real
  QR images pointing at the right URLs before printing.

## What is still placeholder (do NOT treat as final)

Copy, hours, social handles, Scout names/roles, event posters, calendar contents,
and all QR codes are **placeholder**. Real hours currently shown: Mon–Fri 10a–9p,
Sat–Sun 12–8p (academic semester). Verify before printing.

## Conventions / guardrails

- Keep the shared header + footer consistent across all three faces ("brand furniture").
- Honor the brand palette and Archivo type (see `docs/BRAND.md`). Headlines are
  Archivo Black, UPPERCASE; body is sentence case, never all-caps.
- The plywood is the surface; printed pieces mount *on* it. Preserve the cleat/mount
  visual language (drop shadows, screw heads, the open-cleat slot on Side 3).
- When editing a render, edit the HTML directly and re-open in a browser to verify.
  There are no dependencies to install.

## Likely next steps (handed off mid-project)

- Align the three footer band heights so they match walking around the pillar.
- Swap reconstructed pattern + placeholder QRs for real assets.
- Convert each face into a production Canva template at exact print dimensions.
- Confirm the plywood "reveal" (bare margin around each mounted panel) as a spec.
