# CC-001 — Component Definition & Packaging Study

**Project:** Desktop Climate Controller  
**Document:** CC-001  
**Revision:** A  
**Date:** 2026-09-23  
**Stage:** Step 1 / Component Definition  
**Status:** PRELIMINARY / FOR REVIEW  
**Units:** mm  
**Fit-critical release:** NOT YET AUTHORIZED

## Scope

This controlled document records the component basis used for the first mechanical packaging study. It separates verified manufacturer dimensions from project-defined values and unresolved placeholder geometry.

No enclosure or fit-critical cutout is released at this stage.

## Revision record

| Rev | Date | Description | Status |
|---|---|---|---|
| A | 2026-09-23 | Initial component definition and workbench packaging study | For review |

## Component specification / BOM

| ID | Component / selected part | Packaging dimensions used | Status | Engineering note |
|---|---|---|---|---|
| C01 | Custom main carrier PCB | 70.0 × 45.0 × 1.6 | PROJECT | Board outline chosen for this concept; mounting holes not frozen. |
| C02 | Espressif ESP32-WROOM-32E | 18.0 ±0.15 × 25.5 ±0.15 × 3.1 ±0.15 | SOURCE | Manufacturer physical dimensions. Antenna keep-out required during layout. |
| C03 | Sensirion SHT31-DIS-B | 2.5 × 2.5 × 0.9 | SOURCE | Locate near ambient ventilation and away from heat sources. |
| C04 | Adafruit 1.3 in OLED, Product 938 | 35.6 × 33.0 board envelope | VERIFY | Final display window and mounting-hole geometry not released. |
| C05 | Bourns PEC11R family | 12 mm package dia.; shaft Ø6.0 ±0.1; M7×0.75; 20 mm shaft option | VERIFY VARIANT | Exact orderable variant must be frozen before panel geometry. |
| C06 | Custom control knob | Ø18 × 12 | PROJECT | Preliminary ergonomic envelope only. |
| C07 | Adafruit USB-C breakout, Product 4090 | 20.4 × 14.2 board envelope | VERIFY | Connector projection, thickness and cutout not released. |
| C08 | Phoenix Contact MKDS 1/2-3.5 family | 2 positions @ 3.5 pitch | VERIFY | Only terminal pitch represented; exact body envelope required. |

### Status legend

- **SOURCE** — dimension confirmed from primary manufacturer documentation.
- **PROJECT** — dimension deliberately selected for this concept.
- **VERIFY** — preliminary/reference value; not authorized for final fit-critical geometry.

## Step 1 workbench status

- Component proxies remain independently editable.
- Main PCB is the workbench origin reference.
- No enclosure has been created.
- No final PCB/component placement has been approved.
- Unverified/reference geometry is explicitly identified as placeholder geometry.
- Step 1 output is a component-definition and packaging-study artifact, not a released mechanical assembly.

## Open items / verification register

| ID | Item | Required action | State | Gate |
|---|---|---|---|---|
| OI-01 | OLED Product 938 | Verify current mechanical drawing, active display window, board thickness, mounting-hole diameter and exact hole centers. | OPEN | Before display window / bosses |
| OI-02 | Bourns PEC11R | Select exact orderable variant and capture complete mechanical drawing. | OPEN | Before front-panel geometry |
| OI-03 | USB-C | Decide breakout vs PCB-mounted receptacle; verify full connector envelope and mating clearance. | OPEN | Before port cutout |
| OI-04 | Phoenix terminal | Freeze exact orderable part; verify body, PCB drill pattern and access clearance. | OPEN | Before PCB holes / opening |
| OI-05 | ESP32 placement | Apply manufacturer antenna placement / keep-out guidance. | OPEN | During layout |
| OI-06 | SHT31 placement | Define ventilation path and thermal separation from heat sources. | OPEN | During layout |
| OI-07 | Fasteners | Select enclosure screw size and thread strategy. | OPEN | Before enclosure details |

## Release condition

Step 1 may be accepted as a **component definition / packaging study**.

It is **not** a fit-critical mechanical release.

Step 2 may begin using verified envelopes, but enclosure features driven by OI-01 through OI-04 remain blocked until the corresponding item is closed.

## Primary sources

1. Espressif Systems — ESP32-WROOM-32E / 32UE datasheet  
   https://documentation.espressif.com/esp32-wroom-32e_esp32-wroom-32ue_datasheet_en.html
2. Sensirion — SHT31-DIS-B product specification  
   https://sensirion.com/products/catalog/SHT31-DIS-B
3. Bourns — PEC11R Series 12 mm Incremental Encoder datasheet  
   https://www.bourns.com/docs/Product-Datasheets/pec11R.pdf
4. Adafruit — 1.3 in 128×64 OLED, Product 938  
   https://www.adafruit.com/product/938
5. Adafruit — USB Type-C Breakout Board, Product 4090  
   https://www.adafruit.com/product/4090
6. Phoenix Contact — MKDS 1/2-3.5 family/product documentation  
   https://www.phoenixcontact.com/

## Document control

The live engineering state remains in `docs/SPEC.md`, `docs/BOM.md`, and `docs/DECISIONS.md`. This file is the controlled Rev A snapshot for Step 1.
