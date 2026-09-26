# Component Mechanical References

This directory contains the project’s mechanical reference cards for components that materially affect enclosure geometry, PCB placement, access openings, keepouts, thermal zoning, or assembly.

## Current priority set

| Component | Card | Drawing status | Modeling status |
|---|---|---|---|
| Densitron DMA024QZHXNT0-1A AMOLED | `DISPLAY_DMA024QZHXNT0-1A.md` | Official mechanical drawing available | Ready for realistic model; FPC bend radius remains provisional |
| Bourns PEC11H-4115F-S0020 encoder | `ENCODER_PEC11H-4115F-S0020.md` | Official dimensional drawing available | Ready for realistic model |
| GCT USB4105 USB-C receptacle | `USB_C_USB4105.md` | Official drawing + footprint available | Ready for realistic model; exact shell-stake suffix still VERIFY |
| A&S Power AS405070 battery | `BATTERY_AS405070.md` | Published cell dimensions available; exact pack drawing not yet obtained | Model only as conservative pack envelope until exact pack variant is frozen |

## Rule

For mechanically significant parts:

1. Read the component card first.
2. Use the linked manufacturer drawing as the primary source.
3. Never replace verified dimensions with old Blender placeholders.
4. Clearly label assumptions and unresolved dimensions.
5. If a component changes, update `docs/BOM.md` and its component card before modifying the master model.

Small ICs and ordinary passives do not need individual 3D drawings unless they become mechanical constraints.
