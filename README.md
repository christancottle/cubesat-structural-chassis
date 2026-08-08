# CubeSat Structural Chassis

A CDS-compliant 1U CubeSat structural chassis — modeled, dimensioned, and structurally verified in SolidWorks over a two-week summer project. This covers the load-bearing subsystem of a CubeSat: the rail/wall chassis and internal mounting deck, built to the CalPoly CubeSat Design Specification (CDS) and verified against a launch load case using SolidWorks Simulation.

## Overview

The goal of this project was to design a real, spec-compliant CubeSat structure from scratch and take it through a complete engineering workflow: parametric CAD modeling, structural finite element analysis (FEA), a design iteration based on analysis results, and formal engineering drawings. This isn't a full CubeSat (no electronics, solar panels, or payload) — it's a focused structures deliverable, similar to what a "structures" subteam on a real CubeSat program would own.

## Design

- **Envelope:** 100 x 100 x 100 mm (1U CubeSat standard)
- **Rails:** 8.5 mm width per the CalPoly CubeSat Design Specification (minimum contact width for the P-POD dispenser), with 1 mm minimum corner fillets
- **Walls:** 1.5 mm thick aluminum panels connecting the rail posts
- **Mounting deck:** internal plate offset from the base, sized to clear the rail posts, with 4x M3 clearance holes (3.2 mm) near the corners for payload mounting
- **Material:** 6061-T6 aluminum

![Isometric view](images/isometric_render.png)
![Section view](images/section_view.png)

*(Section view shows the stepped transition from the thick rail posts to the thin wall panels — this geometry is flush and invisible from the outside, since the outer surface must stay smooth for the dispenser.)*

## Structural Analysis

**Load case:** 10g quasi-static axial acceleration (98 m/s²), representing a typical launch load factor along the tube's long axis — the same direction the rails travel through the P-POD dispenser.

**Fixtures:** the four outer side faces of the tube were fixed, as a simplification of the real rail-to-dispenser contact (the rails are flush with the walls on the outside, so the true contact patch can't be isolated as a separate face without additional split-line work — noted here as a known simplification).

**Contact:** the mounting deck is bonded to the surrounding tube structure, representing a fastened/mounted connection.

**Result:** maximum von Mises stress of 157.4 kPa against a yield strength of 275 MPa for 6061-T6 aluminum — a safety factor of roughly 1,750x.

| Design iteration | Wall thickness | Max stress | Safety factor |
|---|---|---|---|
| Baseline | 2.5 mm | 158.2 kPa | ~1,738x |
| Final | 1.5 mm (+ corner fillets added) | 157.4 kPa | ~1,747x |

**Key finding:** reducing wall thickness by 40% had almost no effect on peak stress. The mounting deck, not the tube walls, governs the peak stress in this load case — meaning the wall thickness has room for further mass optimization without compromising structural margin.

## Repository Contents

```
CAD/          SolidWorks part file (.SLDPRT) and STEP export
drawings/     Dimensioned engineering drawing (PDF)
analysis/     FEA result screenshots and summary
images/       Renders used in this README
```

## Future Work

- Use split-line features to isolate the true rail contact area for a more accurate fixture definition
- Explore relieved/L-shaped rail geometry for further mass savings
- Add additional load cases (lateral acceleration, random vibration)
- Model fasteners/standoffs explicitly rather than using a bonded contact simplification

## Tools

SolidWorks 2024/2025 (CAD), SolidWorks Simulation (FEA)
