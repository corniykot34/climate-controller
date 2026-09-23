# Bill of Materials and Dimensional Sources

This file records selected real-world components and where dimensional information comes from.

**Status labels**
- **SOURCE** — manufacturer/vendor documentation
- **PROJECT** — dimension chosen by us
- **VERIFY** — exact variant/dimension must be rechecked before fit-critical modeling

## BOM

### 1. Main carrier PCB

- Part: custom PCB
- Size: **70.0 × 45.0 × 1.6 mm**
- Status: **PROJECT**
- Note: 1.6 mm is our chosen nominal board thickness. This is not presented as a dimension of a purchased PCB.

### 2. MCU module

- Manufacturer: Espressif Systems
- Part: **ESP32-WROOM-32E**
- Module dimensions: **18.0 × 25.5 × 3.1 mm**
- Status: **SOURCE**
- Source: https://documentation.espressif.com/esp32-wroom-32e_esp32-wroom-32ue_datasheet_en.html
- Note: use the mechanical drawing for final placement, antenna keep-out, and pad geometry.

### 3. Temperature / humidity sensor

- Manufacturer: Sensirion
- Part: **SHT31-DIS**
- Package dimensions: **2.5 × 2.5 × 0.9 mm**
- Interface: I²C
- Status: **SOURCE**
- Product source: https://sensirion.com/products/catalog/SHT31-DIS-P
- Note: final PCB placement must account for thermal isolation and exposure to ambient airflow.

### 4. Display module

- Vendor/manufacturer: Adafruit
- Part: **Monochrome 1.3" 128×64 OLED Graphic Display**, product 938
- Board envelope used for preliminary packaging: approximately **35.6 × 33.0 mm**
- Preliminary mounting-hole spacing: **30.5 × 28.0 mm**
- Status: **VERIFY**
- Source: https://www.adafruit.com/product/938
- Note: verify the exact mechanical drawing/download supplied on the product page before cutting the display window or fixing mounting bosses. Do not rely on this summary alone for fit-critical geometry.

### 5. Rotary encoder

- Manufacturer: Bourns
- Family: **PEC11R**
- Body diameter used for preliminary packaging: approximately **12 mm**
- Shaft diameter: **6.0 mm nominal**
- Threaded bushing: **M7 × 0.75**
- Intended configuration: push switch, nominal 20 mm shaft option
- Status: **VERIFY**
- Datasheet: https://www.bourns.com/docs/Product-Datasheets/pec11R.pdf
- Note: PEC11R is a family with multiple shaft/bushing/switch variants. Freeze an exact manufacturer part number before final front-panel geometry.

### 6. Control knob

- Part: custom
- Preliminary dimensions: **Ø18 × 12 mm**
- Status: **PROJECT**
- Note: visual/ergonomic part; dimensions are not frozen.

### 7. USB-C breakout

- Vendor/manufacturer: Adafruit
- Part: **USB Type C Breakout Board**, product 4090
- Preliminary board envelope: approximately **20.4 × 14.2 mm**
- Status: **VERIFY**
- Source: https://www.adafruit.com/product/4090
- Note: verify the current board drawing/CAD and connector projection before final rear-wall opening.

### 8. External low-voltage output connector

- Manufacturer: Phoenix Contact
- Family/reference: **MKDS 1/2-3.5**, 2-position PCB terminal block, 3.5 mm pitch
- Status: **VERIFY**
- Source: https://www.phoenixcontact.com/en-us/products/printed-circuit-board-terminal-mkds-1-2-35-bd12-1888807
- Note: freeze the exact orderable part number and use its manufacturer drawing before final PCB holes and enclosure opening.

## Important

A vendor product page can change. Where possible, store the manufacturer's PDF mechanical datasheet in `references/datasheets/` and record the exact selected part number and document revision here.

Before modeling any fit-critical cutout, boss, standoff, connector opening, or keep-out, re-open the source and verify the selected variant.
