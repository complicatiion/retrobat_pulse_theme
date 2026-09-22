# RetroBat Compatibility Audit — Pulse Theme

Audit date: 2026-09-22

## Baseline

RetroBat's EmulationStation repository is a Windows build/fork of `batocera-emulationstation`. Pulse Theme already targets theme format version 7, so a complete rewrite is not required.

## Findings

| Area | Original | RetroBat result | Action |
|---|---|---|---|
| Theme format | `formatVersion 7` | Compatible | Kept |
| `controllerActivity` | Used in screen view | Supported | Kept |
| `batteryIndicator` | Used in screen view | Supported | Kept |
| Battery/network paths | Relative SVG paths | Compatible | Kept |
| `menuText/scrollSound` | Present | Not a supported `menuText` property | Removed |
| Gamelist `textlist/scrollSound` | Present | Supported | Kept |
| System `carousel/scrollSound` | Present | Supported | Kept |
| Grid `md_rating` | Declared as `<text>` | Rating metadata expects a rating component | Changed to `<rating>` |
| Background subset | MIX9/MIX10 reused names `mix7`/`mix8` | Duplicate subset names are inconsistent | Changed to `mix9`/`mix10` |
| Conditional max logo | References undefined `system-view-style` subset; same value as default | No useful effect | Removed |
| `${system.theme}` | Used for art lookup | Supported | Kept |
| Relative `/` paths | Used throughout | Valid on Windows EmulationStation | Kept |
| Batocera install path | `/userdata/themes/` | Wrong for RetroBat | Docs changed |

## About `<batteryIndicator>`

It is not removed. The current parser explicitly knows the `batteryIndicator` element and its relevant properties, including `pos`, `size`, `itemSpacing`, `horizontalAlignment`, `networkIcon`, `planemodeIcon`, `incharge`, `full`, `at75`, `at50`, `at25`, `empty`, `visible`, and `zIndex`.

On a desktop PC without a meaningful system battery value, the visual result may naturally differ from a handheld/laptop. That is a runtime-data question, not an XML syntax incompatibility.

## System art / RetroBat systems

The theme uses `./art/${system.theme}.png`, which is the correct dynamic mechanism. RetroBat supports additional systems beyond a typical Batocera installation. If a newly added RetroBat system has no matching PNG in the original `art` directory, that is an asset coverage issue rather than an XML syntax error. The theme also retains `logoText` as a textual system-name element.

## What was deliberately not changed

- Visual layout coordinates
- Wallpaper choices
- Fonts
- Original sound effects outside the unsupported menu property
- Gamelist layout geometry
- Theme accent colors
- Original artwork and image assets
- `theme2.xml` purple-accent concept

This keeps the RetroBat edition visually aligned with the original Pulse Theme instead of turning the compatibility pass into a redesign.
