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

## Review cadence

The open-items file must be checked by the project lead / assistant at fixed workflow moments, not "when remembered":

1. **Before every new Blender/MCP prompt**
   - read `docs/OPEN_ITEMS.md`;
   - identify any item whose `Resolve when` condition has become true;
   - if one is actionable, resolve or explicitly schedule it before moving on.

2. **Immediately after every Blender/MCP result**
   - compare the report against existing open items;
   - add new issues;
   - update measurements/status on existing issues;
   - close any item that has actually been resolved and verified.

3. **Before any task that edits an artifact named in `Resolve in`**
   - for example, before PCB work, review all items whose `Resolve in` is PCB;
   - before enclosure work, review all enclosure items;
   - before prototype work, review all prototype-dependent items.

4. **At each formal review gate**
   - after realistic component modeling;
   - before PCB layout freeze;
   - before enclosure geometry freeze;
   - before prototype release.

The next task must not be generated from chat context alone; the current `OPEN_ITEMS.md` must be checked first.

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

- **Current battery clearances otherwise remain non-colliding.**
  - Safety-envelope to PCB: **7.25 mm**.
  - Safety-envelope to rear wall: **1.30 mm**.
  - Safety-envelope to left/right side walls: **0.50 mm each** after rear-shell redesign.
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

- **Encoder pins penetrate the current rear wall by 0.9 mm.**
  - This is a direct conflict in the current blockout.
  - Resolve only after the realistic PCB / enclosure architecture is being rebuilt.

- **Encoder cosmetic / secondary mechanical details remain provisional.**
  - Flat depth, housing detail and exact pin layout are not yet manufacturer-verified in the Blender model.

- **Encoder push travel is currently feasible.**
  - Nominal **0.5 mm** travel is collision-free and leaves **0.5 mm wheel-to-cover clearance**.
  - At **0.8 mm** travel, modeled clearance is **0.2 mm**.
  - Keep this as a constraint when the front stack is later redesigned.

### USB-C

- **USB4105 shell-stake production suffix is still unresolved.**
  - Current Blender model uses a provisional stake length.
  - Provisional stakes currently stop **0.65 mm above the PCB underside**.
  - Freeze the exact USB4105 suffix before final PCB release.

- **USB-C enclosure opening exists mechanically; production tolerance / DFM remains open.**
  - Current mating face is recessed **0.50 mm** behind the exterior surface.
  - Current opening: **15.60 × 7.18 mm**.
  - Connector-to-opening clearance is at least **1.90 mm**.
  - Plug-approach clearance is at least **0.30 mm** and currently unobstructed.
  - Final tolerance stack, manufacturing method and exact USB4105 stake variant remain unresolved.
  - **Resolve when:** enclosure DFM and connector production variant are frozen.
  - **Blocked by:** final USB4105 suffix + enclosure manufacturing process.
  - **Resolve in:** enclosure / DFM.
  - **Verification:** port opening, plug insertion and connector retention meet drawing tolerances on production-intent geometry.

- **USB-C rear-wall clearance is limited but currently non-colliding.**
  - Provisional shell stakes have **1.15 mm** rear-wall clearance.
  - Rear clearance to the charger / main-regulator reservation is approximately **7.74 mm diagonally**.

- **Some USB4105 internal geometry remains approximate.**
  - Undimensioned internal shell / insulator / contact details and the plug-approach allowance are not production geometry.
  - Use the manufacturer drawing as the source of truth where dimensions are available.

### ESP32-S3-WROOM-2

- **RF compliance is not established for the current ESP32 placement / housing.**
  - Host PCB cutaway beneath the antenna is now implemented mechanically.
  - Current antenna-to-battery safety-envelope clearance remains approximately **7.75 mm**.
  - Rear-shell redesign improved antenna-to-sidewall clearance to **2.00 mm** and rear clearance from antenna surface to **3.40 mm**.
  - The current housing still does not meet the conservative **15 mm** lateral recommendation used for this project; remaining lateral shortfall is **13.00 mm**.
  - Final RF layout / housing interaction must be validated against Espressif guidance and on hardware.
  - **Resolve when:** enclosure geometry and electrical PCB copper layout are both near-final.
  - **Blocked by:** final enclosure + final RF copper/ground layout.
  - **Resolve in:** PCB + enclosure + prototype.
  - **Verification:** manufacturer guidance is satisfied as far as geometry permits and RF performance is validated on prototype hardware.

