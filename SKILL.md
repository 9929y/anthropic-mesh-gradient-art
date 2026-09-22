---
name: anthropic-mesh-gradient-art
description: Generate editorial bitmap or layered SVG illustrations that combine Anthropic-style hand-drawn symbolic linework with premium mesh-gradient studio fields. Use this skill whenever the user asks for Anthropic Art, Claude-style editorial illustration, hand-drawn AI/product/brand visuals, mesh gradient, match gradient, gradient studio, editable SVG layers, governance/status fields, or wants to evolve flat Anthropic visual language into a more atmospheric personal Studio style. Especially use it for conceptual product, brand, AI, operations, system, governance, and case-study hero images where the gradient should carry meaning rather than act as decoration.
---

# Anthropic Mesh Gradient Art

Create illustrations that combine two things:

1. The symbolic clarity of Anthropic-style editorial art: bold black gestural linework, simplified forms, an irregular ivory carrier shape, and one strong metaphor.
2. Yanice's Studio interpretation: a soft mesh-gradient field and subtly mesh-tinted line accents that express system state, atmosphere, risk, trust, energy, or transition instead of behaving like a pretty background.

This skill is for generating a new image direction, not copying official Anthropic assets. Preserve the visual grammar and make a new composition for the user's topic.

## Required Reading

Before generating, read:

- `references/style-spec.md`: detailed style rules, mesh semantics, prompt contract, QA checklist, and failure modes.

When the user asks for SVG, vector, editable layers, layer separation, Figma/Illustrator editing, reusable design assets, or stronger drawing/painting feeling in SVG, also read:

- `references/svg-output.md`: layered SVG construction, group names, vector constraints, and QA checks.

If the image tool supports reference images, include the bundled assets as style references:

- `assets/reference-hand-house.png`
- `assets/reference-object-globe.png`
- `assets/reference-hands-light.png`

Use those assets for stroke behavior, layering, density, and symbolic simplification. Do not copy their exact objects or layout unless the user's topic genuinely calls for a hand, house, globe, or light.

## When To Use

Use this when the user wants any of these:

- Anthropic Art + mesh gradient.
- Claude-style editorial art with a richer gradient Studio layer.
- Product, AI, brand, governance, or operations concepts shown as a symbolic image.
- A case-study hero, product narrative image, social card, blog hero, or presentation visual.
- Layered SVG/vector output that preserves the Anthropic-mesh visual grammar in editable groups.
- Painterly SVG output where editable layers still need rougher hand-drawn strokes, paper grain, organic gradient washes, or less diagram-like marks.
- A gradient that means something: compliance vs risk, source vs edge, calm vs urgency, system health, transition, memory, trust, or uncertainty.

Do not use this for:

- UI screenshots, dashboards, or literal product mockups.
- Logos, icons, or vector-native assets that need deterministic geometry.
- Photorealistic scenes.
- Pure mesh-gradient backgrounds without a symbolic hand-drawn focal concept.

## User Delivery Preference

Yanice’s explicit preference (2026-09-11): never generate PowerPoint, PPT, or PPTX for illustration work, including persona cards. Do not create slide decks as an editable-layer workaround. Use illustration images and, when requested, independent artwork with editable HTML or appropriate design-native files.

## Output Modes

Choose the output mode before composing the prompt or file:

- Bitmap mode: use the available image generation tool when the user wants a finished PNG/JPEG-style illustration, atmospheric texture, or painterly hand-drawn softness.
- Clean layered SVG mode: write a standalone `.svg` file directly when the user asks for SVG, vector, editable, layered, Figma, Illustrator, separated layers, or reusable design-system assets and prioritizes clean editing.
- Painterly layered SVG mode: write a standalone `.svg` file directly when the user asks for SVG but also cares about drawing feeling, texture, illustration quality, or avoiding a diagram/icon look.

Do not promise that an image generation model will emit true layered SVG. In SVG mode, construct the vector asset natively with named `<g>` groups, gradients, and editable paths. Do not embed a raster PNG inside the SVG.

