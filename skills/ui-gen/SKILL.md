---
name: ui-gen
description: Generate composite UI annotation images with the imagegen skill and built-in image_gen tool. Use when the user asks to create an annotated UI mockup, implementation map, SwiftUI/React/Compose/component annotation image, callout-line diagram from a screenshot to code notes, design-to-code visual explanation, or any image showing a design/layout screen beside a component map with connector lines.
---

# UI Gen

## Overview

Use this skill only to generate a single composite image with the `imagegen` skill and built-in `image_gen` tool.

The generated image must combine:

1. A polished design/layout screen.
2. A component map explaining how the screen would be built.
3. Connector lines between visible UI elements and their implementation annotations.

Do not stop at a written prompt when the user asks for an image. Do not substitute HTML, SVG, Mermaid, CSS, or a text-only component map for the image. Use the prompt template only as scaffolding for the `image_gen` request.

Default to platform-agnostic wording unless the user names a stack such as SwiftUI, React, Android Compose, Flutter, HTML/CSS, or a design-system component library.

## Workflow

1. Invoke image generation.
   - Use the `imagegen` skill and the built-in `image_gen` tool by default.
   - Send one strong structured prompt that asks for the full composite image in a single generation.
   - If the user provides an existing screenshot or mockup, treat it as the source design to preserve in the generated composite.
   - If the user asks for this skill but only asks for a reusable text prompt, explain that `ui-gen` is for generating the image; then provide a prompt only if they explicitly confirm they do not want an image.

2. Identify the platform and annotation dialect.
   - iOS: use SwiftUI-style labels such as `VStack`, `ZStack`, `.padding`, `.frame`, `Button`, `Text`.
   - Web: use React/HTML/CSS-style labels such as `<main>`, `Header`, `Grid`, `Button`, `max-width`, `gap`, `padding`.
   - Android: use Jetpack Compose-style labels such as `Column`, `Row`, `Modifier.padding`, `Button`, `Text`.
   - Flutter: use `Scaffold`, `Column`, `Padding`, `SizedBox`, `Text`, `ElevatedButton`.
   - Unknown or mixed: use generic component names with neutral sizing notes.

3. Build the `image_gen` prompt.
   - Specify a landscape canvas, usually `16:9`.
   - Place the design mockup on the left and the component map on the right.
   - Require thin callout lines with small anchor dots at both ends.
   - Ask for crisp, legible annotation text and exact preservation of any visible UI copy.
   - Include size, spacing, padding, alignment, and layout notes when useful.
   - Keep the visual system restrained: mostly neutral background, one accent color for callouts and highlights.

4. Map the screen into annotations.
   Include blocks for the major UI structure:
   - Page or screen container.
   - Layout system and responsive constraints.
   - Header or navigation.
   - Logo, icon, hero image, or primary media.
   - Text hierarchy and typography.
   - Inputs, buttons, forms, and actions.
   - Cards, lists, grids, or content sections.
   - Footer, tab bar, bottom actions, or safe-area behavior.

5. Keep annotation density controlled.
   - Prefer 6-10 callouts for a normal screen.
   - Use short code-like labels, not full implementation files.
   - Put measurements on their own lines: `Width: 320`, `Padding: 24`, `Gap: 16`.
   - Avoid long paragraphs inside annotation blocks.

6. Validate the generated image.
   Check that the result includes both halves, callout lines, readable labels, correct UI copy, sizing/spacing notes, and no unrelated screens or decorative clutter.

## Image Prompt Template

Read `references/composite-ui-annotation-prompt.md` when building the prompt for the `image_gen` tool.

Adapt that template into the tool prompt rather than returning it verbatim, unless the user explicitly confirms they only want a prompt and no image.

## Prompting Notes

- Name the source design explicitly: screenshot, mockup, wireframe, product page, mobile screen, dashboard, or app view.
- If an input image is provided, say to preserve its layout, colors, typography, hierarchy, and visible text.
- If no input image is provided, describe the design screen in enough detail for the generator to create it.
- For platform-specific requests, make the component map feel native to that platform, but keep labels concise.
- For code text, request monospaced, crisp, correctly spelled annotations.
- For callouts, request tidy routing and minimal crossing.
- For dimensions, use the user's units when known; otherwise use platform defaults: points for iOS, dp for Android, pixels/rem for web, logical pixels for Flutter.
