# Approved Manufacturer Sources

This directory is the **source whitelist** for the Environmental Controller project.

## Why these files are links, not mirrored PDFs

Manufacturer documentation is copyrighted, and at least one selected source (Densitron) explicitly prohibits unauthorized duplication of its specification. Therefore the repository stores:

- exact approved manufacturer URLs;
- project-extracted mechanical facts in `docs/components/`;
- status of each source;
- direct CAD links where the manufacturer publishes them.

Do **not** mirror manufacturer PDFs/CAD into a public repository unless the manufacturer's license explicitly permits redistribution.

For modeling/research, follow only the sources listed here. Do not perform general web search.

---

## Display — Densitron DMA024QZHXNT0-1A

**Status:** SELECTED

Official product specification / mechanical drawing:

https://www.densitron.com/files/library/files/products/202505/Product%20Spec_DMA024QZHXNT0-1A_v0.1.pdf

Notes:
- Mechanical drawing is in section 2.2.
- Source document is marked proprietary/confidential and prohibits unauthorized duplication.
- Repository therefore stores only the approved URL and our extracted factual dimensions.

Project card:

`docs/components/DISPLAY_DMA024QZHXNT0-1A.md`

---

## Rotary encoder — Bourns PEC11H-4115F-S0020

**Status:** SELECTED

Official datasheet / mechanical drawing:

https://www.bourns.com/docs/product-datasheets/pec11h.pdf

Project card:

`docs/components/ENCODER_PEC11H-4115F-S0020.md`

---

## USB-C — GCT USB4105

**Status:** SELECTED

Official product page:

https://gct.co/connector/usb4105

Official product drawing:

https://gct.co/files/drawings/usb4105.pdf

Official product specification:

https://gct.co/files/specs/usb4105-spec.pdf

Official GCT 3D CAD generator:

https://gct-embedded.partcommunity.com/3d-cad-models/?info=gct%2Fusb_connector%2Ftype_c%2Ftype_c%2Fhorizontal%2Fusb4105%2Fusb4105.prj

Notes:
- Exact shell-stake suffix is still not production-frozen.
- Do not substitute a distributor/community CAD file when the GCT source is available.

Project card:

`docs/components/USB_C_USB4105.md`

---

## MCU module — Espressif ESP32-S3-WROOM-2-N32R16V

**Status:** SELECTED

Official datasheet:

https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-2_datasheet_en.pdf

Official STEP model:

https://www.espressif.com/sites/default/files/3dmodel/ESP32-S3-WROOM-2.STEP

Official module product listing:

https://www.espressif.com/en/products/modules/esp32-s3-wroom-2

Notes:
- Use the official STEP for mechanical reference when the modeling toolchain can consume it.
- Manufacturer land pattern and antenna placement rules override old placeholder geometry.

Project card:

`docs/components/ESP32_S3_WROOM_2_N32R16V.md`

---

## Temperature / humidity sensor — Sensirion SHT40

**Status:** SELECTED

Official product page:

https://sensirion.com/products/catalog/SHT40

Current official SHT4x datasheet (Version 7.3, June 2026):

https://sensirion.com/media/documents/33FD6951/6A7C10A0/HT_DS_Datasheet_SHT4x_V7.3.pdf

Notes:
- Sensirion datasheet also points to CAD resources for the SHT40 family.
- For enclosure work, sensor placement / thermal isolation / airflow are more important than cosmetic chip detail.

Project card:

`docs/components/SENSOR_SHT40.md`

---

## Charger / power path — TI BQ25185

**Status:** SELECTED

Official product page:

https://www.ti.com/product/BQ25185

Official datasheet:

https://www.ti.com/lit/ds/symlink/bq25185.pdf

---

## Buck-boost regulators — TI TPS63900 ×2

**Status:** SELECTED

Official product page:

https://www.ti.com/product/TPS63900

Official datasheet:

https://www.ti.com/lit/ds/symlink/tps63900.pdf

---

## AMOLED negative-rail converter — TI TPS63700

**Status:** SELECTED

Official product page:

https://www.ti.com/product/TPS63700

Official datasheet:

https://www.ti.com/lit/ds/symlink/tps63700.pdf

---

## Battery fuel gauge — TI BQ27427

**Status:** SELECTED

Official product page:

https://www.ti.com/product/BQ27427

Official datasheet:

https://www.ti.com/lit/ds/symlink/bq27427.pdf

Project card for the TI IC group:

`docs/components/POWER_ICS.md`

---

## Power inductors — Murata DFE252012F family

**Status:** SELECTED

Selected:
- DFE252012F-2R2M=P2 ×2
- DFE252012F-4R7M=P2 ×1

Official Murata family datasheet / drawing:

https://www.murata.com/~/media/webrenewal/products/inductor/chip/tokoproducts/wirewoundmetalalloychiptype/m_dfe252012f.ashx

Project card:

`docs/components/POWER_INDUCTORS.md`

---

## Battery — A&S Power AS405070

**Status:** SELECTED BASELINE / EXACT FINISHED PACK VERIFY

Official manufacturer listing showing AS405070:

https://as-battery.com/index.php/3-subchannelproducts/65120-37V-55mah-lithium-polyme.html

Published data:
- 3.7 V
- 1700 mAh
- nominal cell class 4.0 × 50 × 70 mm
- UL1642 / CE / UN38.3 listed

Important:
- No exact finished-pack mechanical drawing with PCM / wire exit / connector has been approved.
- Do not invent those details.
- Continue to use the conservative project safety envelope until an exact pack SKU is frozen.

Project card:

`docs/components/BATTERY_AS405070.md`

---

# Access rule for Blender/Codex tasks

When project-source lookup is explicitly allowed:

1. Read `docs/BOM.md`.
2. Read the relevant `docs/components/*.md` card.
3. Read this whitelist.
4. Access **only** the exact manufacturer URLs listed here.
5. Do not perform general web search.
6. Do not substitute distributor, marketplace, forum, community CAD, or AI-generated dimensions for manufacturer data.
7. If an approved source cannot be accessed, STOP and report it.
8. All Blender geometry creation/editing must still be done through Blender MCP only.