For painterly SVG, preserve editability but use SVG-native texture techniques: subtle paper grain, roughened ink filters, irregular organic gradient washes, hand-wobbled paths, and duplicate low-opacity offset strokes.

## Core Workflow

1. Extract the topic, intended use, aspect ratio, and whether the user wants text.
2. Compress the idea into one visual metaphor. If the scene needs more than one sentence to explain, reduce it.
3. Decide what the mesh gradient means. Do not let it become a decorative wash.
4. Choose one irregular ivory carrier shape to hold the main metaphor.
5. Place bold near-black hand-drawn marks on the carrier, then decide which small set of lines or symbols should inherit mesh color. Keep black as the readability anchor.
6. Use symbols before text. Only use text when the user asks for exact words.
7. Produce the output through the selected mode:
   - Bitmap mode: generate with the available image generation tool.
   - SVG mode: write the SVG directly using `references/svg-output.md`; choose clean or painterly SVG based on the user's quality/editability tradeoff.
8. Inspect the result. Regenerate or revise bitmap output, or edit SVG output, if it looks like a dashboard, stock vector, generic AI poster, flat Anthropic copy, or gradient-only decoration.
9. Save project-bound images into the current project workspace and report the final path.

## Visual Formula

Use this structure:

```text
full-frame mesh-gradient field
+ one irregular ivory carrier/source shape
+ bold black symbolic linework as the structural skeleton
+ subtle mesh-tinted strokes, edge glows, or status lines where meaning needs emphasis
```

The image should feel like an editorial diagram with emotion, not a software screen and not a marketing poster.

## Mesh Gradient Semantics

Before writing the prompt, assign the mesh a role:

- Governance field: blue-green calm zones show compliance or stability; small clay heat shows violation or risk.
- Memory field: warm ivory and pale fig hold history, knowledge, preferences, or brand DNA.
- System field: sky/cactus gradients show infrastructure, connections, routing, or source-of-truth behavior.
- Tension field: calm zones and small warm pressure zones show conflict, uncertainty, alerts, or handoff friction.
- Transition field: one color family slowly yields to another to show evolution, migration, or decision change.

State the role explicitly in the prompt. Example:

```text
The mesh gradient is a governance state field, not a decorative background: blue-green zones represent compliant locations, pale fig marks optional guidance, and one clay heat spot marks violation risk.
```

## Mesh-Tinted Linework

Do not leave the mesh only in the background when the user asks for a stronger Studio feeling. Let a restrained part of the line system pick up the mesh:

- Keep main object contours, hands, and core symbols mostly near-black `#141413` so the image stays Anthropic-readable.
- Use low-saturation gradient-tinted strokes on connection lines, routes, halos, dotted optional paths, alert pulses, memory roots, or system edges.
- Let the tinted linework echo nearby mesh colors: blue-green for stable paths, pale fig for optional guidance, clay for risk, heather for reasoning or uncertainty.
- Prefer black strokes with subtle colored inner/outer edges over fully rainbow strokes.
- Use no more than 20-30% tinted linework in most images. The viewer should feel mesh entering the drawing, not replacing the drawing.

Avoid:

- Rainbow outlines.
- Neon light trails.
- Fully gradient-filled icons.
- Thin polished vector gradient strokes.
- Glow-heavy AI poster aesthetics.

## Prompt Contract

Use this compact structure and adapt it to the user's topic:

