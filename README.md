# Anthropic Mesh Gradient Art

A portable AI-agent skill for creating editorial bitmap illustrations and layered SVG artwork that combines hand-drawn symbolic linework with semantic mesh-gradient fields.

The mesh gradient is part of the visual narrative rather than decoration: it can communicate governance state, memory, routing, tension, trust, or transition. Primary contours stay near-black while a restrained set of routes, status marks, halos, or edges can inherit softened mesh colors.

## What is included

- `SKILL.md` — trigger description, workflow, output modes, and QA gate.
- `references/style-spec.md` — palette, composition, semantic models, prompting guidance, and failure modes.
- `references/svg-output.md` — native layered SVG construction rules for Figma/Illustrator-friendly output.
- `assets/` — three visual references used for stroke behavior, density, and symbolic simplification.
- `evals/evals.json` — five lightweight behavior checks covering bitmap, clean SVG, and painterly SVG requests.

## Install

Keep the folder name `anthropic-mesh-gradient-art` so relative references continue to work.

For Codex, place the folder under:

```text
~/.codex/skills/anthropic-mesh-gradient-art
```

For Claude Code, place it in the skills directory used by your local setup. The folder must contain `SKILL.md` at its root.

Restart or reload the agent after installation, then ask for an editorial illustration using a semantic mesh gradient or an editable layered SVG.

## Status

This is a working draft. The instruction structure and five eval cases are present, but visual quality still needs qualitative testing across image models and SVG renderers.

Notable revisions:

- Mesh-tinted linework can carry meaning inside the drawing instead of leaving all color in the background.
- Native layered SVG mode uses named editable groups and never embeds a raster image as a shortcut.
- Painterly SVG mode adds rough ink, subtle paper grain, organic washes, and offset companion strokes while preserving editability.

## Attribution and publishing note

The skill is inspired by Anthropic's editorial illustration language but is not affiliated with or endorsed by Anthropic. It is intended to generate new compositions, not copies of official artwork.

The bundled reference images came from an earlier local reference collection. Their redistribution rights have not yet been verified, so this repository should remain private until those assets are replaced with original/licensed references or their license is confirmed. See `NOTICE.md`.
