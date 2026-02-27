# GluCINDa — Glucose: Coherent Import. Neat Data.

> **⚠ RESEARCH AND EDUCATION USE ONLY**
> This software does not have market approval and is intended exclusively for research and
> educational purposes. It is not intended for use in safety-critical systems or in any
> environment in which a software error could lead to damage or injury (e.g., for therapy
> or clinical decision-making purposes). This software is highly experimental and may
> contain errors. It is provided without any warranty (other than copyright as stated in
> Article 6 of the EUPL) and use of the software is entirely at your own risk. There is no
> obligation to provide updates, maintenance, or support.

---

## Overview

GluCINDa is a manufacturer-agnostic continuous glucose monitoring (CGM) data ingestion
layer designed for research applications. It provides automated parsing, normalization,
and structured export of raw CGM data exports across heterogeneous device manufacturers
and file formats. GluCINDa does not perform glucose analysis; it produces clean,
and traceable output suitable for downstream processing and statistical analysis.

Key design principles:

- **Manufacturer-agnostic**: no hardcoded dependencies on any single CGM device or
  export format
- **Full traceability**: all transformations are documented; silent data loss is not
  permitted
- **Reproducible and deterministic**: identical inputs produce identical outputs
- **Stable output schema**: downstream analysis pipelines are not broken by upstream
  format changes
- **Optimized for real-world data**: handles messy, multi-center, and heterogeneous
  exports

---

## Authors and Contributors

Software created by and written under the lead of **Petra M. Baumann**
(Medical University of Graz).

Contributors (by order of appearance):
- A. Grebien

---

## Installation

<!-- ============================================================ -->
<!-- TODO: Replace this section with your existing installation   -->
<!-- content from the GitHub README.                              -->
<!-- ============================================================ -->

Requirements and installation instructions to be documented here. Include Python version
requirements, dependency installation (e.g., `pip install -r requirements.txt`), and any
environment setup steps.

---

## Usage

<!-- ============================================================ -->
<!-- TODO: Replace this section with your existing usage/tutorial -->
<!-- content from the GitHub README.                              -->
<!-- ============================================================ -->

Usage instructions and tutorial content to be documented here. Include basic invocation,
input format expectations, output schema description, and example workflows.

---

## Citation
<!-- ============================================================ -->
<!-- TODO: Update Citation                                       -->
<!--                                                              -->
<!-- ============================================================ -->

When using GluCINDa in your project, please cite:

> PM Baumann, C Buhlheller, A Grebien, C Taucher, F Posch, L Bally, and JK Mader.
> **GluCINDa (Glucose: Coherent Import. Neat Data.) An Open-Source Tool for the Consolidation of
> Continuous Glucose Monitoring Data for Research.** *Proceedings of ABCD 2024*, August 2024.
> URL: http://12.3456/789101112 — DOI: 12.3456/789101112

---

## License

GluCINDa is licensed under the terms of the **European Union Public Licence v. 1.2
(EUPL-1.2)**.

You should have received a copy of the EUPL in a separate `LICENSE` file along with
GluCINDa. If not, see <https://eupl.eu/1.2/en/>.

The EUPL is internationally recognized and written in legally neutral terms, ensuring
broad applicability beyond the European Union. It is compatible with many widely used
open-source licenses, facilitating integration of GluCINDa into international projects.

**Copyright © 2025 Medical University of Graz. All rights reserved.**

---

## Third-Party Libraries

A list of third-party tools, modules, and libraries used in connection with GluCINDa,
together with their respective licenses, is provided in the [`NOTICE`](NOTICE) file.

---

## Export Control

The software (including all related documentation) shall be used and communicated in
compliance with all applicable export control laws. Use by or communication to
persons or countries restricted by regulatory authorities (according to applicable
classification and intended use) is strictly prohibited.