- **ESP32 host-board antenna cutaway is implemented mechanically; copper / RF margin is not yet validated.**
  - The host PCB is now removed beneath the antenna with lateral cutback.
  - Final copper-to-edge margin, ground geometry and RF validation remain unresolved.
  - Housing RF clearance is still insufficient.
  - **Resolve when:** electrical PCB layout and enclosure RF clearance are being finalized.
  - **Blocked by:** final copper layout + enclosure geometry.
  - **Resolve in:** PCB + enclosure + prototype.
  - **Verification:** manufacturer placement/keepout guidance is met in board geometry and RF performance is validated on hardware.

- **ESP32 host land pattern and solder-joint geometry are unresolved.**
  - Castellated pads are represented mechanically, but the final manufacturer land pattern has not yet been implemented on the main PCB.

- **ESP32 shield cosmetic details remain provisional.**
  - Shield sheet thickness and plating detail are not mechanically critical and were not frozen.

### Power stage / PCB power layout

- **Power-stage package geometry is now realistic, but placement is still provisional.**
  - BQ25185, TPS63900 ×2, TPS63700, BQ27427 and three Murata DFE252012F inductors fit in the current reserved area with no physical collisions.
  - Maximum component height above PCB in this group: **1.20 mm**.
  - Minimum clearance to battery safety envelope: **18.25 mm**.
  - Minimum clearance to SHT40: **44.35 mm**.
  - Minimum clearance to ESP32: **25.06 mm**.
  - Minimum clearance to rear enclosure wall: **2.10 mm**.
  - Minimum clearance to AMOLED / FPC: **8.75 mm**.
  - No power component is currently placed directly behind the battery footprint.

- **Converter passive layout is not validated.**
  - Current power-zone reference objects only reserve conceptual area for capacitors / feedback / support passives.
  - Exact capacitor values, footprints, current-loop placement, thermal vias, copper areas and solder allowances remain unresolved.
  - **Resolve when:** real PCB placement and routing begin.
  - **Blocked by:** PCB mechanical layout stage.
  - **Resolve in:** PCB.
  - **Verification:** selected ICs + inductors + required passives fit with manufacturer-recommended placement constraints and no conflict with other mechanical zones.

- **Power-stage thermal implementation is not validated.**
  - No copper pours, thermal vias or real board thermal path are modeled yet.
  - **Resolve when:** PCB copper / routing architecture is defined.
  - **Blocked by:** real PCB layout.
  - **Resolve in:** PCB.
  - **Verification:** charger / regulator thermal paths are implemented without coupling significant heat into the SHT40 sensing region or battery.

### PCB / enclosure

- **Main PCB mechanical outline is rebuilt; electrical layout remains provisional.**
  - Current mechanically rebuilt PCB: **70 × 50 × 1.6 mm**.
  - Mechanical holes, antenna cutaway and sensor tongue are implemented.
  - Production lands, copper, routing, tolerances and exact passive placement remain open for electrical PCB work.

- **Rear / side / bottom shell has been rebuilt; enclosure is not yet fully frozen.**
  - External body remains **76 × 120 × 20 mm**.
  - Rear / top / bottom wall thickness: **1.50 mm**.
  - Side walls: **1.25 mm**.
  - Local antenna relief: **1.00 mm**.
  - Current PCB-to-rear-wall clearance: **0.50 mm**.
  - PCB-to-sidewall clearance: **1.75 mm**.
  - Front stack, SHT40 vent, encoder support, wall mount and manufacturing details remain open.

- **Rear-shell manufacturing details are not frozen.**
  - Current rear shell is a connected manifold mesh with 1.50 mm rear/top/bottom walls, 1.25 mm side walls and 1.00 mm local antenna relief.
  - Draft, radii, seam strategy, assembly split, bosses / fasteners and production process are still unresolved.
  - **Resolve when:** enclosure architecture / assembly method is selected.
  - **Blocked by:** front-stack design + wall-mount / assembly decisions.
  - **Resolve in:** enclosure / DFM.
  - **Verification:** manufacturable shell with defined assembly split, retention method, draft/radii and no component interference.

- **Wall mounting architecture is intentionally deferred.**
  - Do not introduce wall-mount hardware until the internal mechanical architecture is stable.

### Sensor / airflow

