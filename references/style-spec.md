# Anthropic Mesh Gradient Style Specification

## Intent

This skill creates a new hybrid visual language for bitmap generation and layered SVG construction:

- Anthropic-inspired editorial structure provides symbolic clarity.
- Mesh gradient provides Yanice's Studio atmosphere and semantic state.
- Mesh-tinted line accents let that Studio field enter the drawing itself without losing Anthropic-style readability.

The gradient must not be decorative. It should help the viewer understand the system, emotion, or risk structure before reading any explanation.

When the requested output is SVG, preserve the same visual grammar with editable vector layers rather than trying to imitate bitmap texture. Read `svg-output.md` for SVG-specific construction rules.

## Palette

Base:

- Near-black linework: `#141413`
- Ivory carrier: `#FAF9F5`

Mesh field options:

- Cactus `#BCD1CA`: trust, governance, calm systems, institutional steadiness.
- Sky `#6A9BCC`: infrastructure, communication, openness, routing.
- Oat `#E3DACC`: human operations, partnership, warmth.
- Heather `#CBCADB`: research, technical reflection, abstraction.
- Fig/coral pink: creativity, optionality, identity, soft uncertainty.
- Clay `#D97757`: urgency, alert, violation, launch, risk. Use sparingly.

Avoid:

- Dominant purple-blue SaaS gradients.
- Neon gradients.
- Rainbow palettes.
- Dark tech backgrounds.
- Heavy glow, glassmorphism, and glossy lighting.

## Three-Layer Construction

Build exactly three visual layers:

1. Full-frame mesh-gradient field covering every corner.
2. One large irregular ivory carrier shape occupying about 55-75% of the canvas.
3. Bold near-black hand-drawn linework and symbols, with optional tiny accent marks.

The carrier shape should feel like a source, island, memory cell, rule field, or conceptual stage. It is not a UI card.

For layered SVG output, expand these into named editable groups while preserving the same visual order: mesh background, ivory carrier, primary black linework, mesh-tinted accents, persona/subject, and symbols/props.

## Mesh-Tinted Linework Layer

The hybrid style works best when the mesh is not trapped behind the drawing. Let the drawing absorb the field in selected places.

Keep near-black `#141413` for:

- Main object contours.
- Hand contours.
- Primary hub/source shapes.
- Symbols that must read immediately.

Use mesh-tinted strokes for:

- Connection lines between nodes.
- Dotted optional paths.
- Alert pulses or risk edges.
- Memory roots and retrieval paths.
- System routes that leave the ivory carrier and enter the gradient field.
- Thin halos around a source node when the halo communicates state.

Tint behavior:

- Blue/cactus line tint: stable, compliant, trusted, connected.
- Pale fig/coral line tint: optional, creative, soft guidance, unresolved choice.
- Heather tint: reasoning, model interpretation, uncertainty.
- Clay tint: alert, violation, escalation, pressure.

Technique guidance:

- Prefer mostly black strokes with a subtle colored edge, inner tint, or nearby colored echo.
- Use fully colored strokes only for secondary routes, dotted lines, alert marks, or halos.
- Keep tinted linework to roughly 20-30% of visible strokes unless the user explicitly asks for a more experimental look.
- The viewer should still perceive hand-drawn ink first and mesh atmosphere second.

Avoid:

- Rainbow linework.
- Neon trails.
- Glossy gradient vector outlines.
- Perfectly smooth technical curves.
- Replacing all black strokes with color.

## Linework Grammar

- Use thick near-black strokes with rounded ends.
- Keep joins imperfect and slightly wobbly.
- Simplify hands, houses, documents, nodes, paths, tools, and objects into symbolic marks.
- Prefer one dominant relationship: holding, connecting, filtering, protecting, interrupting, translating, routing, or transforming.
- Avoid fine technical line art and perfect icon geometry.

## Mesh As Meaning

Pick one semantic model before prompting:

### Governance Field

Use for brand systems, compliance, approvals, risk control, policy, local operators, and source of truth.

- Blue/cactus zones: compliant or stable areas.
- Pale fig/pink zones: optional guidance or soft decision space.
- Clay/orange heat: violation, escalation, urgency.
- Black lines: policy routes, approval paths, or dependency lines.
- Mesh-tinted lines: status-bearing routes where governance state needs to be felt, such as blue-green compliant paths, pale optional paths, or clay alert paths.

### Memory Field

Use for brand DNA, knowledge base, preferences, historical learning, and prompt context.

- Ivory/oat zones: stored knowledge and human memory.
- Fig zones: voice, taste, identity.
- Sky/cactus zones: retrieval and reuse.
- Mesh-tinted roots: retrieval paths or memory links that move from stored knowledge into use.

