# Composite UI Annotation Prompt

Use this template as scaffolding for the built-in `image_gen` tool when creating a platform-agnostic composite UI annotation image. The expected output is a generated raster image, not a written prompt, HTML mockup, SVG diagram, Mermaid diagram, or text-only component map.

```text
Create a composite UI annotation image in one go.

Canvas:
A clean landscape composition, 16:9 aspect ratio, presentation-ready. Use a white or very light neutral background with faint grid or blueprint-style guide lines. Keep the image minimal, legible, and uncluttered.

Left side:
Show the design/layout screen as a polished mockup.
Platform: [iOS app / Android app / desktop web app / mobile website / dashboard / etc.]
Screen description: [describe the screen, layout, brand, visual style, colors, content, and key UI elements]
If an input image is provided, use it as the source design and preserve its layout, colors, typography, hierarchy, and visible UI structure.

Right side:
Create a component map explaining how the screen would be built in code. Use clean annotation blocks with concise technical labels. Make the annotations platform-appropriate but not overly verbose.

Include annotations for:
- Page/screen container
- Layout system and responsive constraints
- Header/navigation
- Logo, icons, primary images, or media
- Text hierarchy and typography
- Buttons, inputs, forms, and actions
- Cards, lists, grids, or content sections
- Footer, tab bar, bottom actions, or safe-area behavior
- Spacing, padding, sizing, alignment, and breakpoints

For each annotation block, include:
- Component name
- Suggested implementation label
- Size, spacing, padding, alignment, or layout notes where relevant

Example annotation style for generic component maps:
"ScreenContainer"
"Max width: 1200 px"
"Padding: 24 px"
"Grid: 12 columns"

Example annotation style for SwiftUI:
"VStack(spacing: 20)"
".padding(.horizontal, 24)"
".frame(maxWidth: 360)"

Example annotation style for web:
"<main className='page-shell'>"
"max-width: 1120px"
"gap: 32px"

Callout lines:
Draw thin, precise connector lines from each major UI element on the design screen to its matching annotation block. Use small circular anchor dots at both ends. Keep lines tidy and avoid crossing where possible.

Visual style:
High-fidelity UI mockup plus developer annotation diagram. Minimal, modern, crisp, and readable. Use mostly neutral colors with one accent color: [accent color]. Annotation text should be dark charcoal with secondary measurements in gray.

Text requirements:
All visible text must be crisp, correctly spelled, and legible. Preserve exact UI text from the design where provided.

Avoid:
Watermarks, browser chrome unless requested, messy arrows, illegible code, decorative clutter, extra unrelated screens, heavy gradients, and excessive colors.
```

## Platform Label Hints

Use these only when the user names a platform or the source design makes it obvious.

- SwiftUI: `ZStack`, `VStack`, `HStack`, `Text`, `Image`, `Button`, `.frame`, `.padding`, `.safeAreaPadding`.
- React/web: `PageShell`, `Header`, `main`, `section`, `Card`, `Button`, CSS grid/flex, `max-width`, `gap`, `padding`.
- Jetpack Compose: `Scaffold`, `Column`, `Row`, `Text`, `Icon`, `Button`, `Modifier.padding`, `Modifier.fillMaxWidth`.
- Flutter: `Scaffold`, `SafeArea`, `Column`, `Row`, `Padding`, `SizedBox`, `Text`, `ElevatedButton`.
- Generic: `ScreenContainer`, `LayoutGrid`, `Header`, `ContentSection`, `PrimaryAction`, `FooterActions`.
