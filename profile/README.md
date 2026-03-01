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
  export structure
- **Full traceability**: all transformations are documented; silent data loss is not
  permitted
- **Reproducible and deterministic**: identical inputs produce identical outputs
- **Stable output schema**: downstream analysis pipelines are not broken by upstream
  format changes
- **Optimized for real-world data**: handles heterogeneous CGM exports from multiple
  manufacturers and download platforms (Validated: Abbott/LibreView, Dexcom/Clarity, Medtronic/CareLink,
  iCan, Glooko. Provisional: Sibionics, Tandem)

---

## Contributors

Software created and written by:
- Petra M. Baumann (MUG)
- Alexander Grebien (MUG)

Acknowledgments: 
- Christian Taucher (MUG)
- Florian Posch (MUG)
- Lia Bally (INS)
- Julia Mader (MUG)

MUG: Medical University of Graz, Austria

INS: Inselspital Bern, Switzerland

---

## Installation

Download the latest `.whl` file from [GitHub Releases](https://github.com/your-org/glucinda/releases) and install with:
```bash
pip install glucinda-1.0.0-py3-none-any.whl
```

Then launch with 
```bash
glucinda
```


---

## Usage

After launching the GUI, you are in Simple Mode. Select the directory containing the input files, accept the suggested or provide an empty output directory
and press "Run". Switching to Advanced Mode allows for some customization of the documenation and outputs. 

---

## Output Schema

GluCINDa produces a semicolon-delimited CSV containing all extracted CGM data with the following columns: 

| Column | Description |
|--------|-------------|
| `sid` | Subject identifier, derived from the input file name. |
| `date` | Date of measurement (`YYYY/mm/dd`). |
| `time` | Time of measurement (`HH:MM:SS`). |
| `value_num` | Numeric CGM value. Empty if the source value is non-numeric. |
| `unit` | Unit of measurement as it appears in the source column header (e.g. `mg/dl`, `mmol/l`); `undefined` if absent. |
| `value_str` | Non-numeric CGM value (e.g. `High`, `Low`). Empty if the source value is numeric. |
| `record_type` | CGM record type code distinguishing measurement subtypes (LibreView only). |
| `record_type_source_column` | Source column for `record_type` (LibreView only). |
| `manufacturer_assumed` | CGM device manufacturer inferred from the input file structure. |
| `device_id` | Sensor or transmitter identifier from the input file (LibreView, Clarity, Glooko). |
| `device_id_source_column` | Source column for `device_id` (LibreView, Clarity, Glooko). |
| `sequence` | Row-level sequence number as provided by the manufacturer (Clarity, CareLink, iCan). |
| `sequence_source_column` | Source column for `sequence` (Clarity, CareLink, iCan). |
| `download_source_assumed` | Download platform inferred from the input file structure. |
| `source_column` | Column name in the input file from which `value_num` or `value_str` was extracted. |
| `source_file` | Input file name (and sheet name for XLS/X files). |
| `notice` | Parsing-related warnings. Empty if no issues were detected. |
| `further_raw_data_json` | Verbatim source values stored as JSON for full transparency. |

For full details including data types, controlled vocabularies, and transformation notes, see [DATA_DICTIONARY.md](https://github.com/GluCINDa/glucinda-release/DATA_DICTIONARY.md).

---

## Citation
A manuscript describing GluCINDa is currently under review. In the meantime, please cite 
the software using the "Cite this repository" button on the [GluCINDa release repository](https://github.com/GluCINDa/glucinda-release).

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
