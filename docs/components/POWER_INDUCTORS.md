# Power Inductors — Mechanical Reference

## TPS63900 inductors ×2

**Selected part:** Murata **DFE252012F-2R2M=P2**  
**Manufacturer source:** https://www.murata.com/~/media/webrenewal/products/inductor/chip/tokoproducts/wirewoundmetalalloychiptype/m_dfe252012f.ashx

- Inductance: **2.2 µH ±20%**
- Size: **2.5 ±0.2 × 2.0 ±0.2 × 1.2 mm max**
- Saturation-current rating listed by Murata: about **3.3 A**
- Temperature-rise current rating: about **2.3 A**
- Shielded metal-alloy type.

Use one for each TPS63900.

## TPS63700 inductor

**Selected part:** Murata **DFE252012F-4R7M=P2**  
**Manufacturer source:** same DFE252012F family datasheet.

- Inductance: **4.7 µH ±20%**
- Size: **2.5 ±0.2 × 2.0 ±0.2 × 1.2 mm max**
- Saturation-current rating listed by Murata: about **2.1 A**
- Temperature-rise current rating: about **1.5 A**
- Shielded metal-alloy type.

The TPS63700 has a typical 1 A switch-current limit, so this inductor has appropriate current headroom for the present concept.

## Modeling rule

These are among the tallest discrete power parts on the PCB and should be represented as real 2.5 × 2.0 × 1.2 mm bodies rather than generic cubes.
