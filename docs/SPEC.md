# Project Specification

## 1. Product

**Working name:** Desktop Climate Controller

A compact desktop device that measures ambient temperature and relative humidity, displays the readings locally, and can provide a low-voltage control/output connection for an external device or module.

This is a portfolio demonstration project. The enclosure and internal packaging should be plausible and manufacturable rather than a purely visual shell.

## 2. Design intent

The project should demonstrate:

- 3D product modeling
- enclosure design
- component-driven packaging
- design for 3D printing / rapid prototyping
- practical DFM thinking
- assembly and serviceability
- clear presentation of internal construction

Primary modeling tool: **Blender**.

## 3. Mechanical architecture

Current approved decisions:

- Two-part enclosure: upper/main shell + bottom cover
- Assembly with **4 screws**
- Custom carrier PCB
- PCB mounted on internal standoffs
- Front-facing display
- Rotary encoder/push control accessible from exterior
- USB-C accessible through enclosure
- Ventilation near the temperature/humidity sensor
- Low-voltage external output connector

## 4. Current component envelope

Dimensions below are summarized from `BOM.md`. Always use BOM sources when exact component geometry is required.

| Component | Selected part | Nominal model dimensions |
|---|---|---|
| Main PCB | Custom | 70.0 × 45.0 × 1.6 mm |
| MCU module | Espressif ESP32-WROOM-32E | 18.0 × 25.5 × 3.1 mm |
| Temp/RH sensor | Sensirion SHT31-DIS | 2.5 × 2.5 × 0.9 mm |
| Display | Adafruit 1.3" OLED 128×64, product 938 | PCB approx. 35.6 × 33.0 mm; verify full envelope from source before final cutout |
| Rotary encoder | Bourns PEC11R family | Body approx. Ø12 mm; shaft Ø6 mm; bushing M7 × 0.75; exact variant to be frozen before final geometry |
| Control knob | Custom | Ø18 × 12 mm — preliminary project-defined size |
| USB-C module | Adafruit USB Type-C breakout, product 4090 | Approx. 20.4 × 14.2 mm board; verify exact height/connector envelope from source before final cutout |
| External output | Phoenix Contact MKDS 1/2-3.5 family | 2-position, 3.5 mm pitch; exact variant dimensions to be verified before final geometry |

## 5. Preliminary project-defined dimensions

These are **not manufacturer specifications** and may change after layout:

- Custom main PCB: **70.0 × 45.0 × 1.6 mm**
- Enclosure target envelope: approximately **100 × 70 × 30 mm**
- Custom control knob: approximately **Ø18 × 12 mm**

No enclosure wall thickness, clearances, screw sizes, boss dimensions, ventilation geometry, or port clearances are frozen yet.

## 6. Sensor placement requirement

The SHT31 must be positioned near enclosure ventilation and away from significant heat sources such as the ESP32 module. Final layout should minimize self-heating influence on ambient measurements.

## 7. Modeling sequence

1. Freeze component identities and exact dimensions.
2. Create simplified but dimensionally correct component models.
3. Arrange internal layout.
4. Establish enclosure exterior.
5. Add manufacturable features: openings, ventilation, screw bosses, PCB standoffs, cover interface.
6. Check assembly, clearances, wall thicknesses, access, and printability.
7. Produce one exploded-view presentation image.

Stop after the first exploded-view presentation before expanding into additional renders or publication copy.

## 8. Verification rule

Do not treat conversational estimates or remembered dimensions as authoritative.

For any dimension that affects fit:
1. check `docs/BOM.md`;
2. open the linked manufacturer/source document;
3. verify the exact selected variant;
4. update BOM/SPEC if needed;
5. only then model the final fit-critical geometry.
