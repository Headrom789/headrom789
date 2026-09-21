# [Project Name / Assembly Title]

![Hero Render](media/hero-render.png)
*Interactive 3D preview: [Inspect model in browser via GitHub 3D Viewer](cad/stl/complete_assembly.stl) or [Open Interactive Web Viewer](https://autode.sk/your-link)*

---

## 1. Project Overview

Provide a concise 2–4 sentence summary of the assembly, its intended operating environment, and the core problem it solves. 

* **Primary Function:** [e.g., Modular 3-axis mounting bracket for machine automation]
* **Design Type:** [e.g., Sheet metal weldment / Injection molded enclosure / Multi-part precision print]
* **Target Manufacturing Process:** [e.g., FDM/SLA 3D Printing, CNC Milling, 5052-H32 Sheet Bending]
* **Native CAD Platform:** [e.g., Autodesk Fusion 360 / SolidWorks 2026]

---

## 2. Design Constraints & Engineering Requirements

| Metric / Parameter | Target Specification | Achieved / Verified | Notes |
| :--- | :--- | :--- | :--- |
| **Max Envelope** | 150 × 100 × 75 mm | 142 × 95 × 68 mm | Clearance verified against frame |
| **Load Capacity** | 15 kg static load | 22 kg verified | FEA factor of safety: 2.1 |
| **Fastener Standard** | Metric (M3 / M4) | M3 Button Head / M4 SHCS | Fastened with heat-set brass inserts |
| **Deflection Limit** | < 0.25 mm at 100 N | 0.12 mm simulated | Ribbing added along primary bending axis |

---

## 3. Visual Breakdowns & Kinematics

### Exploded View & Sub-Assemblies
![Exploded Assembly View](media/exploded-view.png)

### Mechanism Motion / Clearance Check
![Mechanism Movement GIF](media/linkage-motion.gif)
> *Kinematic notes: Linkage operates with 55° stroke. Minimum clearance between dynamic linkage and exterior housing is 2.5 mm throughout full range of travel.*

---

## 4. Design for Manufacturing (DFM) & Tolerances

* **Draft Angles & Wall Thickness:** Uniform wall thickness of `2.4 mm` maintained across structural shells; `1.5°` draft angle applied to vertical pull faces.
* **Fitment & Clearances:**
  * **Press-Fit Bearings (608-2RS):** Bore toleranced at `+0.00 / -0.02 mm`.
  * **Interlocking Sliding Guides:** Designed with `0.20 mm` diametral clearance to compensate for print swell/machining runout.
* **Fastener Interfaces:** Counterbores sized according to ISO 4762 with `0.4 mm` radial clearance for tool access.

---

## 5. Bill of Materials (BOM)

| Item # | Part Name | Qty | Material / Process | Source / Part # |
| :---: | :--- | :---: | :--- | :--- |
| **01** | Lower Base Bracket | 1 | 6061-T6 Aluminum / CNC Machined | Custom (`cad/step/01_base_bracket.step`) |
| **02** | Top Mounting Arm | 1 | PETG / FDM 0.2 mm Layer Height | Custom (`cad/stl/02_mounting_arm.stl`) |
| **03** | M3×10mm SHCS | 4 | 304 Stainless Steel | McMaster-Carr `91292A113` |
| **04** | M3 Heat-Set Insert | 4 | Brass (Tapered, 4.0 mm OD) | McMaster-Carr `94180A333` |
| **05** | Deep Groove Ball Bearing | 2 | Chromium Steel (8×22×7 mm) | 608-2RS |

---

## 6. Fabrication & Assembly Drawings

Dimensioned 2D engineering drawings with tolerance standards are located in the [`docs/drawings/`](docs/drawings/) directory.

![Drawing Sample](media/drawing-preview.png)
*Download the full production drawing package: [drawing_package_rev_b.pdf](docs/drawings/assembly_drawing.pdf)*

---

## 7. File Structure & CAD Assets

```text
├── cad/
│   ├── native/             # Parametric CAD models (.f3d, .sldprt, .sldasm)
│   ├── step/               # Standardized STEP files (AP214 / AP242)
│   └── stl/                # Mesh files for inspection and 3D printing
├── docs/
│   ├── drawings/           # 2D PDF engineering drawings
│   └── calculations/       # FEA reports and tolerance stack calculations
├── media/                  # Images, turntable GIFs, and inspection photos
└── README.md
