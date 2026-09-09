# SymmetryFlow — Portfolio Site

A single-page portfolio site for **SymmetryFlow**, a Blender addon for vertex weight mirroring and symmetry diagnostics on rigged character meshes.

🔗 **Live site:** https://webdev0486.github.io/symmetryflow-portfolio/

This repo hosts the marketing/showcase page only — it does not contain the SymmetryFlow addon source or distributable files.

## What's here

```
.
├── index.html          # single-page site (no build step, no dependencies)
└── assets/
    ├── site/           # what index.html loads: responsive stills + web video
    └── *.png           # the 4K marketing slides, kept for the Superhive gallery
```

`assets/site/` is 3.2 MB in total. The demo clips are H.264 with a VP9 fallback
rather than GIF — the same footage costs about a fourteenth of the bytes per
second of playback in that format, measured on this material.

## About SymmetryFlow

SymmetryFlow is a Blender addon that solves vertex weight mirroring for rigs
where naive left/right symmetry falls apart — asymmetrical meshes, posed
characters, and overlapping geometry like lips and eyelids.

**Blender 3.6 through 5.1+, except 5.0.0 and 5.0.1.** Those two releases carry a
bug in Blender itself: any add-on that highlights vertices and then leaves Weight
Paint mode closes Blender instantly. It was reproduced with SymmetryFlow
completely uninstalled, and Blender fixed it in 5.1.

## What the page covers

In order, because the page argues rather than lists:

1. **The problem** — Blender's mirror is coordinate-based and all-or-nothing, so
   it stops at the first vertex that is not an exact spatial twin. On a
   character that is the eyelids, lips, ears, teeth, brows and lashes. Shown as
   a before/after pair on one eyelid group.
2. **Two matching engines, chosen automatically** — topological (walks edge
   connectivity, so it survives posed meshes and shape keys) and spatial KD-tree
   (O(log N), for islands and shell-split geometry), with Auto-Detect picking
   per group.
3. **The verification layer** — the L/R Balance panel reporting each pair as
   Balanced, Mismatched or Distorted. The verdict comes from the same function
   Quick Fix acts on, so report and repair cannot contradict each other. This is
   the part no competitor screenshot has, and the page says so.
4. **Four demos**, as video: Mirror All L/R Groups rebuilding 37 deleted groups,
   Mirror Active Group repairing a damaged calf, a mirror landing on a rig that
   is out of rest pose, and the panel naming a mismatched eyelid pair.
5. **The posed-rig case** on its own, because a coordinate mirror cannot do it
   at all: 296 weights back to 438.
6. **What it cannot do** — three limitations stated plainly rather than buried:
   it cannot make an asymmetric mesh symmetrical (Robust Asymmetric Fallback
   recovers what a strict counterpart check would refuse, as much as the
   geometry allows — how much depends on the mesh), vertex counts may differ on
   faces, and hair cards take minutes to analyse.
7. **Compatibility** — the two downloads, and the Blender 5.0.0/5.0.1 warning.

Features the add-on has but the page does not argue — UV-space mirroring,
Auto-Clean Micro-Noise, rest-pose enforcement, custom naming patterns — are in
the product listing and the shipped manual. The page is deliberately shorter
than the feature list.

Every figure quoted on it — 221 weights, 296 → 438, 52/52 — was read back off
the mesh by the recording harness at the moment the take was made, and matches
the product listing.

Those numbers describe the takes on screen, which is why they can be stated
flatly. A recovery PERCENTAGE cannot: how much Robust Asymmetric Fallback gets
back is a property of the mesh, not of the add-on, so the page says what the
option does rather than quoting a share measured on our own fixtures.

## Status

Not on sale yet. **Two** calls to action — one in the hero, one in the closing
section — read "Coming soon on Superhive" and link to
`https://superhivemarket.com/`, which is checked and resolves to Superhive
(formerly Blender Market). They deliberately do not point at a
`/products/` path, because that slug is not confirmed until the listing exists
and a wrong one is a 404 on a live site.

**To publish**, in `index.html`:

```
find     href="https://superhivemarket.com/"
replace  href="https://superhivemarket.com/products/<your-slug>"
```

and change the two "Coming soon on Superhive" labels to whatever the button
should say — searching for `soon` finds every one. A comment at the top of
`index.html` repeats this, so it is findable from the file itself.

Worth doing at the same time: the same assumed slug is baked into `README.txt`,
`CHANGELOG.txt` and `__init__.py` inside the add-on zip, where fixing it costs
a rebuild rather than an edit.

## Deployment

Served via GitHub Pages from the `main` branch root. Any push to `main` updates the live site automatically.

## License

© Dev.Luv.Studios. All rights reserved. Site content and screenshots may not be reused without permission.
