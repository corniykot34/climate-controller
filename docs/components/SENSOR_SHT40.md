# Sensirion SHT40 — Mechanical Reference

**Role:** ambient temperature + relative-humidity sensor  
**Project status:** SELECTED  
**Manufacturer page:** https://sensirion.com/products/catalog/SHT40

## Verified data

- Package: DFN
- Size: **1.5 × 1.5 × 0.5 mm**
- Supply: **1.08–3.6 V**
- Interface: **I²C**
- Average supply current: **0.4 µA**
- Typical RH accuracy: **±1.8 %RH**
- Typical temperature accuracy: **±0.2 °C**

## Modeling rules

The package itself may be represented as a simple accurate DFN block; visual realism of the chip is less important than correct placement.

The mechanically significant geometry is the **sensor environment**, not the chip body:
- locate at a PCB edge / thermally isolated tongue;
- preserve an ambient-air path;
- keep away from ESP32, charger, display-power converters and battery;
- avoid a sealed internal air pocket;
- final PCB should use thermal-isolation strategy such as reduced copper / narrow neck / slots where practical.

Do not create final vent geometry until the enclosure architecture is ready.
