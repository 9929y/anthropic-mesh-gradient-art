# Layered SVG Output

Use this reference when the user asks for SVG, vector output, editable layers, Figma/Illustrator reuse, or layer separation.

## Key Decision

In SVG mode, create a real standalone SVG directly. Do not use raster image generation and do not embed PNG/JPEG assets with `<image>`.

The goal is not photorealistic texture. The goal is an editable vector interpretation of the Anthropic-mesh visual grammar:

- Semantic mesh-gradient field.
- Irregular ivory carrier/source shape.
- Bold near-black editorial linework.
- Selected mesh-tinted route/status/edge marks.
- Simple symbolic props that can be edited as separate groups.

## Recommended Canvas

Choose one of these unless the user specifies another size:

- Square card: `1200 1200`
- Presentation or product narrative: `1600 900`
- Hero: `1920 1080`

Always set an explicit `viewBox`, `width`, and `height`.

## Required Layer Groups

Use named groups so the result imports cleanly into Figma or Illustrator:

```xml
<g id="mesh-gradient-background">...</g>
<g id="ivory-carrier">...</g>
<g id="primary-ink-linework">...</g>
<g id="mesh-tinted-linework">...</g>
<g id="persona-figure">...</g>
<g id="symbols-and-props">...</g>
<g id="optional-text">...</g>
```

Omit `optional-text` only when no text is used. Keep each object family in its own group rather than flattening the whole illustration into one path.

## SVG Structure

Use this high-level structure:

```xml
<svg xmlns="http://www.w3.org/2000/svg" width="1600" height="900" viewBox="0 0 1600 900" role="img" aria-labelledby="title desc">
  <title id="title">...</title>
  <desc id="desc">...</desc>
  <defs>
    <style>
      :root {
        --ink: #141413;
        --ivory: #FAF9F5;
        --cactus: #BCD1CA;
        --sky: #6A9BCC;
        --oat: #E3DACC;
        --heather: #CBCADB;
        --fig: #C46686;
        --clay: #D97757;
      }
    </style>
    <!-- gradients here -->
  </defs>
  <!-- required groups here -->
</svg>
```

Use `<title>` and `<desc>` to describe the persona, concept, and semantic mesh role.

For broad compatibility, put final color values directly on visible SVG elements or classes. Avoid relying on CSS custom properties such as `var(--ink)` for core fills or strokes, because some previewers and import tools may fail those values and render fallback black.

## Mesh Gradient Construction

SVG does not have a native CSS-style mesh gradient primitive. Approximate it with overlapping soft radial gradients, translucent blobs, and optional low-opacity linear gradients.

Good SVG mesh techniques:

- Full-bleed base rectangle in oat or ivory-adjacent color.
- Several large blurred circles or organic paths using `radialGradient`.
- One or two small semantic warm zones for risk or urgency.
- Low-opacity overlays instead of saturated rainbow fields.

Use gradients in `<defs>` with semantic ids, for example:

```xml
<radialGradient id="gradient-compliance" cx="35%" cy="32%" r="55%">
  <stop offset="0%" stop-color="#BCD1CA" stop-opacity="0.92"/>
  <stop offset="100%" stop-color="#BCD1CA" stop-opacity="0"/>
</radialGradient>
<radialGradient id="gradient-risk" cx="78%" cy="28%" r="26%">
  <stop offset="0%" stop-color="#D97757" stop-opacity="0.55"/>
  <stop offset="100%" stop-color="#D97757" stop-opacity="0"/>
</radialGradient>
```

If blur is used, keep it simple:

```xml
<filter id="soft-blur">
  <feGaussianBlur stdDeviation="45"/>
</filter>
```

Do not rely on heavy filters for the main linework. Filters should only soften gradient fields.

## Painterly SVG Mode

Use painterly SVG mode when the user says the clean SVG lacks drawing feeling, feels too diagram-like, or should look closer to an editorial illustration while staying layered.

Painterly SVG should still be native vector SVG. Do not solve this by embedding a generated PNG.

Add drawing feeling through a restrained combination of:

