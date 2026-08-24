# AirGradient AlphaSense ADC Module — Hardware

> KiCad hardware design files for the AirGradient AlphaSense ADC module — the interface board that digitizes the AlphaSense electrochemical gas sensors in the [Open Air Max](https://www.airgradient.com/professional/products/open-air-max/) outdoor air quality monitor.

## Overview

A compact 2-layer board carrying two Texas Instruments ADS1115 16-bit ADCs that read the AlphaSense electrochemical sensors — NO₂ (A43F) and O₃ (A431) — and report to the host monitor over I²C. The supply is filtered through a ferrite bead for clean analog readings.

## Design structure

A single KiCad project in `alphasense-adc/`: one schematic sheet and a 2-layer board. (The project was originally named "ADS1115 for AlphaSense NO2-O3", published on Bitbucket as `alphasense-oa-pcb`, and renamed `alphasense-adc` here; the Gerber filenames inside the archived production zip keep the `alphasense-oa-pcb` naming.)

## Repository structure

```
alphasense-adc/           # KiCad project (schematic + board), production/
libraries/                   # Bundled 3D model libraries
```

## Key components

| Function | Part | Ref |
|---|---|---|
| 16-bit I²C ADC | TI ADS1115IDGSR | U1–U2 |
| Supply filter (ferrite bead) | MMZ2012Y152BT000 | FB1 |
| Host connector (1.25 mm, 8-pin) | Molex 53261-0871 | J1, CN1 |
| Sensor header (2×5 IDC, 2.54 mm) | AWHW2-10G | J2 |

## Toolchain

- **KiCad 9** (file format 2024-12). Symbols and footprints are embedded in the design files; bundled 3D models are referenced project-relative — the project opens without any extra library setup.
- **[Fabrication Toolkit](https://github.com/bennymeg/Fabrication-Toolkit)** plugin — generates the Gerber/BOM/CPL production set in JLCPCB-compatible format.
- Active DRC rules are in `alphasense-adc/alphasense-adc.kicad_dru`.

## Fabrication

`alphasense-adc/production/` holds the ready-to-order set: Gerber zip, BOM, designators, and pick-and-place positions (generated with Fabrication Toolkit, LCSC part numbers for assembly at JLCPCB).

## Versioning & releases

Hardware revisions are tagged on this repository. Per-version release notes and the matching production file set are published on the [GitHub Releases](../../releases) page.

## License

This is open-source hardware. The design files in this repository are licensed under the
[Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/) license — see [LICENSE](LICENSE).

You are free to use, modify, and manufacture these designs, including commercially, provided you credit AirGradient and share derivative designs under the same license.

## Maintainers

AirGradient hardware team.
