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
