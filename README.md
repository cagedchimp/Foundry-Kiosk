# Foundry Kiosk

Design files and scale mockups for the **Weissman Foundry** three-sided plywood
**info pillar** — a freestanding kiosk for the makerspace shared by Babson, Olin,
and Wellesley.

The pillar is ~**7 ft tall × 26 in per face**, three plywood faces joined by
3D-printed corner joints. Printed panels, document holders, a whiteboard, and
8×8 in Scout plaques mount onto the raw plywood on **French cleats** so pieces
swap out without tools.

## Quick start

No build, no dependencies. Open the mockups in any browser:

```
renders/pillar_all_sides_measured.html   # all 3 faces, true scale, with a ruler + measurements
renders/side3_7ft.html                    # Side 3 alone at full 7 ft height
```

## The three faces

| Face | Purpose | Key contents |
|------|---------|--------------|
| **Side 1 — The Foundry** | Evergreen identity | Wordmark, "Bring your idea to life," capability icons, get-started QR |
| **Side 2 — What's Happening** | Live, weekly | US-Letter calendar, 24×18 whiteboard, reserve/drop-in, 11×17 posters |
| **Side 3 — Need Help?** | Scouts & training | Find-a-Scout intro, three 8×8 Scout plaques on a cleat, get-trained QR |

## Repo layout

- `renders/` — HTML scale mockups (the spec drawings)
- `brand/` — wordmark, geometric pattern, Scout plaque reference
- `docs/` — design spec, brand guide, build notes, content checklist
- `CLAUDE.md` — orientation for AI assistants / new collaborators

## Status

Layout and proportions are settled. **Copy, hours, handles, Scout names, posters,
calendar data, and QR codes are placeholder** — see `docs/CONTENT.md` for what to
finalize before printing. Pattern bands in the mockups are SVG reconstructions;
swap for the real `brand/Foundry_Pattern.jpg` in production.

See `docs/DESIGN_SPEC.md` for the full anatomy and decisions.
