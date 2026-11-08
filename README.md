# NYC Pile Calc — 2022 Edition

Axial capacity checks for a single driven steel H-pile or pipe pile, following the 2022 New York City Building Code (Chapter 18), with FHWA static analysis methods for soil-bearing piles.

It is a single static page (`index.html`) with no build step and no server.

## What it checks

**Materials & inputs**
- Steel H-piles (AISC HP shapes or a custom section), and open-end or closed-end pipe piles, which can be concrete filled with optional reinforcing bars
- Service, transient, downdrag and uplift loads (ASD)
- Up to six soil layers above rock, with the pile tip on rock (Class 1a–1c), soft rock (Class 1d) or soil
- Corrosivity: lab results (resistivity, pH, sulfate, chloride) and site conditions, checked against NYC BC 1814.2.1 and 1810.2.12 and FHWA GEC-12 §6.12, plus the protection method
- Scaled cross section and soil profile

**Geotechnical**
- Allowable capacity from one of three sources:
  - the Table 1810.4.1.3 maximum, confirmed by load test
  - a static analysis
  - a load test result
- Static analysis per FHWA GEC-12:
  - granular layers: Nordlund, effective stress (β) or Meyerhof SPT, compared side by side
  - cohesive layers: α (Tomlinson) or β
- 40-ton limit without load tests (1810.3.1), factor of safety 2 in compression and 3 in uplift

**Structural**
- Allowable stresses from Table 1810.8, with the higher 0.5 Fy steel stress where 1810.4.1.5.1 justifies it
- Size requirements from 1811.7 for H-piles and pipe piles
- Steel area reduced only when sacrificial corrosion loss is selected

**Driving & testing**
- Minimum driving resistance from Table 1811.3(a), interpolated, for loads up to 40 tons
- Number of load tests (1810.4), test load, hold time and acceptance settlement

**Output**
- Saved designs and templates
- Calculation package exported as a PDF, with an optional logo

## Limitations

This tool checks axial capacity of a single pile only. Lateral capacity, bending, buckling, splices and group effects are not checked. Static analysis is an estimate; allowable loads above 40 tons must be confirmed by load tests. Code tables were transcribed from the 2022 NYC BC and FHWA chart values were digitized from the FHWA DRIVEN program manual. Verify all values against current references and the project geotechnical report. Results must be reviewed by a licensed professional engineer.

## Hosting on GitHub Pages

1. Create a new repository and add `index.html`, `README.md` and `.nojekyll` at its root.
2. In the repository, open **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, and save.
4. The site is published at `https://<your-user>.github.io/<repo-name>/` within a minute or two.

To run it locally, open `index.html` in a browser.

## Data and privacy

- Inputs, saved designs and the logo are stored in the browser's local storage, on that device only. Nothing is sent to a server.
- Use **Saved designs → Back up designs** to save a `.json` file, and **Restore backup** to load it on another browser or device.
- Clearing site data in the browser deletes saved designs, so keep backups.

## Dependencies

Loaded from public CDNs at run time:
- [jsPDF](https://github.com/parallax/jsPDF) 2.5.1 and [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable) 3.8.2 (cdnjs), for PDF export only
- Archivo and JetBrains Mono fonts (Google Fonts)

The calculations need no network access. PDF export needs to reach cdnjs, and without Google Fonts the page falls back to system fonts.

## References

- [2022 NYC Building Code, Chapter 18](https://www.nyc.gov/assets/buildings/codes-pdf/cons_codes_2022/2022BC_Chapter18_SoilsFoundationsWBwm.pdf)
- [FHWA GEC-12, Design and Construction of Driven Pile Foundations (FHWA-NHI-16-009)](https://www.fhwa.dot.gov/engineering/geotech/pubs/gec12/nhi16009_v1.pdf)
- [FHWA DRIVEN program manual (FHWA-SA-98-074)](https://www.govinfo.gov/content/pkg/GOVPUB-TD2-PURL-gpo117122/pdf/GOVPUB-TD2-PURL-gpo117122.pdf)
