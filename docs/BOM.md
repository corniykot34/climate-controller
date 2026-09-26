# Environmental Controller — Hardware BOM

**Status:** working source of truth  
**Revision:** v0.1 — 2026-09-26

This file is the canonical component list for the current Environmental Controller concept.

## Status legend

- **SELECTED** — current project choice; use this part unless a later revision explicitly replaces it.
- **CUSTOM** — project-designed mechanical/electrical part.
- **PROVISIONAL** — current packaging/design assumption; not yet production-frozen.
- **VERIFY** — exact procurement variant or final electrical/mechanical detail still needs confirmation.

---

## 1. User interface

| Function | Part | Key data | Status | Source / note |
|---|---|---|---|---|
| Color display | **Densitron DMA024QZHXNT0-1A** | 2.4" AMOLED, 450×600 native, used landscape; panel 51.56 × 38.72 × 0.90 mm in landscape; active area 48.96 × 36.72 mm | **SELECTED** | https://www.densitron.com/files/library/files/products/202505/Product%20Spec_DMA024QZHXNT0-1A_v0.1.pdf |
| Touch layer | **Custom capacitive-touch electrode / FPC layer** | Broad touch-capable front area behind cover; wheel/shaft mechanical zone excluded | **CUSTOM / PROVISIONAL** | Intended to be read by ESP32-S3 touch inputs; final electrode geometry requires prototype tuning |
| Rotary encoder | **Bourns PEC11H-4115F-S0020** | Push switch; Ø6 mm D-shaft; 15 mm shaft; rear body depth ≈6.5 mm; body ≈11.8 × 12.8 mm | **SELECTED** | https://www.bourns.com/docs/product-datasheets/pec11h.pdf |
| Rotary wheel | **Custom glossy wheel** | Ø52 mm × 6 mm current design target | **CUSTOM / SELECTED DESIGN** | External visual geometry is part of the chosen design direction |

### Interaction decision

- **Wake from deep sleep:** press the rotary encoder.
- Touch sensing is enabled after wake.
- The display is not intended to remain continuously on.

---

## 2. Main controller and sensing

| Function | Part | Key data | Status | Source / note |
|---|---|---|---|---|
| MCU / Wi-Fi / BLE | **Espressif ESP32-S3-WROOM-2-N32R16V** | 32 MB flash, 16 MB PSRAM; module 25.5 × 18.0 × 3.1 mm | **SELECTED** | https://documentation.espressif.com/esp32-s3-wroom-2_datasheet_en.html |
| Temperature / humidity | **Sensirion SHT40** | 1.5 × 1.5 × 0.5 mm; I²C | **SELECTED** | https://sensirion.com/products/catalog/SHT40 |

### Sensor placement requirements

- SHT40 must sit in a thermally isolated edge/tongue region.
- Keep it away from ESP32, charging circuitry, AMOLED power circuitry, and battery heat.
- Preserve a direct future ambient-air path.
- Final vent geometry is not yet frozen.

---

## 3. Battery and charging

| Function | Part | Key data | Status | Source / note |
|---|---|---|---|---|
| Battery | **A&S Power AS405070** | 1S Li-Po, 3.7 V, 1700 mAh; cell class ≈4.0 × 50 × 70 mm | **SELECTED BASELINE / VERIFY SKU** | https://www.as-battery.com/ — exact protected pack / lead option must be frozen before procurement |
| Charger / power path | **TI BQ25185** | 1-cell Li-Ion/Li-Po charger with power path and battery temperature monitoring | **SELECTED** | https://www.ti.com/product/BQ25185 |
| Battery fuel gauge | **TI BQ27427** | I²C single-cell fuel gauge | **SELECTED** | https://www.ti.com/product/BQ27427 |
| Battery temperature sensing | **NTC thermistor** | Mounted thermally to cell for BQ25185 TS input | **VERIFY** | Exact NTC value / package to be frozen at schematic stage |

### Battery packaging assumptions

- Current mechanical design envelope for the selected battery: **72.5 × 50.5 × 5.0 mm**.
- This 5.0 mm thickness is a **project packaging allowance**, not a manufacturer cell dimension.
- Do not rigidly clamp the pouch.
- Preserve swelling/assembly allowance and electrical insulation from PCB solder/features.
- Current autonomy target: **months, not weeks**; final verified battery-life figure requires firmware duty-cycle and measured display/system consumption.

