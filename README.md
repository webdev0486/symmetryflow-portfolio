# SymmetryFlow — Portfolio Site

A single-page portfolio site for **SymmetryFlow**, a Blender addon for vertex weight mirroring and symmetry diagnostics on rigged character meshes.

🔗 **Live site:** https://webdev0486.github.io/symmetryflow-portfolio/

This repo hosts the marketing/showcase page only — it does not contain the SymmetryFlow addon source or distributable files.

## What's here

```
.
├── index.html          # single-page site (no build step)
└── assets/             # screenshots and feature graphics
```

## About SymmetryFlow

SymmetryFlow is a Blender 4.x+ addon that solves vertex weight mirroring for rigs where naive left/right symmetry falls apart — asymmetrical meshes, posed characters, and overlapping geometry like lips and eyelids.

Highlights covered on the page:

- **Pair / Single mirror modes** — transfer weights between counterpart groups, or symmetrize a center-line group internally
- **Auto-Detect Direction & Tolerance** — scans weight density and scales the KD-Tree search radius to mesh size automatically
- **UV Space Mirroring** — mirrors via 2D UV layout for posed or asymmetrical meshes, with nearest-neighbor fallback for unmatched vertices
- **Normal Alignment Check** — prevents weight bleed-through on double-sided geometry (lips, eyelids)
- **Auto-Clean Micro-Noise** — strips ghost weights below a configurable threshold
- **Enforce Armature Rest Pose** — mirror weights mid-animation without manually clearing the pose
- **Symmetry Health Diagnostics** — reports exact vertex mismatch counts before you commit to a fix
- **Quick Fix Solver** — one-click topological resolution for mismatched vertex groups

## Deployment

Served via GitHub Pages from the `main` branch root. Any push to `main` updates the live site automatically.

## License

© Dev.Luv.Studios. All rights reserved. Site content and screenshots may not be reused without permission.
