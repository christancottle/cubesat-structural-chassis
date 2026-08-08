## CubeSat Structural Chassis

A CDS-compliant 1U CubeSat structural chassis, designed and 
structurally verified in SolidWorks.

## Overview
Brief 2-3 sentences: what it is, why you built it, what it 
demonstrates (CAD modeling + FEA verification workflow).

## Design
- 100 x 100 x 100 mm envelope (1U CubeSat standard)
- 8.5 mm rails per CalPoly CubeSat Design Specification, 1 mm 
  corner fillets
- Internal mounting deck with 4x M3 clearance holes
- Material: 6061-T6 aluminum

![Isometric view](images/isometric_render.png)
![Section view](images/section_view.png)

## Structural Analysis
- Load case: 10g quasi-static axial acceleration (launch condition)
- Fixture: outer rail-contact faces fixed (P-POD dispenser simplification)
- Result: max stress 157 kPa vs. 275 MPa yield → safety factor ~1,750x

| Design | Wall thickness | Max stress | Safety factor |
|---|---|---|---|
| Baseline | 2.5 mm | 158.2 kPa | 1,738x |
| Final | 1.5 mm | 157.4 kPa | 1,747x |

**Key finding:** wall thickness isn't the limiting factor — the 
mounting deck governs peak stress, so wall mass was reduced with 
negligible structural impact.

## Files
- `CAD/` — SolidWorks part + STEP export
- `drawings/` — dimensioned engineering drawing
- `analysis/` — FEA screenshots and results summary

## Future work
- Split-line rail contact faces for more accurate fixture modeling
- Further mass optimization (relieved/L-shaped rails)
- Additional load cases (lateral, vibration)

## Tools
SolidWorks 2024/2025, SolidWorks Simulation
