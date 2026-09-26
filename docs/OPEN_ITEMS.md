# Environmental Controller — Open Items

**Purpose:** single source of truth for anything intentionally deferred for later review.

Whenever a task reveals a detail that is:
- unresolved,
- provisional,
- too tight for production confidence,
- intentionally postponed,
- dependent on a later PCB / enclosure / prototype stage,

add it here immediately.

Do not rely on chat history for deferred engineering issues.

---

## Active open items

### Display / FPC

- **FPC-to-PCB clearance is only 0.15 mm.**
  - No collision was detected in the current Blender model.
  - This is too tight to treat as production-safe.
  - Revisit during PCB placement / connector definition.

- **Display connector fit is unresolved.**
  - Current model uses a provisional connector reserve only.
  - Exact connector / interface implementation must be selected before final PCB and enclosure design.

- **Display FPC exit geometry remains provisional.**
  - Current route is mechanically plausible.
  - Minimum modeled inner bend radius: **3.15 mm**.
  - Project assumption: **R = 3.0 mm minimum**, not manufacturer-certified.

- **Display FPC width and thickness remain provisional.**
  - Replace with manufacturer-confirmed geometry if/when exact data becomes available.

### Battery

- **Exact finished AS405070 pack variant is not frozen.**
  - Cell baseline: 3.7 V, 1700 mAh, nominal cell size about 4 × 50 × 70 mm.
  - Exact PCM, wire exit, lead length and connector remain unresolved.
  - Current Blender/mechanical work must continue to use the conservative project safety envelope, not pretend the finished pack is fully defined.

### Touch

- **Broad front capacitive-touch electrode / FPC architecture is not frozen.**
  - Full free front-glass area is intended to be touch-capable after wake.
  - Final electrode geometry, routing and controller implementation require prototype validation.

### PCB / enclosure

- **Main PCB outline and component placement are still provisional.**
  - Current approximate PCB: 70 × 48.5 × 1.6 mm.
  - Final PCB must be rebuilt around realistic component geometry.

- **Current enclosure dimensions are provisional packaging results only.**
  - Current blockout: approximately 76 × 120 × 20 mm body, ~27 mm including wheel.
  - Must be revalidated after realistic component replacement.

- **Wall mounting architecture is intentionally deferred.**
  - Do not introduce wall-mount hardware until the internal mechanical architecture is stable.

### Sensor / airflow

- **SHT40 ambient-air path is not finalized.**
  - Sensor remains intended for a thermally isolated edge/tongue region.
  - Final vent / airflow geometry must be designed with the enclosure, not during component blockout.

---

## Closed items

Move items here only after they are actually resolved and reflected in the relevant BOM/component card/model.

---

## Rule for future Blender/MCP work

If a Blender/MCP task reports a new unresolved mechanical issue, tight clearance, provisional dimension, or deferred design decision:

1. Do **not** solve it unless that task explicitly includes solving it.
2. Add it to this file immediately.
3. Reference this file before later packaging, PCB, or enclosure work.
