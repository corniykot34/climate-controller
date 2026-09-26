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

## How we know an item is ready to resolve

Do not rely on intuition or on a vague project stage.

Every active open item must carry these fields:

- **Resolve when:** the concrete condition that makes the item actionable.
- **Blocked by:** the dependency that must exist first.
- **Resolve in:** the artifact where the fix belongs (component model / PCB / enclosure / firmware / prototype).
- **Verification:** the measurable check that proves the item is actually closed.

Example:

> **Encoder bushing cannot clamp the current front cover**
> - Resolve when: the front-stack architecture and encoder mounting method are being designed.
> - Blocked by: realistic encoder geometry + front-cover stack.
> - Resolve in: enclosure / midframe geometry.
> - Verification: bushing, washer and nut clamp the support correctly while preserving required push travel and wheel clearance.

An item is ready to resolve only when all information in **Blocked by** is available and the project is currently editing the artifact named in **Resolve in**.

If those conditions are not met, the item stays open.

---

## Resolution workflow

This file is not a parking lot.

Every open item must have a clear stage when it is revisited and then either:
- **RESOLVED** — fix implemented and verified in the model / PCB / enclosure;
- **SUPERSEDED** — no longer relevant because the architecture changed;
- **ACCEPTED RISK** — intentionally kept with an explicit reason;
- **BLOCKED** — cannot be resolved until a named dependency is available.

### Review gates

Open items must be reviewed at these project gates:

1. **After realistic component modeling**
   - resolve component-model inaccuracies;
   - confirm which packaging conflicts are real.

2. **Before PCB layout freeze**
   - resolve land patterns, holes, connector footprints, antenna keepout, power-zone placement, sensor thermal isolation, and FPC connector issues.

3. **Before enclosure geometry freeze**
   - resolve wall clearances, battery retention/swelling allowance, USB-C cutout, encoder mounting stack, display/front-cover stack, airflow path, and wall-mount architecture.

4. **Before prototype release**
   - review every remaining active item;
   - nothing may remain silently open.

When an item is resolved, move it from **Active open items** to **Closed items** with:
- resolution date;
- what changed;
- where it was changed;
- verification result.

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
  - Exact PCM, wire exit, lead length, connector, seam construction and retention remain unresolved.
  - Current Blender/mechanical work uses the conservative project safety envelope, not a claimed production pack.

- **Current AS405070 safety-envelope side clearance is below target.**
  - Modeled safety envelope: **72.5 × 50.5 × 5.0 mm**.
  - Minimum sidewall clearance: **0.25 mm**.
  - Project target: **0.50 mm**.
  - This is geometrically non-colliding but not yet acceptable as a production clearance.
  - Resolve during enclosure / battery-retention redesign, not during component-modeling passes.

- **Current battery clearances otherwise remain non-colliding.**
  - Safety-envelope to PCB: **7.75 mm**.
  - Safety-envelope to rear wall: **1.30 mm**.
  - Physical pouch rear clearance: **1.80 mm**.
  - Forward Z space over pouch footprint: at least **10.05 mm**.
  - AMOLED clearance: **9.55 mm**.
  - FPC clearance: **3.70 mm**.
  - Encoder clearance: **16.35 mm**.
  - USB-C clearance: **49.52 mm**.

- **Battery-to-ESP32 RF spacing must be re-evaluated after final RF / PCB layout.**
  - Physical pouch to antenna: approximately **8.04 mm**.
  - Safety envelope to modeled antenna keepout: **7.75 mm**.
  - Current spacing is non-colliding but does not by itself establish RF compliance.

- **Tab / lead exit remains provisional.**
  - Current model reserves a nonphysical **1.25 mm short-edge strip** inside the project envelope.
  - Finished-pack suitability is not established.

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

### USB-C

- **USB4105 PCB mounting features are not yet implemented in the PCB.**
  - SMT tails currently meet the PCB top plane plausibly.
  - Shell stakes penetrate **0.95 mm** into the currently unperforated **1.6 mm PCB**.
  - Locating pegs penetrate **0.60 mm** into the unperforated PCB.
  - Final PCB must add the manufacturer-defined pads / through-holes / locating holes.

- **USB4105 shell-stake production suffix is still unresolved.**
  - Current Blender model uses a provisional stake length.
  - Provisional stakes currently stop **0.65 mm above the PCB underside**.
  - Freeze the exact USB4105 suffix before final PCB release.

- **USB-C enclosure cutout is intentionally deferred.**
  - Current mating face is recessed **0.50 mm** behind the exterior surface.
  - Minimum shell-to-enclosure clearance is **0.30 mm**.
  - Plug-approach reference volume is currently unobstructed.
  - Final cutout / chamfer / tolerance stack must be designed during enclosure DFM.

- **USB-C rear-wall clearance is limited but currently non-colliding.**
  - Provisional shell stakes have **1.15 mm** rear-wall clearance.
  - Rear clearance to the charger / main-regulator reservation is approximately **7.74 mm diagonally**.

- **Some USB4105 internal geometry remains approximate.**
  - Undimensioned internal shell / insulator / contact details and the plug-approach allowance are not production geometry.
  - Use the manufacturer drawing as the source of truth where dimensions are available.

### ESP32-S3-WROOM-2

- **RF compliance is not established for the current ESP32 placement.**
  - The module antenna faces the PCB edge but does **not** overhang the base PCB.
  - Current main PCB remains directly beneath the full modeled **18 × 6 mm antenna footprint**.
  - Espressif recommends placing the module PCB antenna outside the base board when possible; if that is not possible, the base board should be cut away below and beside the antenna to provide clearance.
  - Current antenna-to-battery clearance: **7.75 mm**.
  - Current antenna-to-enclosure-sidewall clearance: **1.50 mm**.
  - Final RF layout must be checked against Espressif's module-placement guidance and later validated on hardware.

- **ESP32 host-board antenna keepout is not yet implemented.**
  - Underlying host-board copper / ground / traces beneath the antenna region remain unresolved.
  - The current PCB blockout should not be interpreted as a valid RF layout.

- **ESP32 host land pattern and solder-joint geometry are unresolved.**
  - Castellated pads are represented mechanically, but the final manufacturer land pattern has not yet been implemented on the main PCB.

- **ESP32 shield cosmetic details remain provisional.**
  - Shield sheet thickness and plating detail are not mechanically critical and were not frozen.

- **Existing Blender battery does not match the current BOM battery.**
  - This is expected because the battery replacement pass has not yet been performed.
  - Replace the old battery geometry with the AS405070 baseline before any final antenna / packaging conclusion is made.

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
