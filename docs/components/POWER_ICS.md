# Power / Charging ICs — Mechanical Reference

These ICs are mechanically small. For the realistic PCB model, use accurate package envelopes and footprints, but do not spend modeling time on package cosmetic detail.

## TI BQ25185 — charger / power path

**Status:** SELECTED  
**Source:** https://www.ti.com/product/BQ25185

- Package: **WSON DLH-10**
- Body: **2.2 × 2.0 mm**
- Package height class: **0.8 mm max**
- Exposed thermal pad; charger thermal design must be represented by PCB copper / placement, not a large 3D heatsink.
- Keep away from SHT40 and do not place directly behind the battery.

## TI TPS63900 — buck-boost regulator ×2

**Status:** SELECTED  
**Source:** https://www.ti.com/product/TPS63900

- Package: **WSON DSK-10**
- Body: **2.5 × 2.5 mm**
- Height: **0.8 mm max**
- Use two devices:
  1. main low-power rail
  2. AMOLED positive rail
- TI states a compact complete solution area around **21 mm²**, so the PCB model must include the surrounding inductor/capacitor area rather than showing the IC alone.

## TI TPS63700 — AMOLED negative rail

**Status:** SELECTED  
**Source:** https://www.ti.com/product/TPS63700

- Package: **VSON DRC-10**
- Body: **3.0 × 3.0 mm**
- Height: **1.0 mm max**
- Requires external 4.7 µH inductor and associated capacitors.
- Keep in the display-power zone, away from SHT40.

## TI BQ27427 — battery fuel gauge

**Status:** SELECTED  
**Source:** https://www.ti.com/product/BQ27427

- Package: **DSBGA YZF-9**
- Body from current TI package drawing: approximately **1.59–1.65 mm × 1.55–1.61 mm**
- Height: **0.625 mm max**
- Ball pitch: **0.5 mm**
- Mechanically negligible for enclosure depth but should be represented on a realistic populated PCB.

## Modeling rule

These ICs do **not** need individual hero-level models.
Use correct package dimensions, orientation marks if useful, and realistic surrounding passives/zones.
