# Desktop Climate Controller

A portfolio-oriented product-development project for CAD Crowd: a compact desktop temperature/humidity controller designed around real electronic components and a manufacturable two-part enclosure.

## Goal

Demonstrate a practical workflow from component selection and spatial layout through enclosure design, prototyping, DFM considerations, and presentation.

The project is modeled primarily in Blender. Precision CAD/STEP deliverables may be added later if the project requires them.

## Current concept

- Desktop temperature/humidity controller
- Approximate enclosure target: 100 × 70 × 30 mm (not yet frozen)
- Two-part enclosure
- Four-screw assembly
- Internal custom carrier PCB
- OLED display
- Rotary encoder with push switch
- ESP32 module
- SHT31 temperature/humidity sensor
- USB-C connection
- Low-voltage external output

## Documentation

- `docs/SPEC.md` — current approved project specification and design requirements
- `docs/BOM.md` — real components, manufacturer part numbers, dimensions, and sources
- `docs/DECISIONS.md` — design decisions and their rationale
- `references/README.md` — reference/datasheet storage policy
- `blender/README.md` — Blender working-file location and modeling notes
- `renders/README.md` — presentation output
- `exports/README.md` — exported manufacturing/interchange files

## Source-of-truth rule

Manufacturer datasheets/product documentation are the primary source for component dimensions. `SPEC.md` is the project's working source of truth. Any project-defined dimension must be explicitly labeled as a design decision rather than a manufacturer specification.