- Paper grain: a low-opacity `feTurbulence` layer over the background and/or clipped inside the ivory carrier.
- Rough ink: a mild `feDisplacementMap` filter on linework groups, usually scale `2-4` on a `1600 x 900` canvas.
- Duplicate strokes: one primary black stroke plus one thinner low-opacity companion stroke with a slightly different path or position.
- Organic washes: irregular filled paths with radial gradients, not only perfect blurred circles.
- Imperfect symbols: hand-wobbled storefronts, documents, hands, counters, or campaign cards instead of precise icon geometry.

Good painterly structure:

```xml
<filter id="rough-ink" x="-5%" y="-5%" width="110%" height="110%">
  <feTurbulence type="fractalNoise" baseFrequency=".02" numOctaves="2" seed="17" result="warp"/>
  <feDisplacementMap in="SourceGraphic" in2="warp" scale="2.6" xChannelSelector="R" yChannelSelector="G"/>
</filter>

<g id="primary-ink-linework" filter="url(#rough-ink)">
  <path d="..." fill="none" stroke="#141413" stroke-width="12" stroke-linecap="round"/>
  <path d="..." fill="none" stroke="#141413" stroke-width="7" opacity=".32" stroke-linecap="round"/>
</g>
```

Keep the effect delicate. If the file feels like a filter demo, reduce texture. The persona and metaphor should stay clearer than the grain.

Tradeoff:

- More painterly SVG means more filters and companion paths.
- Some design tools may import filters as appearance effects or rasterized effects.
- Preserve editability by keeping the main objects and strokes in separate named groups even when filters are used.

## Linework Rules For SVG

Preserve Anthropic-style readability:

- Main contours use `stroke="#141413"`.
- Use `stroke-linecap="round"` and `stroke-linejoin="round"`.
- Use thick strokes, usually `8` to `18` px on a `1600 x 900` canvas.
- Make curves slightly imperfect with cubic Beziers or polylines.
- Use `fill="none"` for most linework and simple flat fills for carrier or props.

Use mesh-tinted strokes only for secondary meaning:

- Stable paths: cactus/sky gradient strokes.
- Optional guidance: fig/heather dotted strokes.
- Risk/violation: short clay stroke, alert edge, pulse, or triangle.
- Source-of-truth routes: black primary route with a subtle colored echo nearby.

Keep tinted linework to about 20-30% of the visible strokes. Avoid fully gradient-coloring the persona outline, hands, faces, or main props.

## Irregular Carrier Shape

The carrier is not a rounded rectangle or UI card. Draw it as one organic ivory path, for example:

```xml
<path d="M260 165 C410 92 650 112 820 150 C1010 192 1220 156 1350 270 C1465 370 1415 590 1300 690 C1160 815 920 770 735 785 C520 802 322 790 215 658 C108 525 120 250 260 165 Z"
      fill="#FAF9F5"/>
```

The shape should feel like a conceptual stage, source field, memory cell, or governance island. It should hold the main metaphor without becoming a dashboard panel.

## Symbol Library

Prefer small reusable symbolic shapes:

- Lock: mandatory rule.
- Dotted path: optional guidance.
- Check: approved or healthy.
- Stacked dots/ticks: queue or pending review.
- Triangle or short clay mark: risk/violation.
- Storefront: local restaurant location.
- Central node/source: brand kit, memory, HQ, system truth.
- Hand/person: stewardship, judgment, operator action.

Keep symbols simple enough to edit. Avoid tiny labels unless the user asks for exact text.

## SVG QA

Before returning the result, inspect the file:

- It opens as SVG source and contains no `<image>` tag.
- It has `<title>` and `<desc>`.
- It has the required named groups.
- Main contour strokes are near-black and visibly thicker than secondary route lines.
- Mesh-tinted strokes are semantic, not decorative rainbow outlines.
- The background covers the full viewBox.
- The concept remains one metaphor at thumbnail scale.
- The file imports as editable vector layers rather than one flattened blob.

Report any limitations honestly. SVG can be layered and editable, but it will have less natural texture than a bitmap image generation result.