---

## 4. Power rails

| Function | Part | Key data | Status | Source / note |
|---|---|---|---|---|
| Main low-power rail | **TI TPS63900** | Buck-boost regulator | **SELECTED** | https://www.ti.com/product/TPS63900 |
| AMOLED positive rail | **TI TPS63900** | Second device dedicated to display supply | **SELECTED** | https://www.ti.com/product/TPS63900 |
| AMOLED negative rail | **TI TPS63700** | Inverting DC/DC for OLED negative rail | **SELECTED** | https://www.ti.com/product/TPS63700 |
| TPS63900 inductors | **Murata DFE252012F-2R2M**, ×2 | 2.2 µH; 2.5 × 2.0 × 1.2 mm | **SELECTED** | Use one per TPS63900 |
| TPS63700 inductor | **Murata DFE252012F-4R7M=P2** | 4.7 µH; 2.5 × 2.0 × 1.2 mm max | **SELECTED** | Murata DFE252012F family; current rating provides headroom over TPS63700 typical 1 A switch limit |

### Power / thermal requirements

- Do not place charger or display-power hot zones directly behind the battery.
- Keep power zones away from SHT40.
- Use PCB copper / vias appropriately for thermal spreading.
- AMOLED rails must be hardware-disableable during sleep.

---

## 5. USB-C

| Function | Part | Key data | Status | Source / note |
|---|---|---|---|---|
| USB-C receptacle | **GCT USB4105** | Horizontal PCB top mount; approx. 8.94 mm max width × 7.35 mm length × 3.31 mm profile | **SELECTED** | https://gct.co/connector/usb4105 |
| CC resistors | **5.1 kΩ Rd**, ×2 | CC1 / CC2 sink configuration | **SELECTED VALUE / VERIFY PACKAGE** | Package to be frozen with schematic |
| USB ESD protection | **TBD low-capacitance USB ESD device** | Protect USB pins | **VERIFY** | Freeze during schematic design |

USB-C is for **charging and service/data** and is accessed from the **bottom edge**.

---

## 6. PCB and mechanical project parts

| Function | Part | Key data | Status |
|---|---|---|---|
| Main PCB | **Custom PCB** | Current mechanically rebuilt PCB ≈70 × 50 × 1.6 mm | **PROVISIONAL** |
| Front cover | **Custom glossy black touch-capable cover** | Current packaging assumption 1.5 mm | **PROVISIONAL** |
| Rear / side enclosure | **Custom enclosure** | Current wall assumption 1.5 mm | **PROVISIONAL** |
| Display adhesive / optical stack | **OCA / foam / adhesive layer** | Current nominal allowance 0.25 mm | **PROVISIONAL** |
| AMOLED flex bend | **FPC routing allowance** | Current packaging assumption R = 3 mm | **PROVISIONAL / VERIFY** |

### Current packaging result

Current blockout result, **not production-frozen**:

- Body: approximately **76 × 120 × 20 mm**
- Installed depth with wheel: approximately **27 mm**
- Wheel: **Ø52 × 6 mm**
- Current PCB: approximately **70 × 50 × 1.6 mm**

These dimensions must be rechecked after replacing blockout components with realistic mechanical models.

---

## 7. Support components not yet production-frozen

The following are intentionally not assigned final manufacturer P/Ns yet:

- USB ESD device
- battery NTC
- regulator capacitors and feedback passives
- decoupling capacitors
- encoder debounce components
- touch-series / protection components
- PCB connectors for display / battery as required
- final battery connector / lead configuration

These are to be frozen during schematic / PCB development, not guessed during mechanical blockout.

---

## 8. Rules for future work

1. **Check this file before giving Blender/MCP component dimensions.**
2. Do not resurrect old parts from the discarded first architecture unless this BOM is explicitly revised.
3. Manufacturer dimensions override old Blender placeholder geometry.
4. Any component replacement must update this file first.
5. Packaging dimensions marked PROVISIONAL are not production claims.
6. The design remains cordless in normal use: USB-C is for occasional charging/service.
