# Component Mechanical References

This directory contains the project’s mechanical reference cards for components that materially affect enclosure geometry, PCB placement, access openings, keepouts, thermal zoning, or assembly.

## Mechanical reference set

| Component | Card | Drawing / source status | Modeling status |
|---|---|---|---|
| Densitron DMA024QZHXNT0-1A AMOLED | `DISPLAY_DMA024QZHXNT0-1A.md` | Official mechanical drawing available | Ready; FPC bend radius remains provisional |
| Bourns PEC11H-4115F-S0020 encoder | `ENCODER_PEC11H-4115F-S0020.md` | Official dimensional drawing available | Ready |
| GCT USB4105 USB-C receptacle | `USB_C_USB4105.md` | Official drawing + footprint available | Ready; exact shell-stake suffix still VERIFY |
| A&S Power AS405070 battery | `BATTERY_AS405070.md` | Published cell dimensions; exact finished-pack drawing not yet obtained | Conservative pack envelope only |
| ESP32-S3-WROOM-2-N32R16V | `ESP32_S3_WROOM_2_N32R16V.md` | Official dimensions, land pattern and STEP model available | Ready |
| Sensirion SHT40 | `SENSOR_SHT40.md` | Official package dimensions available | Ready; placement/airflow matters more than cosmetic model |
| TI charger / regulator / gauge ICs | `POWER_ICS.md` | Official TI package data available | Ready as accurate package blocks |
| Murata power inductors | `POWER_INDUCTORS.md` | Official family drawings/specs available | Ready |

## Rule

For mechanically significant parts:

1. Read `docs/BOM.md` first.
2. Read the relevant component card.
3. Use the linked manufacturer drawing / CAD as the primary source.
4. Never replace verified dimensions with old Blender placeholders.
5. Clearly label assumptions and unresolved dimensions.
6. If a component changes, update `docs/BOM.md` and its component card before modifying the master model.

Small ICs and ordinary passives do not need hero-level 3D modeling unless they become mechanical constraints.
