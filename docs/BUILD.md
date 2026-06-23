# Build Notes — physical fabrication

These are practical notes for building the real pillar. The HTML renders are the
visual spec; this is the "how it goes together" side.

## Structure

- Three plywood faces, **~26 in wide × ~84 in tall** each.
- Corners joined by **3D-printed corner joints** (printed in-house). Consider whether
  the geometric pattern wraps/embosses these as a brand detail.
- Birch plywood is the finished surface — **seal it** (matte poly or hardwax-oil) so it
  doesn't yellow or get grubby in a makerspace. Keep it matte, not glossy/orange.

## Mount system (French cleats)

- A cleat rail runs horizontally where pieces hang. Printed panels, document holders,
  the whiteboard, and Scout plaques all lift on/off the rail — no tools to swap.
- Preserve a consistent **plywood reveal** (bare margin around each mounted panel,
  target ~1–2 in on all sides) so the exposed wood looks intentional.
- In the mockups, every mounted piece shows a drop shadow + screw heads to signal it
  sits proud of the wood. Side 3 shows an **open cleat** slot (dashed 8×8 footprint)
  where the next Scout hangs their plaque.

## Piece sizes (printed/physical)

| Piece | Size | Notes |
|-------|------|-------|
| Event posters (Side 2) | **11×17 in** | Acrylic sleeve or clips |
| Weekly calendar (Side 2) | **US Letter 8.5×11 portrait** | Google Calendar "Print" export; paper holder |
| Whiteboard (Side 2) | **24×18 in** landscape | Real dry-erase board; sits proudest — plan mount depth |
| Scout plaques (Side 3) | **8×8 in** square | 3 across one shared cleat; French-cleat hangers |
| Printed panels (headers/green panels/footer) | sized to cleat module | Built as Canva templates |

Three 8×8 plaques + gaps fit across the 26 in face (verify the gap math against the
final reveal spec).

## Production artwork

- Build each printed panel as a **Canva template** at exact print dimensions.
- Replace mockup placeholders with real assets:
  - reconstructed SVG pattern → crops of `brand/Foundry_Pattern.jpg`
  - placeholder QR grids → real scannable QR images with correct URLs
  - placeholder copy/hours/handles/names → finalized content (see CONTENT.md)
- Keep the wordmark as vector; recolor per background (green on light, white on dark).

## Reuse

The header and footer are shared "furniture." Build them once and reuse across all
three faces; only the middle content field changes per side.
