# A&S Power AS405070 — Battery Mechanical Reference

**Role:** rechargeable 1S Li-Po pouch cell  
**Project status:** SELECTED BASELINE / EXACT PACK VARIANT VERIFY  
**Manufacturer family/source:** https://www.szaspower.com/landingpage/lithium-polymer-battery.html  
**Certification listing:** https://www.szaspower.com/company-news/lithium-polymer-battery-product-certification-form-as-power-battery.html

## Verified published cell data

- Model family: **AS405070**
- Nominal voltage: **3.7 V**
- Capacity: **1700 mAh**
- Published nominal cell size: **4.0 × 50.0 × 70.0 mm**
- Listed certifications include **UL1642 / UN38.3 / CE**.

## Current project mechanical envelope

For packaging studies use:

- **72.5 × 50.5 × 5.0 mm**

This is a **project allowance**, not a manufacturer drawing dimension.

It intentionally includes space for:
- pouch / tab / lead reality
- assembly tolerance
- swelling allowance

## Packaging rules

- Do not rigidly clamp the pouch between hard parts.
- Maintain at least **0.5 mm XY** to smooth retainers/walls in blockout.
- Preserve at least **1.0 mm Z allowance** on the pouch side where deformation/swelling may occur.
- If facing populated PCB or solder joints, keep at least **1.0 mm separation plus insulation**.
- Keep charger/display-power hot zones away from the cell.
- NTC thermal contact to the cell is required for the charger TS input.

## Important limitation

A complete manufacturer mechanical drawing for the exact protected pack / lead / connector configuration has **not yet been obtained**.

Therefore:
- do not model tabs, PCM board, wires or connector as verified geometry yet;
- exact pack SKU, wire exit, PCM placement and connector must be frozen before the final enclosure design;
- this battery is suitable as the current capacity/size baseline, but not yet as a production-frozen battery assembly.
