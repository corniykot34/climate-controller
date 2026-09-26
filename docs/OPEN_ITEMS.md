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

### Encoder / wheel stack

- **Current wheel bore does not provide positive rotational locking on the encoder D-shaft.**
  - Current shaft engagement in the modeled wheel region is **4.1 mm**.
  - Tip clearance is **0.8 mm**.
  - Engagement is mechanically plausible, but the current circular bore must later be replaced by a real D-shaft hub / retention solution.

- **Encoder bushing cannot clamp the current front cover.**
  - In the present geometry, the bushing terminates **3.4 mm behind the rear surface of the front cover**.
  - Nut and washer fit the bushing itself, but cannot reach / clamp the current front structure.
  - Front support / encoder mounting architecture must be redesigned later; do not fake it during component-modeling passes.

- **Encoder pin / PCB geometry is unresolved.**
  - Provisional rear-facing pins currently intersect the unperforated PCB through the full **1.6 mm PCB thickness**.
  - Final pin geometry and the real manufacturer footprint / board holes must be used during PCB design.

- **Encoder pins penetrate the current rear wall by 0.9 mm.**
  - This is a direct conflict in the current blockout.
  - Resolve only after the realistic PCB / enclosure architecture is being rebuilt.

- **Encoder body currently contacts the PCB mounting plane.**
  - Verify whether this contact matches the actual Bourns mounting arrangement when the real footprint / mounting scheme is implemented.

- **Encoder cosmetic / secondary mechanical details remain provisional.**
  - Flat depth, housing detail and exact pin layout are not yet manufacturer-verified in the Blender model.

- **Encoder push travel is currently feasible.**
  - Nominal **0.5 mm** travel is collision-free and leaves **0.5 mm wheel-to-cover clearance**.
  - At **0.8 mm** travel, modeled clearance is **0.2 mm**.
  - Keep this as a constraint when the front stack is later redesigned.

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
