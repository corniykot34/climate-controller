# CC-001 — Component Definition & Packaging Study

**Revision:** A  
**Date:** 2026-09-23  
**Stage:** Step 1 / Component Definition  
**Status:** Preliminary / For Review

## Deliverable

The controlled Step 1 engineering package is:

`CC-001_Component_Definition_RevA.pdf`

The package contains:

1. document control and revision record;
2. component specification / BOM;
3. Blender component workbench / packaging study;
4. open-items and verification register;
5. primary-source traceability.

## Release status

Step 1 is accepted as a **component definition / packaging study** only.

It is **not a fit-critical mechanical release**. Final enclosure openings, mounting bosses, PCB holes, and connector cutouts must not be derived from components still marked VERIFY / UNVERIFIED.

## Open verification gates

- OI-01 — Adafruit OLED Product 938 mechanical drawing / active area / mounting holes
- OI-02 — exact Bourns PEC11R orderable variant
- OI-03 — final USB-C implementation and connector envelope
- OI-04 — exact Phoenix Contact terminal part
- OI-05 — ESP32 antenna placement / keep-out
- OI-06 — SHT31 airflow and thermal separation
- OI-07 — enclosure fastener/thread strategy

The PDF is the client-facing record for Step 1; `SPEC.md`, `BOM.md`, and `DECISIONS.md` remain the editable project source of truth.
