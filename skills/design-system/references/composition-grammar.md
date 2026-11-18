# Composition Grammar

Reference for `design-system`. Palette, layout, voice, and density are separate axes. This file owns the mix rules. Token values stay in `token-and-component-specs.md`. Domain fit stays in the **ux-product-shaper** archetype catalog.

## 1. Record

Write one composition ID:

`palette × layout × voice × density × primary-module`

Example: `aizome-indigo × L4 × V4 × high-density × chart`.

`data-preset` is the palette ID (one of the 13). `data-layout` is `L1`–`L6`. `data-voice` is `V1`–`V4`. When `data-layout` or `data-voice` is absent, use that palette's canonical triple. New work sets both attributes whenever they differ from the canonical triple.

Primary module is one of `thesis`, `table`, `chart`, `canvas`, `form`.

## 2. Expressive Structure & Relaxed Constraints

These slots provide structural discipline while preserving expressive aesthetics:

- Palette, voice, layout, and spacing come from the published catalogs. No 14th hue, no 5th voice. Display and hero headings (`--font-display`) may use font weight up to `700` for bold expressiveness, while UI labels use `500` and body uses `400`.
- At most 2 primary families plus 1 monospace face, taken from the chosen voice.
- Neutral base surface plus 1 primary accent, allowing controlled secondary accents (such as warm gold, subdued indigo, or muted moss) for layered depth or secondary tags. Status colors stay semantic.
- Body text >= 4.5:1. Large text and UI boundaries >= 3:1. Measure both themes.
- Subtle box shadows and soft border depth (e.g. `box-shadow: 0 1px 3px rgba(0,0,0,0.04), 0 4px 12px rgba(0,0,0,0.03)`) are permitted for tactile card elevation, but no garish neon, purple-blue hero gradients, emoji icons, or unrequested chrome.
- No nested bordered cards inside cards.
- Surface mode matches the job. Split incompatible postures into two screens.
- One focal point, one primary CTA, the 8 states, and WCAG 2.2 AA targets.
- Chart colors stay semantic. Do not place the dossier clay series on `aizome-indigo`, `plotly-white`, `ggplot2-grammar`, or `geist-zinc`.
- Family grammar holds: `L5` cells stay flush hairlines; `simple-white` keeps Tufte spines; `apple-hig` squircles do not sit inside an `L5` lattice; `material-you` stays shadowless; `V2` italics do not set a dense numeric table.
- Radius stays on the shared scale, except the published family radii: `apple-hig` 16px squircles, `material-you` 24px cards and pill indicators.

Density defaults from the surface mode. The owner may lock the other value in the pair.

| Surface mode | Density |
| :--- | :--- |
| Mode A | Contemplative. Balanced only when the owner locks it. |
| Mode B | High-density. Balanced only when the owner locks it. |
| Mode C | Balanced. High-density only when the owner locks it. |

## 3. Open Choices (at most 4)

When the owner did not lock the axis:

1. Which legal palette in the job band.
2. Which legal layout in the job band.
3. Which legal voice in the job band.
4. Which primary module, justified in one sentence from the screen's primary question.

A fifth invention (new color, extra chrome, extra font) fails review.

## 4. Job Bands

Rows are ordered. The canonical triple is legal on that palette's best-fit job. Warm Zen presets (`dossier`, `zen-garden`, `chronicle`, `sumi-ink`) are available across all job bands alongside specialized domain archetypes:

| Job band ID | Legal compositions |
| :--- | :--- |
| `editorial-brief` | `dossier×L1×V1`, `sumi-ink×L4×V1`, `chronicle×L3×V2`, `zen-garden×L2×V2` |
| `long-form` | `zen-garden×L2×V2`, `dossier×L2×V1`, `sumi-ink×L2×V1`, `chronicle×L3×V2` |
| `ops-monitor` | `dossier×L5×V3`, `sumi-ink×L5×V3`, `shoji-grid×L5×V3`, `geist-zinc×L5×V4`, `aizome-indigo×L1×V3` |
| `quant-surface` | `dossier×L1×V3`, `zen-garden×L2×V3`, `plotly-white×L1×V4`, `simple-white×L2×V4`, `ggplot2-grammar×L5×V3`, `aizome-indigo×L4×V3` |
| `studio-night` | `yugen-noir×L6×V2`, `sumi-ink×L6×V1`, `dossier×L6×V1`, `geist-zinc×L6×V4` |
| `native-consumer` | `dossier×L1×V4`, `zen-garden×L1×V4`, `apple-hig×L1×V4`, `material-you×L6×V4` |
| `developer-console` | `dossier×L5×V3`, `sumi-ink×L5×V3`, `shoji-grid×L1×V3`, `geist-zinc×L5×V3`, `aizome-indigo×L5×V3` |

## 5. Selection by Semantic Intent

1. An axis the owner names is fixed.
2. When requirements are open or delegated, select by **semantic intent**: default to the honored Zen palette (`dossier` or appropriate warm Zen preset `zen-garden`, `chronicle`, `sumi-ink`) matching the task's editorial and cognitive requirements.
3. Adapt to context: if the user prompt, domain, or environment calls for platform-native conventions (macOS/iOS), statistical paper output, or developer CLI ergonomics, select the best semantic match from the job band (e.g. `apple-hig` for native apps, `plotly-white` or `simple-white` for pure statistical plots, `geist-zinc` for developer consoles).
4. When the user explicitly requests customization or comparison, offer up to 3 unranked legal rows from the job band.
5. If a locked axis leaves no row in the band, stop under Contradiction Halt. Ask the owner to change the axis or the band.
6. Write one sentence for the primary module. Same product and same job band reuse the recorded composition. Variety is across job bands.

## 6. Illegal Mixes

Fail the composition when any line is true:

- `L2` with high-density.
- `L5` with squircle cards or nested cards.
- `V2` as the face of a dense numeric table.
- An accent used as a status color, or uncontrolled competing primary accents (controlled secondary accent is permitted for tags or secondary indicators).
- Heavy drop shadows on a `material-you` surface (which relies on tonal surface elevation).
- A warm decorative gradient on `geist-zinc`.
- A palette, layout, or voice ID outside the catalogs.
- Pure `#000000` ink on a warm-paper palette. `apple-hig` dark canvas may keep its published `#000000`.
