# Design Decision Log

## D-001 — Portfolio target

**Decision:** Build the project as a CAD Crowd portfolio/showcase piece aimed at product-development, enclosure, prototyping, DFM, and 3D-printing work.

**Reason:** The project should demonstrate broadly transferable product-development skills rather than a narrow decorative niche.

## D-002 — Primary modeling tool

**Decision:** Model primarily in Blender.

**Reason:** Blender is the established working tool for this project. The showcase should represent real capability rather than pretending the workflow is based on parametric CAD. Precision CAD/STEP work can be added if a specific deliverable requires it.

## D-003 — Product concept

**Decision:** Desktop temperature/humidity controller.

**Reason:** It provides a believable component-driven enclosure problem with display, controls, ventilation, PCB packaging, connectors, and assembly details without requiring complex mechanisms.

## D-004 — Enclosure fastening

**Decision:** Use four screws rather than snap fits for the first version.

**Reason:** Easier to model and validate well, straightforward to assemble/service, and useful for demonstrating bosses, standoffs, clearances, and real assembly logic.

## D-005 — Electronics scope

**Decision:** Use real existing components for packaging, but do not design a production electronic schematic/PCB in this portfolio phase.

**Reason:** The portfolio case is about product/enclosure development. Simplified component models are sufficient for spatial design, while real component dimensions keep the result credible.

## D-006 — Documentation authority

**Decision:** Manufacturer documentation is primary evidence; repository documentation is the working source of truth.

**Reason:** Prevents remembered/chat-derived dimensions from silently becoming engineering facts. Project-defined dimensions must be labeled explicitly.