### System Field

Use for product infrastructure, AI workflows, routing, and networks.

- Sky/cactus zones: system paths and stable infrastructure.
- Heather zones: analysis, model reasoning, abstraction.
- Clay accent: bottleneck or failure point.
- Mesh-tinted route segments: system paths that change state as they move through the workflow.

### Tension Field

Use for tradeoffs, alerting, uncertainty, governance pressure, or quality review.

- Calm zones should dominate.
- Warm pressure zones should be small and meaningful.
- Do not make the whole image anxious.
- Clay-tinted line segments should identify exactly where pressure enters the system.

### Transition Field

Use for migration, strategy shift, product evolution, or before/after narrative.

- Let one color family gradually yield to another.
- Avoid hard splits unless the user's concept is explicitly binary.
- A route line may gradually shift tint to show the transition, but the primary drawing still needs black anchor strokes.

## Composition Rules

Square card:

- Use a centered or slightly off-center focal cluster.
- Occupy about 65-75% of the frame.
- Keep at least 10% breathing room.

Wide hero:

- Place the cluster to one side only if copy space is needed.
- Let the mesh continue across the copy-safe area.
- Keep the ivory carrier large enough to read.

16:9 product narrative:

- Use a wider mesh field with one central carrier and a few surrounding nodes.
- Avoid turning the image into a process diagram.

## Symbol Rules

Prefer symbols over text:

- Lock: mandatory rule.
- Dotted path: optional guidance.
- Check mark: approved or healthy.
- Stacked ticks/dots: queue or pending review.
- Alert triangle or warm mark: violation/risk.
- Hand: human oversight, judgment, stewardship.
- House/storefront: local operator or business location.
- Hub/node: source of truth, memory, policy, system center.

Use no text by default. If the user needs text, keep it short and exact.

## Prompting Notes

Name the style carefully:

Good:

```text
Anthropic-inspired editorial linework combined with a semantic mesh-gradient Studio field.
```

Risky:

```text
Anthropic style with mesh gradient background.
```

The second phrasing often produces a simple background swap. The first phrasing tells the model why the gradient exists.

When the user asks for the linework to carry mesh feeling, add:

```text
Let selected connection lines and status marks inherit softened mesh colors while keeping the primary contours near-black. The line system should feel touched by the mesh field, not replaced by rainbow gradient strokes.
```

When the user asks for SVG/layers/editability, do not prompt a raster image model for SVG. Switch to native SVG construction and use the style language as design guidance.

## Failure Modes And Fixes

Flat Anthropic copy:

- Problem: looks like the original art with a gradient behind it.
- Fix: make mesh zones interact with nodes, paths, risk, memory, or transition, and tint selected routes or status marks.

Black-only linework:

- Problem: the image has a mesh background, but all drawing marks remain pure black, so the Studio layer feels separate.
- Fix: add mesh-tinted route segments, dotted paths, halos, or alert edges while keeping main silhouettes near-black.

Over-colored linework:

- Problem: every contour is gradient-colored and the image loses its Anthropic editorial skeleton.
- Fix: restore black as the primary contour color and restrict color to status-bearing paths or small symbolic marks.

Dashboard drift:

- Problem: image becomes panels, charts, screens, or app UI.
- Fix: remove screens and ask for one symbolic object relationship.

Generic AI poster:

- Problem: neon, glowing orbs, robots, tech fog.
- Fix: specify flat editorial linework, restrained mesh, no 3D, no glow-heavy cyber aesthetics.

Stock vector:

- Problem: perfect geometry, thin clean lines, corporate illustration.
- Fix: request uneven rounded black ink, simplified naive forms, imperfect joins.

Too busy:

- Problem: many icons, many status marks, flowchart feeling.
- Fix: keep one carrier shape, one metaphor, 3-6 supporting marks only.

Text-heavy:

- Problem: labels explain the concept.
- Fix: replace labels with symbols and only keep exact user-provided words when required.

## Example Prompt Summary

```text
Illustrate a headquarters brand manager governing a multi-location restaurant brand system. Use one metaphor: a hand steadies a central Brand Kit source while restaurant nodes sit inside a mesh governance field. The mesh is semantic: blue-green zones mean compliant locations, pale fig means optional guidance, and a tiny clay heat spot means violation risk. Keep an irregular ivory carrier and bold black hand-drawn primary contours. Let selected connection lines and the violation path inherit softened mesh colors, with clay only on the risky route. Use symbolic locks/checks/dotted paths/alert marks, no text, no dashboard, no HR cues.
```