```text
Use case: stylized-concept
Asset type: [case-study hero / editorial card / product narrative image / social image]
Primary request: Illustrate [topic] through the single metaphor of [metaphor].

Scene/backdrop: full-frame premium mesh gradient covering every corner. The gradient means [semantic role]. Use soft overlapping fields of [palette choices]. No flat solid background, no white border, no transparent canvas.

Layer system: mesh-gradient field behind one irregular ivory #FAF9F5 carrier shape; near-black #141413 gestural linework and symbolic marks on top. Add restrained mesh-tinted line accents on [routes/status lines/alert marks/memory roots/system edges], echoing the surrounding gradient colors while preserving black as the structural anchor. Allow controlled line spill into the gradient field only when it supports the metaphor.

Subject: [one dominant symbolic object or relationship]. Include [supporting nodes/symbols] only if they serve the core metaphor.

Style/medium: Anthropic-inspired editorial illustration language; bold uneven rounded black ink strokes; simplified objects and anatomy; deliberate asymmetry; flat two-dimensional forms; premium Studio mesh atmosphere.

Composition/framing: [square / 16:9 / wide hero / portrait]. One focal cluster occupying roughly [60-75%] of the frame, with generous breathing room and thumbnail readability.

Color palette: near-black #141413 primary linework; ivory #FAF9F5 carrier; mesh fields from cactus #BCD1CA, sky #6A9BCC, oat #E3DACC, heather #CBCADB, pale fig/coral, and tiny clay #D97757 only for emphasis. Mesh-tinted line accents may use softened versions of those same colors, but should stay sparse and legible.

Text (verbatim): [none / exact short text]. Prefer symbols over labels.

Constraints: preserve symbolic clarity; mesh must carry meaning; keep the canvas opaque; avoid dashboards, UI screenshots, logos, photorealism, 3D, glossy SaaS gradients, neon, rainbow palettes, dense detail, and copied reference composition.
```

## Good Patterns

- A hand steadies a central source while small nodes sit in different mesh states and connection lines subtly shift from black into blue-green or clay status strokes.
- A central memory seed sends black line roots into soft gradient fields.
- A small clay alert zone interrupts a calm blue-green system field.
- A dotted path moves from pale uncertainty into a clearer ivory source, with dots softly inheriting the nearby mesh color.
- A cluster of simplified objects is held by one irregular carrier shape, not boxed into UI cards.

## Bad Patterns

- Anthropic line art pasted on a random colorful gradient.
- Black-only line art where the mesh never enters the drawing system.
- Gradient line art with no black anchor.
- A literal dashboard with panels, charts, app windows, and metrics cards.
- A generic AI poster with glowing orbs, neon purple-blue fog, or robotic imagery.
- Too many icons arranged as a formal flowchart.
- Perfect vector geometry with thin lines and polished corporate stock illustration style.
- Text labels explaining everything the image should imply visually.

## QA Gate

Accept the image only if:

- Every corner is covered by an intentional mesh gradient.
- The mesh has an explainable semantic role.
- At least one meaningful path, status line, edge, halo, or symbol has a restrained mesh-tinted treatment when the user asks for a stronger Studio feeling.
- The image still has an ivory carrier/source shape.
- Black linework is bold, uneven, and hand-drawn; mesh-tinted line accents support it rather than replacing it.
- The concept reads as one metaphor at thumbnail size.
- There is no dashboard, UI screenshot, logo, HR/recruiting cue, or generic AI-poster look.
- The palette is restrained: black, ivory, a controlled mesh family, and one tiny warm accent if needed.

For SVG mode, also accept only if:

- The file is a real standalone SVG with named layer groups, not a raster image embedded in SVG.
- Mesh gradients, ivory carrier, black linework, mesh-tinted linework, persona/subject, and symbols/props are separated into editable groups.
- The SVG includes `<title>` and `<desc>` and has no scripts, external images, or external font dependencies.
- Layer names make sense in Figma or Illustrator after import.

For painterly SVG mode, also accept only if:

- Main lines have at least one hand-drawn quality, such as slight wobble, rough filter displacement, or low-opacity offset companion strokes.
- Mesh fields use organic washes or uneven patches rather than only perfect circles.
- Texture remains subtle and does not hide the layer structure or make the file feel like a raster export.
- The output still communicates the persona/story more strongly than the filter effect.

If a generated image is basically the original Anthropic Art with only a gradient swap, revise the prompt so the mesh changes the composition and meaning.

## Output

When finished, report:

- The saved image path or SVG path.
- The prompt summary.
- The mesh semantic role.
- Any concerns, especially if text accuracy or style fidelity needs another iteration.
