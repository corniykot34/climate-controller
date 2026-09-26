# Densitron DMA024QZHXNT0-1A — Mechanical Reference

**Role:** 2.4" colour AMOLED display  
**Project status:** SELECTED  
**Manufacturer source:** https://www.densitron.com/files/library/files/products/202505/Product%20Spec_DMA024QZHXNT0-1A_v0.1.pdf

## Verified mechanical data

- Overall panel: **38.72 × 51.56 × 0.90 mm** in native portrait orientation.
- Project orientation: **landscape**, therefore **51.56 × 38.72 × 0.90 mm**.
- Active area: **36.72 × 48.96 mm** native portrait.
- Project active area in landscape: **48.96 × 36.72 mm**.
- Surface treatment: glare, 6H.
- Driver IC: RM690B0.
- Interfaces: SPI / MCU / MIPI.

## Packaging rules

- Display sits behind the continuous glossy front cover.
- No exposed bezel/open rectangular hole in the exterior design.
- Current optical/adhesive allowance: **0.25 mm nominal**.
- Current flex bend assumption: **R = 3 mm**, clearly marked PROVISIONAL.
- Do not model a sharp FPC fold.
- Do not place rigid geometry inside the flex bend corridor.

## Still unresolved

- Exact FPC exit geometry must be modeled from the manufacturer mechanical drawing.
- Manufacturer does not state a numerical minimum bend radius in the current datasheet; the project's R=3 mm value is not a production claim.
- Final display connector / board-interface implementation remains to be frozen.

## Modeling instruction

For Blender/MCP, use the manufacturer panel envelope and drawing as the source of truth. Do not use the old breakout-board geometry.
