# Espressif ESP32-S3-WROOM-2-N32R16V — Mechanical Reference

**Role:** MCU + Wi-Fi + Bluetooth LE module  
**Project status:** SELECTED  
**Manufacturer datasheet:** https://documentation.espressif.com/esp32-s3-wroom-2_datasheet_en.html  
**Manufacturer PDF:** https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-2_datasheet_en.pdf

## Verified mechanical data

- Module: **ESP32-S3-WROOM-2-N32R16V**
- Overall size: **18.0 ±0.2 × 25.5 ±0.2 × 3.1 ±0.15 mm**
- On-board PCB antenna.
- Recommended land pattern and antenna keepout are defined in the datasheet.
- Espressif provides an official STEP model for the module.

## Modeling rules

- Prefer the official Espressif STEP model over a hand-built placeholder.
- Place the antenna end at or near the main-PCB edge.
- Do not place battery, dense copper, shielding, or large conductive parts directly behind the antenna area.
- Preserve the manufacturer-recommended antenna keepout geometry; do not replace it with the old generic 15 mm box if the actual land-pattern/placement drawing is available.
- EPAD soldering is optional mechanically but improves thermal performance; final PCB design must follow Espressif layout guidance.

## Thermal / packaging note

The module itself is not the dominant steady-state heat source in the intended sleep-heavy duty cycle, but it must still have a real copper/ground thermal path and must not be buried directly against the battery or SHT40 sensing zone.