- **SHT40 ambient-air path is not finalized.**
  - Current bottom-edge airflow route is geometrically plausible but blocked by the solid enclosure wall.
  - Sensor opening is immediately unobstructed internally.
  - Front cover clearance above sensing opening: **14.36 mm**.
  - Rear-wall clearance: **2.10 mm**.
  - Bottom-wall clearance: **2.75 mm**.
  - **Resolve when:** enclosure airflow / vent architecture is being designed.
  - **Blocked by:** realistic component set + enclosure architecture — now substantially available.
  - **Resolve in:** enclosure.
  - **Scheduled:** immediately after the front-stack / encoder-support pass so it remains a separate single-scope enclosure task.
  - **Verification:** open ambient-air path exists from exterior to sensing region without hard obstruction and without exposing the sensor to direct internal heat flow.

- **SHT40 thermal isolation is not yet verified.**
  - Current distance to battery: approximately **52.26 mm**; battery safety-envelope clearance **52.00 mm**.
  - Current distance to ESP32 / antenna region: approximately **26.25 mm**.
  - Current distance to nearest power zone: approximately **40.73 mm**.
  - These separations are favorable, but the current tongue remains continuously connected and approximately **6 mm wide**.
  - Sensirion guidance indicates no underlying copper except the pin pads, and central-pad soldering is discouraged.
  - **Resolve when:** the real PCB outline, copper strategy, and sensor tongue are being designed.
  - **Blocked by:** realistic PCB layout stage.
  - **Resolve in:** PCB.
  - **Verification:** sensor zone uses an appropriate copper/thermal-isolation strategy and prototype temperature error remains within the chosen system accuracy target.

- **SHT40 PCB isolation geometry is implemented mechanically but not thermally validated.**
  - Current concept uses a **2 mm neck** and **4 mm sensor tip**, with land and no-underlying-copper reference regions.
  - Electrical copper strategy and prototype thermal validation remain open.
  - **Resolve when:** real copper layout is defined and the first prototype is available.
  - **Blocked by:** electrical PCB layout + prototype.
  - **Resolve in:** PCB + prototype.
  - **Verification:** manufacturer land constraints are met and measured temperature error remains within the chosen system target.

- **SHT40 cavity-detail modeling remains provisional.**
  - Final package used: **1.5 × 1.5 × 0.54 mm** from Sensirion Figure 15.
  - Cavity depth / internal cosmetic detail was not treated as production geometry.
  - **Resolve when:** only if a higher-fidelity component model is actually required for documentation or interference analysis.
  - **Blocked by:** need for such fidelity.
  - **Resolve in:** component model.
  - **Verification:** revised geometry matches manufacturer source data.

---

## Closed items

### 2026-09-26 — Rear-shell USB / battery clearance conflicts — RESOLVED

- Rebuilt rear / side / bottom housing shell without changing external **76 × 120 × 20 mm** body size.
- Eliminated the previous approximately **1.0 mm USB-C / bottom-wall collision**.
- Added a real USB-C enclosure opening; plug approach remains unobstructed.
- Increased battery safety-envelope side clearance from **0.25 mm** to **0.50 mm** on both sides.
- Preserved **0.50 mm** PCB-to-rear-wall clearance.
- Remaining USB production tolerances, RF clearance and enclosure manufacturing details stay active above.

### 2026-09-26 — PCB mechanical conflict cleanup — RESOLVED

- Encoder pin locations were corrected to the Bourns push-switch drawing.
- Added PCB holes / support slots so encoder pins no longer penetrate solid PCB.
- Encoder body now seats without PCB penetration.
- Added USB4105 stake slots and locating holes; modeled stakes/pegs now clear the PCB.
- Added ESP32 antenna cutaway so host PCB no longer occupies the antenna keepout region.
- Added SHT40 narrowed tongue / isolation geometry.
- Remaining production lands, retention, copper, thermal and RF validation items stay active above.

### 2026-09-26 — Blender battery placeholder mismatch — RESOLVED

- Replaced the obsolete battery placeholder with the AS405070 baseline.
- Added physical pouch geometry at **70 × 50 × 4 mm**.
- Added the project safety envelope at **72.5 × 50.5 × 5.0 mm**.
- Verified that the physical pouch fits without collision.
- Remaining pack-specific and side-clearance issues stay active above.

Move items here only after they are actually resolved and reflected in the relevant BOM/component card/model.

---

## Rule for future Blender/MCP work

If a Blender/MCP task reports a new unresolved mechanical issue, tight clearance, provisional dimension, or deferred design decision:

1. Do **not** solve it unless that task explicitly includes solving it.
2. Add it to this file immediately.
3. Reference this file before later packaging, PCB, or enclosure work.
